# Custom Encrypter for Laravel

This package uses Laravel's encryption but allows you to specify a custom passphrase instead of using the application key.
This can be useful if some of the database data should be encrypted so that only someone with the passphrase can decrypt it.

## Install

Via Composer

``` bash
$ composer require taylornetwork/encrypter
```

## Setup

`TaylorNetwork\Encrypter\Encrypter` is ready to run right out of the box.

## Usage

Instantiate `TaylorNetwork\Encrypter\Encrypter`

The class requires 1 parameter, the passphrase you want to encrypt/decrypt with.

``` php
$passphrase = 'secret 123';

$encrypter = new TaylorNetwork\Encrypter\Encrypter($passphrase);
```

*Note: Laravel's Encrypter class requires a passphrase of exactly 16 characters, `TaylorNetwork\Encrypter\Encrypter` will lengthen or shorten the supplied passphrase and then encode it using base64 before passing it to Laravel's Encrypter class so that you can supply any length of passphrase you want.*

### Available Methods

#### encrypt (mixed $data)

Encrypts the data given or returns `false` if the encryption failed.

``` php
$data = 'This is some data to encrypt';

$encrypter->encrypt($data);
```

Returns

``` php
'eyJpdiI6Ikc5aVdmUzhWcTRIM2xaMFZtQmVhamc9PSIsInZhbHVlIjoidFJmZHY3c1pcL25MZUtpOGlaM1NYa0JEY0FtbGtKTVVVZnRwaXJJbkNkU2srR3BPNlwvTlwvQ24xM0VUZ1lsc2xSMCIsIm1hYyI6ImZjYTU1YzU5NjFhYWM3NTNkOTFiNDk5YTNhMzIwMzhiMzQ0NjZhMDQyNWFjMTExZWVjY2QxOGM5NGExNmRjMGIifQ=='
```

#### decrypt (string $encryptedData)

Decrypts the data given or returns `false` if the decryption failed.

``` php
$data = 'eyJpdiI6Ikc5aVdmUzhWcTRIM2xaMFZtQmVhamc9PSIsInZhbHVlIjoidFJmZHY3c1pcL25MZUtpOGlaM1NYa0JEY0FtbGtKTVVVZnRwaXJJbkNkU2srR3BPNlwvTlwvQ24xM0VUZ1lsc2xSMCIsIm1hYyI6ImZjYTU1YzU5NjFhYWM3NTNkOTFiNDk5YTNhMzIwMzhiMzQ0NjZhMDQyNWFjMTExZWVjY2QxOGM5NGExNmRjMGIifQ==';

$encrypter->decrypt($data);
```

Returns

``` php
'This is some data to encrypt'
```

## Credits

- Main Author: [Sam Taylor][link-author]

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

[link-author]: https://github.com/taylornetwork