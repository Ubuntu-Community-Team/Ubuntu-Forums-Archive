---
title: "phar stream wrappers doesn't work [php]"
date: 2010-10-16
forum: Server Platforms
---

### Post by moreweb on 2010-10-16
Hi all,
I have a problem with phar: simply, stream wrappers doens't work.
I've followed all tutorials on php.net but the error is always the same. Maybe something wrong on my ubuntu server?

> Ubuntu 10.04.1 LTS / Apache/2.2.14 (Ubuntu)
> PHP 5.3.2-1ubuntu4.5 with Suhosin-Patch (cli) (built: Sep 17 2010 13:41:55) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2010 Zend Technologies
    with the ionCube PHP Loader v3.3.20, Copyright (c) 2002-2010, by ionCube Ltd., and
    with Xdebug v2.0.5, Copyright (c) 2002-2008, by Derick Rethans

This:
[PHP]<?php
$p = new Phar('./my.phar', 0, 'my.phar');
echo $p->getStub();
echo "==NEXT==\n";
$p->setStub("<?php
function __autoload($class)
{
      include 'phar://' . str_replace('_', '/', $class);
}
Phar::mapPhar('myphar.phar');
include 'phar://myphar.phar/startup.php';
__HALT_COMPILER();");
echo $p->getStub();[/PHP]
output:
```
PHP Fatal error:  Uncaught exception 'RuntimeException' with message 'Unable to read stub' in /home/mw/www/test/test.php:3
Stack trace:
#0 /home/mw/www/test/test.php(3): Phar->getStub()
#1 {main}
  thrown in /home/mw/www/test/test.php on line 3
```
This:
[PHP]<?php
try {
      $p = new Phar(dirname(__FILE__) . '/brandnewphar.phar', 0, 'brandnewphar.phar');
      $p['a.php'] = '<?php var_dump("Hello");';
      $p->setStub('<?php var_dump("First"); Phar::mapPhar("brandnewphar.phar"); __HALT_COMPILER(); ?>');
      include 'phar://brandnewphar.phar/a.php';
      var_dump($p->getStub());
      $p['b.php'] = '<?php var_dump("World");';
      $p->setStub('<?php var_dump("Second"); Phar::mapPhar("brandnewphar.phar"); __HALT_COMPILER(); ?>');
      include 'phar://brandnewphar.phar/b.php';
      var_dump($p->getStub());
} catch (Exception $e) {
      echo 'Write operations failed on brandnewphar.phar: ', $e;
}
?>[/PHP]
output:
```
PHP Warning:  include(): Failed opening 'phar://brandnewphar.phar/a.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /home/mw/www/test/create_stub.php on line 6
PHP Stack trace:
PHP   1. {main}() /home/mw/www/test/create_stub.php:0
string(84) "<?php var_dump("First"); Phar::mapPhar("brandnewphar.phar"); __HALT_COMPILER(); ?>
"
PHP Warning:  include(): Failed opening 'phar://brandnewphar.phar/b.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /home/mw/www/test/create_stub.php on line 10
PHP Stack trace:
PHP   1. {main}() /home/mw/www/test/create_stub.php:0
string(85) "<?php var_dump("Second"); Phar::mapPhar("brandnewphar.phar"); __HALT_COMPILER(); ?>
"

```

Suggestions?

Thanks,
Marco

---

### Post by 448191 on 2010-10-16
You're trying to fetch the stub before you define it on L#3.

---

### Post by moreweb on 2010-10-16
Yep, I wrote a bad sample. 
And also the second have a wrong path. Like the main .phar that I use.. It was compiled in a wrong way.

Thanks

---

### Post by moreweb on 2010-10-16
Mmm.. no, include problem persists.
Works the second example for you?

---

### Post by 448191 on 2010-10-16
I get this, but that may be because ther'es nothing in the phar for me:


kleijn@goliath:~/NetBeansProjects/Junk$ php index.php 
string(5) "Hello"
string(84) "<?php var_dump("First"); Phar::mapPhar("brandnewphar.phar"); __HALT_COMPILER(); ?>
"
string(5) "World"
string(85) "<?php var_dump("Second"); Phar::mapPhar("brandnewphar.phar"); __HALT_COMPILER(); ?>
"
jkleijn@goliath:~/NetBeansProjects/Junk$ php index.php 
string(5) "Hello"
string(84) "<?php var_dump("First"); Phar::mapPhar("brandnewphar.phar"); __HALT_COMPILER(); ?>
"
string(5) "World"
string(85) "<?php var_dump("Second"); Phar::mapPhar("brandnewphar.phar"); __HALT_COMPILER(); ?>
"
jkleijn@goliath:~/NetBeansProjects/Junk$

---

