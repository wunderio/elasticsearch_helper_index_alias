# Elasticsearch Helper Index Alias

`elasticsearch_helper_index_alias` is a module that provides following additional
functionality while managing re-indexes from the administrative UI.

- Adds version index capabilities
- Adds index alias functionality for pointing aliases to index version.
- Useful for re-indexing large datasets after changes to index mappings.

## Requirements

* Drupal 8 or Drupal 9
* [Elasticsearch Helper][elasticsearch_helper] module
* [Elasticsearch Helper Index management][elasticsearch_helper_index_management]
  module.

## Installation

Elasticsearch Helper Index Alias can be installed via the
[standard Drupal installation process](https://www.drupal.org/docs/extending-drupal/installing-drupal-modules).

## Configuration

* Install and enable [Elasticsearch Helper][elasticsearch_helper] module.
* Install and enable [Elasticsearch Helper Index management][elasticsearch_helper_index_management]
  module.
* Install and enable [Elasticsearch Helper Index Alias][elasticsearch_helper_index_alias]
  module.
* Go to the `admin/config/search/elasticsearch_helper/index_management/indices` to manage re-indexes

## Usage

1. Install `Elasticsearch` search engine ([how-to][elasticsearch_download]).
2. Install [``Elasticsearch Helper``][elasticsearch_helper] module, configure it and create indices using `ElasticsearchIndex` type plugins in a custom module.
3. Install and enable [Elasticsearch Helper Index management][elasticsearch_helper_index_management] module.
4. Install and enable [Elasticsearch Helper Index Alias][elasticsearch_helper_index_alias] module.
5. Go to the `admin/config/search/elasticsearch_helper/index_management/indices` to manage re-indexes.
6. To manage your index, select Index Management secondary tab
7. To manage your index aliases, select Aliases Management secondary tab
8. To check your index status, select Indices Status secondary tab

### Setting up Index versions
- Create and setup versioned indexes (See `VersionedIndex.php` from Elasticsearch Helper examples)

### Incrementing Index versions
- Go to index alias management from the Admin menu: Configuration > Search and Metadata > Elasticsearch Helper > Index Management
- Go to the Aliases Management secondary tab
- Increment the index version as needed after changes to index field mapping.
- Export the new version configuration and commit.

### Deploying New Index Versions and Pointing Aliases
- Run `drush eshs` to setup new index versions during deployment
- Re-index entities from Index Management secondary tab
- When re-indexing is done, verify that the new index version contains documents from the Indices Status secondary tab
- Finally point the aliases to the new index version by clicking "Update index aliases to the latest index version" from the Aliases Management secondary tab


[elasticsearch_download]: https://www.elastic.co/downloads/elasticsearch
[elasticsearch_helper]: https://www.drupal.org/project/elasticsearch_helper
[elasticsearch_helper_index_management]: https://www.drupal.org/project/elasticsearch_helper_index_management
[elasticsearch_helper_index_alias]: https://www.drupal.org/project/elasticsearch_helper_index_alias
[elasticsearch_client]: https://github.com/elastic/elasticsearch-php
