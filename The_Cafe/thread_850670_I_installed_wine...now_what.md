---
title: "I installed wine...now what?"
date: 2008-07-05
forum: The Cafe
---

### Post by adamogardner on 2008-07-05
Well I originally wanted it for my itunes.  but people say it won't work and it hasn't for me.  but let me ask:  I have a Verizon 595 aircard (broadband) that runs on a windows partition.  my fantasy is to get it to work on Ubuntu.  and I am taking two approaches so far since everyone has a different idea.  Is there a way to run my aircard through Wine and pour it to get internet?  I have no experience with this so please consider that your reply.

---

### Post by chucky chuckaluck on 2008-07-05
you could try safari for windows and foobar2000.

---

### Post by Separ on 2008-07-05
Don't use Wine to install the driver, use ndiswrapper. Latest version available at [ndiswrapper.sourceforge.net](ndiswrapper.sourceforge.net)

(Although check their supported cards list first, if it's not there it may still work though.)

And as for the Itunes thing, Songbird now has ipod support and it's interface is basically like itunes but what it does do is let you search internet music sites like Skreemr for tracks and you can download them in one click. [getsongbird.com](getsongbird.com)

---

### Post by mips on 2008-07-06
> **adamogardner said:**
> I have a Verizon 595 aircard (broadband) that runs on a windows partition.  my fantasy is to get it to work on Ubuntu.

Do you need this card to work in a mobile or desktop (fixed location) environment?

For desktop you have two options:
1. Buy a external ethernet router that this card plugs into.
2. Install the kpc650 linux driver

For mobile/laptop setup:
1. Install the kpc650 linux driver

For kpc650 driver google "ubuntu kpc650" or "linux kpc650" or see:
[http://ubuntuforums.org/showthread.php?t=77364](http://ubuntuforums.org/showthread.php?t=77364)
[https://forums.gentoo.org/viewtopic-t-427992.html](https://forums.gentoo.org/viewtopic-t-427992.html)
[http://www.linuxforums.org/forum/wireless-internet/76655-verizon-wireless-kyocera-kpc650-broadband-card.html](http://www.linuxforums.org/forum/wireless-internet/76655-verizon-wireless-kyocera-kpc650-broadband-card.html)

For external routers see:
[http://www.dlink.com/products/category.asp?cid=129&sec=0](http://www.dlink.com/products/category.asp?cid=129&sec=0)
[http://www.cradlepoint.com/mbr1000/mbr1000.php](http://www.cradlepoint.com/mbr1000/mbr1000.php)
[http://www.kyocera-wireless.com/kr2-router/](http://www.kyocera-wireless.com/kr2-router/)
[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1160093298732&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=9873239789B16](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1160093298732&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=9873239789B16)
[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175242816711&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=1671139789B17](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175242816711&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=1671139789B17)

I do not know who your service provider is bu I STRONGLY suggest you check with your SP and the router vendor that your card will work in it.

Please add the following tags to this post mobile,broadband,router as I can only add two tags.

---

