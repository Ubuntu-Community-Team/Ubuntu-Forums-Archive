---
title: "Ubuntu Server Questions"
date: 2011-03-02
forum: Server Platforms
---

### Post by thunderclap on 2011-03-02
I have two questions regarding Ubuntu.  I currently help admin a site on a VPS running what looks to be Ubuntu 5.12.  We have to move to a new VPS service next month and they offer several different OS's (CentOS, Ubuntu, Debian, etc.) and I want to stick with Ubuntu.  The service offers pre-install of Ubuntu 9 or 8 (32-bit or 64-bit).  I'm going to go with at least version 9, but am curious if I can (or should) upgrade it to version 10.10.  Thoughts?  Also, after a lot of research, it seems most people recommend using the 32-bit version to keep memory usage to a minimum, yet the Ubuntu site recommends the 64-bit version.  What are your thoughts?

So, to paraphrase, should I use Ubuntu 9 or should I upgrade to 10.10, and should I use the 32-bit or 64-bit version?

The VPS specs are: 1024MB RAM, burst memory to 2048MB, 60GB storage, CPU burst at 4 cores @ 2.67GHz each.  The site is primarily a vBulletin CMS & Forum site with some WP, but we are going to be migrating the WP stuff to Joomla soon.

---

### Post by garfonzo on 2011-03-02
Go with 10.04 if possible as it has long term support. That is all I can answer with my knowledge set.

---

### Post by stlsaint on 2011-03-02
if ubuntu server 10.04 is offered go with it and 64bit! cheers \\:D/

---

### Post by wormyblackburny on 2011-03-02
RedHat......

---

### Post by rbishop on 2011-03-02
I say go with 10.4LTS. That is what I run on my servers, and never had a problem with it.  I have had a few problems with my 10.10 desktop, but those were probably me just messing with stuff.

---

### Post by SeijiSensei on 2011-03-03
If your provider doesn't offer a 10.04 or 10.10 image, you'll be faced with upgrading the distro.  If you'd like to avoid that, my VPS provider, [Linode]("http://www.linode.com/faq.cfm#which-distributions-do-you-offer"), has Ubuntu 10.04 and 10.10 images available.

---

### Post by HugoSerrano on 2011-03-03
It's like they say, go to 10.04 LTS!

Regards!

---

### Post by bsntech on 2011-03-03
Yep, 10.04 64-bit.  If you are not running 64-bit, you won't be able to address over 4 GB of memory.

Running 10.04 on my systems and they are running very well.  I was running 8.04 up to a couple of months ago - then upgraded to 10.04.

Brian S.
[http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/](http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/)

---

