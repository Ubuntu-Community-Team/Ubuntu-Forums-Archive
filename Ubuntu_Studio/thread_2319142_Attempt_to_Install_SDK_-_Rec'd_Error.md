---
title: "Attempt to Install SDK - Rec'd Error"
date: 2016-04-01
forum: Ubuntu Studio
---

### Post by Rick St. George on 2016-04-01
Want to Learn Programming / Coding. Followed instructions at 
[URL="http://developer.ubuntu.com/en/start/ubuntu-sdk/installing-the-sdk/"]http://developer.ubuntu.com/en/start/ubuntu-sdk/installing-the-sdk/
[/URL]on UbuntuStudio 14.04. Installed PPA, and upon installing SDK received the following Error.

> 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-sdk : Depends: ubuntu-sdk-ide but it is not going to be installed
E: Unable to correct problems, you have held broken packages.




Was I not supposed to install this in UbuntuStudio? What went wrong?

Thanks!
Rick

---

### Post by mörgæs on 2016-04-02
Please post the output from ```
sudo apt-get update
``` and ```
sudo apt-get dist-upgrade
``` in CODE tags.

---

### Post by Rick St. George on 2016-04-20
Still got the same ERROR ?!?!?

Any other suggestions? Do I need SDK to learn coding? What language is it in?

---

### Post by Rick St. George on 2016-04-26
After looking at Post #2 again, I see you actually wanted the output. See below;

```

stephen:~$ sudo add-apt-repository ppa:ubuntu-sdk-team/ppa
 Ubuntu SDK Release PPA for Ubuntu 14.04 LTS, 15.10 and 16.04 LTS.

Upgrade with:

sudo add-apt-repository ppa:ubuntu-sdk-team/ppa && sudo apt update && sudo apt dist-upgrade && sudo apt install ubuntu-sdk-ide

== Ubuntu 14.04 LTS and newer ==

Ubuntu 14.04 LTS had Qt 5.x, Ubuntu UI Toolkit and SDK updates during its main development cycle. This PPA offers post-release SDK updates, including Qt Creator & Ubuntu plugins updates. The emulator included (or a mobile device attached to the computer) makes it possible to test apps in the very latest Ubuntu phone/tablet environment.

Ubuntu 15.04 has reached end of its support. 15.10 users are also encouraged to upgrade to 16.04 LTS as soon as possible.

== Earlier Ubuntu versions ==

Ubuntu 12.04 LTS has older versions of packages offered in this PPA, but the SDK support has moved to the newer releases. It's however usable for example for general Qt 5 usage.

GENERAL NOTES
-------------

1. Qt4 and Qt5 developer tools are co-installable thanks to the qtchooser tool. See 'man qtchooser' for more information.

2. The packaging is mostly done at Debian git (http://anonscm.debian.org/gitweb/ (pkg-kde/qt)).
 More info: https://launchpad.net/~ubuntu-sdk-team/+archive/ubuntu/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpkpg9x7rj/secring.gpg' created
gpg: keyring `/tmp/tmpkpg9x7rj/pubring.gpg' created
gpg: requesting key C7122F9B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpkpg9x7rj/trustdb.gpg: trustdb created
gpg: key C7122F9B: public key "Launchpad PPA for Ubuntu SDK team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK

```

So Then I Ran;

```

