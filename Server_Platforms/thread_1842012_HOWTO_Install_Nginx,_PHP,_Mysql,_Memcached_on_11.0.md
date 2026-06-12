---
title: "HOWTO: Install Nginx, PHP, Mysql, Memcached on 11.04"
date: 2011-09-10
forum: Server Platforms
---

### Post by davidY on 2011-09-10
This is not a production deployments. It is for personal use. I have tried to enforce UTF8 wherever possible. There may be some permissions stuff i forgot, but this should mostly work.

**Install components:**
```
# nginx
sudo apt-get install -y nginx
# php and debugging
sudo apt-get install -y php5-cli php5-fpm php-apc
sudo apt-get install -y php5-xdebug 
# mysql - it will ask you to set up a root account
sudo apt-get install -y mysql-server mysql-client mysql-query-browser
# memcached
sudo apt-get install -y memcached
```

**Make a folder to serve from**
```
sudo mkdir -p /www/personal/php
sudo mkdir -p /www/personal/static
sudo mkdir -p /var/log/nginx.personal
sudo chmod a+rw -R /www/personal
```

**Configure nginx**
Create a new config file for nginx. The config files are located in /etc/nginx/sites-available.
```
sudo gedit /etc/nginx/sites-available/personal
```
```
server {
    listen 8983;
    server_name localhost;
    server_tokens off;
    access_log /var/log/nginx.personal/access.log;
    error_log /var/log/nginx.personal/error.log;
    root /www/personal/static;

    # things that end in php will search the php folder instead
    location ~ \.php$ {
        fastcgi_pass 127.0.0.1:9000;
        fastcgi_index index.php;
        include fastcgi_params;
        fastcgi_param SCRIPT_FILENAME /www/personal/php$fastcgi_script_name;
    }
}
```

**Make a database**
```
mysql-query-browser
```
Log in with your root mysql account. In the small editor type: ```
create database personal
```
Click the Execute query button.
Click on File > New Script Tag and paste the following and then click execute: 
```
use personal;
create table test (
    id bigint not null primary key auto_increment,
    info text character set utf8
) engine = innodb default charset=utf8 collate=utf8_unicode_ci;
insert into test (info) values ('Hello, world; or &#922;&#945;&#955;&#951;&#956;&#941;&#961;&#945; &#954;&#972;&#963;&#956;&#949;; or &#12371;&#12435;&#12395;&#12385;&#12399; &#19990;&#30028;');
```

**Create a databse user with less privileges**
```
mysql-admin
```
Log in with your root mysql account. Click on the "Users Administration" tab. Click "New Users". Create a user called: php_user. Go to "Schema Privileges". Select the personal database. Assign the privileges to select, update and delete. 

**Set up debugging on PHP**
```
sudo gedit /etc/php5/conf.d/xdebug.ini
```
Add these if not already there
```
xdebug.default_enable=1
xdebug.var_display_max_depth=8
xdebug.trace_format=3
html_errors=1
display_errors=on
```

**Make Static HTML**
```
gedit /www/personal/php/index.html
```
```
<html>
    <head>
        <meta http-equiv="content-type" content="text/html; charset=utf-8">
    </head>
    <body>
        <h1>Hello</h1>
        This is working?
    </body>
</html>
```
Test it out at [http://localhost:8983/](http://localhost:8983/)

**Test PHP <-> DB**
```
gedit /www/personal/php/db_test.php
```
```
<?
    header('Content-Type: text/html; charset=utf-8');
    mb_internal_encoding('UTF-8');
    
    $connection = new PDO(
        'mysql:host=localhost;port=3306;dbname=personal;charset=UTF-8', 
        'php_user', 
        'password', 
        array(
            PDO::ATTR_PERSISTENT => true,
            PDO::ATTR_DEFAULT_FETCH_MODE => PDO::FETCH_OBJ,
            PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,
        )
    );
    $connection->exec('set names utf8');
    $connection->exec('set character set utf8');
    $statement = $connection->prepare('select * from test where id = :id');
    $statement->execute(array(
        'id' => 1
    ));
    $data = $statement->fetchAll();
    $statement->closeCursor();
?>

<html>
    <head>
        <meta http-equiv="content-type" content="text/html; charset=utf-8">
    </head>
    <body>
        <?=var_dump($data)?>
    </body>
</html>
```
Test it out at [http://localhost:8983/db_test.php](http://localhost:8983/db_test.php)

**Test PHP <-> Memcache**
```
gedit /www/personal/php/memcache_test.php
```
```
<?
    $memcache = new Memcache;
    $memcache->connect('localhost', 11211) or die ("Could not connect");
    $tmp = (object) array(
        'a' => 'asdf',
        'b' => 564,
        'c' => 59.2,
        'd' => array(0, true, null, 'h'),
    );
    $memcache->set('key', $tmp) or die ("Failed to memcache it");
    echo var_dump($memcache->get('key'));

```
Test it out at [http://localhost:8983/memcache_test.php](http://localhost:8983/memcache_test.php)

---

