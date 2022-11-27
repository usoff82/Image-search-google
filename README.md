# Google Image Search
> Search images using Google Custom Search 


## Installation

```
$ npm i image-search-google

```


## Usage

**Note**: You'll need to [set up your own Google Custom Search Engine](#set-up-google-custom-search-engine) to execute queries.

```js
const imageSearch = require('image-search-google');

const client = new imageSearch('CSE ID', 'API KEY');
const options = {page:1};
client.search('APJ Abdul kalam', options)
	.then(images => {
		/*
		[{
			'url': item.link,
            'thumbnail':item.image.thumbnailLink,
            'snippet':item.title,
            'context': item.image.contextLink
		}]
		 */
	})
	.catch(error => console.log(error););

// search for certain size
client.search('Mahatma Gandhi', {size: 'large'});

// search for certain type
client.search('Indira Gandhi', {type: 'face'});
```
## Set up Google Custom Search Engine

Please see Google's [API documentation](https://developers.google.com/custom-search/json-api/v1/reference/cse/list#parameters) for details on the option and response properties and their possible values. Note that the option names used here may differ slightly (e.g. no `img` prefix).

Google deprecated their public Google Images API, so to search for images you need to sign up for Google Custom Search Engine.
Here are the steps you need to do:

### 1. Create a Google Custom Search Engine

You can do this here: [https://cse.google.com/cse](https://cse.google.com/cse).

Do not specify any sites to search but instead use the "Restrict Pages using Schema.org Types" under the "Advanced options".
For the most inclusive set, use the Schema: `Thing`. Make a note of the CSE ID.

### 2. Enable Image Search

In your search engine settings, enable "Image search".

### 3. Set up a Google Custom Search Engine API

Register a new app and enable Google Custom Search Engine API here: [Google Developers Console](https://console.developers.google.com).
Make a note of the API key.


## API

### Client(cseId, apiKey)

#### cseId

Type: `string`

The [identifier](https://developers.google.com/custom-search/json-api/v1/overview#prerequisites) for a Custom Search Engine to use.

#### apiKey

Type: `string`

The [credentials](https://support.google.com/googleapi/answer/6158857?hl=en) for accessing Google's API.

### Instance

##### option

Type: `object`

The full description is [here](https://developers.google.com/custom-search/v1/reference/rest/v1/cse/list).

## License

Isc © 