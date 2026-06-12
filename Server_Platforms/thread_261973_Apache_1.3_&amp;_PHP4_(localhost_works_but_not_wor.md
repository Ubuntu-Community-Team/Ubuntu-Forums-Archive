---
title: "Apache 1.3 &amp; PHP4 (localhost works but not working from another machine)"
date: 2006-09-21
forum: Server Platforms
---

### Post by Nap_BlownApart on 2006-09-21
Hi,

I am very new to Linux, but not new to computers.

I've installed Apache 1.3.34, PHP4.4.4.2, mod-php4, MySQL 4.1.15, & phpMyAdmin 4.2.8.1-1, and ODBC for PHP4. (Along with whatever was automatically added by Synaptic)

I have my basic Apache working ok with localhost and from another machine on my lan, so I am now trying to get PHP working. (MySQL is next, followed by phpMyAdmin.)

I am having problems getting PHP to work properly though.
I have edited my httpd.conf file and have the following lines in it:
[b]AddModule mod_php4.c
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps
LoadModule php4_module libexec/libphp4.so[/b] (At the bottom of the httpd.conf I've added this line even though it is already in my module.conf.)

**include /etc/apache/conf.d** (automatically added by one of the php package installations)

The **modules.conf** file has a number of Loadmodule entries, all automatically generated.

In my public_html folder, I have a PHP script that prints the server time and connects to a database.

When I browse this script through localhost, it returns the server time (which is good) and I get a call to undefined function mysql_connect() error   (I assume this is because I haven't configured MySQL and ODBC yet, nor have I setup the database this script is connecting to.)

**When I browse the same script from another machine, I get a window popup asking me to save the PHP file on my computer. Why?**

QUESTIONS:
(1)Can someone please diagnose what I haven't done correctly?
(2)Why does the module.conf file contain all the LoadModule statements when I thought they were supposed to be in the httpd.conf file?
(3)Can anyone help me with a reference doc/link that will explain how to setup everything else related to having a LAMP server running? (Every step seems to be a major battle for no apparent reason.)

Cheers,
Nap

---

### Post by mssever on 2006-09-21
> **Nap_BlownApart said:**
> **When I browse the same script from another machine, I get a window popup asking me to save the PHP file on my computer. Why?**
You must have a mime type mis-configured, probably because PHP isn't installed correctly. Also, have you tried browsing that location from the server but using the server's external address?
> QUESTIONS:
(1)Can someone please diagnose what I haven't done correctly?First, is there a really good reason that you're using an outdated version of Apache, PHP, and MySQL? I would recommend using the latest versions--especially of Apache.

I'd suggest removing everything you've installed so far--including configuration--and starting over with the current versions. In particular, Apache 2 uses quite a different setup than Apache 1.
```
 sudo aptitude install php5 php5-mysql libapache2-mod-php5 mysql-server phpmyadmin
``` This will bring in Apache2, as well.

Everything should be set up automatically. If not:
```
cd /etc/apache2/mods-enabled
sudo ln -s ../mods-available/php5.conf .
sudo ln -s ../mods-available/php5.load .
sudo apache2ctl graceful
```Also, look in /etc/apache2/ports.conf and make sure that Apache is set to listen on the correct addresses/ports. The easiest way is to say Listen 80.
> (2)Why does the module.conf file contain all the LoadModule statements when I thought they were supposed to be in the httpd.conf file?Because it's a lot easier to manage Apache's settings if everything isn't in one humongous file. Instead, the various files are included from /etc/apache2/apache2.conf.
> (3)Can anyone help me with a reference doc/link that will explain how to setup everything else related to having a LAMP server running? (Every step seems to be a major battle for no apparent reason.) Have a look at [http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06). I haven't read it, though, so I can't vouch for it. I do know from glancing at it that it adds a lot of unnecessary steps.

---

### Post by Nap_BlownApart on 2006-09-21
Firstly, there must have been a reason for installing outdated versions, especially since Ubuntu will automatically install the latest ones for you.

So, am I stupid, and decided to stuff up my install?

No.  In the real world, web hosting services are using Apache 1.3.37 (which I couldn't find, so I installed 1.3.34), PHP 4.4.4 (which I was able to find), MySQL 4.1.21 (which I wasn't able to find either so I installed 4.1.15) and phpMyAdmin 2.8.0.2 (of which I could only find version 4.2.8.1-1)

Since I want to develop applications that will work in my development environment **as well as** the real world, I decided that I should mirror the setup that web hosters have.

Instead of polluting my question with condesending nonsense, why don't you start a campaign urging the web hosting companies to upgrade their systems.  If you succeed, let me know, and I will upgrade.

Nap

---

### Post by Nap_BlownApart on 2006-09-21
The reason that ACCESS.CONF and SRM.CONF were merged into the HTTPD.CONF is exactly the opposite of what you are saying.

After spending hours and hours working on this problem, is this the best answer I can get?

---

### Post by Nap_BlownApart on 2006-09-21
Thnx for the link to that article, very well done.

However, here is a quote from an experience user's comment below the main article:

*As an experienced Linux user and admin (I have use Linux on the desktop exclusively for about 5 years, and have been using Linux longer; I have also setup many Linux servers), I have to recommend some changes. **First, you should use Apache 1.3.x not 2. Apache 2 is insecure.** Second, if you have to use a gui, XFCE is much more lightweight, and the desktop of choice for the admins who can't live without a gui. Third, you should NEVER use proftpd for your ftp server; use vsftp instead. Proftp is not secure, whereas vsftpd was designed to be secure from the start, and is the choice of "those who know." For instance, kernel.org (the site which hosts the Linux kernel itself) uses vsftp.*

---

### Post by mssever on 2006-09-21
> **Nap_BlownApart said:**
> Firstly, there must have been a reason for installing outdated versions, especially since Ubuntu will automatically install the latest ones for you.

So, am I stupid, and decided to stuff up my install?

No.  In the real world, web hosting services are using Apache 1.3.37 (which I couldn't find, so I installed 1.3.34), PHP 4.4.4 (which I was able to find), MySQL 4.1.21 (which I wasn't able to find either so I installed 4.1.15) and phpMyAdmin 2.8.0.2 (of which I could only find version 4.2.8.1-1)

Since I want to develop applications that will work in my development environment **as well as** the real world, I decided that I should mirror the setup that web hosters have.

Instead of polluting my question with condesending nonsense, why don't you start a campaign urging the web hosting companies to upgrade their systems.  If you succeed, let me know, and I will upgrade.

Nap
Calm down! I never implied that you were stupid or that you wanted to mess things up. The reason that I suggested what I did is because those suggestions have fixed other people's problems in other threads.

I agree that webhosts are a problem--especially when it comes to PHP4 vs. PHP5 (although there are some that have their heads screwed on properly and support PHP5 or even both). I run both PHP4 and PHP5 side-by-side on my development server. Now THAT was a real challenge to set up!

I've never had problems, though, running Apache2 and hosting on Apache 1. (And by the way, not all hosts run Apache 1.) And since it's been a long time since I've run my own Apache 1, I can't help you in situations where the two versions differ. For me, setup was automatic.

Aside from running dual PHP versions, my setup uses the latest versions of Apache, MySQL, and phpMyAdmin. And I haven't had problems--even on outdated hosts--except for exporting from the current phpMyAdmin, which sets collation and older servers don't like it.

I just thought of something else: I don't have any AddModule lines in my Apache configuration, and my LoadModule line is as follows: ```
LoadModule php4_module /usr/lib/apache2/modules/libphp4.so
``` I don't know if this is merely a version difference or if it's a mis-configuration. Given that PHP seems to work for you in some situations suggest the former.
> **Nap_BlownApart said:**
> The reason that ACCESS.CONF and SRM.CONF were merged into the HTTPD.CONF is exactly the opposite of what you are saying.
I don't know anything about access.conf or srm.conf (which are lowercase, not uppercase, BTW), but I'm very confident that the answer I gave applies to the Debian and Ubuntu versions of Apache. If you compile from source, you still get a single unwieldly file. In the end, though, what does it matter? Either it works or it doesn't.
> After spending hours and hours working on this problem, is this the best answer I can get?You might get better answers if you were a little more polite. Also, my guess is that you won't find very many people on this forum who know and use old versions of those programs.

---

### Post by mssever on 2006-09-21
> **Nap_BlownApart said:**
> ***First, you should use Apache 1.3.x not 2. Apache 2 is insecure.***
Hmm... I've never heard of security issues in Apache 2, and Wikipedia doesn't know of any, either. I'd like to know some specifics.

---

### Post by Nap_BlownApart on 2006-09-21
Every time I ask a question, I get people expressing their opinions about what I should have done.  Unfortunately that's not the nature of my questions.

My original post was not impolite, and I stand by the question raised in it.  If you choose to respond in the manner which you did, spend a micro-second and think how a person would react to your response.
I've been working with computers and programming for 25 years, so whilst I'm not by anymeans an expert in Linux, I am familiar with technology.
If you don't want to answer my questions, please don't post in th e thread, it's as simple as that. Even after all that has transpired above, you are still referencing Apache 2, which is not what I intend to run.

I will open a new thread with the original question since I don't think others need to read our exchanges.

Cheers,
Nap

---

