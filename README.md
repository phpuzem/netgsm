# Laravel 5 Netgsm Sms Paketi

[![Latest Stable Version](https://poser.pugx.org/busayo/laravel-volt/v/stable.svg)](https://packagist.org/packages/phpuzem/sms)
[![Latest Unstable Version](https://poser.pugx.org/busayo/laravel-volt/v/unstable.svg)](https://packagist.org/packages/phpuzem/sms)
[![License](https://poser.pugx.org/phpuzem/sms/license.svg)](LICENSE)
[![Total Downloads](https://poser.pugx.org/phpuzem/sms/d/total.png)](https://packagist.org/packages/phpuzem/sms)


Bu paketin kullanılabilmesi için Netgsm ```https://www.netgsm.com.tr/``` firmasına üye olunup, php api desteği açtırılmalıdır.

Komut satırından bu kodu çalıştırınız:
```
composer require phpuzem/sms dev-master
```

```config/app.php``` dosyasına aşağıda bulunan satırları ekliyoruz.
```php
return array(
    // ...

    'providers' => array(
        // ...

        Phpuzem\Netgsm\SmsServiceProvider::class,
    ),

    // ...

    'aliases' => array(
        // ...

        'Sms' => Phpuzem\Netgsm\Facades\SmsFacade::class,
    ),
);
```
# Ayarlar

```code
php artisan vendor:publish --provider="Phpuzem\Netgsm\SmsServiceProvider"
```
komutunu kullanarak ``` config/sms/sms.php``` dosyasını yayınlıyoruz.

### sms.php

```code
return [
    "usercode"  => "Netgsm Kullanıcı Adınız",
    "password"  => "Netgsm Kullanıcı Şifreniz",
    "startdate" => "",
    "stopdate"  => "",
    "type"      => "1:n",
    "msgheader" => "Netgsm Php Apisinde Onaylanan Sms Başlığınız",
    "tr"        => false, (true TR karakterli, false TR karaktersiz gönderir.)
];

```

Kullanıma hazır!

#Kullanımı
```php
public function index()
	{
		return \Sms::sendsms('merhaba','905325087092');
	}
```
