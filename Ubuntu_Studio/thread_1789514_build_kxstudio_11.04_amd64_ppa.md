---
title: "build kxstudio 11.04 amd64 ppa"
date: 2011-06-23
forum: Ubuntu Studio
---

### Post by ken78724 on 2011-06-23
What's missing/what's needed? Have a plain 11.04 install + repositories, here's what terminal says: 
ken@ken-System-Product-Name:~$ sudo add-apt-repository ppa:kxstudio-team/ppa
[sudo] password for ken: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv A809F6C307B583133B3891B287538FEDDF8063EB

gpg: requesting key DF8063EB from hkp server keyserver.ubuntu.com

gpg: key DF8063EB: public key "Launchpad PPA for KXStudio Team" imported

gpg: Total number processed: 1

gpg:               imported: 1  (RSA: 1)

ken@ken-System-Product-Name:~$ sudo add-apt-repository ppa:kxstudio-team/kernel

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv A809F6C307B583133B3891B287538FEDDF8063EB

gpg: requesting key DF8063EB from hkp server keyserver.ubuntu.com

gpg: key DF8063EB: "Launchpad PPA for KXStudio Team" not changed

gpg: Total number processed: 1

gpg:              unchanged: 1

ken@ken-System-Product-Name:~$ sudo apt-get-update

sudo: apt-get-update: command not found

ken@ken-System-Product-Name:~$ uname -a

Linux ken-System-Product-Name 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

ken@ken-System-Product-Name:~$ 

 
Will be here a few minutes,then away 36 hours for a root canal & crown. :KS

---

### Post by Toz on 2011-06-24
> **ken78724 said:**
> ~$ sudo apt-get-update

sudo: apt-get-update: command not found
Should be:```
sudo apt-get update
```

> Will be here a few minutes,then away 36 hours for a root canal & crown. :KS
Ouch. Good luck.

---

