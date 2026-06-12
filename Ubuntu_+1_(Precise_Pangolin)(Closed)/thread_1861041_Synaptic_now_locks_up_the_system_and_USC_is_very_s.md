---
title: "Synaptic now locks up the system and USC is very slooooow"
date: 2011-10-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Quackers on 2011-10-15
Not to mention the fact that software sources won't open from the repositories menu in synaptic. It just goes busy for a few seconds but no software sources window opens :-(
sudo apt-get update works without any errors though :-)

---

### Post by ventrical on 2011-10-15
Mine  PP install is just rocking here.

---

### Post by Quackers on 2011-10-15
:-)  so was mine earlier :-)
Don't know what's caused this. I had to REISUB to get out of it. Everything just locked up but there was no sign of any disc activity. 
Very odd!

---

### Post by ventrical on 2011-10-15
I used synaptic to download and install vlc  and have all the latets updates.

  I'll update again and re-boot.

---

### Post by ventrical on 2011-10-15
All I got (after a bunch of updates earlier) was:

---

### Post by ventrical on 2011-10-15
here:

---

### Post by dino99 on 2011-10-15
get something different with synaptic: can run it from menu, but get a crash if i want to open Settings -> repos

---

### Post by Quackers on 2011-10-15
Ventrical the extras repositories don't exist yet for PP. You can comment them out for the moment.

dino99, I can run synaptic from its icon and it opens up fine - if a bit slow to initialise. Up to an hour ago it worked fine, except for not being able to open up software sources. Now it just locks up the whole system trying to initialise :-(

---

### Post by ventrical on 2011-10-15
My Precise pre-setup has never worked better! 

  I do however  have two other Oneiric installs and one Maveric install on this hdd so I may side with caution and use an old USB install for my PP experimetns/testings.

---

### Post by ventrical on 2011-10-15
> **Quackers said:**
> Ventrical the extras repositories don't exist yet for PP. You can comment them out for the moment.

dino99, I can run synaptic from its icon and it opens up fine - if a bit slow to initialise. Up to an hour ago it worked fine, except for not being able to open up software sources. Now it just locks up the whole system trying to initialise :-(


Thank you for that clarification.

---

### Post by Quackers on 2011-10-15
You're very welcome :-)

Synaptic just ran ok!  Gremlins methinks.

---

### Post by ventrical on 2011-10-15
> **Quackers said:**
> You're very welcome :-)

Synaptic just ran ok!  Gremlins methinks.

None of my buisness really .. - but does you Sony have a Centrino processor?

---

### Post by Quackers on 2011-10-15
Intel Core 2 Duo T7700

---

### Post by arpanaut on 2011-10-15
> **Quackers said:**
> Not to mention the fact that software sources won't open from the repositories menu in synaptic. It just goes busy for a few seconds but no software sources window opens :-(
sudo apt-get update works without any errors though :-)

Had this issue last night and was too tired to post.

Re: software-properties-gtk doesn't start 
Seems that there is a Return of bug: [https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/364092](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/364092)

The solution is in the bug report...
```
gksudo gedit /usr/share/python-apt/templates/Ubuntu.info
```after the intro stanza and before "Suite: oneiric"  cupy and paste <insert the following text>
```

Suite: precise
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-powerpc: http://ports.ubuntu.com/
MatchURI-powerpc: ports.ubuntu.com|archive.ubuntu.com
BaseURI-lpia: http://ports.ubuntu.com/
MatchURI-lpia: ports.ubuntu.com|archive.ubuntu.com
MirrorsFile-amd64: /usr/share/python-apt/templates/Ubuntu.mirrors
MirrorsFile-i386: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 12.04 'Precise Pangolin'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: precise
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*12.04
MatchURI: cdrom:\[Ubuntu.*12.04
Description: Cdrom with Ubuntu 12.04 'Precise Pangolin'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: precise-security
ParentSuite: precise
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-powerpc: http://ports.ubuntu.com/
MatchURI-powerpc: ports.ubuntu.com/ubuntu
BaseURI-lpia: http://ports.ubuntu.com/
MatchURI-lpia: ports.ubuntu.com/ubuntu
Description: Important security updates

Suite: precise-updates
ParentSuite: precise
RepositoryType: deb
Description: Recommended updates

Suite: precise-proposed
ParentSuite: precise
RepositoryType: deb
Description: Pre-released updates

Suite: precise-backports
ParentSuite: precise
RepositoryType: deb
```Now software-properties-gtk is back to normal.

hth

P.S. This issue came after doing the sudo sed bit to get the PP repos and after changing to the main server, then software-properties broke.

---

### Post by Quackers on 2011-10-15
Thanks arpanaut.
Is that to replace the "Suite: oneiric" and all the stuff after, or just to paste all that before "Suite: oneiric"?
Many thanks.

---

### Post by arpanaut on 2011-10-15
paste in before...  leave the rest.

This was an issue back in Maverick testing and was supposed to be fixed
I don't know why it popped up this time around and does not seem to be affecting everyone

---

### Post by Quackers on 2011-10-15
Thanks again, trying it now :-)

