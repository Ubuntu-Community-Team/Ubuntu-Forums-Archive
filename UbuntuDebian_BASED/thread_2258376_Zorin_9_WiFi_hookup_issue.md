---
title: "Zorin 9 WiFi hookup issue"
date: 2014-12-27
forum: Ubuntu/Debian BASED
---

### Post by jesselashcraft on 2014-12-27
Greetings Tribe!  Hope you had a good holiday.

I can't get my WiFi to engage.  It knows a strong signal is present but the arrows on the AWN keep turning and the "Connect" button on the Authentication box with password line never highlights for selection.  

I know I've got the right network selection and the hardware works because the WiFi is OK with XP (on the same machine). 

What can I try?  Please be specific.

Thanks in advance.

---

### Post by Bucky Ball on 2014-12-27
*Thread moved to **Ubuntu/Debian BASED**.*

Please be aware that the main support areas here are for 'questions regarding Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, and Mythbuntu.'

While you are welcome to post in this sub-forum, Zorin have a forum [HERE]("http://zoringroup.com/forum/viewforum.php?f=3").

Good luck.

---

### Post by jesselashcraft on 2014-12-27
> **Bucky Ball said:**
> Please be aware that the main support areas here are for 'questions regarding Ubuntu...

Thanks Bucky.  I'm new to the community and I don't know what I'm talking about most of the time. Since Zorin is based on Ubuntu, I thought I'd cast a broadest net for the widest array of expertise. 

So just to be clear, Ubuntu is the operating system and with all the programs and utilities included, that would be called Zorin.  Am I getting that right?

---

### Post by Rob Sayer on 2014-12-27
I don't blame anyone for trying here for something like this.  I've seen the zorin support site.

Having used mint I've had to search here and askubuntu before for similar issues I needed a backport for or whatever.  You will need to know which version of ubuntu it's based on, what wireless adapter you have, and probably the kinux kernel version.  But non ubuntu distros aren't actually supported here.  It'd probably be faster to look it up yourself.

Good luck and don't try anything that doesn't say it's for the ubuntu release your OS is based on.

---

### Post by Bucky Ball on 2014-12-27
All good. Most things that work for Ubuntu should work for Zorin (but that is a presumption on my part). ;)

As Rob Sayer mentioned, just make sure you know which Ubuntu kernel and release your Zorin is based on. Try this in a terminal:

```
uname -a
```

That should give you the kernel details. It should show something like:

```
3.13.0-43-generic
```

---

### Post by jesselashcraft on 2014-12-28
Thanks fellas.  That code yields: 

"Linux Transport-1300e 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:43:42 UTC 2014 i686 i686 i686 GNU/Linux"

Could it be a driver issue?

---

### Post by Bucky Ball on 2014-12-29
I believe 3.13.0-30-generic is a 14.04 kernel, but a very old one. Having no idea of Zorin I don't know where they're up to with the kernels, but 14.04 is currently at 3.13.0-43-generic.

Have you tried:
```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

That should get you to the newest kernel used in your version of Zorin, whatever that kernel might be. ;)

PS: The kernel you have indicates that your Zorin is based on Ubuntu Trusty 14.04 LTS.

---

