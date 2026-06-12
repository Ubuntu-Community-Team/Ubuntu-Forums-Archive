---
title: "dapper - php4 - MSSQL"
date: 2006-08-11
forum: Server Platforms
---

### Post by kingmoffa on 2006-08-11
Hi all, 

I've moved over from centos to dapper for various reasons. Im now having trouble setting up my laptop development machine with apache php4  and mssql support. I get the error:

Fatal error: Call to undefined function: mssql_connect() 

I have enable the multiverse and universe repos and installed. The packages I installed are:

libapache2-mod-php4
php4
php4-common
php4-cli
php4-domxml
php4-gd
php4-mysql
php4-odbc
php4-sybase


There seems to be a few posts/articles on the web about mssql support not working / being unreliable - mainly relating to php5. The various instructions usually involve compiling php5 from source using apt-get source php5.

I do not want php5 - and want to stay at version 4. Anyone have any ideas? apt-get source php4 does nothing.

---

### Post by kingmoffa on 2006-08-11
edit: 

the command line part of php seems to work ok.

Will now go through my /etc/php4/apache2/php.ini file again.

---

### Post by kingmoffa on 2006-08-11
SOLVED:

extension=sybase_ct.so

needs to be added to the /etc/php4/apache2/php.ini file. 

The cli was updated automatically, this one wasn't.

---

