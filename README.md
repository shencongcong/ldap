<h1 align="center"> ldap </h1>

<p align="center"> ldap.</p>


## Installing

```shell
$ composer require shencongcong/ldap -vvv
```

## Usage

```php
use Shencongcong\Ldap\Ldap;

$config = [
    'default' => [
        // 网关调用策略，默认：顺序调用
        'strategy' => \Shencongcong\Ldap\Strategies\OrderStrategy::class,
        // 默认可用的发送网关
        'gateways' => [
            'home','idc'
        ],
    ],
    'gateways' => [
        'home' => [
            'url' => 'LDAP://10.0.0.110/',
        ],
        'idc' => [
            'url' => 'LDAP://10.0.0.150/',
        ],
    ],
];

$ldap = new Ldap($config);

1. 验证账号密码
$username = 'xxxx';
$password = 'xxxx';
$gateways = ['home',idc];
$res = $ldap->ldapCheck($username,$password,$gateways);

2. 根据用户名模糊查找用户
$username = 'xxxx';
$gateways = ['home',idc];
$res = $ldap->userSearch($username,$gateways);

3. 根据邮箱模糊查找用户
$email = 'xxxx';
$gateways = ['home',idc];
$res = $ldap->emailSearch($email,$gateways);


```

TODO

## Contributing

You can contribute in one of three ways:

1. File bug reports using the [issue tracker](https://github.com/shencongcong/ldap/issues).
2. Answer questions or fix bugs on the [issue tracker](https://github.com/shencongcong/ldap/issues).
3. Contribute new features or update the wiki.

_The code contribution process is not very formal. You just need to make sure that you follow the PSR-0, PSR-1, and PSR-2 coding guidelines. Any new code contributions must be accompanied by unit tests where applicable._

## License

MIT