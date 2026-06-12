---
title: "Making Ubuntu Earn it's Keep"
date: 2008-09-28
forum: Server Platforms
---

### Post by Vegan on 2008-09-28
Well lets see, LAMP=Linux, Apache, MySQL and PHP. So can this platform manage to be useful for more then a web host?

I noticed a program called wget what when I tested:

wget [www.microsoft.com](www.microsoft.com)

I found a file, default.aspx in the current directory. Can I parse this file to detect strings and conditionally exploit results. Than nuke the file as obsolete.

I wrote a Windows program to post sitemap.xml files but I wanted to try the same solution on the LAMP machine.

---

### Post by cariboo on 2008-09-28
From man wget:

>  GNU Wget is a free utility for non-interactive download of files from
       the Web.  It supports HTTP, HTTPS, and FTP protocols, as well as
       retrieval through HTTP proxies.

What you have done is download the Microsoft equivalent to index.html. You should be able to open the file with any text editor.

BTW you downloaded Ubuntu for free, why does it have to earn it's keep. :)

Jim

---

### Post by Vegan on 2008-09-28
what I want 2 do is test the retrieved file for certain conditions. Been looking at a range of ideas.

---

### Post by lykwydchykyn on 2008-09-28
Seeing as it's just an ascii html file, your favorite interpreted language will probably work just fine.  I'd recommend Python with BeautifulSoup or maybe Perl.

I don't know how LAMP works into that, but you are being a bit cryptic.

---

### Post by Vegan on 2008-09-29
LAMP is Linux, Apache, MySQL and PHP. LAMP is a de facto standard for a Linux web server solution. LAMP made phpBB real easy to deploy even in a vhost environment like I indulge in.

Its obvious that LAMP has been honed to be useful. I hope it can continue to be capable as time goes forward.

I have Python and every other language I have ever heard of all installed. They consume little space so I tend to install them all in case it comes in handy.

---

