---
title: "Ubuntu Feisty, stand-alone server in a colo."
date: 2007-05-05
forum: Server Platforms
---

### Post by Yourname on 2007-05-05
Hello,

I'm a total newb. I have a few things I know about on Linux. But this might help me get started.
My work has a lot of rack space at a carrier hotel, and I'd like to put in a server there.

I'd like to be able to run/host my websites on that box.
Is there a tutorial or a thread that explains how I'd go about doing that, all the way from installation, hostname to doing the dns stuff to actually get the hosting done properly?

I can't try cPanel, Plesk or Directadmin because of their prices. I'd like to use something free if possible.
I checked out ISPconfig and Webmin, personally ISPconfig looked more responsive (Just doesn't have a manual explaining things, but explains how a check button needs to be pressed, etc) 

Anyway, any manual, or book that'll teach me A-Z of everything I outlined, please?
PS: I tried Google, nothing good seems to be coming up. Only explains a part of things which confuses me even more, lol.

---

### Post by Schalken on 2007-05-05
Using the Ubuntu server CD, you will have the option of installing the LAMP stack (Linux, Apache, MySQL and PHP). This will give you a complete webserver (Apache) with a database backend (MySQL) and a programming language (PHP). Then all you need to do is hook it up to the Internet with a DNS server for a domain name. That last part I know nothing about. :P

But this howto looks good: [http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)

---

### Post by Yourname on 2007-05-05
Schalken, thanks a lot for that reply.
I've used the howtoforge howto's before. And so far everything is good.

Except, I really don't know how to go about things rather than just installing them.

---

