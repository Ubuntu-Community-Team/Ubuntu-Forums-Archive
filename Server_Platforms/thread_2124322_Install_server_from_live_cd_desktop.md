---
title: "Install server from live cd desktop"
date: 2013-03-10
forum: Server Platforms
---

### Post by MadsRH on 2013-03-10
Hi

Is it possible to install the latest Ubuntu server (LAMP) from an old desktop live cd?

---

### Post by Cheesemill on 2013-03-10
The components that make up the LAMP stack are available in the standard Ubuntu repositories. They can be installed on any version of Ubuntu.

You'll need an internet connection to install them if you only have a desktop CD, as only the server installation CD contains the packages.

---

### Post by lykwydchykyn on 2013-03-10
technically, yes, but it's not terribly easy.  It involves the "debbootstrap" command.

Here's a writeup I did on how to install Debian with this method, but the same can apply to Ubuntu as well.  

[http://www.alandmoore.com/blog/2011/12/29/how-to-install-debian-offline/](http://www.alandmoore.com/blog/2011/12/29/how-to-install-debian-offline/)

---

### Post by MadsRH on 2013-03-10
> **lykwydchykyn said:**
> technically, yes, but it's not terribly easy.  It involves the "debbootstrap" command.

Here's a writeup I did on how to install Debian with this method, but the same can apply to Ubuntu as well.  

[http://www.alandmoore.com/blog/2011/12/29/how-to-install-debian-offline/](http://www.alandmoore.com/blog/2011/12/29/how-to-install-debian-offline/)

OMG! I was hoping there was some kind of **sudo apt-get installer ubuntu lamp server** :(

It's an old computer that can't boot from USB and I don't have any empty CD-ROMs. But I think I will head down to the store to buy some tomorrow - that'll proberly be easier.

Thanks for the answer both of you

---

### Post by tgalati4 on 2013-03-10
Close:

```
sudo apt-get install tasksel
```

Run tasksel and pick LAMP.

---

### Post by steeldriver on 2013-03-11
> **MadsRH said:**
> OMG! I was hoping there was some kind of **sudo apt-get installer ubuntu lamp server** :(


**If** you have access to the repositories here's almost exactly that:-

```

$ sudo apt-get install **lamp-server^**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'apache2-utils' for task 'lamp-server'
Note, selecting 'libwrap0' for task 'lamp-server'
.
.
.
Note, selecting 'apache2' for task 'lamp-server'
Note, selecting 'mysql-server-core-5.5' for task 'lamp-server'
Note, selecting 'apache2.2-common' for task 'lamp-server'
Note, selecting 'mysql-server' for task 'lamp-server'
Note, selecting 'ssl-cert' for task 'lamp-server'
Note, selecting 'perl-modules' for task 'lamp-server'
Note, selecting 'libmysqlclient18' for task 'lamp-server'
Note, selecting 'php5-mysql' for task 'lamp-server'
Note, selecting 'php5-cli' for task 'lamp-server'
Note, selecting 'libapache2-mod-php5' for task 'lamp-server'
Note, selecting 'libaprutil1' for task 'lamp-server'
Note, selecting 'php5-common' for task 'lamp-server'

```

---

### Post by koenn on 2013-03-11
the OP is asking about doing it from a **live cd**. A live CD doesn't offer any of options like tasksel  etc, it just installs a default  desktop. You can add LAMP later, but you'll still running a standard ubuntu desktop. 

So either that (a desktop with LAMP), or lykwydchykyn's approach.

---

### Post by tgalati4 on 2013-03-11
I think you can boot a Live DVD, create a mountpoint on a harddisk, chroot into that mountpoint, then apt-get update and apt-get install server components (I don't know if there is a meta-package for that) then tasksel, then lamp.

---

### Post by lykwydchykyn on 2013-03-12
The OP was also asking about installing the **latest version** from an **old CD**.   If this is possible at all, it'd require debootstrap.

> 
I think you can boot a Live DVD, create a mountpoint on a harddisk, chroot into that mountpoint, then apt-get update and apt-get install server components (I don't know if there is a meta-package for that) then tasksel, then lamp. 


This is the method I laid out, except you can't just chroot into an empty directory and start doing apt-get.  You need the core OS there first, which is what the debootstrap command does.  In a nutshell, you:

- create partitions
- mount /
- run debootstrap on the / directory
- chroot into your new /
- apt-get install a kernel and grub

---

### Post by koenn on 2013-03-12
all in all, it's probably way easier to download the mini.iso (only a handfull of MB), burn a CD, and go.

---

### Post by MadsRH on 2013-03-12
Hi again. **THANKS **for all the feedback guys!

This old computer I'm using, is so old that it can't boot from USB. I didn't have a blank CD-ROM (who has such a legacy media laying around these days) and couldn't buy on because it was sunday. BUT now I've burned my very own 12.04.2 server disk and installed it :P

Everything works perfect, but there's an issue that I'll have to start a new thread about ( so I don't write two different questions in one post )

Thanks again!

---

### Post by koenn on 2013-03-13
> **MadsRH said:**
>  (who has such a legacy media laying around these days)

people who work/play with legacy hardware, i'd think ... :)

---

