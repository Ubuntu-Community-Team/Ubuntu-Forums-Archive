---
title: "apt-get update problem"
date: 2005-05-10
forum: Repositories &amp; Backports
---

### Post by ron126 on 2005-05-10
when i "apt-get update" in root, i get this...


Err [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/main Packages
  403 Forbidden
Ign [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/main Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Packages
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Release [102B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Err [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/universe Packages
  403 Forbidden
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Packages
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Release [108B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Release [104B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Sources
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Release [110B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Release
Ign [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/universe Release
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Release
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Release
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Release
Fetched 424B in 11s (38B/s)
Failed to fetch [http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/main/binary-i386/Packages.gz](http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/universe/binary-i386/Packages.gz](http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/universe/binary-i386/Packages.gz)  403 Forbidden
Reading Package Lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


What can i do to correct this?
Help appreciated.

---

### Post by nemin on 2005-05-10
[QUOTE=ron126]
[http://ubuntu-bp.sourceforge.net[/url] forbidden]
Reading Package Lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
[/QUOTE]
Quote from [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net)
"As of 02/08/2005, Ubuntu backports has officially moved to the UbuntuForums site. You will be redirected momentarily.
Update your bookmarks & sources.list!"

See [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

### Post by ron126 on 2005-05-10
To edit the source.list, i need to become root, or else it's read only. How do i exactly do it??  :-#

---

### Post by ron126 on 2005-05-10
oh, i just got it, thanks nemin! you're greaT!

---

### Post by ron126 on 2005-05-10
eb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) distribution sections separated by a space


 ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe




I add a line at the top.  Is this correct? Or can anyone copy and paste the standard one please.

Please help.

---

### Post by nemin on 2005-05-10
[QUOTE=ron126]eb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) distribution sections separated by a space


 ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe




I add a line at the top.  Is this correct? Or can anyone copy and paste the standard one please.
[/QUOTE]
You mean the CD-rom line? Insert your CD-rom and enter ```
apt-cdrom add
``` to be sure you have to correct one.

---

### Post by ron126 on 2005-05-10
Nono, no cd rom,i just want to edit my sourcefile.list but i thought i did something wrong. Did i add the line correctly? I also saw the Hoary configuration, must i add them too? How to add the line correcT? 

Please help.

---

### Post by ron126 on 2005-05-10
[PHP]deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted


## Uncomment the following two lines to fetch updated software from the network

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe[/PHP]


This is what is inside my sourcelist.


And when i apt-get update, this is what i get


[PHP]Err http://ubuntu-bp.sourceforge.net warty-backports/main Packages
  403 Forbidden
Ign http://ubuntu-bp.sourceforge.net warty-backports/main Release
Get:1 http://backports.ubuntuforums.org hoary-backports/main Packages [8981B]
Err http://ubuntu-bp.sourceforge.net warty-backports/universe Packages
  403 Forbidden
Hit http://archive.ubuntu.com warty/main Packages
Hit http://security.ubuntu.com warty-security/main Packages
Hit http://security.ubuntu.com warty-security/main Release
Hit http://archive.ubuntu.com warty/main Release
Hit http://archive.ubuntu.com warty/restricted Packages
Hit http://archive.ubuntu.com warty/restricted Release
Hit http://archive.ubuntu.com warty/main Sources
Hit http://archive.ubuntu.com warty/main Release
Get:2 http://archive.ubuntu.com warty/restricted Sources [1024B]
Hit http://archive.ubuntu.com warty/restricted Release
Hit http://archive.ubuntu.com warty/main Packages
Hit http://archive.ubuntu.com warty/main Release
Hit http://archive.ubuntu.com warty/restricted Packages
Hit http://security.ubuntu.com warty-security/restricted Packages
Hit http://security.ubuntu.com warty-security/restricted Release
Hit http://security.ubuntu.com warty-security/main Sources
Hit http://security.ubuntu.com warty-security/main Release
Hit http://security.ubuntu.com warty-security/restricted Sources
Hit http://security.ubuntu.com warty-security/restricted Release
Ign http://ubuntu-bp.sourceforge.net warty-backports/universe Release
Get:3 http://backports.ubuntuforums.org hoary-backports/main Release [93B]
Get:4 http://backports.ubuntuforums.org hoary-backports/universe Packages [8772B]
Get:5 http://backports.ubuntuforums.org hoary-backports/universe Release [97B]
Get:6 http://backports.ubuntuforums.org hoary-backports/multiverse Packages [20B]
Get:7 http://backports.ubuntuforums.org hoary-backports/multiverse Release [99B]
Hit http://archive.ubuntu.com warty/restricted Release
Hit http://archive.ubuntu.com warty/main Sources
Hit http://archive.ubuntu.com warty/main Release
Get:8 http://archive.ubuntu.com warty/restricted Sources [1024B]
Get:9 http://backports.ubuntuforums.org hoary-backports/restricted Packages [20B]
Get:10 http://backports.ubuntuforums.org hoary-backports/restricted Release [99B]
Get:11 http://backports.ubuntuforums.org hoary-extras/main Packages [2131B]
91% [Waiting for headers] [11 Packages 347/2131B 16%] [Connecting to ftp.nerim.net (2001:7a8:1:5::14)]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com warty/restricted Sources
  Sub-process gzip returned an error code (1)
Get:12 http://backports.ubuntuforums.org hoary-extras/main Release [90B]
Get:13 http://backports.ubuntuforums.org hoary-extras/universe Packages [854B]
Get:14 http://backports.ubuntuforums.org hoary-extras/universe Release [94B]
Get:15 http://backports.ubuntuforums.org hoary-extras/multiverse Packages [20B]
Hit http://archive.ubuntu.com warty/restricted Release
Hit http://archive.ubuntu.com warty/universe Packages
Hit http://archive.ubuntu.com warty/universe Release
Hit http://archive.ubuntu.com warty/universe Sources
Hit http://archive.ubuntu.com warty/universe Release
Hit http://archive.ubuntu.com warty/multiverse Packages
Get:16 http://backports.ubuntuforums.org hoary-extras/multiverse Release [96B]
Get:17 http://backports.ubuntuforums.org hoary-extras/restricted Packages [3959B]
Get:18 http://backports.ubuntuforums.org hoary-extras/restricted Release [96B]
Hit http://archive.ubuntu.com warty/multiverse Release
Hit http://archive.ubuntu.com warty/multiverse Sources
Hit http://archive.ubuntu.com warty/multiverse Release
Hit ftp://ftp.nerim.net stable/main Packages
Hit ftp://ftp.nerim.net stable/main Release
Hit ftp://ftp.nerim.net unstable/main Packages
Hit ftp://ftp.nerim.net unstable/main Release
Hit ftp://ftp.nerim.net testing/main Packages
Hit ftp://ftp.nerim.net testing/main Release
Fetched 26.5kB in 15s (1731B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/restricted/source/Sources.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/universe/binary-i386/Packages.gz  403 Forbidden
Reading Package Lists... Done
W: Duplicate sources.list entry http://archive.ubuntu.com warty/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com warty/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.[/PHP]

Please help.

---

### Post by nemin on 2005-05-10
Please do yourself a favour and start with a new sources.list, based on this one:
[http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)

---

### Post by ron126 on 2005-05-10
When i "gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907" after i saved the editted file, it gives a connection timeout message after waiting for a long while. Is anything wrong?

this is the error message

```
gpg: can't get key from keyserver: Connection timed out
gpg: Total number processed: 0
```


Please help.

---

### Post by nemin on 2005-05-10
[QUOTE=ron126]When i "gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907" after i saved the editted file, it gives a connection timeout message after waiting for a long while. Is anything wrong?[/QUOTE]
This is not a necessary step, you can skip it if you want AFAIK.

---

### Post by ron126 on 2005-05-10
Ok, i copy the source list from the sample, the one with backport resporitories, and then i apt-get update again, and this is what happen..

[PHP]Err cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages
  Please use apt-cdrom to make this CD recognized by APT. apt-get update cannot be used to add new CDs
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Release
Err cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages
  Please use apt-cdrom to make this CD recognized by APT. apt-get update cannot be used to add new CDs
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Release
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/main Release
Hit http://security.ubuntu.com hoary-security/main Packages
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://archive.ubuntu.com hoary/multiverse Release
Get:1 http://security.ubuntu.com hoary-security/main Release [102B]
Get:2 http://backports.ubuntuforums.org hoary-backports/main Packages [8981B]
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://archive.ubuntu.com hoary/multiverse Release
Hit http://security.ubuntu.com hoary-security/restricted Packages
Get:3 http://security.ubuntu.com hoary-security/restricted Release [108B]
Hit http://security.ubuntu.com hoary-security/main Sources
Get:4 http://security.ubuntu.com hoary-security/main Release [104B]
Hit http://security.ubuntu.com hoary-security/restricted Sources
Get:5 http://security.ubuntu.com hoary-security/restricted Release [110B]
Hit http://security.ubuntu.com hoary-security/universe Packages
Get:6 http://security.ubuntu.com hoary-security/universe Release [106B]
Hit http://security.ubuntu.com hoary-security/universe Sources
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Get:7 http://security.ubuntu.com hoary-security/universe Release [108B]
Hit http://us.archive.ubuntu.com hoary/restricted Release
Hit ftp://ftp.nerim.net stable/main Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit ftp://ftp.nerim.net stable/main Release
Hit http://us.archive.ubuntu.com hoary/main Release
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit ftp://ftp.nerim.net unstable/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Release
Hit ftp://ftp.nerim.net unstable/main Release
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit ftp://ftp.nerim.net testing/main Packages
Get:8 http://us.archive.ubuntu.com hoary-updates/main Release [101B]
Hit ftp://ftp.nerim.net testing/main Release
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Get:9 http://us.archive.ubuntu.com hoary-updates/restricted Release [107B]
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Get:10 http://us.archive.ubuntu.com hoary-updates/main Release [103B]
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Get:11 http://us.archive.ubuntu.com hoary-updates/restricted Release [109B]
Hit http://us.archive.ubuntu.com hoary/universe Packages
Hit http://us.archive.ubuntu.com hoary/universe Release
Hit http://us.archive.ubuntu.com hoary/universe Sources
Hit http://us.archive.ubuntu.com hoary/universe Release
Get:12 http://backports.ubuntuforums.org hoary-backports/main Release [93B]
Get:13 http://backports.ubuntuforums.org hoary-backports/universe Packages [8772B]
Get:14 http://backports.ubuntuforums.org hoary-backports/universe Release [97B]
Get:15 http://backports.ubuntuforums.org hoary-backports/multiverse Packages [20B]
Get:16 http://backports.ubuntuforums.org hoary-backports/multiverse Release [99B]
Get:17 http://backports.ubuntuforums.org hoary-backports/restricted Packages [20B]
Get:18 http://backports.ubuntuforums.org hoary-backports/restricted Release [99B]
Get:19 http://backports.ubuntuforums.org hoary-extras/main Packages [2131B]
Get:20 http://backports.ubuntuforums.org hoary-extras/main Release [90B]
Get:21 http://backports.ubuntuforums.org hoary-extras/universe Packages [854B]
Get:22 http://backports.ubuntuforums.org hoary-extras/universe Release [94B]
Get:23 http://backports.ubuntuforums.org hoary-extras/multiverse Packages [20B]
Get:24 http://backports.ubuntuforums.org hoary-extras/multiverse Release [96B]
Get:25 http://backports.ubuntuforums.org hoary-extras/restricted Packages [3959B]
Get:26 http://backports.ubuntuforums.org hoary-extras/restricted Release [96B]
Fetched 26.6kB in 1m5s (409B/s)
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD recognized by APT. apt-get update cannot be used to add new CDs
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD recognized by APT. apt-get update cannot be used to add new CDs
Reading Package Lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.[/PHP]


What should i do?

Please help.

---

### Post by mrshark on 2005-05-11
[QUOTE=ron126]When i "gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907" after i saved the editted file, it gives a connection timeout message after waiting for a long while. Is anything wrong?
this is the error message
```
gpg: can't get key from keyserver: Connection timed out
gpg: Total number processed: 0
```
Please help.[/QUOTE]
i used the following, because wwwkeys.eu.pgp.net was unaccessible for 2 weeks, till now...

keyserver.kjsl.com

---

### Post by nemin on 2005-05-11
[QUOTE=ron126]Ok, i copy the source list from the sample, the one with backport resporitories, and then i apt-get update again, and this is what happen..

[apt-get update output]

What should i do?
[/QUOTE]Remove the CD lines from sources.list and use ```
apt-cdrom add 
```to add them again.

---

### Post by ron126 on 2005-05-11
Which CD lines? Is it the first line? I've try to edit the first line in various ways but it just cant apt-get update. Please show me the model of how the line should be editted.
This is my sources.list...


[PHP]deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main

deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted[/PHP]


Pleae help. Thanks

---

### Post by fng on 2005-05-11
Are you using warty or hoary?

In the first posts, you have warty sources, in the last posts, you have hoary sources.

---

### Post by nemin on 2005-05-12
[QUOTE=ron126]Which CD lines? Is it the first line? I've try to edit the first line in various ways but it just cant apt-get update. [/QUOTE]
*Remove* it. Even better, remove your whole sources.list and create a new one. Add at least:
```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

``` 
And if you want:
```
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse
```
Then do apt-get update.
If it still doesn't work, post the whole error message and your whole sources.list. Hope this helps.

---

### Post by ron126 on 2005-05-12
CheeeeeRR to Nemin, you're really great, it works finally.... :razz: 

thanks a million~~

---

