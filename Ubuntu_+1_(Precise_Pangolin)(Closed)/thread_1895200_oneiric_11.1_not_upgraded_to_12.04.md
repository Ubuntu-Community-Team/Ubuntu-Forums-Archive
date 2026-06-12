---
title: "oneiric 11.1 not upgraded to 12.04"
date: 2011-12-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by pdk on 2011-12-14
Updated my repository on 11.1 /etc/apt/sources.list
changed oneiric to precise.
Ran the upgrades using the update manager gui (it did not tell me a new distribution was available). The kernel did not update to 3.2 from 3.0
running on a 32 bit machine.
Looking at updates available I see that linux-image-3.2.0-4-generic is for 64 bit.
Is there 32 bit image available ?

Peter

---

### Post by Frogs Hair on 2011-12-14
12.04 will come as 64 bit by default when released .  An option to download 32 bit will be available when the release is final , but I don't know about right now . It appears the daily build is 64 bit .

---

### Post by nothingspecial on 2011-12-14
Moved to Ubuntu +1

---

### Post by grahammechanical on 2011-12-14
The 12.04 distribution will not be available until April 1204. It has not yet been developed. This is why update manager does not tell you that a new distribution is available.

What you can do and may be you have already done it is change some bits of 11.10 to the 12.04 bits as they are developed. When I run System Info it tells me that I am using 11.10. When I run System Monitor it says I am using Release 12.04 (Precise). It also says Kernel Linux 3.2.0-3. 

I did not get the 3.2 kernel through Update Manager. I got it through the Synaptic Package Manager. If you search for Kernel you may find that the 3.2 kernel is marked with a grey icon (exclamation mark) telling you that it is available for upgrade. Or, you can click Mark All Upgrades and then click Apply and see what you get. That is how I upgraded my 3.0 kernel to a 3.2 kernel.

You should also do daily updates. Then you will see your Oneiric/Precise OS turn into a Precise OS over the coming months.

Regards.

P.S. I am 64bit machine and OS.

P.P.S. Using Synaptic I see that the 3.2.0.3.3 kernel is marked for Upgrade to 3.2.0.4.4 kernel. Update manager does not yet give me that upgrade.

---

### Post by ventrical on 2011-12-14
sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list

then

sudo apt-get update && sudo apt-get dist-upgrade

then

sudo apt-get update

sudo apt-get upgrade

sudo update-grub

---

### Post by cariboo on 2011-12-14
If the op is running a 32bit version, his system will still be a 32bit system after the upgrade. 

@pdk, to see if you are actually running Precise, open a terminal and type the following command:

```
cat /etc/lsb-release
```

If your system has completed the upgrade, you should see the following output:

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"

```

---

### Post by BC59 on 2011-12-14
> **pdk said:**
> 
Is there 32 bit image available ?

You can install it from here manually:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc5-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc5-precise/)

---

### Post by paul_in_london on 2011-12-14
> **pdk said:**
> Updated my repository on 11.1 /etc/apt/sources.list
changed oneiric to precise.
Ran the upgrades using the update manager gui (it did not tell me a new distribution was available). The kernel did not update to 3.2 from 3.0
running on a 32 bit machine.
Looking at updates available I see that linux-image-3.2.0-4-generic is for 64 bit.
Is there 32 bit image available ?

Peter

I'm not sure why Update Manager (which I never use) is offering you a 64 bit kernel if you're running a 32 bit install.

If you've changed all of your sources.list entries from oneiric to precise you could run:

```
sudo aptitude update
sudo aptitude full-upgrade
```

but your system sounds in a strange state so you might be better off installing precise from a daily build:

cdimage.ubuntu.com/daily-live/current/

---

### Post by pdk on 2011-12-16
Thanks for all the replies.
When I first tried to install the 11.1 64 bit iso I got memory errors and assumed that I could only install 32bit version. I did install that.
Then I decided to upgrade to Pangolin.
When I looked at the kernels available in package manger I found that the 64 bit was shown. I installed it successfuly. Now I have a wonderful mix of software
lsb_release -a shows that I have pangolin 64 bit kernel
ldd /bin/bash shows i386.
Not to worry any more ...
It doesn't crash and I will make a plan
Peter

---

### Post by jbicha on 2011-12-16
Frogs Hair, I believe Ubuntu 12.04 will still be 32-bit by default since that works on all Intel-compatible PCs whereas 64-bit won't work on many netbooks and pre-Pentium D computers.

---

### Post by jerrylamos on 2011-12-17
BTW, upgrade after upgrade does in my experience use up more and more and more disk space....

So I do an install at milestones, like Alpha 1.  Much less disk space, but then updates start creeping in again.

precise pretty boring so far.  It's primarily to be a realy LTS maybe 5 years ? so they're not doing much to upset the apple cart.

Jerry

p.s. Always if using an "unstable" development release have at least one other partition with a "stable" release for recovery purposes. "unstables" can and will crash after an update. Example, if you've got an 11.10, then do a new partition install to 12.04 unstable.  5 GB is plenty I use 10 GB if available.

---

### Post by BC59 on 2011-12-17
I have the sense that installing a version on development at this early stage, has no sense, because the developers doesn't pay a lot of attention to our bug reports, since the whole system is not yet shaped.

---

### Post by fabricator4 on 2011-12-17
> **BC59 said:**
> I have the sense that installing a version on development at this early stage, has no sense, because the developers doesn't pay a lot of attention to our bug reports, since the whole system is not yet shaped.

Not really, the whole point of testing development releases is bug reports, from the developers point of view.

If the develops already know there are problems, or if there are many duplicate bug reports for a problem then it may seems as though they slow or even uninterested.

Chris

---

### Post by cariboo on 2011-12-17
> **BC59 said:**
> I have the sense that installing a version on development at this early stage, has no sense, because the developers doesn't pay a lot of attention to our bug reports, since the whole system is not yet shaped.

If you aren't getting any action on bug reports you have submitted, you may be doing it wrong. I'd suggest you review [this]("https://help.ubuntu.com/community/ReportingBugs") wiki page.

---

