---
title: "Ubuntu Kylin thinking it's Kali linux GNU ?"
date: 2015-12-13
forum: Ubuntu/Debian BASED
---

### Post by michael_4 on 2015-12-13
Whenever I log in into my computer it says it's kali linux, it's clearly not. The design is changing as well to match kali linux, What the hell is happening? Someone please help me.

```
root@Miko:~# sudo apt-get update
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily InRelease
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise InRelease                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                                    
Get:1 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources [550 B]               
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-updates InRelease                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security InRelease                         
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Get:2 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages [604 B]        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Get:3 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages [800 B]         
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-backports InRelease                      
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://repo.kali.org](http://repo.kali.org) kali-bleeding-edge InRelease                          
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily Release.gpg                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://apt.simplexsolutionsinc.com](http://apt.simplexsolutionsinc.com) wheezy InRelease                        
Hit [http://security.kali.org](http://security.kali.org) sana/updates InRelease                            
Hit [http://http.kali.org](http://http.kali.org) sana InRelease                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily Release                                      
Get:4 [http://apt.simplexsolutionsinc.com](http://apt.simplexsolutionsinc.com) wheezy/main amd64 Packages [683 B]    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://repo.kali.org](http://repo.kali.org) kali-bleeding-edge/main amd64 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Get:5 [http://security.kali.org](http://security.kali.org) sana/updates/main amd64 Packages [252 kB]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Get:6 [http://http.kali.org](http://http.kali.org) sana/main amd64 Packages [12,8 MB]                  
Hit [http://repo.kali.org](http://repo.kali.org) kali-bleeding-edge/main i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Get:7 [http://apt.simplexsolutionsinc.com](http://apt.simplexsolutionsinc.com) wheezy/main i386 Packages [20 B]      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                          
Ign [http://archive.ubuntukylin.com:10006](http://archive.ubuntukylin.com:10006) trusty InRelease                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                          
Hit [http://archive.ubuntukylin.com:10006](http://archive.ubuntukylin.com:10006) trusty Release.gpg                    
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://archive.ubuntukylin.com:10006](http://archive.ubuntukylin.com:10006) trusty Release                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://repo.kali.org](http://repo.kali.org) kali-bleeding-edge/main Translation-en_US             
Ign [http://repo.kali.org](http://repo.kali.org) kali-bleeding-edge/main Translation-en                
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-backports/restricted Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-backports/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/main Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://apt.simplexsolutionsinc.com](http://apt.simplexsolutionsinc.com) wheezy/main Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted Sources                
Ign [http://apt.simplexsolutionsinc.com](http://apt.simplexsolutionsinc.com) wheezy/main Translation-en              
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-backports/restricted amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse Sources                
Hit [http://archive.ubuntukylin.com:10006](http://archive.ubuntukylin.com:10006) trusty/main amd64 Packages            
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-backports/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/main amd64 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted amd64 Packages         
Hit [http://archive.ubuntukylin.com:10006](http://archive.ubuntukylin.com:10006) trusty/main i386 Packages             
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-backports/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe amd64 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse amd64 Packages         
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                          
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                           
  404  Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/main i386 Packages                
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-backports/multiverse i386 Packages       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en_US                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted i386 Packages          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                          
Ign [http://archive.ubuntukylin.com:10006](http://archive.ubuntukylin.com:10006) trusty/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe i386 Packages            
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-backports/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse i386 Packages          
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-backports/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/main Translation-en               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse Translation-en         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted Translation-en         
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily/main Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe Translation-en           
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily/restricted Sources                       
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily/universe Sources                         
Hit [http://security.kali.org](http://security.kali.org) sana/updates/contrib amd64 Packages               
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily/multiverse Sources                       
Hit [http://security.kali.org](http://security.kali.org) sana/updates/non-free amd64 Packages              
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily/main amd64 Packages                      
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily/restricted amd64 Packages                
Get:8 [http://security.kali.org](http://security.kali.org) sana/updates/main i386 Packages [253 kB]        
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily/universe amd64 Packages                  
Get:9 [http://http.kali.org](http://http.kali.org) sana/main i386 Packages [12,8 MB]                   
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily/multiverse amd64 Packages                
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily/main i386 Packages                       
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily/restricted i386 Packages                 
Ign [http://security.kali.org](http://security.kali.org) sana/updates/contrib Translation-en_US            
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily/universe i386 Packages                   
Ign [http://http.kali.org](http://http.kali.org) sana/contrib Translation-en_US                        
Ign [http://security.kali.org](http://security.kali.org) sana/updates/contrib Translation-en               
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily/multiverse i386 Packages                 
Ign [http://http.kali.org](http://http.kali.org) sana/contrib Translation-en                           
Ign [http://security.kali.org](http://security.kali.org) sana/updates/main Translation-en_US               
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily/main Translation-en                      
Ign [http://http.kali.org](http://http.kali.org) sana/main Translation-en_US                           
Ign [http://security.kali.org](http://security.kali.org) sana/updates/main Translation-en                  
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily/multiverse Translation-en                
Ign [http://http.kali.org](http://http.kali.org) sana/main Translation-en                              
Ign [http://security.kali.org](http://security.kali.org) sana/updates/non-free Translation-en_US           
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily/restricted Translation-en                
Ign [http://http.kali.org](http://http.kali.org) sana/non-free Translation-en_US                       
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily/universe Translation-en                  
Ign [http://security.kali.org](http://security.kali.org) sana/updates/non-free Translation-en              
Ign [http://http.kali.org](http://http.kali.org) sana/non-free Translation-en                          
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-updates/main Sources                     
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-updates/restricted Sources               
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-updates/universe Sources                 
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-updates/multiverse Sources               
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-updates/main amd64 Packages              
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-updates/restricted amd64 Packages        
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-updates/universe amd64 Packages          
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-updates/multiverse amd64 Packages        
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-updates/main i386 Packages               
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-updates/restricted i386 Packages         
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-updates/universe i386 Packages           
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-updates/multiverse i386 Packages         
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-updates/main Translation-en              
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-updates/multiverse Translation-en        
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-updates/restricted Translation-en        
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-updates/universe Translation-en          
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-backports/main Sources                   
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-backports/universe Sources               
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-backports/main amd64 Packages            
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-backports/universe amd64 Packages        
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-backports/main i386 Packages             
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-backports/universe i386 Packages         
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-backports/main Translation-en            
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) wily-backports/universe Translation-en        
Hit [http://security.kali.org](http://security.kali.org) sana/updates/contrib i386 Packages                
Hit [http://security.kali.org](http://security.kali.org) sana/updates/non-free i386 Packages               
Hit [http://http.kali.org](http://http.kali.org) sana/non-free amd64 Packages                          
Hit [http://http.kali.org](http://http.kali.org) sana/contrib amd64 Packages                           
Hit [http://http.kali.org](http://http.kali.org) sana/non-free i386 Packages                           
Hit [http://http.kali.org](http://http.kali.org) sana/contrib i386 Packages                            
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_US               
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en
Fetched 25,6 MB in 1min 20s (317 kB/s)
W: Failed to fetch [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

It's downloading kali linux packages?!?

---

### Post by howefield on 2015-12-13
Open a terminal and post back here with the output of...

```
cat /etc/os-release
```

---

### Post by michael_4 on 2015-12-13
```
PRETTY_NAME="Kali GNU/Linux 2.0 (sana)"
NAME="Kali GNU/Linux"
ID=kali
VERSION="2.0 (sana)"
VERSION_ID="2.0"
ID_LIKE=debian
ANSI_COLOR="1;31"
HOME_URL="http://www.kali.org/"
SUPPORT_URL="http://forums.kali.org/"
BUG_REPORT_URL="http://bugs.kali.org/"
mikas@Miko:~$
```

---

### Post by Bucky Ball on 2015-12-13
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by howefield on 2015-12-13
Why do you think it is Kylin.. ?

---

### Post by michael_4 on 2015-12-13
Because I downloaded it as kylin. It also when i log on say "Ubuntu Kylin"

---

### Post by deadflowr on 2015-12-13
It's amazing it says anything, with all those added repos.
But it says kali over all else because you have the latest kali repo packages, which take precedent over the older kylin packages.
(newer always gets installed, over older)

Sidenote, you need to ditch the openshot ppa you have and use the daily version instead
[https://launchpad.net/~openshot.developers/+archive/ubuntu/daily](https://launchpad.net/~openshot.developers/+archive/ubuntu/daily)

The ppa you have is fairly out-of-date.

---

### Post by michael_4 on 2015-12-13
And how do I install them?

---

### Post by deadflowr on 2015-12-13
> **michael_4 said:**
> And how do I install them?
Well, being as it is now unclear what the overall design of the system is, it's best to remove the old ppa and add the newer one using the command line.
To remove the old, it should be
```
 sudo add-apt-repository -r ppa:openshot.developers/ppa 
```
and to add the new one
```
 sudo add-apt-repository ppa:openshot.developers/daily
```
then re-run the apt-get update command, to double check that the newer ppa is properly added.

---

### Post by michael_4 on 2015-12-13
```
W: Failed to fetch http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/wily/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/wily/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Well...

Nvm I fixed it

Thank you so much for the help

---

### Post by Bucky Ball on 2015-12-13
Please share with us how and mark the thread as solved (see first link in my signature). Thanks. :)

---

