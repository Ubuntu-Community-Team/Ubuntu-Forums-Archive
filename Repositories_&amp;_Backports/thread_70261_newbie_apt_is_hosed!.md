---
title: "newbie: apt is hosed?!"
date: 2005-09-29
forum: Repositories &amp; Backports
---

### Post by samakv on 2005-09-29
I was doing an upgrade and my baby nephew pushed the reset button. Now when going back, I did this: sudo apt-get update and I get the following output
> 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Packages
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/universe Packages [5456B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/multiverse Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages [111kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/universe Packages [4917B]
96% [5 Packages gzip 0]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Sub-process gzip returned an error code (1)
96% [6 Packages gzip 0]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/universe Packages
Sub-process gzip returned an error code (1)
Fetched 3474B in 3s (906B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary-updates/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


I'm using Hoary.

My old window$ self says I install everything again but I'd rather not. Is there a way to fix it instead of installing all over again? Everything else works except apt; Gnome, Open Office, Evolution, etc. I need some packages installed and, oh bother, I'd rather not install all over again. 

Please do respond and thank you.


Sam akv

---

### Post by adwait on 2005-09-29
Try
```

sudo apt-get install -f

```

---

### Post by lerrup on 2005-09-29
Off the top of my head, I would say use synaptic as it will give you hints on what to do in situations such as this ( I've had the same happen to me).

Just update, mark upgrades and follow what it says.

---

### Post by GTvulse on 2005-09-29
Hmmmm.... Try this:
```

sudo rm /var/lib/apt/lists/archive.*

```
refresh your apt lists:
```
apt-get update
```
rebuld your installed package database:
```
sudo apt-cache gencaches
```
and then try again:
```
sudo apt-get dist-upgrade
```

---

### Post by samakv on 2005-09-29
Tried all of the above. Then tried dradul's. After using dradul's solution, everything seems normal. Thanks.

All seems normal except some glitches. I think I can live with it for now until Breezy becomes official.

I can give post the latest output if anyone needs it.

samakv

---

