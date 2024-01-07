# Local Storage Library

The Local Storage Library is a simple PHP library that provides a convenient way to store and retrieve data with optional encryption. It is designed to work similarly to `stdClass` but with the added functionality of saving and loading data to and from a file.

## Installation

You can install the Local Storage Library using [Composer](https://getcomposer.org/). Run the following command:

```bash
composer require ucscode/local-storage
```

### Installation without Composer

If you prefer not to use Composer, you can manually include the Local Storage Library in your project by following these steps:

1. Clone the [Github repository](https://github.com/ucscode/local-storage) and extract the zipped content into your project directory.

2. In your PHP code, include the `LocalStorage.php` file:

```php
require_once 'path/to/src/LocalStorage.php';
```

## Encryption

By default, the library uses gzdeflate and gzinflate for basic data compression. However, you can enhance security with OpenSSL encryption by simply providing a security key during instantiation.

## Usage

If the instantiation file already contains LocalStorage data, the LocalStorage instance will be automatically populated with that data.

```php
use Ucscode\LocalStorage\LocalStorage;

$filepath = 'path/to/storage/file.txt';

$localStorage = new LocalStorage($filepath);
```

Optionally, a secret key can be added during instantiation to enhance security.

```php
$optionalSecretKey = "my_secret_key";

$localStorage = new LocalStorage($filepath, $optionalSecretKey);
```

### Creating & Accessing

```php
$localstorage->author = "Ucscode";
$localStorage->data = [];
$localStorage->data['foundation'] = "User Synthetics";
$localStorage->data['description'] = "Save encrypted contents into local file instead of database";

$localStorage->data['foundation']; // User Synthetics
```

### Saving Data

The data within LocalStorage will not be automatically saved unless the save method is explicitly called.

```php
$localStorage->save();
```

### Retrieving All Data

To retrieve an array of all data available in local storage, utilize the `getContext` method.

```php
$localStorage->getContext(); // [author => Ucscode, data => [...]]
```

## Contributing &amp; Feedback

If you encounter any issues, have suggestions, or want to contribute to the Local Storage Library, please open an [issue](https://github.com/ucscode/local-storage/issues) on the GitHub repository.

## License

This Local Storage Library is open-source software licensed under the [MIT license](https://opensource.org/licenses/MIT).
