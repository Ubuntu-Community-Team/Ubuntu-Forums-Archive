---
title: "[SOLVED] HOWTO Ubuntu Server, HTTPD, Perl CGI, PHP &amp; MySQL with minimal memory"
date: 2008-03-06
forum: Server Platforms
---

### Post by aoakley on 2008-03-06
I've written a guide to installing Ubuntu Server, Lighttpd (an 
alternative to the Apache web server), Perl CGI, PHP and & MySQL on a 
machine (or virtual machine) with 64MB of memory or less.

[http://www.aoakley.com/articles/2008-03-06-ubuntu-minimal-memory.php](http://www.aoakley.com/articles/2008-03-06-ubuntu-minimal-memory.php)

Comments very much appreciated, in particular the MySQL config.

Although Ubuntu does provide a LAMP default install in Ubuntu Server 
edition, this requires 256MB memory. In particular, Apache and 
especially the default MySQL install are real memory hogs, and are 
designed for reasonably heavy-use environments. I saw around 200MB RAM 
in use with no users connected!

My config, in contrast, is designed for test/development environments or 
very low-use websites, typically serving no more than 6 concurrent users 
and only simple SQL requests. My tests under Ubuntu 6 LTS Server showed 
less than 34MB of memory in use.

In particular, my config is suitable for very cheap VPS hosting accounts 
such as vpsville.ca , tektonic.net , cheapvps.co.uk and so forth - 
basically your own root-access Internet server for less than ten dollars a month!

Setup

First, install Ubuntu Minimal.

Next, just issue the following commands:

sudo su -
apt-get install lighttpd php5 mysql-server-5.0 php5-mysql
lighty-enable-mod cgi

mv /etc/mysql/my.cnf /etc/mysql/my.cnf-orig
cat <<! >/etc/mysql/my.cnf
# Example MySQL config file for tiny systems

# Main MySQL server options
[mysqld]
port = 3306
socket = /var/run/mysqld/mysqld.sock

# No locking at all!
skip-locking

# Set internal buffers, caches and stacks very low
key_buffer = 16K
max_allowed_packet = 16K
table_cache = 1
sort_buffer_size = 16K
read_buffer_size = 16K
read_rnd_buffer_size = 1K
net_buffer_length = 1K
thread_stack = 16K

# Don't listen on a TCP/IP port at all.
# Will still work provided all access is done via localhost
skip-networking
server-id = 1

# Skip Berkley and Inno DB types
skip-bdb
skip-innodb

# Set the query cache low
query_cache_limit = 1048576
query_cache_size = 1048576
query_cache_type = 1

# Set various memory limits very low, disable memory-hogging extras
[mysqldump]
quick
max_allowed_packet = 16K
[mysql]
no-auto-rehash
[isamchk]
key_buffer = 16K
sort_buffer_size = 16K
[myisamchk]
key_buffer = 16K
sort_buffer_size = 16K
[mysqlhotcopy]
interactive-timeout
!

/etc/init.d/mysql restart
/etc/init.d/lighttpd restart
exit

-- 
Andrew Oakley

---

