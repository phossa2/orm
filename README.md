# phossa2/orm
[![Build Status](https://travis-ci.org/phossa2/orm.svg?branch=master)](https://travis-ci.org/phossa2/orm)
[![Code Quality](https://scrutinizer-ci.com/g/phossa2/orm/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/phossa2/orm/)
[![Code Climate](https://codeclimate.com/github/phossa2/orm/badges/gpa.svg)](https://codeclimate.com/github/phossa2/orm)
[![PHP 7 ready](http://php7ready.timesplinter.ch/phossa2/orm/master/badge.svg)](https://travis-ci.org/phossa2/orm)
[![HHVM](https://img.shields.io/hhvm/phossa2/orm.svg?style=flat)](http://hhvm.h4cc.de/package/phossa2/orm)
[![Latest Stable Version](https://img.shields.io/packagist/vpre/phossa2/orm.svg?style=flat)](https://packagist.org/packages/phossa2/orm)
[![License](https://img.shields.io/:license-mit-blue.svg)](http://mit-license.org/)

**phossa2/orm** is an ORM library for PHP. **STILL IN DEV**

It requires PHP 5.4, supports PHP 7.0+ and HHVM. It is compliant with [PSR-1][PSR-1],
[PSR-2][PSR-2], [PSR-3][PSR-3], [PSR-4][PSR-4], and the proposed [PSR-5][PSR-5].

[PSR-1]: http://www.php-fig.org/psr/psr-1/ "PSR-1: Basic Coding Standard"
[PSR-2]: http://www.php-fig.org/psr/psr-2/ "PSR-2: Coding Style Guide"
[PSR-3]: http://www.php-fig.org/psr/psr-3/ "PSR-3: Logger Interface"
[PSR-4]: http://www.php-fig.org/psr/psr-4/ "PSR-4: Autoloader"
[PSR-5]: https://github.com/phpDocumentor/fig-standards/blob/master/proposed/phpdoc.md "PSR-5: PHPDoc"

Installation
---
Install via the `composer` utility.

```bash
composer require "phossa2/orm"
```

or add the following lines to your `composer.json`

```json
{
    "require": {
       "phossa2/orm": "2.*"
    }
}
```

Usage
---

Create the orm instance,

```php
use Phossa2\Orm\Orm;

$orm = new Orm();
```

Concepts
---

- **Property**

  A single data slice, usually corresponds to an underlying column in the db
  table (*storage*), and its constraints & processors (*logic*).

  A *virtual* property has no corresponding storage column in db table.

- **Schema**

  Consists of *properites*, constraints, processors and relations.

  - By default, one schema corresponds to one underlying table (*storage*).

  - Different tables may map to same schema.

    e.g. `tbl_user1` and `tbl_user2` map to the same schema `UserSchema`.

  - One schema may be consist of other schemas from inheritance, thus may have
    a couple of underlying tables which share the same primary key.

  - If one schema inherit another schema, all the properties, constraints,
    processors and relations are carried over to the new schema.

  - schema level scope is supported

- **Relation**

  Logic connection between *schemas* or between *models* ?

- **Model**

  A class implementing a schema.

  - Different models may be mapped to one schema (n:1)

    e.g. `Novel` model is a child model of `Book`. Both share the same schema,
    `BookSchema`. But, both models may or may not use same underlying table.

  - Inherits a model, including everyting, but can override relations, scope,
    processors etc.

  - model level scope overrides schema level scope

Features
---

- <a name="anchor"></a>**Feature One**

APIs
---

- <a name="api"></a>`LoggerInterface` related

Change log
---

Please see [CHANGELOG](CHANGELOG.md) from more information.

Testing
---

```bash
$ composer test
```

Contributing
---

Please see [CONTRIBUTE](CONTRIBUTE.md) for more information.

Dependencies
---

- PHP >= 5.4.0

- phossa2/shared >= 2.0.21

License
---

[MIT License](http://mit-license.org/)
