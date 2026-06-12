---
title: "Postfix refuses POP clients after mysqlizing back end"
date: 2009-01-04
forum: Server Platforms
---

### Post by bluethundr on 2009-01-04
Hello,

I have attempted to mysqlize the backend of my postfix config. Since doing that I have not been able to connect to my server via pop clients. I am using courier as my pop server. I am suffering authentication failures even though the correct username and password are supplied.

Here is my main.cf file

[http://paste.debian.net/25166/](http://paste.debian.net/25166/)

And these are the supporting files that are supposed to convert my postfix configuration to a mysql backend.

[http://paste.debian.net/25167/](http://paste.debian.net/25167/)
[http://paste.debian.net/25168/](http://paste.debian.net/25168/)
[http://paste.debian.net/25169/](http://paste.debian.net/25169/)
[http://paste.debian.net/25170/](http://paste.debian.net/25170/)
[http://paste.debian.net/25171/](http://paste.debian.net/25171/)
[http://paste.debian.net/25172/](http://paste.debian.net/25172/)

And here are my (sanitized) log files:

[http://paste.debian.net/25178/](http://paste.debian.net/25178/)


This is really driving me crazy, any help at all would be greatly appreciated. Huh

---

### Post by spiderbatdad on 2009-01-04
how about your authmysqlrc?
Also setting for myorigin and mydestination seem wrong, but noting to do with the auth error you're getting. Maybe verify your table data.

---

### Post by bluethundr on 2009-01-04
Thanks very much for your reply. Here is my authmysqlrc (sanitized)

[http://paste.debian.net/25238/](http://paste.debian.net/25238/)

Do I need to mention this in my main.cf somewhere? I did have the port option set to 0 initially, but I have reset it to 3306. Are there perhaps other changes that need to be made? Because making that one change and restarting/reloading postfix did not do the trick.

---

### Post by spiderbatdad on 2009-01-05
so... depending on how you set up the tables in mysql...for example "users" would have fields "clear" and "crypt" for passwords, and these fields get named in authmysqlrc
My own is simple: [http://paste.ubuntu.com/100677/](http://paste.ubuntu.com/100677/)

```
MYSQL_CRYPT_PWFIELD	crypt

##NAME: MYSQL_CLEAR_PWFIELD:0
#
#
#MYSQL_CLEAR_PWFIELD	clear


```

This guide has some good examples of table creation for mysql: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

