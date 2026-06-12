---
title: "Question regarding a site and an article"
date: 2009-10-24
forum: Security
---

### Post by brusegadi on 2009-10-24
Hello and thank you for reading my message.

I wanted to install an icons themes, and I was wondering if things like:

[http://linux.softpedia.com/get/Desktop-Environment/Icons/gTango-35664.shtml](http://linux.softpedia.com/get/Desktop-Environment/Icons/gTango-35664.shtml)

are safe.

On a second note, I came across this article on security:

[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

The claim is that to make ubuntu safer there are at least three modifications the user has to carry out: 
(i)   reconfigure shared memory
(ii)  disable ssh login
(iii) limit access to the "su" program

I know what (ii) means, so I tried to carry it out on my jaunty install.  To my surprise, the file /etc/ssh/sshd_config was not found.  Does that mean I am compromised, or does it mean that jaunty does not have that file by default (ie, that for jaunty, (ii) is already taken care of.)  
I do not know what (i) and (iii) mean, can someone explain?  Thank you for taking the time to read and respond to my message!

B

---

### Post by scorp123 on 2009-10-24
> **brusegadi said:**
>  On a second note, I came across this article on security:
[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)  Stupid article, IMHO. They make it sound as if Ubuntu was a big security risk out of the box. It certainly isn't. If you want to learn more about Ubuntu's security, stick to the "stickies" in the forum. 

> **brusegadi said:**
>  (ii)  disable ssh login  You didn't read correctly. Make sure you read stuff correctly before you follow any tutorials. You're not supposed to "disable ssh login", you're just supposed to disable "root login per SSH" ... But root's account isn't enabled per default on Ubuntu. So no reason to panic

> **brusegadi said:**
>  (iii) limit access to the "su" program  Not really relevant on Ubuntu for as long as the user with "sudo" access (usually the first user account that gets created during installation) keeps their password for themselves and for as long as "root" remains disabled (which is the case per default).

> **brusegadi said:**
>  I know what (ii) means, so I tried to carry it out on my jaunty install.  To my surprise, the file /etc/ssh/sshd_config was not found.  SSH server is not installed per default ;)  No installed software == that software's config files won't be around on your system. Plain simple as that.

> **brusegadi said:**
> Does that mean I am compromised You're not using Windows anymore. Let go of your Windows-thinking. Computers don't crash. Viruses don't exist. And "defragmenting disks" ... oh well. Here on Linux we have heard about that funny ritual Microsoft users waste their time with. But as our file systems try very very hard to avoid fragmentation in the first place we are excluded from doing that funny activity. But we have the famous "Bluescreen of Death" ... it exists as screensaver. :D

Enjoy your Linux. Oh, and as you don't have to waste time anymore with defragmenting disks and hunting for "anti-this" and "anti-that" programs, you may want to read this:

"Linux is not Windows"
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by wilee-nilee on 2009-10-24
There are a number of icon themes in synaptic you might start there.

---

### Post by brusegadi on 2009-10-24
Thanks!  I appreciate all the info.

---

