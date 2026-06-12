---
title: "Ubuntu &amp; Firefox [Version]"
date: 2009-09-09
forum: The Cafe
---

### Post by GreenDance on 2009-09-09
Hi, could someone tell me please, why does Ubuntu not carry the latest version of Firefox? :(

Many Thanks.

---

### Post by snowpine on 2009-09-09
Probably because you are using the Ubuntu release from April (9.04 Jaunty) or older? :) Firefox 3.5.x will be the default browser in next month's 9.10 Karmic Koala.

---

### Post by longtom on 2009-09-09
There is a way to install the newest FF in Ubuntu (those versions still supported).  Just have a search in the forums or google.  I use Ubuntu 8.04 and have the newest programs for what I need them to be new and have them added to sources so they update automatically when updates are available. (Office, Gimp, Opera...)

However, you are not going to find those in the standard repositories.  And when Karmic appears that FF version will be outdated as well - but tried and tested.  These repositories will be frozen as soon as that particular version is released.  Only the next version of Ubuntu will have newer software in it's standard repositories.

If it is too much hassle or you prefer to be bleeding edge all the time, look for a distro with rolling releases.  To avoid a flame war I will not come up with sample names, you'll find them I'm sure.

This is how I understand it.  Others are welcome to add and correct as necessary.

---

### Post by 3rdalbum on 2009-09-09
Ubuntu's software is stable - if you perform ordinary system updates, you will get bug fixes and security fixes, but you will not suddenly find that a program looks different or that a feature you used to use has gone (or has moved).

Firefox 3.5 isn't an automatic update for Ubuntu, partly because it's not been fully tested, and partly because the last thing a system administrator wants to do is get phone calls from clients complaining that their software looks different or (worse) no longer works properly.

Firefox 3.5 might not be an automatic update, but it is available in the repositories in the firefox-3.5 package.

---

### Post by wojox on 2009-09-09
I've got it

Firefox site says 3.5.2

My version Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.2) Gecko/20090803 Ubuntu/9.04 (jaunty) Shiretoko/3.5.2

---

### Post by GreenDance on 2009-09-09
I'm looking on my server, and noticed apache and php aren't the latest version either, seems the ubuntu team are slow on bringing the latest versions.:(

---

### Post by hockeytux on 2009-09-09
3.5 is just called Shiretoko (for the moment). You can download it from Mozilla's website as normal:

[HERE]("http://download.mozilla.org/?product=firefox-3.5.2&os=linux&lang=en-GB")

---

### Post by snowpine on 2009-09-09
> **GreenDance said:**
> I'm looking on my server, and noticed apache and php aren't the latest version either, seems the ubuntu team are slow on bringing the latest versions.:(

Read the replies to your original post... that's just not how Ubuntu works: it is a stable operating system with time-based releases. ;) If you are running 9.04 Jaunty, you get whichever versions were stable in April 2009. If you're running 8.04, you get whichever versions were stable in April 2008. And so forth.

If you ever have questions about which app versions are part of which Ubuntu release, check out:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by RabbitWho on 2009-09-09
I just downloaded the new version from the firefox website... 

Did I do something wrong?

I'm using swiftfox now anyway.

---

### Post by LowSky on 2009-09-09
> **GreenDance said:**
> I'm looking on my server, and noticed apache and php aren't the latest version either, seems the ubuntu team are slow on bringing the latest versions.:(

Ubuntu isn't late. It locks the version of software on each release. This means that the no application will be added that can potential not work or break your system. Sure no one expects Firefox to break an install, but its the norm of the release. and very simple to get the newest version.

---

### Post by wojox on 2009-09-09
> **RabbitWho said:**
> I just downloaded the new version from the firefox website... 

Did I do something wrong?

I'm using swiftfox now anyway.

You can download 3.5.2 from the repo's

---

### Post by GreenDance on 2009-09-09
how can i get the very latest apache php and mysql?

---

### Post by cariboo on 2009-09-09
Is there a compelling reason why you need the latest versions of Apache2 and Php5? Everything works well as it is and is secure.

---

### Post by GreenDance on 2009-09-09
> **cariboo907 said:**
> Is there a compelling reason why you need the latest versions of Apache2 and Php5? Everything works well as it is and is secure.

I guess not :-|

---

### Post by Earl_Maroon on 2009-09-09
To anyone who wants the most up-to-date Firefox, it can easily be updated with the Ubuntuzilla.py script.

[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

It should upgrade FF flawlessly.

---

### Post by snowpine on 2009-09-09
> **GreenDance said:**
> how can i get the very latest apache php and mysql?

By researching where to get the latest version (google?), then installing/compiling it yourself. Ubuntu is not going to change its release cycle for your convenience. :)

---

