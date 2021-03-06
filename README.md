SpreeSunspotSearch
==================

Adds Solr search to Spree using [Sunspot]:https://github.com/sunspot/sunspot . This is a moving targer and is very beta and should be treated as such. This is compatable with the current 0.70 release of Spree only due to gem requirements.


Install
=======

I make the assumption that you have a functioning Spree store and are just extending the search capabilities with Sunspot/Solr

Add spree_sunspot_search to your Gemfile and run bundler.

`gem 'spree_sunspot_search', git: 'git://github.com/jbrien/spree_sunspot_search.git'`

add the following to the Gemfile if you are not using another solr install locally for testing and development. The rake tasks for starting and stop this for development are included automatically for your use.

`group :test, :development do`
`  gem 'sunspot_solr'`
`end`

bundle install

Install the solr.yml file from Sunspot.

`rails g sunspot_rails:install`

Copy the Initializer

`rake spree_sunspot:install`

Running
=======

Start up Solr (bundled with Sunspot's install)

`rake sunsport:solr:run`

Build the index for the first time

`rake sunspot:reindex`

Customise the Facets Shown
--------------------------

Edit the initializer and specify you Product Properties, Product Options, and Price Ranges as an array

supposing you have model manufacturer and gender as addition properties you would add the following to the initializer

`PRODUCT_PROPERTY_FACETS = [:brand, :model, :manufacturer, :gender]`

same goes for product options

`PRODUCT_OPTION_FACETS = [:color, :size]`

and price ranges

`PRODUCT_PRICE_RANGES = ["0-25", "25-50", "50-100", "100-150"]

Testing
=======

Pending

TODOs
=====

*Add an automatic MAX value for price facets (e.g. Above <max_said_value>)
*Sorting by facet criteria and Solr analytics (Best result, Popular, etc.)
*Open the Sunspot DSL to utilise all the additional data and analytics available through Solr
*Get the Taxon browsing (e.g. Categories) to utilise the Solr data for speed boosts


Copyright (c) 2011 John Brien Dilts, released under the New BSD License
