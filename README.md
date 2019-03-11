[![](https://img.shields.io/maintenance/yes/2019.svg)](https://github.com/inspiredminds/contao-maker-bundle)
[![](https://img.shields.io/packagist/v/inspiredminds/contao-maker-bundle.svg)](https://packagist.org/packages/inspiredminds/contao-maker-bundle)
[![](https://img.shields.io/packagist/dt/inspiredminds/contao-maker-bundle.svg)](https://packagist.org/packages/inspiredminds/contao-maker-bundle)

Contao Maker Bundle
=====================

This is an extension of the [Symfony Maker Bundle](https://github.com/symfony/maker-bundle), providing autoloading in the Contao Managed Edition as well as additional commands specific to a Contao installation.

## Installation

```
composer require --dev inspiredminds/contao-maker-bundle
```

## Commands

See the [Symfony Maker Bundle documentation](https://symfony.com/doc/current/bundles/SymfonyMakerBundle/index.html#usage) on how to use the commands, how to list all commands and how to display help text for each command.

The following is a list of Contao Managed Edition specific commands, that are introduced in this bundle.

### `make:autowiring`

In order to be able to use commands, services, event listeners etc. in your app under the `src/` folder, you need load these services in your app config. This command generates or updates the the following files in order to use autowiring for your app:

* `app/config/services.yml`
* `app/config/config.yml`
* `composer.json`

_Note:_ since the Contao Managed Edition still uses the old Symfony structure, the command still generates the config files under `app/config/` rather than just `config/`.

### `make:contao-manager-plugin`

This generates an `App\ContaoManager\Plugin` class. The actual namespace depends on your [configured app namespace](https://symfony.com/doc/current/bundles/SymfonyMakerBundle/index.html#configuration). It also adds a `getBundles` method where a bundle depending on your configured app namespace will be loaded. Example: if your maker config looks like this:

```yml
maker:
    root_namespace: 'Acme'
```

the command will load a `AcmeBundle::class` after the `ContaoCoreBundle::class`.