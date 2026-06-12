---
title: "php-fpm is mixing configs of different vhosts."
date: 2013-03-05
forum: Server Platforms
---

### Post by bvidinli on 2013-03-05
The newest problem is: php-fpm is mixing configs of different vhosts.
let me explain,
I have a vhost section like:


server {
listen 80;
server_name sub1.something.com;
....
root   /var/www/httpdocs;
#access_log /var/log/nginx/debug-fpm.log debug_phpfpm;
include fastcgi_params;
try_files $uri =404;
limit_req   zone=one  burst=3;
limit_conn phplimit 5;
fastcgi_param  PHP_ADMIN_VALUE "open_basedir=/var/www/httpdocs/somedir11";
fastcgi_param  PHP_ADMIN_VALUE "doc_root=/var/www/httpdocs";
fastcgi_pass   127.0.0.1:9000;
fastcgi_index  index.php;
fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;

fastcgi_read_timeout 300;
}

and another section similar but different server_name:


server {
listen 80;
server_name sub2.something.com;
....
fastcgi_param PHP_ADMIN_VALUE "open_basedir=/var/www/httpdocs/somedir22";
}


the problem is this:
even the user goes to sub1.something.com, the open_basedir of second vhost section (somedir22) is applied. It seems that, php or php-fpm or nginx or whatever it is, remembering some previous state of PHP_ADMIN_VALUE.
what may be the problem ?
I also suspect this before, because I see logs in syslog, showing wrong filenames.
for ex: php syslog(LOG_WARNING,"log from file1") generates a log in syslog,
syslog(LOG_WARNING,"log from file2")
I saw in past, logs are mixed somehow. wrong message is displayed with wrong prefix (of syslog line).

Is there a setting that causes php-fpm (or anything) remembers some other state ?
Any suggestion ?


Note1: I have single pool for all web requests/subdomains. this may cause problem ?

---

### Post by bvidinli on 2013-03-06
I solved almost all of my problems, by trying and reading a lot of things. Something may be a bug. nginx guys should look at here, or I am wrong at some points. 
Here are results.

1.
"fastcgi_param PHP_ADMIN_VALUE " directive must be used only once, if you used it twice, then, only second one has affect.
If you need more than one php admin value, write them in single statement, by separating with newlines, so; if you need like:

fastcgi_param PHP_ADMIN_VALUE "open_basedir=/var/www/httpdocs/somedir11";
fastcgi_param PHP_ADMIN_VALUE "doc_root=/var/www/httpdocs";

then, write this like this:

fastcgi_param PHP_ADMIN_VALUE "open_basedir=/var/www/httpdocs/somedir11
doc_root=/var/www/httpdocs";


2. 
if you write PHP_ADMIN_VALUE in a vhost, its affect continues in other vhosts too. 
So, if you write PHP_ADMIN_VALUE in one vhost (nginx server section), even if you don't write any PHP_ADMIN_VALUE in another vhost, it behaves as if you wrote there.

The solution is to write PHP_ADMIN_VALUE in all vhosts, either with a value, or vithout a value, but write it. 
so, if you write:

fastcgi_param PHP_ADMIN_VALUE "open_basedir=/var/www/httpdocs/somedir11";

in one vhost,  and you don't want any open_basedir in another vhost, write in other vhost:

fastcgi_param PHP_ADMIN_VALUE "";

otherwise, previous PHP_ADMIN_VALUE is somehow remembered by nginx/php-fpm (this may be a bug)

3.
do not use /etc/init.d/nginx reload
but use
/etc/init.d/nginx restart

As I experienced, reload does not actually reloads some fastcgi_param parameters. 

I also used sometime /etc/init.d/php5-fpm restart


Hope this helps somebody... 

My other problem remains impact: [http://ubuntuforums.org/showthread.php?t=2117111](http://ubuntuforums.org/showthread.php?t=2117111)
I just applied a workaround by disable_functions
But I need a more correct solution about that.

---

### Post by ebuildy on 2013-12-03
Actually this is normal behavior. PHP-FPM has pool of worker process. When you use with Nginx, all your virtual host will have the same PHP-FPM pool ! With the same configuration. So in your case, you should create different PHP-FPM pool, where you can override some php.ini params.

Each pool will have a socket listen (or a different IP/port).

---

