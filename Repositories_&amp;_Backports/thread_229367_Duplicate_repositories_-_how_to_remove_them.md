---
title: "Duplicate repositories - how to remove them?"
date: 2006-08-04
forum: Repositories &amp; Backports
---

### Post by matjaz_pirnovar on 2006-08-04
> W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)


I have changed my sources.list, can explain how later and got duplicated repositories when running Update manager (checking for updates). At the end of checking a warning window popped up telling me that I have duplicate sources.list entries (see above).

How do I get rid of them?

Thanks.

Matjaz

---

### Post by ape on 2006-08-04
Open up a terminal and edit the /etc/apt/sources.list file.  You can remove the duplicate entries there.

---

### Post by matjaz_pirnovar on 2006-08-04
Hi, thankx.

Just, I don't want to mess things up, since they are repositories.

This is my /etc/apt/sources.list file:

What do I need to edit/delete here?

> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

Plus if you could comment if this list is commonly "okay" and if you'd add/change something in general?

Thanks, M

---

### Post by ape on 2006-08-04
This list looks just fine to me.  I also don't see why you're getting an error message.  I used your list above as my sources.list and didn't see any error message.

---

### Post by matjaz_pirnovar on 2006-08-04
Hey Ape,

Thanks for helping.

I don't know either...

I started changing sources.list after  "could not download all repositorie indexes" message, most of them were talking about bad header line or some sub.bz. error or similar (can check).

I believe somehow previous sources list retained some entries. Is that possible???? Before I used some gb. (British) mirrors. Now they are still there! Together with the new ones I think!? I think that could be the problem. What do you think?

