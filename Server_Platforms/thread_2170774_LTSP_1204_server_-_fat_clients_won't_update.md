---
title: "LTSP 1204 server - fat clients won't update"
date: 2013-08-27
forum: Server Platforms
---

### Post by theller on 2013-08-27
I have an LTSP server that will run updates with apt-get but when I chroot into the clients I cannot update or install to the client image. Most of the posts I found with similar problems had at least a few things updating. With me it's nothing. Here is what I get on update:

```
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://us.archive.ubuntu.com precise InRelease                             
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://dl.google.com stable InRelease                                      
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://ppa.launchpad.net precise InRelease                                 
Err http://archive.canonical.com precise Release.gpg                           
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security Release.gpg                    
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://dl.google.com stable Release.gpg                                    
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Err http://extras.ubuntu.com precise Release.gpg                               
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Ign http://security.ubuntu.com precise-security Release                        
Ign http://archive.canonical.com precise Release                               
Ign http://extras.ubuntu.com precise Release                                   
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net precise InRelease                                 
Err http://us.archive.ubuntu.com precise Release.gpg                           
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-updates Release.gpg                   
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise Release.gpg                               
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Ign http://dl.google.com stable/main TranslationIndex                          
Err http://us.archive.ubuntu.com precise-backports Release.gpg                 
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://archive.canonical.com precise/partner TranslationIndex              
Err http://ppa.launchpad.net precise Release.gpg                               
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://us.archive.ubuntu.com precise Release                               
Err http://ppa.launchpad.net precise Release.gpg                               
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise Release.gpg                               
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Ign http://us.archive.ubuntu.com precise-updates Release                       
Ign http://ppa.launchpad.net precise Release                                   
Ign http://us.archive.ubuntu.com precise-backports Release                     
Ign http://ppa.launchpad.net precise Release                                   
Ign http://ppa.launchpad.net precise Release                                   
Ign http://security.ubuntu.com precise-security/main TranslationIndex          
Ign http://ppa.launchpad.net precise Release                                   
Ign http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Ign http://security.ubuntu.com precise-security/restricted TranslationIndex    
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://security.ubuntu.com precise-security/universe TranslationIndex      
Err http://dl.google.com stable/main i386 Packages                             
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://dl.google.com stable/main Translation-en_US                         
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign http://us.archive.ubuntu.com precise/main TranslationIndex                 
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Err http://archive.canonical.com precise/partner Sources                       
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://dl.google.com stable/main Translation-en                            
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com precise/main Sources                              
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Err http://archive.canonical.com precise/partner i386 Packages                 
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Err http://extras.ubuntu.com precise/main i386 Packages                        
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://us.archive.ubuntu.com precise/universe TranslationIndex             
Err http://archive.canonical.com precise/partner Translation-en_US             
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com precise/main Translation-en_US                    
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.canonical.com precise/partner Translation-en                
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Err http://extras.ubuntu.com precise/main Translation-en                       
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Ign http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Ign http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Ign http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Ign http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Ign http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Ign http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Ign http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Err http://security.ubuntu.com precise-security/main Sources                   
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/restricted Sources             
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/universe Sources               
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/multiverse Sources             
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/main i386 Packages             
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/restricted i386 Packages       
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/universe i386 Packages         
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/multiverse i386 Packages       
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Sources                              
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main i386 Packages                        
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Sources                              
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main i386 Packages                        
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/main Translation-en_US         
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Sources                              
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/main Translation-en            
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/multiverse Translation-en_US   
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main i386 Packages                        
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/multiverse Translation-en      
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/restricted Translation-en_US   
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/restricted Translation-en      
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Sources                              
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/universe Translation-en_US     
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main i386 Packages                        
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/universe Translation-en        
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en_US                    
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en                   
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en_US                
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en                   
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en_US                
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en                   
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en_US                
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise/main Translation-en                   
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
23% [Connecting to us.archive.ubuntu.com]^Z                                
[1]+  Stopped                 sudo apt-get update


```

I stopped it after an hour because nothing was working.

Here is /opt/ltsp/i386/etc/apt/sources.list
```
# 

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423.2)]/ precise main restricted

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423.2)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

Any ideas? Does anyone know the wicked spirit that has entered my clients? Can I post any other info?

---

### Post by theller on 2013-08-27
I think I got it. The answer came from this page [http://www.thefanclub.co.za/how-to/configure-update-auto-login-ubuntu-12-04-ltsp-fat-clients](http://www.thefanclub.co.za/how-to/configure-update-auto-login-ubuntu-12-04-ltsp-fat-clients) and the code I needed was:

sudo cp /etc/resolv.conf /opt/ltsp/i386/etc/resolv.conf

I forgot the DNS# changed.

---

