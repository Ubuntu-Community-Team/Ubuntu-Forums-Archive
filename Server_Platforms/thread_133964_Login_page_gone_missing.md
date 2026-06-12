---
title: "Login page gone missing"
date: 2006-02-21
forum: Server Platforms
---

### Post by alamba on 2006-02-21
Hi,

I have the following setup for a client of mine: 
1. Sugar 4.0.1b
2. apache2
3. php5
4. mysql

As of yesterday the implementation (on a hosted webserver) was working just fine. As of today the login page just doesn't come up:

[http://X.X.X.X/apache2-default/Suga...in&module=Users](http://X.X.X.X/apache2-default/Suga...in&module=Users)

The above URL returns and empty white page. Not sure what's gone wrong. Please help.

Akshay

PS: I tried [http://X.X.X.X/apache2-default/Suga....1b/install.php](http://X.X.X.X/apache2-default/Suga....1b/install.php) to see if any page is being delivered and it opened just fine. Restart of apache2 didn't help either.

---

### Post by uopjohnson on 2006-02-21
What do your apache logs say?
/var/log/apache/error_log

---

### Post by alamba on 2006-02-22
Nothing abnormal in the logs. Tried reinstalling PHP but that didn't work either.

A

---

### Post by uopjohnson on 2006-02-22
I'm not familiar with sugar at all, does it have its own logs?  If you are seeing a blank page in php it almost lways indicates a parse error somewhere; especially if you are able to view other pages.

---

### Post by alamba on 2006-02-25
Thanks John. Given my very limited programming skills and the fact that this particular box didn't have any data (new installation) and the client was eager to get this up and running and just did a clean installation.

I believe you have to explicitly start logs in sugar. I would'nt know where to start debugging a parse error (or even what that really means!!)

A

---

