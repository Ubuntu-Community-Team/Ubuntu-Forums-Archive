---
title: "Wine mouse cursor problems when using a 3D DirectX application."
date: 2012-01-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bejiitas_wrath on 2012-01-29
Hello there.

I am using a program, Doombuilder 1.68 and this is a Doom map editor I am running with Wine 1.3.37 on Ubuntu 12.04 Precise. Previously the 3D viewing mode would work perfectly with my version of Wine, but after installing some updates to upgrade to a newer version of Wine, the mouse cursor will no longer work properly.

When I move the mouse to look around in the 3D viewing mode it will spin around crazily and it is very difficult to aim it at something. I have installed DirectX 10 downloaded from the web and it worked fine until now. Is there a way to downgrade the Wine packages to fix this error or should I wait until this is fixed?

---

### Post by overdrank on 2012-01-29
Moved to Ubuntu +1 (Precise Pangolin)

---

### Post by sonnet on 2012-01-29
How did you install wine 1.3.37?
I added the wine repository,
but when I open synaptic and search for wine I find (just doing now after I updated the rep):
- wine : latest stable 1.2
- wine 1.3 : stuck at version 1.3.28
- wine1.3:i386  : this is at version 1.3.37
**_But I have ubuntu 64bit.._**

Also it is supposed to be the first rc of the 1.4 (which is the version after 1.3.37). But only the packages wine1.3-gecko* are listed as 1.4

---

### Post by bejiitas_wrath on 2012-01-30
> **sonnet said:**
> How did you install wine 1.3.37?
I added the wine repository,
but when I open synaptic and search for wine I find (just doing now after I updated the rep):
- wine : latest stable 1.2
- wine 1.3 : stuck at version 1.3.28
- wine1.3:i386  : this is at version 1.3.37
**_But I have ubuntu 64bit.._**

Also it is supposed to be the first rc of the 1.4 (which is the version after 1.3.37). But only the packages wine1.3-gecko* are listed as 1.4
This is the Wine version I have on Ubuntu 12.04 with the latest updates.

```

john@deep-thought ~ $ wine --version
wine-1.3.37
john@deep-thought ~ $ 

```I am wanting to know how to downgrade this Wine version or if this bug can be fixed.

And this is a copy of my /etc/apt/sources.lst file.

```

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Alpha i386 (20100803.1)]/ precise main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://au.archive.ubuntu.com/ubuntu/ precise universe
deb http://au.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://au.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review                                                             
## or updates from the Ubuntu security team.                                                                                            
# deb http://au.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse                                        
# deb-src http://au.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse                                    
                                                                                                                                        
## Uncomment the following two lines to add software from Canonical's                                                                   
## 'partner' repository.                                                                                                                
## This software is not part of Ubuntu, but is offered by Canonical and the                                                             
## respective vendors as a service to Ubuntu users.                                                                                     
# deb http://archive.canonical.com/ubuntu precise partner                                                                               
# deb-src http://archive.canonical.com/ubuntu precise partner                                                                           
                                                                                                                                        
deb http://security.ubuntu.com/ubuntu precise-security main restricted                                                                  
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted                                                              
deb http://security.ubuntu.com/ubuntu precise-security universe                                                                         
deb-src http://security.ubuntu.com/ubuntu precise-security universe                                                                     
deb http://security.ubuntu.com/ubuntu precise-security multiverse                                                                       
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

```

if I coment out the multiverse repository and then run **sudo apt-get update && sudo apt-get upgrade** will this fix my problem?

---

### Post by vhaarr on 2012-01-31
I think you need to downgrade the x server and all related packages, because WINE does not yet support the XInput changes in xserver 1.12 as far as I know.

---

### Post by P-I H on 2012-01-31
I have the same problem, which started after the upgrade to xserver 1.12.
I suppose it will be fixed before the release.

---

### Post by NepenthesXD on 2012-03-02
Same bug here.
I posted on the Wine forums, it seems nobody took it seriously.
[http://forum.winehq.org/viewtopic.php?t=14676](http://forum.winehq.org/viewtopic.php?t=14676)

---

### Post by NepenthesXD on 2012-03-07
Here is the bug report on Launchpad :
[https://bugs.launchpad.net/ubuntu/+source/xinput/+bug/948938](https://bugs.launchpad.net/ubuntu/+source/xinput/+bug/948938)

Please report here if you experience this bug.

---

