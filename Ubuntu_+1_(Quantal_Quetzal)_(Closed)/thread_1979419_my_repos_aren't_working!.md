---
title: "my repos aren't working!"
date: 2012-05-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by codingman on 2012-05-13
I can't add repos to quantal, it always searches for the repos from the freeze of quantal, not the precise packages and repos. I'm also getting an error in gnome, saying that the repo data is outdated, and that is can't find the refresh of it. 

Any help is appreciated!
Codingman

---

### Post by codingman on 2012-05-13
I'll report it as a bug if i need to.

---

### Post by dino99 on 2012-05-13
reporting prior beta is useless

post:

cat /etc/apt/sources.list

---

### Post by codingman on 2012-05-13
Here you go:
```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta i386 (20120328)]/ precise main restricted

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
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://packages.mate-desktop.org/repo/ubuntu precise main
deb-src http://packages.mate-desktop.org/repo/ubuntu precise main

```

---

### Post by dino99 on 2012-05-13
So i suppose you have already understood where is the problem  :lolflag:

here is the "quantal" subforum, not "precise" as you are using.

---

### Post by codingman on 2012-05-13
I had upped to quantal, but now it says Precise!!!

---

### Post by codingman on 2012-05-13
Look at the update process then :-k 
```
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]                                                                                                         
Ign http://ppa.launchpad.net quantal InRelease                                                                                                                
Ign http://ppa.launchpad.net precise InRelease                                                                                                                
Ign http://ppa.launchpad.net quantal InRelease                                                                                                             
Ign http://security.ubuntu.com precise-security InRelease                                                                                                  
Ign http://extras.ubuntu.com precise InRelease                                                                                                             
Ign http://us.archive.ubuntu.com precise InRelease                                                                                                         
Ign http://us.archive.ubuntu.com precise-updates InRelease                                                                                           
Ign http://us.archive.ubuntu.com precise-backports InRelease                                                                                                  
Get:2 http://dl.google.com stable Release [1,347 B]                                                                                                           
Ign http://ppa.launchpad.net quantal Release.gpg                                                                                                     
Hit http://ppa.launchpad.net precise Release.gpg                                                                                            
Hit http://security.ubuntu.com precise-security Release.gpg                                                                                 
Get:3 http://extras.ubuntu.com precise Release.gpg [72 B]                                                             
Hit http://us.archive.ubuntu.com precise Release.gpg                                                                                                
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                                                                                                  
Hit http://packages.mate-desktop.org precise InRelease                                                                                                        
Ign http://ppa.launchpad.net quantal Release.gpg                                                                                                              
Ign http://ppa.launchpad.net quantal Release                                                                                                        
Get:4 http://extras.ubuntu.com precise Release [11.9 kB]                                                              
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                                                                                        
Hit http://packages.mate-desktop.org precise/main Sources                                                                                             
Hit http://security.ubuntu.com precise-security Release                                                                                               
Hit http://ppa.launchpad.net precise Release                                                                                                           
Hit http://us.archive.ubuntu.com precise Release                                                                                                              
Ign http://ppa.launchpad.net quantal Release                                                                                                                  
Hit http://security.ubuntu.com precise-security/main Sources                                                                                          
Hit http://packages.mate-desktop.org precise/main i386 Packages                                                                 
Ign http://packages.mate-desktop.org precise/main TranslationIndex                                                              
Hit http://us.archive.ubuntu.com precise-updates Release                                                                        
Ign http://ppa.launchpad.net quantal/main TranslationIndex                                                                                                    
Hit http://security.ubuntu.com precise-security/restricted Sources                                                
Hit http://security.ubuntu.com precise-security/universe Sources                                                                        
Hit http://security.ubuntu.com precise-security/multiverse Sources                                                                      
Hit http://security.ubuntu.com precise-security/main i386 Packages                                                                      
Hit http://security.ubuntu.com precise-security/restricted i386 Packages                                          
Get:5 http://dl.google.com stable/main i386 Packages [1,268 B]                                                                          
Hit http://us.archive.ubuntu.com precise-backports Release                                                                                   
Hit http://us.archive.ubuntu.com precise/main Sources                                                                                                         
Hit http://us.archive.ubuntu.com precise/restricted Sources                                                                                                   
Hit http://us.archive.ubuntu.com precise/universe Sources                                                                                                     
Hit http://us.archive.ubuntu.com precise/multiverse Sources                                                                                                   
Hit http://us.archive.ubuntu.com precise/main i386 Packages                                                                                                   
Get:6 http://extras.ubuntu.com precise/main Sources [476 B]                                                                                                   
Hit http://security.ubuntu.com precise-security/universe i386 Packages                                                                                        
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages                                                                     
Hit http://security.ubuntu.com precise-security/main TranslationIndex                                                  
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                                            
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                                                                  
Hit http://ppa.launchpad.net precise/main Sources                                                                                            
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                                      
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                             
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages                                                      
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                                                        
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages                                                      
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                                                         
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex                                                                         
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex                                                                         
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex                                                                           
Hit http://us.archive.ubuntu.com precise-updates/main Sources                                                                                
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources                                                                          
Get:7 http://extras.ubuntu.com precise/main i386 Packages [555 B]                                                                            
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                                                   
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                                                                                     
Ign http://ppa.launchpad.net quantal/main TranslationIndex                                                                                   
Hit http://us.archive.ubuntu.com precise-updates/universe Sources                                                                            
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources                                                    
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages                                                                          
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages                                                                    
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages                                                                      
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages                                                                    
Hit http://security.ubuntu.com precise-security/main Translation-en                                                                          
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                                              
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex                                                                       
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex                                                                 
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex                                           
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex                                             
Hit http://us.archive.ubuntu.com precise-backports/main Sources                                                                              
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources                                                                        
Hit http://us.archive.ubuntu.com precise-backports/universe Sources                                                                          
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources                                                                        
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages                                                                        
Hit http://security.ubuntu.com precise-security/restricted Translation-en                                                                    
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages                                                                  
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages                                                                    
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages                                                                  
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex                                                                     
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex                                                               
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex                                                               
Hit http://security.ubuntu.com precise-security/universe Translation-en                                                                      
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex                                                                 
Hit http://us.archive.ubuntu.com precise/main Translation-en                                                           
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en                               
Hit http://us.archive.ubuntu.com precise/restricted Translation-en                                                     
Hit http://us.archive.ubuntu.com precise/universe Translation-en                                                       
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en                                                   
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en                       
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en                                             
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en                                               
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en                           
Err http://ppa.launchpad.net quantal/main Sources                                                                      
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages                                                                
  404  Not Found
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en                                           
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en                                           
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en                                             
Err http://ppa.launchpad.net quantal/main Sources                                                                      
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages                                          
  404  Not Found
Ign http://ppa.launchpad.net quantal/main Translation-en_US                
Ign http://packages.mate-desktop.org precise/main Translation-en_US        
Ign http://ppa.launchpad.net quantal/main Translation-en                   
Ign http://ppa.launchpad.net precise/main Translation-en_US                
Ign http://ppa.launchpad.net precise/main Translation-en                   
Ign http://ppa.launchpad.net quantal/main Translation-en_US                
Ign http://extras.ubuntu.com precise/main Translation-en_US                                                        
Ign http://packages.mate-desktop.org precise/main Translation-en                            
Ign http://dl.google.com stable/main TranslationIndex                 
Ign http://ppa.launchpad.net quantal/main Translation-en              
Ign http://extras.ubuntu.com precise/main Translation-en
Ign http://dl.google.com stable/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Fetched 15.8 kB in 3s (4,674 B/s)
W: Failed to fetch http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
armeen@ubuntu:~$ ubuntu-software-center
No command 'ubuntu-software-center' found, did you mean:
 Command 'lubuntu-software-center' from package 'lubuntu-software-center' (universe)
ubuntu-software-center: command not found
armeen@ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta i386 (20120328)]/ precise main restricted

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
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://packages.mate-desktop.org/repo/ubuntu precise main
deb-src http://packages.mate-desktop.org/repo/ubuntu precise main
armeen@ubuntu:~$ sudo gedit /etc/apt/sources.list
[sudo] password for armeen: 
armeen@ubuntu:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Ign http://ppa.launchpad.net quantal InRelease                                                                                                                
Ign http://ppa.launchpad.net precise InRelease                                                                                                                
Ign http://ppa.launchpad.net quantal InRelease                                                                                                       
Get:1 http://dl.google.com stable Release.gpg [198 B]                                                                                                
Ign http://security.ubuntu.com precise-security InRelease                                                                                                     
Ign http://extras.ubuntu.com precise InRelease                                                                                                       
Ign http://us.archive.ubuntu.com precise InRelease                                                                                                   
Ign http://us.archive.ubuntu.com precise-updates InRelease                                                                                           
Ign http://us.archive.ubuntu.com precise-backports InRelease                                                                                         
Get:2 http://dl.google.com stable Release [1,347 B]                                                                                                  
Ign http://ppa.launchpad.net quantal Release.gpg                                                                                                     
Get:3 http://extras.ubuntu.com precise Release.gpg [72 B]                                                        
Get:4 http://security.ubuntu.com precise-security Release.gpg [198 B]                                                                           
Get:5 http://us.archive.ubuntu.com precise Release.gpg [198 B]                                                                                    
Get:6 http://dl.google.com stable/main i386 Packages [1,268 B]                                                                                    
Hit http://packages.mate-desktop.org precise InRelease                                                                                       
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                              
Hit http://extras.ubuntu.com precise Release                                                                                            
Get:7 http://security.ubuntu.com precise-security Release [49.6 kB]                                                                      
Get:8 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]                                                                         
Ign http://dl.google.com stable/main TranslationIndex                                                                                            
Ign http://ppa.launchpad.net quantal Release.gpg                                                                                                 
Hit http://packages.mate-desktop.org precise/main Sources                                                                  
Hit http://extras.ubuntu.com precise/main Sources                                                                          
Get:9 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]                                                   
Ign http://ppa.launchpad.net quantal Release                                                                                                                
Hit http://extras.ubuntu.com precise/main i386 Packages                                                                                          
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                                                       
Hit http://packages.mate-desktop.org precise/main i386 Packages                                                                                  
Ign http://packages.mate-desktop.org precise/main TranslationIndex                                                                               
Get:10 http://us.archive.ubuntu.com precise Release [49.6 kB]                                                                                    
Hit http://ppa.launchpad.net precise Release                                                                                                               
Ign http://ppa.launchpad.net quantal Release                                                                                                                  
Get:11 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]                                                                                         
Get:12 http://security.ubuntu.com precise-security/main Sources [7,089 B]                                                                                     
Ign http://ppa.launchpad.net quantal/main TranslationIndex                                                                                                    
Get:13 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]                                                                                       
Get:14 http://security.ubuntu.com precise-security/restricted Sources [14 B]                                                                                  
Get:15 http://security.ubuntu.com precise-security/universe Sources [3,653 B]                                                                                 
Get:16 http://security.ubuntu.com precise-security/multiverse Sources [696 B]                                                                                 
Get:17 http://security.ubuntu.com precise-security/main i386 Packages [32.9 kB]                                                                               
Hit http://ppa.launchpad.net precise/main Sources                                                                                                             
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                                                       
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                                    
Get:18 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]                                                                            
Get:19 http://security.ubuntu.com precise-security/universe i386 Packages [8,594 B]                                                                           
Ign http://ppa.launchpad.net quantal/main TranslationIndex                                                                                                    
Get:20 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,393 B]                                                                         
Hit http://security.ubuntu.com precise-security/main TranslationIndex                                                                                         
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                                                                                   
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                                                                                   
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                                                                                     
Get:21 http://us.archive.ubuntu.com precise/main Sources [934 kB]                                                                                             
Ign http://dl.google.com stable/main Translation-en_US                                                                                                        
Ign http://dl.google.com stable/main Translation-en                                                                                             
Hit http://security.ubuntu.com precise-security/main Translation-en                                                       
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                                                 
Hit http://security.ubuntu.com precise-security/restricted Translation-en                                                 
Hit http://security.ubuntu.com precise-security/universe Translation-en                                                   
Ign http://extras.ubuntu.com precise/main Translation-en_US                                                               
Err http://ppa.launchpad.net quantal/main Sources                                                    
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages                       
  404  Not Found
Ign http://extras.ubuntu.com precise/main Translation-en                                            
Ign http://packages.mate-desktop.org precise/main Translation-en_US                                 
Err http://ppa.launchpad.net quantal/main Sources                             
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages 
  404  Not Found
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://packages.mate-desktop.org precise/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Get:22 http://us.archive.ubuntu.com precise/restricted Sources [5,470 B]
Get:23 http://us.archive.ubuntu.com precise/universe Sources [5,019 kB]
Get:24 http://us.archive.ubuntu.com precise/multiverse Sources [155 kB]                                                                                       
Get:25 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB]                                                                                     
Get:26 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,431 B]                                                                                
Get:27 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]                                                                                 
Get:28 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]                                                                                 
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                                                                                                
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex                                                                                          
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex                                                                                          
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex                                                                                            
Get:29 http://us.archive.ubuntu.com precise-updates/main Sources [31.2 kB]                                                                                    
Get:30 http://us.archive.ubuntu.com precise-updates/restricted Sources [765 B]                                                                                
Get:31 http://us.archive.ubuntu.com precise-updates/universe Sources [10.1 kB]                                                                                
Get:32 http://us.archive.ubuntu.com precise-updates/multiverse Sources [696 B]                                                                                
Get:33 http://us.archive.ubuntu.com precise-updates/main i386 Packages [96.5 kB]                                                                              
Get:34 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [770 B]                                                                          
Get:35 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [27.7 kB]                                                                          
Get:36 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [1,393 B]                                                                        
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex                                                                                        
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex                                                                                  
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex                                                                                  
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex                                                                                    
Get:37 http://us.archive.ubuntu.com precise-backports/main Sources [700 B]                                                                                    
Get:38 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]                                                                               
Get:39 http://us.archive.ubuntu.com precise-backports/universe Sources [1,680 B]                                                                              
Get:40 http://us.archive.ubuntu.com precise-backports/multiverse Sources [14 B]                                                                               
Get:41 http://us.archive.ubuntu.com precise-backports/main i386 Packages [559 B]                                                                              
Get:42 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]                                                                         
Get:43 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [1,391 B]                                                                        
Get:44 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [14 B]                                                                         
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex                                                                                      
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex                                                                                
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex                                                                                
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex                                                                                  
Hit http://us.archive.ubuntu.com precise/main Translation-en                                                                                                  
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en                                                                                            
Hit http://us.archive.ubuntu.com precise/restricted Translation-en                                                                                            
Hit http://us.archive.ubuntu.com precise/universe Translation-en                                                                                              
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en                                                                                          
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en                                                                                    
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en                                                                                    
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en                                                                                      
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en                                                                                        
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en                                                                                  
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en                                                                                  
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en                                                                                    
Fetched 12.7 MB in 17s (733 kB/s)                                                                                                                             
W: Failed to fetch http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by VMC on 2012-05-13
This was covered in another unrelated topic. Until there is a official quantal iso, the repos will report precise. 

I'll try to find the info.

edit: From this [topic]("http://ubuntuforums.org/showthread.php?t=1969670"), read [this]("http://ubuntuforums.org/showpost.php?p=11884883&postcount=86").

---

### Post by cariboo on 2012-05-13
I'd suggest you create a backup of your /etc/apt/sources.list, then use gedit search and replace to replace precise with quantal in your original /etc/apt/sources.list and see what happens. If things go wrong, you can always revert from you backup.

---

### Post by codingman on 2012-05-14
take a look at my sources.list file:
```
# deb cdrom:[Ubuntu 12.10 _Precise Pangolin_ - i386 (20120328)]/ precise main restricted

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
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://packages.mate-desktop.org/repo/ubuntu precise main
deb-src http://packages.mate-desktop.org/repo/ubuntu precise main
``` 

There is nothing in there that says quantal or quetzal, but if you look at my update code; three posts ago, you'll see that it says quantal a bunch of times, is there somewhere else i can keep the repos only in precise?

---

### Post by arpanaut on 2012-05-14
what is the result of```
 cat /etc/apt/sources.list.d/*
```As I remember you "accidentally" upgraded to Quantal, Maybe the process didn't get completed???

I think that you have a mixed bag of repositories esp. PPA's 

Lets see the output of that command and see what's up.

---

### Post by codingman on 2012-05-14
here:
```
# deb http://ppa.launchpad.net/alecive/antigone/ubuntu quantal main
# deb-src http://ppa.launchpad.net/alecive/antigone/ubuntu quantal main
# deb http://ppa.launchpad.net/alecive/antigone/ubuntu quantal main
# deb-src http://ppa.launchpad.net/alecive/antigone/ubuntu quantal main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
deb http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu quantal main
deb-src http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu quantal main
deb http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu precise main
deb-src http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu precise main
deb http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu precise main
deb-src http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu precise main
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu quantal main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu quantal main
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu quantal main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu quantal main

```

---

### Post by ts3 on 2012-05-15
I had a similar error but with different repositories, the extras repository for quantal (from what I saw in your sources.list you had precise for extras so that was working for you).  The error I had, for comparison purposes, is here:

```
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
tsj@linux-laptop:~$
```

I checked the webpages in the message ([http://extras.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/quantal/main/source/Sources) etcetera) and it looked like those pages did not exist yet so the updater could not find the repository and errored out.  I removed the repository by unchecking "Independent" in the software centre which commented out the extras repositories in /etc/apt/sources.list and have been able to apt-get update && apt-get upgrade without problems. 

I imagine the issue is due to third party developers not having started on quantal yet :)

You can try to disable/comment out the repos that give you errors on apt-get update and see what happens.

Cheers

Edited to add: For what it's worth, my quantal install was a clean install rather than an upgrade from precise, accidental or otherwise.  However, the installer saw the precise partition and offered to export user settings.  I exported the settings for one user  which may explain why I had the extras repository enabled in quantal even though the repo does not exist yet.

---

### Post by codingman on 2012-05-15
> **ts3 said:**
> 
You can try to disable/comment out the repos that give you errors on apt-get update and see what happens.

Cheers

That won't solve it. It's not like it not downloading and connecting to my extra added PPA's is not allowing it to update the system itself.

I just wanted to connect to some PPA's.

---

### Post by ts3 on 2012-05-15
> **codingman said:**
> That won't solve it. It's not like it not downloading and connecting to my extra added PPA's is not allowing it to update the system itself.

I just wanted to connect to some PPA's.

I was looking at the output in post#6: if you scroll down and look at the warnings you got just before apt-get quit without updating you can see that the updater could not connect to some websites with ppa's and gave a warning with a 404 error.  

When you try to open one of the links from your post in a browser, for example this [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)

the link shows that the webpage does not exist (yet).  This makes me think that after all the updater does not connect to that ppa and that's what causes the failure to update.

Of course, YMMV

---

### Post by codingman on 2012-05-16
> **ts3 said:**
> I was looking at the output in post#6: if you scroll down and look at the warnings you got just before apt-get quit without updating you can see that the updater could not connect to some websites with ppa's and gave a warning with a 404 error.  

When you try to open one of the links from your post in a browser, for example this [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)

the link shows that the webpage does not exist (yet).  This makes me think that after all the updater does not connect to that ppa and that's what causes the failure to update.

Of course, YMMV
I know they do not exist. The reason I made this thread entirely is so that I could ask if there was any way I could specify to go to the Precise link until the PPA's are updated and have Quantal support.

---

### Post by ts3 on 2012-05-16
> **codingman said:**
> I know they do not exist. The reason I made this thread entirely is so that I could ask if there was any way I could specify to go to the Precise link until the PPA's are updated and have Quantal support.

OK, I might have misunderstood and actually I still am not sure if I understand what you're after so apologies.  

If you disable the repos that are not working you will likely get quantal support for everything else (apt-get update && apt-get upgrade will work as usual).  

If you are asking if you can change the non-working ppas to precise and still have a working system I reckon you can find out by trial and error: back up your existing sources.list, change the non-working repos to precise and see what happens.  If things break restore from back-up.

If you are asking about something else entirely my apologies again for not understanding your question: in that case I'm officially out of ideas.

Cheers & good luck

---

