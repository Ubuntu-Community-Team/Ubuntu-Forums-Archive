---
title: "Disco as next 19.04 release"
date: 2018-10-30
forum: Ubuntu Development Version
---

### Post by dino99 on 2018-10-30
Its a very early news, but archives have been named and not populated yet.

Full name:  Disco Dingo
[https://launchpad.net/ubuntu/disco](https://launchpad.net/ubuntu/disco)

---

### Post by harry332 on 2018-10-30
You are fast nad early.
Disco Dingo, it is like Dancing Dog.
So, the toolchain has not been uploaded yet, or?

---

### Post by zika on 2018-10-30
```
[COLOR=#000000][FONT=Monaco]:~$ lsb_release -a[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]No LSB modules are available.[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]Distributor ID: Ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]Description:    Ubuntu Disco Dingo (development branch)[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]Release:        19.04[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]Codename:       disco
```[/FONT][/COLOR]

---

### Post by harry332 on 2018-10-30
Fine, the tool chain is uploaded.
And, everything is working fine.
First update is the python3.7.

---

### Post by LwIh%*7 on 2018-10-30
Hmm is that the actual name? 'cause there's an actual company called Disco Dingo LLC link [https://www.discodingo.com/](https://www.discodingo.com/) - could this cause problems for Canonical with them using a trademarked name?????

---

### Post by harry332 on 2018-10-31
No issues with this.
Disco Dingo is only a code name (two words).
About trademarks:
© 2018 Canonical Ltd. Ubuntu and Canonical are registered trademarks of Canonical Ltd.

---

### Post by zika on 2018-10-31
If You try a scenario to purge python2.7 and python3.6 You might get a glipse of where 19.04 is going... ;)

---

### Post by actionmystique on 2018-11-01
@[[COLOR=#000000]harry332[/COLOR]]("https://ubuntuforums.org/member.php?u=1842132")
Trying to upgrade from 18.10 to 19.04 is unsuccessful with: "do-release-upgrade --devel-release":

# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.10
Release:	18.10
Codename:	cosmic

# do-release-upgrade --devel-release
Checking for a new Ubuntu release
Upgrades to the development release are only 
available from the latest supported release.

---

### Post by cecilpierce on 2018-11-01
How do you upgrade from 18.10 to 19.04 ? 
I forgot, lost my notes !!!

---

### Post by slickymaster on 2018-11-01
> **cecilpierce said:**
> How do you upgrade from 18.10 to 19.04 ? 
I forgot, lost my notes !!!
```
sudo sed -i 's/cosmic/disco/g' /etc/apt/sources.list
sudo apt-get update && sudo apt-get upgrade
sudo reboot
```

---

### Post by harry332 on 2018-11-01
I always do the upgrade by manually changing the distro name in the file /etc/apt/sources.list and then by running the Synaptic Packaga Manager.
You just need to know the new distro name. For example Cosmic Cuttlefish is named "cosmic" and Disco Dingo is named "disco".

---

### Post by zika on 2018-11-01
Or, simply put, use &#8222;devel&#8220; and let the rolling distribution start. It works, also, with all the files for other ppa's in subfolder, at least it did for me for several releases for several years now... ;)

---

### Post by actionmystique on 2018-11-02
> **zika said:**
> Or, simply put, use „devel“ and let the rolling distribution start. It works, also, with all the files for other ppa's in subfolder, at least it did for me for several releases for several years now... ;)
Interesting trick which looks like **testing** for Debian instead of buster.
However, using it triggers a warning which may or may not raise issues: "Conflicting distribution"
```
# cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu devel main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu devel main restricted multiverse universe
# apt update
Get:1 http://archive.ubuntu.com/ubuntu devel InRelease [243 kB]
Get:2 http://archive.ubuntu.com/ubuntu devel/main Sources [826 kB]
Get:3 http://archive.ubuntu.com/ubuntu devel/restricted Sources [5,904 B]
Get:4 http://archive.ubuntu.com/ubuntu devel/multiverse Sources [189 kB]
Get:5 http://archive.ubuntu.com/ubuntu devel/universe Sources [9,337 kB]
Get:6 http://archive.ubuntu.com/ubuntu devel/main i386 Packages [1,007 kB]
Get:7 http://archive.ubuntu.com/ubuntu devel/main amd64 Packages [1,019 kB]
Get:8 http://archive.ubuntu.com/ubuntu devel/main Translation-en [513 kB]
Get:9 http://archive.ubuntu.com/ubuntu devel/main amd64 DEP-11 Metadata [475 kB]
Get:10 http://archive.ubuntu.com/ubuntu devel/main DEP-11 48x48 Icons [123 kB]
Get:11 http://archive.ubuntu.com/ubuntu devel/main DEP-11 64x64 Icons [237 kB]
Get:12 http://archive.ubuntu.com/ubuntu devel amd64 Contents (deb) [40.8 MB]
Get:13 http://archive.ubuntu.com/ubuntu devel i386 Contents (deb) [40.1 MB]
Get:14 http://archive.ubuntu.com/ubuntu devel/restricted amd64 Packages [9,304 B]
Get:15 http://archive.ubuntu.com/ubuntu devel/restricted i386 Packages [9,564 B]
Get:16 http://archive.ubuntu.com/ubuntu devel/restricted Translation-en [3,888 B]
Get:17 http://archive.ubuntu.com/ubuntu devel/multiverse amd64 Packages [158 kB]
Get:18 http://archive.ubuntu.com/ubuntu devel/multiverse i386 Packages [147 kB]
Get:19 http://archive.ubuntu.com/ubuntu devel/multiverse Translation-en [113 kB]
Get:20 http://archive.ubuntu.com/ubuntu devel/multiverse amd64 DEP-11 Metadata [48.5 kB]
Get:21 http://archive.ubuntu.com/ubuntu devel/multiverse DEP-11 48x48 Icons [8,931 B]
Get:22 http://archive.ubuntu.com/ubuntu devel/multiverse DEP-11 64x64 Icons [221 kB]
Get:23 http://archive.ubuntu.com/ubuntu devel/universe i386 Packages [8,735 kB]
Get:24 http://archive.ubuntu.com/ubuntu devel/universe amd64 Packages [8,792 kB]
Get:25 http://archive.ubuntu.com/ubuntu devel/universe Translation-en [5,058 kB]
Get:26 http://archive.ubuntu.com/ubuntu devel/universe amd64 DEP-11 Metadata [3,378 kB]
Get:27 http://archive.ubuntu.com/ubuntu devel/universe DEP-11 48x48 Icons [2,546 kB]
Get:28 http://archive.ubuntu.com/ubuntu devel/universe DEP-11 64x64 Icons [8,424 kB]
Fetched 133 MB in 21s (6,311 kB/s)                                                                                                                           
Error: Timeout was reached
Reading package lists... Done
Building dependency tree       
Reading state information... Done
111 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Conflicting distribution: http://archive.ubuntu.com/ubuntu devel InRelease (expected devel but got disco)

```

So I reverted back to disco.

---

### Post by mrfelker on 2018-11-02
Did you try sudo update-manager -d.?   I had no problems doing the upgrade this way.   Also you can now download an iso from the ubuntu daily servers if you want a clean/VM install.

---

### Post by jbicha on 2018-11-02
> **mrfelker said:**
> Also you can now download an iso from the ubuntu daily servers if you want a clean/VM install.

The installer isn't working yet. See the [other thread]("https://ubuntuforums.org/showthread.php?t=2405196").

---

### Post by VMC on 2018-11-02
Lubuntu 19.04 Disco ISO, on the other hand installs. It uses Calamares installer instead of Ubiquity.

---

### Post by zika on 2018-11-03
> **actionmystique said:**
> Interesting trick which looks like **testing** for Debian instead of buster.
However, using it triggers a warning which may or may not raise issues: "Conflicting distribution"
So I reverted back to disco.Those warnings are OK. Just informing You that there is a reroute to latest distro... No harm, just warning.

---

### Post by cariboo on 2018-11-03
I just upgraded to Disco using:

```
sudo sed -i 's/cosmic/disco/g' /etc/apt/sources.list
```

and

```
sudo apt update && sudo apt dist-upgrade
```

and so it begins. :)

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=19.04
DISTRIB_CODENAME=disco
DISTRIB_DESCRIPTION="Ubuntu Disco Dingo (development branch)
```

---