I didn't use the sudo sed command, but I changed all oneirics to precises, which amounts to the same thing of course.

---

### Post by Quackers on 2011-10-15
Aha! :-)  Fixed again. Thanks!

As my original problems seem to be fixed now (almost) I'll mark the thread as solved.

---

### Post by arpanaut on 2011-10-15
Yay!   Glad to be of service.

I think it had to do with the new Python that came down in the initial updates after changing repos.
I ran software-sources-gtk in a terminal and investigated the errors.
That reminded me of the  bug back in Maverick and went searching.

Seems to have worked for two of us now, so maybe it will help others.

---

### Post by Quackers on 2011-10-15
You remembered a bug back in maverick!  ooh, I've had a sleep since then :-)

---

### Post by arpanaut on 2011-10-15
LOL  This old mind surprises me sometimes.

Used to have a very acute memory... alas not so much anymore.
Too many trips to the Pub, maybe

---

### Post by VinDSL on 2011-10-15
> **arpanaut said:**
> Had this issue last night and was too tired to post.
w00t!

Well worth the wait.  :)

"Synaptic" repo info is displaying again.

Let me go check "Software Sources" in "System Settings"...

Bingo!  Works like a champ.  Thanks!

---

### Post by VinDSL on 2011-10-15
> **Quackers said:**
> Ventrical the extras repositories don't exist yet for PP. You can comment them out for the moment.
I've been using Oneiric extras repos.

```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb-src http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb-src http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb-src http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu **[COLOR="Red"]oneiric[/COLOR]** main
deb-src http://extras.ubuntu.com/ubuntu **[COLOR="Red"]oneiric[/COLOR]** main
```


Gets rid of the errors, and it's just 3rd party stuff anyway...


