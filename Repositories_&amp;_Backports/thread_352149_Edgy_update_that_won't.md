---
title: "Edgy update that won't"
date: 2007-02-02
forum: Repositories &amp; Backports
---

### Post by Mike Wilson on 2007-02-02
Among today's 'recommended updates' for my Edgy-64 install, one seems to be missing from at least the Canada and 'main' repositories. Updater gives this message when it fails:

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/python-wxversion_2.6.3.2.1.5ubuntu0.1_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/python-wxversion_2.6.3.2.1.5ubuntu0.1_all.deb)
  404 Not Found

If it's absent, how did update-notifier get primed with the name of this file?

As of the following AM, the file was in place and updating was routine. However, slips in synchronization are still puzzling (not to mention off-putting for newbies).

---

### Post by dkeller on 2008-06-19
I also have this problem...

Where did all the edgy repositories disappear from [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) ??

This is what this I get when I run sudo apt-get update. After that is my sources.list. Any help is appreciated.
               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
Get:1 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed Release.gpg           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg            
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) edgy Release.gpg [189B]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                 
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) edgy Release                                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed Release               
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) edgy/free Packages                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) edgy/non-free Packages             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
Fetched 2B in 2s (1B/s)  
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-proposed/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-proposed/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-proposed/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-proposed/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-proposed/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-proposed/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-proposed/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-proposed/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

Here is my sources.list
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
 deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) edgy free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen

---

### Post by myyykeym on 2008-06-22
Hi, I'm having the exact same problem.  Seems we waited too long to upgrade from Edgy- since it's not a LTS, they took it off all the official mirrors probably in April with the new release.  I checked about 12 of them, and none had it.  :(

You may have done what I did.  Sometime when these packages were still available, I updated my packages list, but didn't perform the full download.  Then they took them off.  Now when I tried to upgrade to Feisty, those packages that have changed since my last download could not be upgraded, thereby keeping the upgrade from progressing.

Anyone have any ideas where to get the final versions of packages from Edgy before they took it down?  :confused:

Thanks!


Update:  I just checked every single mirror (!) and, although a few have Hoary :confused:(before Dapper!), none has Edgy. :(

I might try upgrading by editing my sources.list to Feisty, BUT this might still cause problems with the non-updated packages, since Edgy knows it's missing them.  Hmmmm.....

---

### Post by myyykeym on 2008-06-22
This thread:

[http://ubuntuforums.org/showthread.php?t=468043&highlight=feisty+upgrade&page=2](http://ubuntuforums.org/showthread.php?t=468043&highlight=feisty+upgrade&page=2)

pretty much explains the situation, and a possible solution.  I'm in the process of trying it, and I'll post my results.

Cheers!


Update:  In /etc/apt/sources.list, I used: 

[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)

(Since the [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)  url they gave in that thread takes you down a wrong path.)
Update also the security lines with this same url, as the needed security packages are apparently contained within that directory as opposed to being contained in a separate one as they are for a supported release.

Update#2:  This worked, and apparently successfully updated Edgy to its final version before support dropped away.

BUT, when I go to update-manager and try to upgrade to Feisty it still hangs on the missing Edgy packages in the official supported mirrors.  I tried concatenating both sources.list files (pointing to official and old releases mirrors), but this didn't help.  Still working on it......

---

### Post by myyykeym on 2008-06-22
OK, some success! 

First I edited sources.list to Feisty, then did

sudo aptitude update

This successfully updated my packages list to Feisty!!

Now, I am in the process of successfully upgrading!!!  (I just *know* it will be successful....!)

---

