---
title: "Upgrade from 10.4.1 LTS to 10.10 server"
date: 2010-10-11
forum: Server Platforms
---

### Post by Xylian on 2010-10-11
Hi,
some time ago I've installed Ubuntu LTS 10.4.1 on my linux server because I tought that the long-term-support version was the server version... then, I realized that there was also an Ubuntu Server edition... so, is it possible to upgrade my current installation to 10.10 Server edition? what should I do? 

Thank you very much, bye

---

### Post by Xylian on 2010-10-11
Should I simply modify the APT sources.list file?

```

# 
# deb cdrom:[Ubuntu-Server 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.2)]/ lucid main restricted

#deb cdrom:[Ubuntu-Server 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.2)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://it.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://it.archive.ubuntu.com/ubuntu/ lucid universe
deb http://it.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://it.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://it.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://it.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://it.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse


```

---

### Post by slakkie on 2010-10-11
There is no need to change anything. The server edition might only install a different type of kernel, which you can install yourself. There is no need to install the 10.10 server edition (10.04 has a server edition as well.. ).

```

# The -s is to simulate the action, remove if everything is ok.
# The -y is to say yes on all questions, remove if you want to 
# do stuff interactivly.
$ aptitude install -s -y linux-{image,headers}-server  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following NEW packages will be installed:
  linux-headers-2.6.32-25-generic-pae{a} linux-headers-generic-pae{a} linux-headers-server 
  linux-image-2.6.32-25-generic-pae linux-image-generic-pae linux-image-server 
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 32.4MB of archives. After unpacking 109MB will be used.
Would download/install/remove packages.

```

Then reboot, select the correct kernel and there is your server edition of Ubuntu.


And upgrading is done differently, see my signature for a link to the wiki on how to upgrade Ubuntu :)

---

### Post by Xylian on 2010-10-11
I've just found the following link: [Network Upgrade for Ubuntu Servers (Recommended)]("https://help.ubuntu.com/community/MaverickUpgrades#Network%20Upgrade%20for%20Ubuntu%20Servers%20%28Recommended%29")

I'm backing up my installation and then I'll try what is suggested at the above link.. BTW, thank you ;-)

---

### Post by slakkie on 2010-10-11
> **Xylian said:**
> I've just found the following link: [Network Upgrade for Ubuntu Servers (Recommended)]("https://help.ubuntu.com/community/MaverickUpgrades#Network%20Upgrade%20for%20Ubuntu%20Servers%20%28Recommended%29")

I'm backing up my installation and then I'll try what is suggested at the above link.. BTW, thank you ;-)
It explains the same details as the guide in the link in my signature. Best of luck!

Be ware though, it will not upgrade you to a "server edition" it will just do the upgrade from the command line (without a GUI). If you don't have the linux-{image,headers}-server packages installed, you will not get them by running do-release-upgrade. You will still need to install them manually. Eitherway, best of luck.

---

### Post by Xylian on 2010-10-11
> **slakkie said:**
> It explains the same details as the guide in the link in my signature. Best of luck!

Be ware though, it will not upgrade you to a "server edition" it will just do the upgrade from the command line (without a GUI). If you don't have the linux-{image,headers}-server packages installed, you will not get them by running do-release-upgrade. You will still need to install them manually. Eitherway, best of luck.

If I remember well (I don't have a pc while I'm writing), you can tell to the do-release-upgrade command that you are upgrading a server... Doesn't this work?

