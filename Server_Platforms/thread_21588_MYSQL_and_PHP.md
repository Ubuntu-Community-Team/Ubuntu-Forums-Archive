---
title: "MYSQL and PHP"
date: 2005-03-23
forum: Server Platforms
---

### Post by obelix on 2005-03-23
Ok there is certainly something funky going on with the way that Ubuntu has setup its mysql installation. I can create databases and make connections and everything inside of webmin which uses CGI. But any php based applications simply can't make connections to the database. 

I found this on the PHP website and I'm wondering if anyone can help? I am totally confused as to what to do... and redefining the database connection within PHP is NOT an option. I need mysql to just WORK with PHP. This is the part of Linux I hate... it takes so damn long to get a production system going. I installed MYSQL through apt.


Debian (and "flavors" of Debain such as Ubuntu Linux) installations of mysqld place the socket file on a directory OTHER than /tmp/mysql.sock causing php connection problems.  A quick workaround, as described in the docs above, is to specify ":/path/to/socket in the server parameter in db_connect.  Here is an example where mysql socket is located at /var/run/mysqld/mysqld.sock:

function open_connection() {
  $host = "localhost:/var/run/mysqld/mysqld.sock";
  $user = "root";
  $passwd = NULL;
  $db_name = "ipd";
  return db_connect($host, $user, $password, $db_name);
}

---

### Post by Nachtwind on 2005-03-23
just let me ask a question... does it work if you simply write "localhost" instead of the path you did?

---