```
vindsl@Zuul:~$ sudo apt-get update
[sudo] password for vindsl: 
Ign http://archive.ubuntu.com precise InRelease                                
Ign http://archive.ubuntu.com precise-updates InRelease                        
Ign http://archive.ubuntu.com precise-backports InRelease                      
Ign http://archive.ubuntu.com precise-security InRelease                       
Get:1 http://archive.ubuntu.com precise Release.gpg [198 B]                    
Hit http://archive.ubuntu.com precise-updates Release.gpg                      
Hit http://archive.ubuntu.com precise-backports Release.gpg                    
Hit http://archive.ubuntu.com precise-security Release.gpg                     
Get:2 http://archive.ubuntu.com precise Release [49.6 kB]                      
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://archive.canonical.com oneiric InRelease                             
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Ign http://deb.opera.com stable InRelease                                      
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://deb.opera.com stable Release.gpg                                    
Hit http://archive.canonical.com oneiric Release                               
Hit http://archive.ubuntu.com precise-updates Release                          
Hit http://archive.ubuntu.com precise-backports Release                        
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://deb.opera.com stable Release                                        
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Hit http://archive.ubuntu.com precise-security Release                         
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://deb.opera.com stable/non-free i386 Packages                         
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Get:3 http://archive.ubuntu.com precise/main Sources [878 kB]                  
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Get:4 http://archive.ubuntu.com precise/restricted Sources [5,351 B]           
Get:5 http://archive.ubuntu.com precise/universe Sources [4,677 kB]            
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://deb.opera.com stable/non-free Translation-en                       
Get:6 http://archive.ubuntu.com precise/multiverse Sources [149 kB]            
Get:7 http://archive.ubuntu.com precise/main i386 Packages [1,227 kB]          
Get:8 http://archive.ubuntu.com precise/restricted i386 Packages [8,216 B]     
Get:9 http://archive.ubuntu.com precise/universe i386 Packages [4,468 kB]      
Get:10 http://archive.ubuntu.com precise/multiverse i386 Packages [119 kB]     
Get:11 http://archive.ubuntu.com precise/main TranslationIndex [74 B]          
Get:12 http://archive.ubuntu.com precise/multiverse TranslationIndex [73 B]    
Get:13 http://archive.ubuntu.com precise/restricted TranslationIndex [72 B]    
Get:14 http://archive.ubuntu.com precise/universe TranslationIndex [75 B]      
Hit http://archive.ubuntu.com precise-updates/main Sources                     
Hit http://archive.ubuntu.com precise-updates/restricted Sources               
Hit http://archive.ubuntu.com precise-updates/universe Sources                 
Hit http://archive.ubuntu.com precise-updates/multiverse Sources               
Hit http://archive.ubuntu.com precise-updates/main i386 Packages               
Hit http://archive.ubuntu.com precise-updates/restricted i386 Packages         
Hit http://archive.ubuntu.com precise-updates/universe i386 Packages           
Hit http://archive.ubuntu.com precise-updates/multiverse i386 Packages         
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex            
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex        
Hit http://archive.ubuntu.com precise-backports/main Sources                   
Hit http://archive.ubuntu.com precise-backports/restricted Sources             
Hit http://archive.ubuntu.com precise-backports/universe Sources               
Hit http://archive.ubuntu.com precise-backports/multiverse Sources             
Hit http://archive.ubuntu.com precise-backports/main i386 Packages             
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages       
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages         
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages       
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex          
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex      
Hit http://archive.ubuntu.com precise-security/main Sources                    
Hit http://archive.ubuntu.com precise-security/restricted Sources              
Hit http://archive.ubuntu.com precise-security/universe Sources                
Hit http://archive.ubuntu.com precise-security/multiverse Sources              
Hit http://archive.ubuntu.com precise-security/main i386 Packages              
Hit http://archive.ubuntu.com precise-security/restricted i386 Packages        
Hit http://archive.ubuntu.com precise-security/universe i386 Packages          
Hit http://archive.ubuntu.com precise-security/multiverse i386 Packages        
Hit http://archive.ubuntu.com precise-security/main TranslationIndex           
Hit http://archive.ubuntu.com precise-security/multiverse TranslationIndex     
Hit http://archive.ubuntu.com precise-security/restricted TranslationIndex     
Hit http://archive.ubuntu.com precise-security/universe TranslationIndex       
Hit http://archive.ubuntu.com precise/main Translation-en                      
Hit http://archive.ubuntu.com precise/multiverse Translation-en                
Hit http://archive.ubuntu.com precise/restricted Translation-en                
Hit http://archive.ubuntu.com precise/universe Translation-en                  
Hit http://archive.ubuntu.com precise-updates/main Translation-en              
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en        
Hit http://archive.ubuntu.com precise-updates/universe Translation-en          
Hit http://archive.ubuntu.com precise-backports/main Translation-en            
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en      
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en      
Hit http://archive.ubuntu.com precise-backports/universe Translation-en        
Hit http://archive.ubuntu.com precise-security/main Translation-en             
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en       
Hit http://archive.ubuntu.com precise-security/restricted Translation-en       
Hit http://archive.ubuntu.com precise-security/universe Translation-en         
Fetched 11.6 MB in 30s (379 kB/s)                                              
Reading package lists... Done
vindsl@Zuul:~$ 

```

---

