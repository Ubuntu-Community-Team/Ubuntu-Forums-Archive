---
title: "Help with building a server"
date: 2010-09-24
forum: Server Platforms
---

### Post by paulc8481 on 2010-09-24
HELP !  I have taken a number of programming classed and am now into php.  I am very interested in building my own server to host my pages but configuring a server is new and has me stumped.  Can anyone give me a kick start as how to begin this process and what software I will need.  I have already burned Ubunto desktop and server software onto a disk as an ISO file so that would be ready to go, but as far as the rest of the configurations during installation I am clueless.  Can nyone help or point me in the right dirction as far as a easy to understan tutorial?
 
Thanks P

---

### Post by CharlesA on 2010-09-24
It depends on what you want to do.

If you want to just use the machine to host your files and whatnot, install the server version and select LAMP Server during install.

If you want to build and test on the same machine, just install the desktop version and then run this command from a terminal:

```
sudo tasksel install lamp-server
```

More info [here]("https://help.ubuntu.com/community/ApacheMySQLPHP").

---

### Post by HermanAB on 2010-09-25
Linux is Linux is Linux...

Being here, I assume that you are running Ubuntu.  So guess what, you are already running a server.  All you need to do is install whatever you want with apt-get.

---

### Post by paulc8481 on 2010-09-25
Not being very versed in unix,  The server version seems a bit confusing.  Can I use the Desk top version, down load the LAMP services and use my computer to develope, test and Host my web pages that I creat for my class (PHP)?  
 
Thanks P

---

### Post by koenn on 2010-09-25
> **paulc8481 said:**
>  Can I use the Desk top version, down load the LAMP services and use my computer to develope, test and Host my web pages that I creat for my class (PHP)? 
didn't CharlesA and Herman AB suggest exactly that already

---

### Post by lemuriaX on 2010-09-25
You might find this useful:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by CharlesA on 2010-09-25
> **paulc8481 said:**
> Not being very versed in unix,  The server version seems a bit confusing.  Can I use the Desk top version, down load the LAMP services and use my computer to develope, test and Host my web pages that I creat for my class (PHP)?  
 
Thanks P

Yes, you can do that.

---

### Post by drdos2006 on 2010-09-25
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

