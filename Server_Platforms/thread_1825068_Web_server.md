---
title: "Web server"
date: 2011-08-14
forum: Server Platforms
---

### Post by Jakemurray on 2011-08-14
Is there any resource to learn everything about servers and how they work from the ground up? ive tried google but i keep getting results that assume i have some knowledge of command line/GUI servers. if i know absolutely nothing about servers, their operating systems, and how to run a server, where should i start looking.
i need to know everything about servers from the absolute ground up. not just installing.
i just dont know where to look, thanks.

---

### Post by rubylaser on 2011-08-14
Might be easier to point you in the right direction if you mention what you'd like your server to accomplish, and if you'd need directions to understand concepts such as networking / system administration / etc, of if you already understand conceptually what you want.

---

### Post by Jakemurray on 2011-08-14
i just want a server that can host a simple website for the family to post pictures, blog, etc.
but eventually i plan to make a more complex website which will require databases, it will be more or less a very simple amazon.com.

---

### Post by volkswagner on 2011-08-15
> **Jakemurray said:**
> Is there any resource to learn everything about servers and how they work from the ground up? ive tried google but i keep getting results that assume i have some knowledge of command line/GUI servers. if i know absolutely nothing about servers, their operating systems, and how to run a server, where should i start looking.
i need to know everything about servers from the absolute ground up. not just installing.
i just dont know where to look, thanks.

To learn everything about servers is a long process.  There are folks with ten years of experience that would be lying if they said they know everything.

Since "everything" is such a broad subject you would be lost finding a starting point. It would be a good idea to pick some core functions and start with it, such as "web server".  You can learn about the [Apache2]("http://httpd.apache.org/"), [nginx]("http://nginx.net/"), [lighttpd]("http://www.lighttpd.net/")

I also believe learning hands on is worthwhile.  Jump in and try to accomplish your goals.  This way you can research specific terms such as, web based admin for linux, blog software for apache2, open source web gallery, etc.....

An [excellent resource]("http://ubuntuforums.org/showthread.php?t=1046738") is stickied at the top of this thread.   Also [howtoforge.com]("http://www.howtoforge.com/") has great how-to's for installing.

My advice is to try a server install without a GUI, and no web administration package such as webmin or the like.  The server is completely configured using text files.  To become intimately familiar with the inner workings, you should be comfortable editing these files.  The command line also offers powerful commands for checking status of the system, network, disk usage, performance, etc.

I'm no expert, and maybe just recently considered myself no longer a newbie.  I still have a lot to learn, but I was in your shoes once.  I tried reading before doing, just did not work for me.  Learning really started once I had a specific task to complete, then I researched how to get there.

---

### Post by Jakemurray on 2011-08-15
Thanks a ton i really appreciate the links and advice!

---

### Post by jramshu on 2011-08-15
Here's a good place to start. Didn't see them mentioned. 

[https://help.ubuntu.com/11.04/serverguide/C/index.html](https://help.ubuntu.com/11.04/serverguide/C/index.html)
[https://help.ubuntu.com/10.10/serverguide/C/index.html](https://help.ubuntu.com/10.10/serverguide/C/index.html)
[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

These will cover the basics, the other links have been provided. If you run into problems you can always come back and ask here.

Look at Content Management System, such as [Joomla!]("http://www.joomla.org") and [Drupal]("http://drupal.org/"). I am currently using Joomla!. It's takes a little time to get used to, but once you understand the basics of it, it's quit easy to use.

Or you could start learning HTML and CSS, takes a little more time though. lol

---

### Post by jramshu on 2011-08-17
I should add one thing about CMS, and data bases. 

Keep them updated!!! SQLi is very common, plugins for CMS, and CMS's themselves sometimes have vulnerabilities. They will allow your data to be compromised. 

Read, read, read everything you can on security and 0 day exploits for the software you run!!!!!

---

### Post by rbishop on 2011-08-17
If you are not very familiar with doing things via the command line one suggestion would be to use

[http://www.webmin.com]("http://www.webmin.com/")

It is very easy to install via the command line.  Once installed you will be able to configure most everything you want/need from a Webpage. 

Download and installation instructions are here:

[http://www.webmin.com/download.html](http://www.webmin.com/download.html)

Hope this helps a little bit.

---

### Post by hawk2010 on 2011-08-17
Goto [www.howtoforge.com](www.howtoforge.com)

---

