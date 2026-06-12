---
title: "How to make Ubuntu obscurity"
date: 2010-06-09
forum: Security
---

### Post by thangnguyen on 2010-06-09
Dear all
My system have Ubuntu with Apache/MySQL and PHP running on it. Everytime I access my system, the response header is like this:
> DateWed, 09 Jun 2010 18:11:11  GMT

ServerApache/2.2.14 (Ubuntu)

X-Powered-ByPHP/5.3.2-1ubuntu4

Vary Accept-Encoding

Content-Encodinggzip

Content-Length44

Keep-Alivetimeout=15, max=98

ConnectionKeep-Alive

Content-Typetext/html
I've hearted that we can change these information for obscurity (such as: Server: IIS6 (Windows Server 2003)...
So how can I do it? Do I need to revise the source code of Apache and compile it? Which file should be revise?
Thank you

---

### Post by cdenley on 2010-06-09
The server header is controlled by the "ServerTokens" apache configuration option, and the "X-Powered-By" header can be disabled with "expose_php" in /etc/php5/apache2/php.ini.

[http://httpd.apache.org/docs/2.2/mod/core.html#servertokens](http://httpd.apache.org/docs/2.2/mod/core.html#servertokens)
[http://php.net/manual/en/ini.core.php](http://php.net/manual/en/ini.core.php)

---

### Post by thangnguyen on 2010-06-10
Thank cdenley.
As I understand, the ServerTokens just allow us choose one of the options:
> ServerTokens Prod[uctOnly]
Server sends (*e.g.*): Server:       Apache
ServerTokens Major
Server sends (*e.g.*): Server:       Apache/2
ServerTokens Minor
Server sends (*e.g.*): Server:       Apache/2.0
ServerTokens Min[imal]
Server sends (*e.g.*): Server:       Apache/2.0.41
ServerTokens OS
Server sends (*e.g.*): Server: Apache/2.0.41       (Unix)
ServerTokens Full (or not specified)
Server sends (*e.g.*): Server: Apache/2.0.41       (Unix) PHP/4.2.2 MyMod/1.2So it will reveal at least : Apache. Can we remove this or change the name (such as IIS) to hide the server type, so that, in certain degree, mislead hackers?

---

### Post by Helkaluin on 2010-06-10
Hi,

The tone of this guide might be slightly unfriendly, but it does explain well (including changing the 'Apache' string): [http://attrition.org/attrition/how-apache.html](http://attrition.org/attrition/how-apache.html)

---

### Post by anomie on 2010-06-10
@thangnguyen: There is some low-hanging fruit that you've already learned about in this thread (the ServerTokens directive). Updating that is easy and effective. 

A good question to ask yourself: "Is the extra effort (including future maintenance) worth the result of obfuscating my web server name?" 

I'd argue that your time would be much, much, much better spent learning how to properly secure and monitor your Apache web server. To that end, if you have access to a library (or some $$ for a new book), I heartily recommend *Apache Security* by Ivan Ristic.

---

### Post by bodhi.zazen on 2010-06-10
> **anomie said:**
> @thangnguyen: There is some low-hanging fruit that you've already learned about in this thread (the ServerTokens directive). Updating that is easy and effective. 

A good question to ask yourself: "Is the extra effort (including future maintenance) worth the result of obfuscating my web server name?" 

I'd argue that your time would be much, much, much better spent learning how to properly secure and monitor your Apache web server. To that end, if you have access to a library (or some $$ for a new book), I heartily recommend *Apache Security* by Ivan Ristic.

+1 

Security through obscurity is no security at all.

Apache is reasonably secure, it is the modules and CGI (PHP) and Mysql you have to watch as well.

---

### Post by thangnguyen on 2010-06-13
Thank you all.
I've found an article with easy guidance for replacing "Apache" to anything by using Mod_Security. 
[http://slavamarkeyev.com/2010/02/apache-security-by-obscurity/](http://slavamarkeyev.com/2010/02/apache-security-by-obscurity/)
Yes I do think that obscurity alone means nothing, and there're many ways to find the true information of the server. But I want to hide information from script kiddies.

---

### Post by OpSecShellshock on 2010-06-13
> **thangnguyen said:**
> Thank you all.
I've found an article with easy guidance for replacing "Apache" to anything by using Mod_Security. 
[http://slavamarkeyev.com/2010/02/apache-security-by-obscurity/](http://slavamarkeyev.com/2010/02/apache-security-by-obscurity/)
Yes I do think that obscurity alone means nothing, and there're many ways to find the true information of the server. But I want to hide information from script kiddies.

To be honest, it doesn't matter much whether or not the scripts used by malicious parties can find the information as long as they can't do anything with it. There will be a number of failed attempts at RFI from time to time, but that happens to all PHP pages that are accessible from the internet. It's a fully automated process most of the time, which means a given script will throw everything it's aware of at several target servers to see if anything sticks. One of the unfortunate aspects of that approach is that it makes intrusion attempts look bigger/worse than they actually are. But from the legitimate server administrator's point of view, 100 failed attempts aren't really any worse than one or two.

It's far more important to make sure inputs are properly validated and software is up to date.

---

### Post by bodhi.zazen on 2010-06-13
> **OpSecShellshock said:**
> To be honest, it doesn't matter much whether or not the scripts used by malicious parties can find the information as long as they can't do anything with it. There will be a number of failed attempts at RFI from time to time, but that happens to all PHP pages that are accessible from the internet. It's a fully automated process most of the time, which means a given script will throw everything it's aware of at several target servers to see if anything sticks. One of the unfortunate aspects of that approach is that it makes intrusion attempts look bigger/worse than they actually are. But from the legitimate server administrator's point of view, 100 failed attempts aren't really any worse than one or two.

It's far more important to make sure inputs are properly validated and software is up to date.

OpSecShellshock - you hit the nail right on the head. 

:guitar:

---

