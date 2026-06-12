---
title: "problem with Metasploit"
date: 2010-05-17
forum: Security
---

### Post by jubaaa on 2010-05-17
When I use the Mitasploit 3.3
Show me the error message

Uploaded with [ImageShack.us](http://imageshack.us)
msf > load db_postgres
[-] 
[-] The functionality previously provided by this plugin has been
[-] integrated into the core command set.  Use the new 'db_driver'
[-] command to use a database driver other than sqlite3 (which
[-] is now the default).  All of the old commands are the same.
[-] 
[-] Failed to load plugin from /opt/****sploit/msf3/plugins/db_postgres: Deprecated plugin

---

### Post by teh_drizzle on 2010-05-17
Try using (at the msf console): db_driver

This is give you a list of the available database drivers.

Try using sqlite3 for the database driver. 

If nothing is listed try installing the ruby files with (at the bash shell): gem install sqlite3-ruby

---

### Post by jubaaa on 2010-05-18
Thanks for the reply 
I have worked this order
[PHP][/PHP] dh_driver
And appear as in the picture


Uploaded with [ImageShack.us](http://imageshack.us)
```

``` msf > db_driver
[*]    Active Driver: sqlite3
[*]        Available: sqlite3, postgresql

[*]     DB Support: Enable the mysql driver with the following command:
[*]                 $ gem install mysql
[*]     This gem requires mysqlclient headers, which can be installed on Ubuntu with:
[*]                 $ sudo apt-get install libmysqlclient-dev

---

### Post by cariboo on 2010-05-18
Please use thumbnails when attaching an image to a post.

---

### Post by teh_drizzle on 2010-05-18
You should be set to go:

db_driver sqlite3
db_create yourdatabasename

Start metasploiting...

---

