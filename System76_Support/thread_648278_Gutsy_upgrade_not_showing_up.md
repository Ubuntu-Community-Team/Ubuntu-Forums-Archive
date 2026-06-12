---
title: "Gutsy upgrade not showing up"
date: 2007-12-23
forum: System76 Support
---

### Post by G-Dawg on 2007-12-23
I can't figure out why the gutsy upgrade isn't showing up on my update manager.  I'm still using feisty, have completed all other upgrades, but it just says my system is up to date.  No option for upgrading to gutsy!

Any ideas?

---

### Post by PmDematagoda on 2007-12-23
Post the results of:-

```
cat /etc/lsb-release
```
and
```
cat /etc/apt/sources.list
```
and
```
sudo apt-get update
```

---

### Post by G-Dawg on 2007-12-23
Update: "sudo update-manager -c" seemed to fix the problem.  Found that in another forum thread.  Not sure what it did but the update now shows up.

---

### Post by G-Dawg on 2007-12-23
Okay I spoke to soon, I thought I saw the gutsy upgrade button but it seems to have disappeared... here is what shows up when I run what you asked me for:

```
cat /etc/lsb-release
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"

```
cat /etc/apt/sources.list
```
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

```
sudo apt-get update
```[/QUOTE]
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Translation-en_CA                 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Translation-en_CA           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Translation-en_CA
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release.gpg [191B]        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Translation-en_CA      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release                             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Packages                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Packages                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Sources  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Fetched 3B in 2s (1B/s)
Reading package lists... Done

---

### Post by thomasaaron on 2007-12-24
I'm coming in a bit late on this conversation, but, in principle, you must first completely update your system:

(I'm assuming you're already running Feisty here, and not Edgy. You have to progress through all of them in order to reach Gutsy without a fresh install...)

sudo apt-get update && sudo apt-get --assume-yes dist-upgrade

Then you should be able to follow these directions:
[http://knowledge76.com/index.php/GutsyUpgrade](http://knowledge76.com/index.php/GutsyUpgrade)

---

### Post by SaurabhOnRails on 2008-03-11
HI There I am facing the Same problem,

here are the results of my commands, please help me with the upgrade .The same thing,my upgrade manager is not showing up the option to upgrade.I am on Feisty.

cat /etc/lsb-release

DISTRIB_DESCRIPTION="DebianEdu/Skolelinux (terra)"
DISTRIB_RELEASE=3.2
DISTRIB_CODENAME=etch

gedit /etc/apt/sources.list

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse


 sudo apt-get update

Password:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Translation-en_IN                 
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_IN
Get:3 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty Release.gpg [191B]         
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/main Translation-en_IN       
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/restricted Translation-en_IN 
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/universe Translation-en_IN
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/multiverse Translation-en_IN 
Get:4 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-updates Release.gpg [191B] 
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-updates/main Translation-en_IN
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-updates/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-updates/universe Translation-en_IN
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-updates/multiverse Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages         
Get:5 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-backports/main Translation-en_IN    
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-backports/restricted Translation-en_IN
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-backports/universe Translation-en_IN
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-backports/multiverse Translation-en_IN
Get:6 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Translation-en_IN           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Translation-en_IN             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Translation-en_IN           
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-security/main Translation-en_IN        
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Translation-en_IN         
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release           
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-security/restricted Translation-en_IN
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-security/universe Translation-en_IN
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-security/multiverse Translation-en_IN
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty Release
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-updates Release
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-backports Release
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-security Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release             
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/main Packages               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/restricted Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/universe Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/multiverse Packages
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-backports/main Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-security/main Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-security/universe Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-security/multiverse Packages
Get:8 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-updates/main Packages [239kB]
99% [8 Packages gzip 0]          
gzip: stdin: not in gzip format
Err [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty-updates/main Packages
  Sub-process gzip returned an error code (1)
Fetched 8B in 16s (0B/s)
Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://nl.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by thomasaaron on 2008-03-12
SaurabhOnRails,

That first command shows you are running Debian Etch (which we do not support), but your sources.list looks like you're running Feisty (which we do support). So, which is it?

If you're running Debian Etch, that will not upgrade to Gutsy. You;ll have to actually install Gutsy.

If you're running Feisty, you  must first completely update your system:
sudo apt-get update && sudo apt-get --assume-yes dist-upgrade

Then you should be able to follow these directions:
[http://knowledge76.com/index.php/GutsyUpgrade](http://knowledge76.com/index.php/GutsyUpgrade)

---

### Post by SaurabhOnRails on 2008-03-19
You are right, i think I might have installed some Kernel Patch of Etch,sometime, because I have been using Feisty on My system since the time It was released.
It always shows system up to date after running apt-get update.
For the time being I cant remove this because all my business data is on the system,I need to take a reliable backup and do stuff on my system.

If there something else you can suggest,Please do

Thanks

Saurabh

---