### Post by ken78724 on 2011-07-05
hmmmm just did the update on my 10.04.02; guess I best wake up....
k78724@Kproductions:~$ sudo apt-get update
Ign cdrom://Kubuntu 10.04 _Lucid Lynx_ - Release Candidate amd64 (20100419.1)/ lucid/main Translation-en_US
Ign cdrom://Kubuntu 10.04 _Lucid Lynx_ - Release Candidate amd64 (20100419.1)/ lucid/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/falk-t-j/lucid/ubuntu/](http://ppa.launchpad.net/falk-t-j/lucid/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/kxstudio-team/kernal/ubuntu/](http://ppa.launchpad.net/kxstudio-team/kernal/ubuntu/) lucid/main Translation-en_US
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]                        
Ign [http://ppa.launchpad.net/kxstudio-team/kernel/ubuntu/](http://ppa.launchpad.net/kxstudio-team/kernel/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/kxstudio-team/ppa/ubuntu/](http://ppa.launchpad.net/kxstudio-team/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_US              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) lucid/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/user/ppa-name/ubuntu/](http://ppa.launchpad.net/user/ppa-name/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [13.9kB]                          
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [8,127B]                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                       
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                       
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Get:4 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US
Get:5 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Ign [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release                       
Get:6 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                           
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Get:7 [http://dl.google.com](http://dl.google.com) stable Release [1,351B]                             
Get:8 [http://dl.google.com](http://dl.google.com) stable Release [1,338B]                             
Get:9 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Get:10 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,248B]                      
Get:11 [http://dl.google.com](http://dl.google.com) stable/main Packages [469B]                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Get:12 [http://dl.google.com](http://dl.google.com) stable/main Packages [759B]                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages             
Fetched 29.5kB in 7s (3,799B/s)                                                
W: Failed to fetch [http://ppa.launchpad.net/kxstudio-team/kernal/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/kxstudio-team/kernal/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
k78724@Kproductions:~$

---

### Post by Toz on 2011-07-05
You have a spelling error in the kxstudio entry - you have **kernal** when you should have **kernel**. Make the correction and the update should work again. 

The entry is probably in the **/etc/apt/sources.list** file.```
gksudo gedit /etc/apt/sources.list
``` If it's not there, look for a related file in **/etc/apt/sources.list.d**

---

### Post by ken78724 on 2011-07-07
Toz: I put <gksudo gedit /etc/apt/sources.list> in terminal on my 10.04.02 PC & have no idea where to go with this output ????

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# deb cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/ intrepid main multiverse restricted universe
deb cdrom:[Kubuntu 10.04 _Lucid Lynx_ - Release Candidate amd64 (20100419.1)]/ lucid main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
# deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports restricted main multiverse universe

tried the same on my 11.04 PC but the build bounces/cant report it for unknown reasons. Have lost orientation...

---

### Post by Toz on 2011-07-07
It's not in your sources.list file. In the terminal window, can you type in:```
ls -l /etc/apt/sources.list.d
``` and post back the results?

---

### Post by ken78724 on 2011-07-10
Toz, been away. Thanks:
k78724@Kproductions:~$ ls -l /etc/apt/sources.list.d
total 108
-rw-r--r-- 1 root root  62 2011-07-07 06:42 falk-t-j-lucid-lucid.list
-rw-r--r-- 1 root root  62 2011-07-07 06:42 falk-t-j-lucid-lucid.list.save
-rw-r--r-- 1 root root 176 2011-07-07 06:42 google-chrome.list
-rw-r--r-- 1 root root 176 2011-07-07 06:42 google-chrome.list.save
-rw-r--r-- 1 root root 175 2011-07-07 06:42 google-earth.list
-rw-r--r-- 1 root root 175 2011-07-07 06:42 google-earth.list.save
-rw-r--r-- 1 root root 180 2011-07-07 06:42 google-talkplugin.list
-rw-r--r-- 1 root root 180 2011-07-07 06:42 google-talkplugin.list.save
-rw-r--r-- 1 root root  65 2011-07-07 06:42 gwibber-daily-ppa-lucid.list
-rw-r--r-- 1 root root  65 2011-07-07 06:42 gwibber-daily-ppa-lucid.list.save
-rw-r--r-- 1 root root  68 2011-07-07 06:42 kxstudio-team-kernal-lucid.list
-rw-r--r-- 1 root root  68 2011-07-07 06:42 kxstudio-team-kernal-lucid.list.save
-rw-r--r-- 1 root root  68 2011-07-07 06:42 kxstudio-team-kernel-lucid.list
-rw-r--r-- 1 root root  68 2011-07-07 06:42 kxstudio-team-kernel-lucid.list.save
-rw-r--r-- 1 root root  65 2011-07-07 06:42 kxstudio-team-ppa-lucid.list
-rw-r--r-- 1 root root  65 2011-07-07 06:42 kxstudio-team-ppa-lucid.list.save
-rw-r--r-- 1 root root 313 2011-07-07 06:42 medibuntu.list
-rw-r--r-- 1 root root 313 2010-05-09 01:45 medibuntu.list.distUpgrade
-rw-r--r-- 1 root root 313 2011-07-07 06:42 medibuntu.list.save
-rw-r--r-- 1 root root  66 2011-07-07 06:42 michael-gruz-canon-lucid.list
-rw-r--r-- 1 root root  66 2011-07-07 06:42 michael-gruz-canon-lucid.list.save
-rw-r--r-- 1 root root  74 2011-07-07 06:42 mozillateam-firefox-stable-lucid.list
-rw-r--r-- 1 root root  74 2011-07-07 06:42 mozillateam-firefox-stable-lucid.list.save
-rw-r--r-- 1 root root 416 2011-07-07 06:42 opera.list
-rw-r--r-- 1 root root 416 2011-07-07 06:42 opera.list.save
-rw-r--r-- 1 root root  61 2011-07-07 06:42 user-ppa-name-lucid.list
-rw-r--r-- 1 root root  61 2011-07-07 06:42 user-ppa-name-lucid.list.save
k78724@Kproductions:~$

---

### Post by Toz on 2011-07-10
What is the contents of **kxstudio-team-kernal-lucid.list** and **kxstudio-team-kernel-lucid.list**?

I'm guessing you may have to delete **kxstudio-team-kernal-lucid.list** if it contains something like:
```
http://ppa.launchpad.net/kxstudio-team/[COLOR="Red"]kernal[/COLOR]/ubuntu lucid main
```(note the incorrect spelling of the word kernel)

---

### Post by ken78724 on 2011-07-11
> **Toz said:**
> What is the contents of **kxstudio-team-kernal-lucid.list** and **kxstudio-team-kernel-lucid.list**?

I'm guessing you may have to delete **kxstudio-team-kernal-lucid.list** if it contains something like:
```
http://ppa.launchpad.net/kxstudio-team/[COLOR="Red"]kernal[/COLOR]/ubuntu lucid main
```(note the incorrect spelling of the word kernel)

so what does one do to clean up the errors? 
-rw-r--r-- 1 root root 68 2011-07-07 06:42 kxstudio-team-kernal-lucid.list
-rw-r--r-- 1 root root 68 2011-07-07 06:42 kxstudio-team-kernal-lucid.list.save

---

### Post by Toz on 2011-07-11
Delete those two files and re-run:
```
sudo apt-get update
```

---

### Post by ken78724 on 2011-07-12
Toz, This post refers to getting kxstudio on two PCs

1. involves the kxstudio ppa on 10.04.02 64bit amd. As recommended, I'll delete the two lines where kernal is misspelled
2. involves the kxstudio ppa on 11.04 amd 64 bit PC
On PC with 11.04 64amd LTS after I built kxstudio with the falkTX PPA, I downloaded Canon drivers for the MX420X printer and then reviewed those builds in terminal / got following results 7-12-11: 
ken@ken-System-Product-Name:~$ ls -l /etc/apt/sources.list.d

total 32

-rw-r--r-- 1 root root 180 2011-07-09 19:54 google-talkplugin.list

-rw-r--r-- 1 root root 180 2011-07-09 19:54 google-talkplugin.list.save

-rw-r--r-- 1 root root 140 2011-07-09 19:54 kxstudio-team-kernel-natty.list

-rw-r--r-- 1 root root 140 2011-07-09 19:54 kxstudio-team-kernel-natty.list.save

-rw-r--r-- 1 root root 134 2011-07-09 19:54 kxstudio-team-ppa-natty.list

-rw-r--r-- 1 root root 134 2011-07-09 19:54 kxstudio-team-ppa-natty.list.save

-rw-r--r-- 1 root root 136 2011-07-09 19:54 michael-gruz-canon-natty.list

-rw-r--r-- 1 root root 136 2011-07-09 19:54 michael-gruz-canon-natty.list.save

ken@ken-System-Product-Name:~$ 


So Toz, do you concur, the build should be operative?

---

### Post by ken78724 on 2011-07-23
Toz & CWilson: 

I know it appears obvious. But I don't get it how one deletes lines. How do U go about deleting lines. What work around is used to delete lines showing "kernal" ???????????? 

this PC runs, but those lines force me to do without kxstudio, pitivi etc. 

Highly important video products remain zeroed. :confused::lolflag:

---

### Post by Toz on 2011-07-23
> **ken78724 said:**
> Toz & CWilson: 

I know it appears obvious. But I don't get it how one deletes lines. How do U go about deleting lines. What work around is used to delete lines showing "kernal" ???????????? 

this PC runs, but those lines force me to do without kxstudio, pitivi etc. 

Highly important video products remain zeroed. :confused::lolflag:

Open a Terminal window and type in:
```
gksudo gedit /etc/apt/sources.list
```
delete the line(s) where kernel is mispelled, then save the file.

The other way is to go to the Software Sources menu item, go to the Other Software tab, and uncheck the entry that is mispelled.

---

### Post by ken78724 on 2011-07-30
Toz: 
finally back - just removed lines from the results on the first gksudo you recommended & saved the source file. Have not shut down and rebooted. Now before doing that reboot, I tried a gksudo on your 2nd recommended /etc.... .list.d and get the following terminal report: 
ken@ken-System-Product-Name:~$ gksudo gedit /etc/apt/sources.list
ken@ken-System-Product-Name:~$ gksudo gedit /etc/apt/sources.list.d
ken@ken-System-Product-Name:~$ /etc/apt/sources.list.d
bash: /etc/apt/sources.list.d: Is a directory
ken@ken-System-Product-Name:~$ gksudo gedit /etc/apt/sources.list.d

(gedit:2643): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.SYYUZV': No such file or directory

(gedit:2643): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
ken@ken-System-Product-Name:~$ 

Am totally guessing what these actions are doing. So let me reboot and go water the plants outside and see if my now slowed PC comes back to life.

---

### Post by ken78724 on 2011-07-31
Tried to get into Kubuntu by doing an Install / Upgrade KDE 4.7.0 to Kubuntu via PPA [this applies an UbuntuBuzz.org post of 30 Jul 2011, which
uses kubuntu official PPA channel to get the latest update of KDE 4.7.0, It uses the following terminal code: 
sudo apt-add-repository ppa:kubuntu-ppa/backports 
sudo apt-get update 
sudo apt-get upgrade 

After rebooting, I wanted to get firefox to repair a basic FF function that lets U insert a website in the URL bar, which does not exist, truly a bug. So, I said download Firefox 6 Beta through the following UbuntuBuzz.org recommended command :
sudo add-apt-repository ppa:mozillateam/firefox-next 
sudo apt-get update 
sudo apt-get install firefox 

I see the following help and will now post the above FF bug to launchpad. 
Firefox 6 Beta may contain a lot of bugs, help firefox team to build best Firefox by reporting it bugs on this link [https://bugs.launchpad.net/ubuntu-mozilla-ppa-bugs/+filebug](https://bugs.launchpad.net/ubuntu-mozilla-ppa-bugs/+filebug).

---

### Post by Pablo_F on 2011-08-01
Hi ken, 

/etc/apt/sources.list.d is a directory where you have files that point to software sources other than the official ubuntu's in /etc/apt/sources.list.

Try 

cd /etc/apt/sources.list.d/
ls

You have to edit the files. 

Alternatively, use Software Center, Edit, "Software sources".

I think that you are aware that if you tinker with software sources you can end up messing up your system. 

Cheers, Pablo

---

