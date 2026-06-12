---
title: "linux-ubuntu-modules-2.6.22-14-generic"
date: 2008-05-27
forum: Security
---

### Post by grewolf on 2008-05-27
I received this in my update manager but when I read info about this it says not to install this.  Is this ok to install?  I am using Gutsy Gibbon Desktop and just general home computer use for the family.  I would consider mine an normal ubuntu system. 

Here is one of the warnings I read 

debian-installer udeb package

Warning: This package is intended for the use in building debian-installer images only. Do not install it on a normal Ubuntu system.

---

### Post by yaztromo on 2008-05-28
Hi.

Please run terminal and then type

```
sudo apt-get update
```

Then paste here the output from this command, you can safely press n to any questions.

```
sudo apt-get dist-upgrade
```

---

### Post by grewolf on 2008-05-28
I typed in the terminal sudo apt-get update but in regards to the command sudo apt-get dist-upgrade - won't that upgrade my system to hardy?  I am currently happy with gutsy and just got it to where I wanted it and am worried that if I upgrade the distro that I will need to spend hours/weeks/ months trying to get it back to how I have it working now.  I have posted the output to sudo apt-get update below 



Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_CA               
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_CA                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-en_CA                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_CA             
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_CA                     
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release                                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_CA     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_CA     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_CA   
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_CA 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_CA         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_CA
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_CA           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_CA     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_CA       
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Sources                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_CA
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_CA            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_CA      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_CA        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_CA      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Fetched 6B in 1s (3B/s)  
Reading package lists... Done

---

### Post by yaztromo on 2008-05-29
apt-get dist-upgrade performs an "intelligent" system upgrade with better resolution of dependencies than simply typing apt-get upgrade. It's safe to type and won't upgrade your system to hardy.

From the looks of your apt-get update you have some repositories enabled which might be causing the problem, such as ppa.launchpad.net. I would suggest going back to official repositories only to see if it helps.

Open synaptic
Go to settings -> repositories
Go to the third party tab and untick the ppa and medibuntu repositories
Click reload
Then mark all upgrades and see if you can update without trouble

---

### Post by grewolf on 2008-05-29
> **yaztromo said:**
> 
Then mark all upgrades and see if you can update without trouble


I think I made a mistake.  I can update alright I just want to know should I do this particular update as info I found on the web said not to install on a normal Ubuntu system 

[COLOR=Red] Warning: This package is intended for the use in building debian-installer images only. Do not install it on a normal Ubuntu system.[/COLOR]

---

