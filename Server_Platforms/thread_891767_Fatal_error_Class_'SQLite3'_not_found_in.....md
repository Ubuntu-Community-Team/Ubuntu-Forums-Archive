---
title: "Fatal error: Class 'SQLite3' not found in...."
date: 2008-08-16
forum: Server Platforms
---

### Post by 4partee on 2008-08-16
Running 8.04 64bit desktop w/LAMP added and would like to try out SQLite3 with PHP.

I get the error when running the example from:
[http://us.php.net/manual/en/sqlite3.open.php](http://us.php.net/manual/en/sqlite3.open.php)

as follows:

root@voyager:/var/www/foliofn# cat example.php; php example.php 
<?php
$db = new SQLite3('mysqlitedb.db');

$db->exec('CREATE TABLE foo (bar STRING)');
$db->exec("INSERT INTO foo (bar) VALUES ('This is a test')");

$result = $db->query('SELECT bar FROM foo');
var_dump($result->fetchArray());
?>

Fatal error: Class 'SQLite3' not found in /var/www/foliofn/example.php on line 2
root@voyager:/var/www/foliofn# 

I have used synaptic to install anything I could find related to SQLite/SQLite3.

Any Ideas?

John

---

### Post by anjanesh on 2008-10-12
Same here. I have SQLITE3 extension enabled with version 3.4.2 and yet this doesnt work !
I did sudo apt-get install php5-sqlite php5-slite3

---

### Post by pldaniels on 2008-10-13
Likewise here.  I've installed all the php-sqlite packages and accessories for it (yes, and php5-sqlite3 etc) to no avail (restarted apache).

Hope there's a fix for this :(

---

### Post by anjanesh on 2008-10-13
The installation section [http://php.net/manual/en/sqlite3.installation.php]("http://us3.php.net/manual/en/sqlite3.installation.php") doesnt have anything in it !
Is this still in development ?

---

### Post by wsams on 2009-01-23
These instructions should get the SQLite3 class installed.

```

$ sudo apt-get install php5-cli php5-dev make
$ sudo apt-get install libsqlite3-0 libsqlite3-dev
$ sudo apt-get install php5-sqlite3
$ sudo apt-get remove php5-sqlite3
$ cd ~
$ wget http://pecl.php.net/get/sqlite3-0.6.tgz
$ tar -zxf sqlite3-0.6.tgz
$ cd sqlite3-0.6/
$ sudo phpize
$ sudo ./configure
$ sudo make
$ sudo make install
$ sudo apache2ctl restart

```

Thanks again Anthony. :)

---

### Post by Spoom on 2009-10-02
Note that this doesn't actually get PHP to load the extension, so once you've compiled the SQLite3 extension as shown above:

```
cd /etc/php5/conf.d
sudo nano sqlite3.ini
```

...and insert this into the file:

```
# configuration for php SQLite3 module
extension=sqlite3.so
```

Save and then restart Apache:

```
sudo /etc/init.d/apache2 restart
```

And the SQLite3 class should be available in PHP.

By the way, currently there is no installation candidate for php5-sqlite3 in Jaunty, so don't worry if the install complains about that; just continue on, since you're compiling it from source anyway.

---

### Post by 4partee on 2009-10-22
Thanks wsams and Spoom;

John

---

### Post by kyouren on 2010-03-06
Apparently a change of method to PDO, see comment by user pomax in [http://www.php.net/manual/en/intro.sqlite3.php](http://www.php.net/manual/en/intro.sqlite3.php)

The PDO (PHP Data Object) is documented here - [http://www.php.net/manual/en/book.pdo.php](http://www.php.net/manual/en/book.pdo.php)

I successfully used:

      <?php
        
         /* create new database (OO interface) */
         $db2 = new PDO('sqlite:/my_folder/db_php.sqlite'); 
        /* $db2 = new SQLite3("/my_folder/db_php.sqlite"); */
        /* create table foo and insert sample data */
        $db2->exec("BEGIN;
        CREATE TABLE foo (name);
        INSERT INTO foo (name) VALUES('Ilia');
        INSERT INTO foo (name) VALUES('Ilia2');
        INSERT INTO foo (name) VALUES('Ilia3');
        COMMIT;");
      /* execute a query */   

         $sql = "SELECT name FROM foo";
        foreach ($db2->query($sql) as $row) {
            print $row['name'] . "\t";

        }
        /* not generally needed as PHP will destroy the connection */
        $db2 = null;

        ?> 

PS When I tried the sqlite_open, I got a Sqlite 2 file

---

### Post by bobatomik on 2010-04-27
You can use the karmic repository:
[http://packages.ubuntu.com/hardy/php-sqlite3](http://packages.ubuntu.com/hardy/php-sqlite3)
[http://packages.ubuntu.com/hardy/php5-sqlite3](http://packages.ubuntu.com/hardy/php5-sqlite3)

---

