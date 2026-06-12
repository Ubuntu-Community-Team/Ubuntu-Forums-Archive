---
title: "PHP on Windows &amp; Linux whats the difference?"
date: 2006-06-27
forum: Server Platforms
---

### Post by ade234uk on 2006-06-27
Just out of interest what is the difference with the code. All that I should imagine is that path in php scripts go from home/ubuntu/Desktop to C:\home\ubuntu\Desktop

Is it pain running php on Windows regarding paths etc

Today I finally got a small Ubuntu server up and running I am well chuffed, I want to eventually ditch my websites and run them myself on this server, however what I wanted was just run a testing area in Windows for the moment considering all my work is done in Dreamweaver.

---

### Post by Maggot on 2006-06-27
I have no idea but personally I found setting LAMP (Linux Apache MySQL and PHP) was easier than WAMP (Windows).

---

### Post by Ryan H on 2006-06-27
If you allready have a hosts DONOT ditch them. With them your sites are on a fiber optical line that can support thousands of connections at once and has tons and tons of bandwidth. If you host your site yourself it's off your internet connection and unless you have a T1 line, it will be extremely slow for your users and yourself. Secondly for you to have your own domain you would have to set up a DNS, which can take a while.

There are some differences in PHP for Linux and PHP for Windows, but it's not actualy in PHP, but the Operating systems. They handle things slightly differently, you most likely won't notice it. It's important to test on each platform, but you most likely won't have to change anything for it to work in the other.

-Ryan H

---

### Post by youROCK on 2006-06-27
You know, the difference is very little, especially if you do not use OS-specific functions (e.g. system() ;) ). PHP, Apache, MySQL... all are made to be platform-independent :).

---

### Post by ade234uk on 2006-06-27
Is it a case of changing paths from / to c:\ some php scripts require this. For example writing information to a file.
When you say T1 is this like ADSL?

---

### Post by lamego on 2006-06-27
You don't need to care about the slashes direction, just use the unix style and they will work on both platforms (php will convert them to the windows style when/if required), please note that I am not referring to path names which include windows drives on it.

---

### Post by ade234uk on 2006-06-28
I set up WAMP on windows. I am quite suprised that it works quite well. I can now test my websites before uploading to the server. I used to have one opinion about this. The only error I get is with sending mail.

My next step will be to set up LAMP on my own Linux box. 

Is there a download for Ubuntu that has LAMP on it. Is everything done for you this way, ie does php & mysql work out of the box with Apache, or is there lots of configuration involved? WAMP was very painless, there where only three changes I had to make these where the php.ini file, import table to mysql and change conn.php file and that was it.

I have learnt so much in the last 24 hours. I had a little knowledge before, but once you get Wamp running and your site works on it you want it to work on a Linux server.

---

### Post by dk_pa on 2006-06-28
The new Ubuntu server CD (6.06) has a LAMP install option.

---

### Post by Ryan H on 2006-06-28
You can very easiely set up Apache, PHP, and mySQL on Ubuntu Desktop and develope on here. Or optionaly you can get the server version and set up LAMP in one click, but keep in mind this is a server, so you wouldn't be developing on it but on a different PC, usualy networked.

-Ryan H

---

