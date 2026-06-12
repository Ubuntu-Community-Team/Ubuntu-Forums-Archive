---
title: "apt-get udate"
date: 2005-09-22
forum: Repositories &amp; Backports
---

### Post by naga123 on 2005-09-22
[IMG]Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
  403 Forbidden
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
  403 Forbidden
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
  403 Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
  403 Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Sources
  403 Forbidden
Reading package lists...[/IMG] 


when i tried to use apt-get update I am getiing this errors plz help me out
Before a week it worked fine. but now what is going wrong with this??

---

### Post by Xian on 2005-09-22
I'm reading into those 403's fine now.
Try another 'apt-get update'.

---

### Post by listen on 2005-09-23
sorry i am a newbie here...
i was trying to install vlc media player...thru synaptic pkt mngr and i get the following "warning" pop up box during start-up of the mngr..

W: Couldn't stat source package list [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary/main Packages (/var/lib/apt/lists/mirror.mcs.anl.gov_pub_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary/restricted Packages (/var/lib/apt/lists/mirror.mcs.anl.gov_pub_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)

i tried to do a "sudo apt-get install vlc" in the terminal window and  also get some error msgs regarding the ftp website...

i had downloaded the xmms prgram yesterday or the day b4...and there wasnt any errors during startup...

that is why i am finding out if the server is down or something...not sure how the SPM works in the first place....

regards
mark

---

### Post by Xian on 2005-09-23
Those "stat (2 No such file or directory)" errors are generally caused by not updating the most recent source list. Try the command below in a terminal and then attempt the package installation procedure again.

```
$ sudo apt-get update
```

---

### Post by listen on 2005-09-23
bingo......thanks XIAN...

---

### Post by naga123 on 2005-09-26
xian what do u mean by 
another "apt-get update"

---

### Post by christooss on 2005-09-26
run apt-get update again.

---

### Post by naga123 on 2005-09-26
same problem i.e., 403 forbidden

---

### Post by listen on 2005-09-26
normally, we do not need to use the "backports" repositories....have u tried commenting them out in the /etc/apt/sources.list file?

---

### Post by naga123 on 2005-09-28
ya, I tried but no use.
 what could be reason for 403 forbidden????

any body plz give me sources.list which works fine

---

### Post by XDevHald on 2005-09-28
The Backports are now Offical. [http://www.ubuntuforums.org/showthread.php?t=69681&highlight=Backports]("http://www.ubuntuforums.org/showthread.php?t=69681&highlight=Backports")

---

### Post by listen on 2005-09-28
below is mine 4 yr reference..  ..small hiccups once in a while due to the 'preview' edition of 'Breezy' but they get solved later by following updates usually......

regards
listen
PS: u might want to comment out the last 2 lines if u still have problems...
also did an update of the hoary backports ..courtesy from Steve Myers...thanks Steve

deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) breezy main restricted universe multiverse
deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) breezy main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) breezy-updates main restricted
deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) breezy-updates main restricted

deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) breezy-security main restricted
deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

#backup Mirror - FAST
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse
deb [ftp://ftp2.caliu.info/backports](ftp://ftp2.caliu.info/backports) hoary-extras main universe multiverse restricted

---