Btw, I need latest drivers (like the ath9k ones, for which I'm using 2.6.35 backports on 2.6.32), so should I use server or desktop edition for this purpose?

---

### Post by Xylian on 2010-10-12
> **slakkie said:**
> It explains the same details as the guide in the link in my signature. Best of luck!

Be ware though, it will not upgrade you to a "server edition" it will just do the upgrade from the command line (without a GUI). If you don't have the linux-{image,headers}-server packages installed, you will not get them by running do-release-upgrade. You will still need to install them manually. Eitherway, best of luck.

I installed the linux-image-server package and now I'm trying to install the linux-backports-modules-wireless-2.6.35-lucid-server package but it says that it can not be installed.... what should I do?

```

root@ubuntu-alix-server:~# apt-get install linux-backports-modules-wireless-2.6.35-lucid-server
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Alcuni pacchetti non possono essere installati. Questo può voler dire
che è stata richiesta una situazione impossibile oppure, se si sta
usando una distribuzione in sviluppo, che alcuni pacchetti richiesti
non sono ancora stati creati o sono stati rimossi da Incoming.
Le seguenti informazioni possono aiutare a risolvere la situazione: 

I seguenti pacchetti hanno dipendenze non soddisfatte:
  linux-backports-modules-wireless-2.6.35-lucid-server: Dipende: linux-backports-modules-compat-wireless-2.6.35-2.6.32-25-server ma non è installabile  --> it can not be installed
E: Pacchetto danneggiato   --> packet damaged


```

---

### Post by Xylian on 2010-10-12
It seems that the linux-backports-modules-wireless-lucid-server package works only on 64-bit platforms:

[http://packages.ubuntu.com/lucid/linux-backports-modules-wireless-lucid-server](http://packages.ubuntu.com/lucid/linux-backports-modules-wireless-lucid-server)

The generic edition instead supports both i386 and amd64 architectures. So, I must stick to the generic one, since I have a 32-bit cpu (AMD Geode):

[http://packages.ubuntu.com/lucid/linux-backports-modules-wireless-lucid-generic](http://packages.ubuntu.com/lucid/linux-backports-modules-wireless-lucid-generic)

---

### Post by slakkie on 2010-10-12
Try installing:
linux-backports-modules-wireless-lucid-generic-pae

---

### Post by Xylian on 2010-10-12
> **slakkie said:**
> Try installing:
linux-backports-modules-wireless-lucid-generic-pae
It worked, but then I ran a diff on the generic and generic-pae kernel configurations and there are only differences regarding the support of large amounts of RAM and virtualization-related stuff. I did not find any difference about the scheduler and the kernel tick frequency, which I read somewhere should be different between desktop and server kernels, so I definitely do not need the generic-pae kernel and I could stick with the generic one.. What's your opinion?

---

### Post by slakkie on 2010-10-12
I've read that too.

[https://help.ubuntu.com/10.04/serverguide/C/preparing-to-install.html#intro-kernel-diffs](https://help.ubuntu.com/10.04/serverguide/C/preparing-to-install.html#intro-kernel-diffs)

However, I cannot find it here:
[https://help.ubuntu.com/community/ServerFaq](https://help.ubuntu.com/community/ServerFaq)

I would keep the pae kernel, assuming you have more then 3Gb of RAM available. Another option would be to ask the maillinglist (see bottom of the page of the last link) to validate if the statement in the server guide is still correct. The community wiki states something different. Or ask someone in #ubuntu-kernel on irc.

---

### Post by Xylian on 2010-10-13
> **slakkie said:**
> I've read that too.

[https://help.ubuntu.com/10.04/serverguide/C/preparing-to-install.html#intro-kernel-diffs](https://help.ubuntu.com/10.04/serverguide/C/preparing-to-install.html#intro-kernel-diffs)

However, I cannot find it here:
[https://help.ubuntu.com/community/ServerFaq](https://help.ubuntu.com/community/ServerFaq)

I would keep the pae kernel, assuming you have more then 3Gb of RAM available. Another option would be to ask the maillinglist (see bottom of the page of the last link) to validate if the statement in the server guide is still correct. The community wiki states something different. Or ask someone in #ubuntu-kernel on irc.

No, I have only 256Mb of RAM, so the PAE extensions are absolutely unnecessary.. my box is meant to run services like dhcpd, hostapd, named and to act as a router/firewall/AP, with a low power consumption (less than 10W), so it's not really a big server ;-)

EDIT: I've written a post on the ubuntu-server mailing list as you suggested:
[https://lists.ubuntu.com/archives/ubuntu-server/2010-October/004751.html](https://lists.ubuntu.com/archives/ubuntu-server/2010-October/004751.html)

---

### Post by slakkie on 2010-10-13
In that case I think the generic kernel will do just fine.

---

### Post by Xylian on 2010-10-13
> **slakkie said:**
> In that case I think the generic kernel will do just fine.
Yes, I agree with you... but no preemption, less frequent timer interrupts and a different scheduler would also be better for a server which does not need to process interactive jobs, so it was the main reason why I wanted to try the server version of the kernel... before realizing that it does not differ from the generic one. Maybe I'll try to configure and compile the kernel by myself, but I would like to avoid it..

---

