---
title: "gdebi password issue"
date: 2013-04-19
forum: Ubuntu Development Version
---

### Post by carl4926 on 2013-04-19
Latest incarnation of +1
Gdebi is claiming incorrect password

Synaptic and Software Centre are fine

---

### Post by dino99 on 2013-04-19
purge it
search *gdebi* inside /home & system to purge the settings left behind
reinstall gdebi

but the question is : why dont you simply use "sudo dpkg -i <package name>"

---

### Post by sgage on 2013-04-19
gdebi will download dependencies if necessary, dpkg will not.

I am getting the same error. You can use the Ubuntu Software Center - that will pull in dependencies if necessary.

---

### Post by carl4926 on 2013-04-19
> **sgage said:**
> gdebi will download dependencies if necessary, dpkg will not.

I am getting the same error. You can use the Ubuntu Software Center - that will pull in dependencies if necessary.
Yes doing that already
gdebi seems less of a hog - though SC seems improved

---

### Post by pqwoerituytrueiwoq on 2013-04-19
i used gdebi the other day with no issue
used it to install this deb and it worked fine
[http://download.opensuse.org/repositories/home:/alex_sh/Ubuntu_12.04/amd64/gsmartcontrol_0.8.7+nmu1_amd64.deb](http://download.opensuse.org/repositories/home:/alex_sh/Ubuntu_12.04/amd64/gsmartcontrol_0.8.7+nmu1_amd64.deb)

i use use gdebi to open downloaded deb files as it opens much faster than the software center

---

### Post by sgage on 2013-04-19
speed is why I use gdebi as well. This password problem is fairly recent. I notice that if I run a program from Alt-F2 using gksu, it gives the same error. Using gksudo, it does not. This seems odd to me, because gksudo is just a symlink to gksu!. And the two give slightly different authentication dialogs - the gksu one offers to remember the password, the gksudo one does not. I don't know how that can be, but there it is.

I found a fix - run 'gksu-properties' and change the Authentication Mode from 'su' to 'sudo'. Not sure if there are any security issues with this, but it works, and gdebi authenticates properly and all.

---

### Post by tdockery97 on 2013-04-19
I did a fresh install of the 4/19 daily build and the gdebi password problem had disappeared.

---