stephen:~$ sudo apt update && sudo apt dist-upgrade && sudo apt install ubuntu-sdk-ide
Hit http://download.virtualbox.org trusty InRelease
Ign http://download.bitdefender.com bitdefender InRelease                      
Hit http://download.bitdefender.com bitdefender Release.gpg                    
Hit http://download.bitdefender.com bitdefender Release                        
Hit http://download.bitdefender.com bitdefender/non-free amd64 Packages        
Ign http://archive.ubuntu.com trusty InRelease                                 
Hit http://download.virtualbox.org trusty/contrib amd64 Packages               
Hit http://download.bitdefender.com bitdefender/non-free i386 Packages         
Ign http://archive.canonical.com trusty InRelease                              
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:1 http://archive.ubuntu.com trusty-updates InRelease [65.9 kB]             
Hit http://download.virtualbox.org trusty/contrib i386 Packages                
Hit http://archive.canonical.com trusty Release.gpg                            
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty Release                                
Get:2 http://ppa.launchpad.net trusty InRelease [15.5 kB]                      
Hit http://archive.canonical.com trusty/partner Sources                        
Get:3 http://archive.ubuntu.com trusty-security InRelease [65.9 kB]            
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://archive.ubuntu.com trusty Release.gpg                               
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://download.virtualbox.org trusty/contrib Translation-en_US            
Ign http://download.virtualbox.org trusty/contrib Translation-en               
Get:4 http://archive.ubuntu.com trusty-updates/main Sources [273 kB]           
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit https://deb.opera.com stable InRelease                                     
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit https://deb.opera.com stable/non-free amd64 Packages                       
Get:5 http://archive.ubuntu.com trusty-updates/restricted Sources [5,352 B]    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:6 http://archive.ubuntu.com trusty-updates/main amd64 Packages [755 kB]
Hit https://deb.opera.com stable/non-free i386 Packages                       
Get:7 http://ppa.launchpad.net trusty/main amd64 Packages [14.0 kB]            
Get:8 http://ppa.launchpad.net trusty/main i386 Packages [14.3 kB]             
Get:9 http://ppa.launchpad.net trusty/main Translation-en [4,631 B]            
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:10 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Hit http://ppa.launchpad.net trusty Release                                    
Get:11 http://archive.ubuntu.com trusty-updates/main i386 Packages [722 kB]    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign https://deb.opera.com stable/non-free Translation-en_US                    
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign https://deb.opera.com stable/non-free Translation-en                       
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:12 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Hit http://archive.ubuntu.com trusty-updates/main Translation-en               
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Get:13 http://archive.ubuntu.com trusty-security/main Sources [112 kB]   
Get:14 http://archive.ubuntu.com trusty-security/restricted Sources [4,035 B]
Get:15 http://archive.ubuntu.com trusty-security/main amd64 Packages [457 kB]
Get:16 http://archive.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]
Get:17 http://archive.ubuntu.com trusty-security/main i386 Packages [431 kB]   
Get:18 http://archive.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]
Hit http://archive.ubuntu.com trusty-security/main Translation-en              
Hit http://archive.ubuntu.com trusty-security/restricted Translation-en        
Hit http://archive.ubuntu.com trusty Release                                   
Hit http://archive.ubuntu.com trusty/main Sources                              
Hit http://archive.ubuntu.com trusty/restricted Sources                        
Hit http://archive.ubuntu.com trusty/main amd64 Packages                       
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages                 
Hit http://archive.ubuntu.com trusty/main i386 Packages                        
Hit http://archive.ubuntu.com trusty/restricted i386 Packages                  
Hit http://archive.ubuntu.com trusty/main Translation-en                       
Hit http://archive.ubuntu.com trusty/restricted Translation-en                 
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://download.bitdefender.com bitdefender/non-free Translation-en_US     
Ign http://download.bitdefender.com bitdefender/non-free Translation-en        
Fetched 2,997 kB in 13s (225 kB/s)                                             
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-sdk-ide : Depends: gdb-multiarch but it is not installable
                  Depends: phablet-tools but it is not going to be installed
                  Depends: xserver-xephyr but it is not installable
                  Depends: fcitx-libs (>= 4.2.7) but it is not installable
                  Depends: libbotan-1.10-0 but it is not installable
                  Recommends: ubuntu-emulator but it is not going to be installed
                  Recommends: ubuntu-sdk-dev (= 3.5.1~133+201604191700~ubuntu14.04.1) but it is not going to be installed
                  Recommends: python3-scope-harness but it is not installable
                  Recommends: unity-scope-tool but it is not installable
                  Recommends: cmake-extras but it is not installable
E: Unable to correct problems, you have held broken packages.
stephen:~$ 


```

Does this Help? Why are there unmet Dependancies?  HHHMMmmm!?!?

Pulled up Synaptic Package Mgr. Searched for / Marked to Add - ubuntu-sdk-ide & ubuntu-sdk-dev (which included all dependancies).  

Seemed to go smoothly. Now - in the Menu / Development / Ubuntu SDK IDE 
which opens and apparently the Ubuntu-SDK is QtCreator.

Will consider this case closed!
Thanks!
Rick

---

