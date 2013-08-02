# React
[Reactor](http://reactor.xenji.io) is a project that aims to be a searchable directory of React components. [React](http://facebook.github.io/react/docs/getting-started.html) is a Javascript framework, made by the people at facebook. 

# Reactor
[Reactor](http://reactor.xenji.io) is an attempt to collect reusable components all over the world. You can imagine it as something similar to packagist or the [bower](http://bower.io/) package browser. [Reactor](http://reactor.xenji.io) does not aim to replace any of those systems, but to make it easier to find components for your needs. [Reactor](http://reactor.xenji.io) only saves references to e.g. [bower](http://bower.io/) components or other repositories that contain the code.

## Your component here?
Now comes the easy part. Fork this repository, take a look at the example.json file. The example file contains all fields that will be stored in the elasticsearch that drives Reactor.

The indexer is triggered by the post receive hook, so your contribution will be visible shortly after the acceptance of the pull request.

### Example
Here is the content of the example.json with a few comments added to it.

The prefix `IDX` tells you, that this field is used for searching. `FILTER` indicates that this field and it's values are used to build filters in the future.

```json
{
	// IDX The url slug will be used for detail pages or direct links. This is not yet implemented, please add it anyway.
	"slug": "a-url-ready-slug-with-no-spaces-and-stuff",
	
	// IDX The name of your component. Imagine you want to find your component, what would you search for?
	"name": "A one line sentence or just a word you would expect in a headline.",

	// IDX Describe it as good as you can. This description is going into the search index.
	"desc": "A description that shows how cool your stuff is. ",

	// IDX Tag it. Please keep them all lowercase and without spaces. If you need more that two words for a tag, the description might be a better place.
	"tags": ["tags", "that", "we", "can", "use", "for", "filtering", "not", "more", "than", "five"],

	// Your email (invisible on the reactor homepage). If you do not want to share your mail, please just leave it empty. No fake mails, please.
	"author_email": "foo@example.com",
	
	// Your name (visible)
	"author_name": "Dr. Foobar",
	
	// Creation date, format: YYYY-MM-DD (as in MySQL). This field is not index, as it is just for historical research.
	"created": "2013-07-01",

	// IDX Date of the last update. At first, this will be equal to the creation date. The date is indexed for sorting purposes.
	"updated": "2013-07-01",
	
	// FILTER 
	"version_compat": ["0.4.x", "0.3.x"],
	
	// Where is your component hosted?
	"code": "http://where.ever.your.code.is.hosted",
	
	// Is there are homepage, blog article or tutorial?
	"homepage": "http://where.ever.your.homepageOrBlogOrWhatever.is.hosted",
	
	// FILTER Is there a bower package for it?
	"bower_compat": true,
	
	// The identifier for bower
	"bower" : "bower_reference",
	
	// FILTER Use one of ['plain', 'bootstrap2', 'bootstrap3', 'gumby', 'custom-included', 'custom'].
	// -> plain: You use no classes and ids
	// -> bootstrap2, bootstrap3, gumby: you use the styling from those frameworks.
	// -> custom-included: Custom styles, css files included
	// -> custom: Custom styles, no css files. You might want to avaoid this.
	"css_framework": "bootstrap"
}
```