Although I was looking into repositories in Synaptic manager, but there is no duplication although there are 12 entries (but maybe that's not related)

I'm posting previous sources.list here. Could you see any difference??

> deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free



Thanks,  M

---

### Post by matjaz_pirnovar on 2006-08-04
And this is my 'sudo apt-get update' list:

> matjaz@PCPlus:~$ sudo apt-get update
Password:
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release [30.9kB]
Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [44.2kB]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/multiverse Packages [866B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Get: 10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4275B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Get: 11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [12.3kB]
Get: 12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/universe Packages [15.4kB]
Get: 13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages [2043B]
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Get: 14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [11.0kB]
Get: 15 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]
Get: 16 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [1805B]
Get: 17 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources [533B]
Get: 18 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages [2043B]
Get: 19 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [12.3kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get: 20 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [30.9kB]
Get: 21 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [19.6kB]
Get: 22 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages [619kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
99% [22 Packages bzip2 0] [Waiting for headers]                     91.2kB/s 0sbzip2: (stdin) is not a bzip2 file.
Errhttp://archive.ubuntu.com dapper/main Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Get: 23 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [70.0kB]
Get: 24 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get: 25 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages [15.4kB]
Get: 26 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages [866B]
Get: 27 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [46.0kB]
Get: 28 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get: 29 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources [3129B]
Get: 30 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources [427B]
Get: 31 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [14B]
Get: 32 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get: 33 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [14B]
Get: 34 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Get: 35 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources [14B]
Get: 36 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Get: 37 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources [14B]
Get: 38 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources [14B]
Fetched 957kB in 27s (35.0kB/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
matjaz@PCPlus:~$



There are two things that stand out in above list and come up in my error and duplication notes:

> 99% [22 Packages bzip2 0] [Waiting for headers]                     91.2kB/s 0sbzip2: (stdin) is not a bzip2 file.
Errhttp://archive.ubuntu.com dapper/main Packages
  Sub-process bzip2 returned an error code (2)

and 

> W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

These two cause me problems. And there still are gb. entries, despite the fact that I erased previous sources.list (with gb.mirror - British).

There must be a way to clean it up...

Thanks, M

---

### Post by matjaz_pirnovar on 2006-08-05
Any ideas why I have the same sources.list as suggested in posting here ([http://www.ubuntuforums.org/showthread.php?t=229076]("http://www.ubuntuforums.org/showthread.php?t=229076")) and get a note on duplicate entries?

M

---

### Post by ape on 2006-08-06
I'm stumped guys.  I've taken both example sources.list files, copied them into my /etc/apt directory and run 'apt-get update', and in both cases, I don't get any errors regarding duplicate entries.

---

### Post by matjaz_pirnovar on 2006-08-06
Hey Ape,

Could you post your apt-get update for last sources.list (the one you usually have) - eventhough it has no duplicates.

I need to chill out my head...don't have a clue at the moment...

Thanks.

---

### Post by ape on 2006-08-06
okay, here's the sources.list that I usually use:

```
deb http://ubuntu.cs.utah.edu/ubuntu dapper main restricted universe multiverse
deb-src http://ubuntu.cs.utah.edu/ubuntu dapper main restricted universe multiverse

deb http://ubuntu.cs.utah.edu/ubuntu dapper-updates main restricted universe multiverse
deb-src http://ubuntu.cs.utah.edu/ubuntu dapper-updates main restricted universe multiverse

deb http://ubuntu.cs.utah.edu/ubuntu dapper-security main restricted universe multiverse
deb-src http://ubuntu.cs.utah.edu/ubuntu dapper-security main restricted universe multiverse

deb http://ubuntu.cs.utah.edu/ubuntu dapper-backports main universe multiverse restricted

deb http://oss.oracle.com/debian unstable main non-free
deb http://wine.budgetdedicated.com/apt dapper main
deb http://debian.isisetup.ch/ unstable/

```

This produces the following output:

Get: 1 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper Release.gpg [189B]
Get: 2 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates Release.gpg [189B]
Get: 3 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security Release.gpg [189B]
Get: 4 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports Release.gpg [189B]
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable Release.gpg                       
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper Release                         
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates Release                 
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security Release                
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable Release                                         
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg                             
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports Release                             
Ign [http://debian.isisetup.ch](http://debian.isisetup.ch) unstable/ Release.gpg                                
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable/main Packages                                   
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/main Packages                                 
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/restricted Packages             
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/universe Packages               
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/multiverse Packages             
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/main Sources                    
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/restricted Sources              
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/universe Sources                
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/multiverse Sources              
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/main Packages           
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/restricted Packages     
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release                   
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free Packages                 
Hit [http://debian.isisetup.ch](http://debian.isisetup.ch) unstable/ Release                      
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages             
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/universe Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/multiverse Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/main Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/restricted Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/universe Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/multiverse Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/main Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/restricted Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/universe Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/multiverse Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/main Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/restricted Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/universe Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/multiverse Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/main Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/universe Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/multiverse Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/restricted Packages
Ign [http://debian.isisetup.ch](http://debian.isisetup.ch) unstable/ Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://debian.isisetup.ch](http://debian.isisetup.ch) unstable/ Packages
Fetched 4B in 1s (4B/s)  
Reading package lists... Done


(Obviously I had run this already prior to this example).

---

### Post by matjaz_pirnovar on 2006-08-07
Hi Ape,

After putting your data into my sources.list, produced output is:

> matjaz@PCPlus:~$ sudo apt-get update
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Errhttp://security.ubuntu.com dapper-security/multiverse Packages
  Bad header line [IP: 82.211.81.138 80]
Errhttp://security.ubuntu.com dapper-security/universe Packages
  Bad header line [IP: 82.211.81.138 80]
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable Release.gpg
Get: 2 [http://oss.oracle.com](http://oss.oracle.com) unstable Release [170B]
Get: 3 [http://oss.oracle.com](http://oss.oracle.com) unstable/main Packages [386B]
Get: 4 [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free Packages [671B]
Get: 5 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper Release.gpg [189B]
Get: 6 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates Release.gpg [189B]
Get: 7 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security Release.gpg [189B]
Get: 8 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports Release.gpg [189B]
Get: 9 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper Release [34.8kB]
Get: 10 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates Release [30.9kB]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Get: 11 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release [745B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Get: 12 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages [1368B]
Get: 13 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security Release [30.9kB]
Get: 14 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports Release [19.6kB]
Get: 15 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/main Packages [619kB]
Get: 16 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/restricted Packages [4571B]
Get: 17 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/universe Packages [2458kB]
Ign [http://debian.isisetup.ch](http://debian.isisetup.ch) unstable/ Release.gpg
Get: 18 [http://debian.isisetup.ch](http://debian.isisetup.ch) unstable/ Release [692B]
Ign [http://debian.isisetup.ch](http://debian.isisetup.ch) unstable/ Packages
Get: 19 [http://debian.isisetup.ch](http://debian.isisetup.ch) unstable/ Packages [589B]
Get: 20 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/multiverse Packages [95.2kB]
Get: 21 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/main Sources [255kB]
Get: 22 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/restricted Sources [1478B]
Get: 23 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/universe Sources [975kB]
Get: 24 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/multiverse Sources [46.6kB]
Get: 25 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/main Packages [71.6kB]
Get: 26 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/restricted Packages [14B]
Get: 27 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/universe Packages [15.4kB]
Get: 28 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/multiverse Packages [866B]
Get: 29 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/main Sources [46.1kB]
Get: 30 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/restricted Sources [14B]
Get: 31 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/universe Sources [3129B]
Get: 32 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/multiverse Sources [427B]
Get: 33 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/main Packages [44.2kB]
Get: 34 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/restricted Packages [4275B]
Get: 35 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/universe Packages [12.3kB]
Get: 36 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/multiverse Packages [2043B]
Get: 37 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/main Sources [11.0kB]
Get: 38 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/restricted Sources [974B]
Get: 39 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/universe Sources [1805B]
Get: 40 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/multiverse Sources [533B]
Get: 41 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/main Packages [14B]
Get: 42 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/universe Packages [14B]
Get: 43 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/multiverse Packages [14B]
Get: 44 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/restricted Packages [14B]
Fetched 4792kB in 20s (230kB/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz)  Bad header line [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz)  Bad header line [IP: 82.211.81.138 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


Any comments?

At least I don't get duplication note. There are bad header lines????

And this output is different than yours!!!
Why do I have more lines than you???

:confused:  :)

-----------------------------------
PS: I did use gb mirror BEFORE (!).

---

### Post by ape on 2006-08-08
Looks like you still have the gb* and security.ubuntu.com entries in your sources.list, so that would account for the different number of lines.

What if you comment out the gb* and security.ubuntu.com entries and re-run `apt-get update`?

---

### Post by matjaz_pirnovar on 2006-08-08
Hey,

Since previous posting I'm using exact copy of your sources.list (two days now), without any '.gb'. It gave me that result by saving in your sources.list.

Today sudo apt-get update gives okay result, no duplicates or bad header lines. But prior to previous experiences I don't wish to think it is just a matter of time that they come out. But - I get .gb in the result, eventhough there are none in sources.list??? 

Could they ne in the background somewhere?


Anyway here is the outcome of my sudo apt-get update now:

> matjaz@PCPlus:~$ sudo apt-get update
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/universe Packages
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable Release
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable/main Packages
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Get: 3 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper Release.gpg [189B]
Get: 4 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates Release.gpg [189B]
Get: 5 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security Release.gpg [189B]
Get: 6 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports Release.gpg [189B]
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper Release
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates Release
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security Release
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports Release
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/main Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/restricted Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/universe Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/multiverse Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/main Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/restricted Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/universe Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/multiverse Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/main Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/restricted Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/universe Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/multiverse Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/main Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/restricted Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/universe Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/multiverse Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/main Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/restricted Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/universe Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/multiverse Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/main Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/restricted Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/universe Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/multiverse Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/main Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/universe Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/multiverse Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/restricted Packages
Ign [http://debian.isisetup.ch](http://debian.isisetup.ch) unstable/ Release.gpg
Hit [http://debian.isisetup.ch](http://debian.isisetup.ch) unstable/ Release
Ign [http://debian.isisetup.ch](http://debian.isisetup.ch) unstable/ Packages
Hit [http://debian.isisetup.ch](http://debian.isisetup.ch) unstable/ Packages
Fetched 6B in 5s (1B/s)
Reading package lists... Done

How do I uncomment a line if it's not in my sources.list? Is it hidden somewhere in the background?

And  then...sorry for being a nebee...how I uncomment a line...just delete it?

Thx

---

### Post by Jengist on 2006-08-10
Commenting means putting ## in front of code. It's a way programmers use to clarify to themselves and other readers of their code what they are doing without having the machine read and try to act upon those comments. Look at the very first line of the code you quoted in post number 3 in this thread; it actually tells you that. The code posted here shows commenting for the purposes of giving repositories a title and for instructional purposes but you can also use it to disable repositories without deleting them.

You can delete lines from the list and that will remove them from your list of repositories but what if you decide you want them back later? Just adding those ## marks has the same effect but makes getting those repos back much easier.

And no, you can't uncomment something that isn't in your list. There is nothing hidden though.

---

### Post by matjaz_pirnovar on 2006-08-10
> **Jengist said:**
> Commenting means putting ## in front of code. It's a way programmers use to clarify to themselves and other readers of their code what they are doing without having the machine read and try to act upon those comments. Look at the very first line of the code you quoted in post number 3 in this thread; it actually tells you that. The code posted here shows commenting for the purposes of giving repositories a title and for instructional purposes but you can also use it to disable repositories without deleting them.

You can delete lines from the list and that will remove them from your list of repositories but what if you decide you want them back later? Just adding those ## marks has the same effect but makes getting those repos back much easier.

And no, you can't uncomment something that isn't in your list. There is nothing hidden though.

Thanks a lot for explanation about uncommenting, I see now how it works.

I will check again and look if I have any gb.archives.ubuntu entries somewhere since sudo apt-get update shows them, but my soures.list doesn't.

:), M

---

### Post by Jengist on 2006-08-10
Can you post your sources.list one more time? Just cut and paste everything from the top to the bottom and let's see it. I have a feeling you've been looking too hard for the solution and that it may actually be sitting there looking back at you.

I suspect apt-get update is showing the gb.archives first because they are still listed at the start of your sources list as in post #5.

---

### Post by matjaz_pirnovar on 2006-08-10
> **Jengist said:**
> Can you post your sources.list one more time? Just cut and paste everything from the top to the bottom and let's see it. I have a feeling you've been looking too hard for the solution and that it may actually be sitting there looking back at you.

I suspect apt-get update is showing the gb.archives first because they are still listed at the start of your sources list as in post #5.

Hi. Thanks for helping.

My sources list is such - from top to bottom (using command:sudo gedit /etc/apt/sources.list):

> deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper main restricted universe multiverse
deb-src [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper main restricted universe multiverse

deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper-updates main restricted universe multiverse

deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper-security main restricted universe multiverse

deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper-backports main universe multiverse restricted
deb-src [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper-backports main restricted universe multiverse

deb [http://oss.oracle.com/debian](http://oss.oracle.com/debian) unstable main non-free
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb [http://debian.isisetup.ch/](http://debian.isisetup.ch/) unstable/

deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

I thought as well that I might missed gb.ubuntu.archive entries...but...

Wondering...

Regards, M

---

### Post by ape on 2006-08-11
Do you have a directory called /etc/apt/sources.list.d containing any *.list files?  These extra entries will be pulled into your overall repositories when issuing an 'apt-get update'.

---

### Post by matjaz_pirnovar on 2006-08-11
> **ape said:**
> Do you have a directory called /etc/apt/sources.list.d containing any *.list files?  These extra entries will be pulled into your overall repositories when issuing an 'apt-get update'.

I tried to open it with the command: sudo gedit /etc/apt/sources.list.d
and I get a message "Could not open /etc/apt/..."

Then I tried with Alt+F2 and gksudo nautilus (GUI access) and there are 4 files in /etc/apt/sources.list.d:

1. dapper-multiverse.list which says:
> # automatically added by gnome-app-install on 2006-06-22 23:14:48.672174
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates multiverse

2. dapper-multiverse.list.save which says:
> # automatically added by gnome-app-install on 2006-06-22 23:14:48.672174
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates multiverse

3. dapper-universe.list:
> # automatically added by gnome-app-install on 2006-06-22 21:25:41.128067
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates universe

4. dapper-universe.list.save:
> # automatically added by gnome-app-install on 2006-06-22 21:25:41.128067
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates universe

This is really interesting!

There is gb.archive.ubuntu entry in each of them, the same/similar entry that repeats in sudo apt-get update (except /ubuntu/ part).
And the first sentence points out the date 22.June 2006, I think it's the date that I installed dapper (and repositories, using .gb mirror). Hmmm...........

Could these gb.archive.ubuntu files be pulled out when updating??
If yes, what do you recommend doing? Uncommenting them?

Thanks, M

---

### Post by ape on 2006-08-12
Yep, exactly.  Just comment them out and try re-running 'apt-get update'.

---

### Post by matjaz_pirnovar on 2006-08-12
WOW.  Now it worked.

Cool. Didn't know that some repos are automatically stored - even when you change the sources.list.

Thanks guys.

Now my sources list is clean. :) 

(Next thing I will look at are some "bad header" lines that occur occasionally...)

Here it is (if you think something still needs cleaning, let me know):

> matjaz@PCPlus:~$ sudo apt-get update
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Ign [http://debian.isisetup.ch](http://debian.isisetup.ch) unstable/ Release.gpg
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://debian.isisetup.ch](http://debian.isisetup.ch) unstable/ Release
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable Release.gpg
Ign [http://debian.isisetup.ch](http://debian.isisetup.ch) unstable/ Packages
Get: 2 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper Release.gpg [189B]
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Hit [http://debian.isisetup.ch](http://debian.isisetup.ch) unstable/ Packages
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable Release
Get: 3 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates Release.gpg [189B]
Get: 4 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable/main Packages
Get: 5 [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports Release.gpg [189B]
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper Release
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates Release
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security Release
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports Release
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/main Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/restricted Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/universe Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/multiverse Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/main Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/restricted Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/universe Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper/multiverse Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/main Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/restricted Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/universe Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/multiverse Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/main Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/restricted Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/universe Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-updates/multiverse Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/main Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/restricted Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/universe Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/multiverse Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/main Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/restricted Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/universe Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-security/multiverse Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/main Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/universe Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/multiverse Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/restricted Packages
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/main Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/restricted Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/universe Sources
Hit [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) dapper-backports/multiverse Sources
Fetched 5B in 2s (2B/s)
Reading package lists... Done
matjaz@PCPlus:~$


M

---

