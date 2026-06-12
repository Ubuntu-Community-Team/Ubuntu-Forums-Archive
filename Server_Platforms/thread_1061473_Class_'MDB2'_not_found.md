---
title: "Class 'MDB2' not found"
date: 2009-02-05
forum: Server Platforms
---

### Post by brossegan on 2009-02-05
Hello all,

I've installed php-pear, MDB2, and the mysql driver.

pear list output:

```
Installed packages, channel pear.php.net:
=========================================
Package            Version State
Archive_Tar        1.3.2   stable
Console_Getopt     1.2.3   stable
MDB2               2.4.1   stable
MDB2_Driver_mysql  1.4.1   stable
MDB2_Driver_mysqli 1.4.1   stable
PEAR               1.7.2   stable
Structures_Graph   1.0.2   stable
```

However, when I try a basic MDB2 connect with the following code:

```
<?

$dsn = array(
        'phptype' => 'mysql',
        'username' => 'user',
        'password' => 'pass',
        'hostspec' => 'localhost',
        'database' => 'sample'
);

echo ini_get('include_path');

$db = MDB2::connect($dsn);
if (PEAR::isError($db)) {
die($db->getMessage() . ', ' . $db->getDebugInfo());
}

?>
```

I get this output:

```
.:/usr/share/php:/usr/share/php/PEAR:/usr/share/php/MDB2
Fatal error: Class 'MDB2' not found in /var/www/pear/douche.php on line 13
```

The first line is my include_path for php.ini, which includes the correct directories where PEAR and MDB2 are installed. However, it seems as though it isn't picking up the files in this directory correctly or something.

I've messed with the database permissions, file/folder permissions, triple-checked the include_path, installed different versions of the MDB2 & Drivers, but nothing seems to work. I really have no idea what to do at this point.

Any suggestions?

---

