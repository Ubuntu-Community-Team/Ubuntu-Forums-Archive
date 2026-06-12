---
title: "Packages held back at upgrade ?"
date: 2012-04-03
forum: Server Platforms
---

### Post by Terry Su on 2012-04-03
I've tried to upgrade server several times and each time the following occurs:

> 8 packages can be updated.
6 updates are security updates.

Last login: Sun Apr  1 18:54:45 2012 from ks-184-2-104-72.dhcp.embarqhsd.net
terrys@ubusully:~$ sudo apt-get upgrade
[sudo] password for terrys: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  landscape-common linux-headers-server linux-image-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Each time I log in I see the 8 packages can be updated.  Nothing seems to change when i upgrade. Can someone please tell me what is going on.

---

### Post by jerrrys on 2012-04-03
The command would be:

sudo apt-get update && sudo apt-get upgrade

---

### Post by Bucky Ball on 2012-04-03
Err, upgrade to what? If 12.04 LTS, you would expect to get this message ...

12.04 not yet released, beta and still testing. If you are running servers in a production environment a 12.04 LTS upgrade is really not advised or a good idea.

(PS: If this is what you are doing and you are trying from 10.04, be reminded that 10.04 LTS server edition is supported until April 2015 so you have plenty of time. There is absolutely no rush and if it ain't broke, why fix it?) ;)

---

### Post by hawkmage on 2012-04-03
> **jerrrys said:**
> The command would be:

sudo apt-get update && sudo apt-get upgrade
Not what the OP is asking.  The upgrade command is holding back packages like the kernel.  

To update the kernel and other packages you can specifically install them by using "apt-get install" with the package names.

---

### Post by CharlesA on 2012-04-03
> **hawkmage said:**
> Not what the OP is asking.  The upgrade command is holding back packages like the kernel.  

To update the kernel and other packages you can specifically install them by using "apt-get install" with the package names.
Nah, you just need to tell it to do this:

```
sudo apt-get dist-upgrade
```

apt-get upgrade doesn't install new packages, it just updates existing ones.

---

### Post by hawkmage on 2012-04-03
I don't usually use dist-upgrade .  Using dist-upgrade tells APT to use "smart" conflict  resolution system, and it will attempt to upgrade the most important  packages at the expense of less important ones if necessary.  I like to control what get updated.

---

### Post by Terry Su on 2012-04-03
Now I'm a little confused and tired so I'm going to wait till tomorrow to do this.  I just use the apt-get upgrade to install updates to the server.  Usually everything goes well.  I'm not trying to go to a new LTS,  Just want to install updates.

Thanks for your help.  Later.

---

### Post by hawkmage on 2012-04-03
The apt-get command "dist-upgrade" is a bit confusing in that it it really doesn't do a distribution upgrade.  It just enables the "smart" conflict  resolution system.  

By doing an "sudo apt-get dist-upgrade" it will update packages and install new kernels as well as resolve package conflicts.

---

### Post by CharlesA on 2012-04-03
> **hawkmage said:**
> I don't usually use dist-upgrade .  Using dist-upgrade tells APT to use "smart" conflict  resolution system, and it will attempt to upgrade the most important  packages at the expense of less important ones if necessary.  I like to control what get updated.

apt-get upgrade is the same as aptitude safe-upgrade. It only updates currently installed packages. apt-get dist-upgrade is equivalent to aptitude full-upgrade. It even tells you what packages will be installed and asks you to confirm it.

[http://ubuntuforums.org/showthread.php?t=1916099](http://ubuntuforums.org/showthread.php?t=1916099)

As far as I know that is also the only way to update to a newer kernel version because it requires the installation of a new package.


> **Terry Su said:**
> Now I'm a little confused and tired so I'm going to wait till tomorrow to do this.  I just use the apt-get upgrade to install updates to the server.  Usually everything goes well.  I'm not trying to go to a new LTS,  Just want to install updates.

Thanks for your help.  Later.

```
sudo apt-get dist-upgrade
``` will install the updates that are being held back.

---

### Post by QIII on 2012-04-03
> **hawkmage said:**
> I don't usually use dist-upgrade .  Using dist-upgrade tells APT to use "smart" conflict  resolution system, and it will attempt to upgrade the most important  packages at the expense of less important ones if necessary.  I like to control what get updated.

You can still control what gets updated.

Just type "n" and press Enter to not install them.

If you don't update the ones held back, you are not in control of those getting updated either.

Furthermore, when the packages are all in order by the next time around you aren't in control either, unless you peruse the list, type "n" and press enter and then update the 7 or 8 out of 150 updates available.

Six of one, half dozen of the other.

---

### Post by hawkmage on 2012-04-03
> **CharlesA said:**
> apt-get upgrade is the same as aptitude safe-upgrade. It only updates currently installed packages. apt-get dist-upgrade is equivalent to aptitude full-upgrade. It even tells you what packages will be installed and asks you to confirm it.
In the [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto) it says about dist-upgrade" "it will attempt to upgrade the most important packages at the expense of less important ones if necessary"

It is the upgrade more important packages at the expense of less important ones that makes me hesitate at using it.

---

### Post by QIII on 2012-04-03
... if necessary ...

I've been using dist-upgrade for a long time with no catastrophic explosions and zombie attacks at my front door.

---

### Post by hawkmage on 2012-04-03
If there is a conflict and if it decides to sacrifice a less important package does it give any indication of what it is doing?  

I have been bit by blindly allowing an update to fix things.  

Everything works fine if you are using applications that are built by the Linux distro provider and usually any app you build from tarballs but vendor applications can be very temperamental with libraries being updated.  When I find a library dependency I will have a script that will match the suggested updates with the listed app libs and flag possible issues.

---

### Post by jerrrys on 2012-04-04
Well, I was curious so i tried an apt-get update followed by a dist-upgrade.  The dist-upgrade did upgrade my kernel, but I really expected more.  May if I was on 10o4 instead of 12o4 more upgrades would of been offered.

---

### Post by CharlesA on 2012-04-04
> **jerrrys said:**
> Well, I was curious so i tried an apt-get update followed by a dist-upgrade.  The dist-upgrade did upgrade my kernel, but I really expected more.  May if I was on 10o4 instead of 12o4 more upgrades would of been offered.
I've only really seen it update the kernel and maybe one other package, which I cannot recall at the moment. Running 10.04 here.

---

### Post by QIII on 2012-04-04
dist-upgrade does everything upgrade does with the addition of trying to resolve dependencies and the "hold backs".  I've seen it update tens of packages, plus kernels.

It's not going to update more than is available to update, of course, so there is no reason to think that you are going to get a huge number of updates every time.  If you are doing updates regularly you will only see a few at any given time.

I use dist-upgrade almost exclusively, particularly when using a development version.

---

### Post by QIII on 2012-04-04
> **hawkmage said:**
> If there is a conflict and if it decides to sacrifice a less important package does it give any indication of what it is doing?  

I have been bit by blindly allowing an update to fix things.  

Everything works fine if you are using applications that are built by the Linux distro provider and usually any app you build from tarballs but vendor applications can be very temperamental with libraries being updated.  When I find a library dependency I will have a script that will match the suggested updates with the listed app libs and flag possible issues.

And distro provided software can be temperamental when libraries aren't updated.

Again.  Six of one, a half dozen of the other.

---

### Post by Terry Su on 2012-04-04
I love this forum.  I don't have to use it too often but when I do response is quick and very informative.

Frankly Linux is intimidating to me but you folks are helping me around that.

I used  sudo apt-get distro-upgrade  and everything seemed to work fine.  AND I even kind of understand what happened and why.

Thank you all very much for your help.

---

### Post by jerrrys on 2012-04-05
Well, Im a little late in doing this post, but maybe others will find this interesting.

I have one copy of 10.04 that I use as my personal repository.  It has some 300 additional packages (plus dependencies) loaded on it and I thought this would be a good test of dist-upgrade.

So I did apt-get update/upgrade and then followed with a dist-upgrade.

And this time the kernel plus one package was upgraded :)

---

