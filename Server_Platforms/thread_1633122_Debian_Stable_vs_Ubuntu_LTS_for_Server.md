---
title: "Debian Stable vs Ubuntu LTS for Server?"
date: 2010-11-28
forum: Server Platforms
---

### Post by kevin11951 on 2010-11-28
Quick question:

Which is better platform for a professional use server?

Debian Stable or Ubuntu LTS?

The third party software we plan to use, works on both.  Which one is better on it own merits?  

Take into account things like the kernel (Ubuntu for example has its own custom kernel for servers), and other Ubuntu specific customizations.

I keep switching back and forth, and I need to decide so I can recommend one or the other to a client.  Right now, I think I am going to choose Debian Stable.

---

### Post by CharlesA on 2010-11-28
Whatever you want. I've used both and they are about equal.

---

### Post by kevin11951 on 2010-11-28
> **CharlesA said:**
> Whatever you want. I've used both and they are about equal.

Recently, I have had Ubuntu Server Edition 10.04.1 have a few strange issues...

I have Ubuntu setup to do automatic updates via a simple script, and every few months or so, libapache2-mod-php5 gets removed...  Thereby causing me to loose the php function of the web server.

Debian Stable has not done anything like this.

---

### Post by CharlesA on 2010-11-28
I have my 10.04 server completely up-to-date with apache and php and experienced no such problem.

Debian Stable would probably be easier to deal with. Either that or CentOS.

---

### Post by reddevil2064 on 2010-11-29
> **CharlesA said:**
> I have my 10.04 server completely up-to-date with apache and php and experienced no such problem.

Debian Stable would probably be easier to deal with. Either that or CentOS.

I can attest to how easy CentOS is to work with once it is up and running. Especially if stability and well tested packages are what you're looking for. That being said, Debian Stable and 10.04-LTS both have never given me trouble. I'm currently running 10.04 on a production server, full updated, and have only had 1 reboot in the 4 months(ish) time it's been running.

---

### Post by dozycat on 2010-11-29
One thing to consider if the hardware works with debian.
We have a server we wanted to work with debian but we had a problem with the video card so instead we installed ubuntu server and since then we are happy with it. But we are very careful with the upgrades.

---

### Post by CharlesA on 2010-11-29
> **reddevil2064 said:**
> I can attest to how easy CentOS is to work with once it is up and running. Especially if stability and well tested packages are what you're looking for. That being said, Debian Stable and 10.04-LTS both have never given me trouble. I'm currently running 10.04 on a production server, full updated, and have only had 1 reboot in the 4 months(ish) time it's been running.
The only time I've had to reboot is for certain security updates and kernel updates (whenever it prompts me with *** Restart Required ***)

But it's been more frequent since I'm not running anything like Ksplice on the box.

---

### Post by aeiah on 2010-11-29
ask the developers of the 3rd party software which they'd prefer, if they're going to be offering some kind of support.

ive had no problems with our basic LAMP running ubuntu 10.04. uptime is about 75 days right now. never used debian in a server though so i have nothing to compare against.

---

### Post by capscrew on 2010-11-29
It appears that Debian 6 (Squeeze) will have the ZFS file system available via the installer.  Debian with Sun Z Pools That's a big deal for those that have large storage needs.

Debian Stable is...well, just that.  a big +1 for Debian as a mission critical server.

---

### Post by kevinthecomputerguy on 2010-11-30
I can tell you that Debian is very very very stable.
 
Here is what i do. Try Debian first, if it loads, use it. If not use Ubuntu.
 
For the most part i do Debian for servers and Ubuntu for laptops and desktops. But there have been those times where Ubuntu is the only thing that will load.

---

### Post by mdlueck on 2010-11-30
I have had better success with Ubuntu that Debian which was our standard prior to switching to Ubuntu. The software we use seems to have better support for Ubuntu than Debian.

With Debian upgrades were horrid. Often we would end up reloading the box. With Ubuntu they have been pleasant for the most part.

---

