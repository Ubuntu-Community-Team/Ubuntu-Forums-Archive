---
title: "software sources on alpha 3 install of quantal"
date: 2012-08-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Cavsfan on 2012-08-02
I couldn't find anything about this any where. I am having problems updating.
**sudo apt-get update** takes forever and several of the sources get errors and does not connect to.

I just DLed an alpha 3 iso and installed it yesterday. It got a lot of initial updates just fine but, after that. I get errors and it does not complete.
Is there a way I could get a good copy of Quantal sources? Or what should I do?
Thanks

---

### Post by jbicha on 2012-08-02
I have this problem with an annoying [captive portal]("https://en.wikipedia.org/wiki/Captive_portal") at work. The apt sources list gets corrupted, which shouldn't happen.

Anyway, one workaround is to ```
sudo rm /var/lib/apt/lists/*
``` and then run apt-get update again.

---

### Post by Cavsfan on 2012-08-02
> **jbicha said:**
> I have this problem with an annoying [captive portal]("https://en.wikipedia.org/wiki/Captive_portal") at work. The apt sources list gets corrupted, which shouldn't happen.

Anyway, one workaround is to ```
sudo rm /var/lib/apt/lists/*
``` and then run apt-get update again.


Thanks! Here is what I got after cleaning the cache:
```
Get:31 http://security.ubuntu.com quantal-security/universe Translation-en [14 B]                               
Ign http://security.ubuntu.com quantal-security/main Translation-en_US                                                                                                                                      
Err http://ppa.launchpad.net quantal/main amd64 Packages                                                                                                                                                    
  404  Not Found
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US                                                                                                                                
Err http://ppa.launchpad.net quantal/main i386 Packages                                                                                                                                                     
  404  Not Found
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US                                                                                                                                
Ign http://ppa.launchpad.net quantal/main Translation-en_US                                                                                                                                                 
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US                                                                                                                                  
Ign http://ppa.launchpad.net quantal/main Translation-en                                                                                                                                                    
Err http://ppa.launchpad.net quantal/main amd64 Packages                                                                                                                                                    
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages                                                                                                                                                     
  404  Not Found
Ign http://ppa.launchpad.net quantal/main Translation-en_US                                                                                                                                                 
Get:32 http://us.archive.ubuntu.com quantal/multiverse Sources [164 kB]                                                                                                                                     
Get:33 http://us.archive.ubuntu.com quantal/main amd64 Packages [1,146 kB]                                                                                                                                  
Ign http://ppa.launchpad.net quantal/main Translation-en                                                                                                                                                    
Get:34 http://us.archive.ubuntu.com quantal/restricted amd64 Packages [8,597 B]                                                                                                                             
Get:35 http://us.archive.ubuntu.com quantal/universe amd64 Packages [5,338 kB]                                                                                                                              
Get:36 http://us.archive.ubuntu.com quantal/multiverse amd64 Packages [127 kB]                                                                                                                              
Get:37 http://us.archive.ubuntu.com quantal/main i386 Packages [1,146 kB]                                                                                                                                   
Get:38 http://us.archive.ubuntu.com quantal/restricted i386 Packages [8,565 B]                                                                                                                              
Get:39 http://us.archive.ubuntu.com quantal/universe i386 Packages [5,346 kB]                                                                                                                               
Get:40 http://us.archive.ubuntu.com quantal/multiverse i386 Packages [129 kB]                                                                                                                               
Get:41 http://us.archive.ubuntu.com quantal/main Translation-en [658 kB]                                                                                                                                    
Get:42 http://us.archive.ubuntu.com quantal/multiverse Translation-en [97.2 kB]                                                                                                                             
Get:43 http://us.archive.ubuntu.com quantal/restricted Translation-en [2,401 B]                                                                                                                             
Get:44 http://us.archive.ubuntu.com quantal/universe Translation-en [3,671 kB]                                                                                                                              
Get:45 http://us.archive.ubuntu.com quantal-updates/main Sources [14 B]                                                                                                                                     
Get:46 http://us.archive.ubuntu.com quantal-updates/restricted Sources [14 B]                                                                                                                               
Get:47 http://us.archive.ubuntu.com quantal-updates/universe Sources [14 B]                                                                                                                                 
Get:48 http://us.archive.ubuntu.com quantal-updates/multiverse Sources [14 B]                                                                                                                               
Get:49 http://us.archive.ubuntu.com quantal-updates/main amd64 Packages [14 B]                                                                                                                              
Get:50 http://us.archive.ubuntu.com quantal-updates/restricted amd64 Packages [14 B]                                                                                                                        
Get:51 http://us.archive.ubuntu.com quantal-updates/universe amd64 Packages [14 B]                                                                                                                          
Get:52 http://us.archive.ubuntu.com quantal-updates/multiverse amd64 Packages [14 B]                                                                                                                        
Get:53 http://us.archive.ubuntu.com quantal-updates/main i386 Packages [14 B]                                                                                                                               
Get:54 http://us.archive.ubuntu.com quantal-updates/restricted i386 Packages [14 B]                                                                                                                         
Get:55 http://us.archive.ubuntu.com quantal-updates/universe i386 Packages [14 B]                                                                                                                           
Get:56 http://us.archive.ubuntu.com quantal-updates/multiverse i386 Packages [14 B]                                                                                                                         
Get:57 http://us.archive.ubuntu.com quantal-updates/main Translation-en [14 B]                                                                                                                              
Get:58 http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en [14 B]                                                                                                                        
Get:59 http://us.archive.ubuntu.com quantal-updates/restricted Translation-en [14 B]                                                                                                                        
Get:60 http://us.archive.ubuntu.com quantal-updates/universe Translation-en [14 B]                                                                                                                          
Get:61 http://us.archive.ubuntu.com quantal-backports/main Sources [14 B]                                                                                                                                   
Get:62 http://us.archive.ubuntu.com quantal-backports/restricted Sources [14 B]                                                                                                                             
Get:63 http://us.archive.ubuntu.com quantal-backports/universe Sources [14 B]                                                                                                                               
Get:64 http://us.archive.ubuntu.com quantal-backports/multiverse Sources [14 B]                                                                                                                             
Get:65 http://us.archive.ubuntu.com quantal-backports/main amd64 Packages [14 B]                                                                                                                            
Get:66 http://us.archive.ubuntu.com quantal-backports/restricted amd64 Packages [14 B]                                                                                                                      
Get:67 http://us.archive.ubuntu.com quantal-backports/universe amd64 Packages [14 B]                                                                                                                        
Get:68 http://us.archive.ubuntu.com quantal-backports/multiverse amd64 Packages [14 B]                                                                                                                      
Get:69 http://us.archive.ubuntu.com quantal-backports/main i386 Packages [14 B]                                                                                                                             
Get:70 http://us.archive.ubuntu.com quantal-backports/restricted i386 Packages [14 B]                                                                                                                       
Get:71 http://us.archive.ubuntu.com quantal-backports/universe i386 Packages [14 B]                                                                                                                         
Get:72 http://us.archive.ubuntu.com quantal-backports/multiverse i386 Packages [14 B]                                                                                                                       
Get:73 http://us.archive.ubuntu.com quantal-backports/main Translation-en [14 B]                                                                                                                            
Get:74 http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en [14 B]                                                                                                                      
Get:75 http://us.archive.ubuntu.com quantal-backports/restricted Translation-en [14 B]                                                                                                                      
Get:76 http://us.archive.ubuntu.com quantal-backports/universe Translation-en [14 B]                                                                                                                        
Ign http://us.archive.ubuntu.com quantal/main Translation-en_US                                                                                                                                             
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en_US                                                                                                                                       
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en_US                                                                                                                                       
Ign http://us.archive.ubuntu.com quantal/universe Translation-en_US                                                                                                                                         
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en_US                                                                                                                                     
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en_US                                                                                                                               
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en_US                                                                                                                               
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en_US                                                                                                                                 
Ign http://us.archive.ubuntu.com quantal-backports/main Translation-en_US                                                                                                                                   
Ign http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en_US                                                                                                                             
Ign http://us.archive.ubuntu.com quantal-backports/restricted Translation-en_US                                                                                                                             
Ign http://us.archive.ubuntu.com quantal-backports/universe Translation-en_US                                                                                                                               
Fetched 24.5 MB in 34s (711 kB/s)                                                                                                                                                                           
W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```The xswat repo is one I added but, I was able to get the nvidia driver yesterday and install it.
What puzzles me are these which should be good:
```
Err http://ppa.launchpad.net quantal/main amd64 Packages                                                                                                                                                    
  404  Not Found
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US                                                                                                                                
Err http://ppa.launchpad.net quantal/main i386 Packages                                                                                                                                                     
  404  Not Found
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US                                                                                                                                
Ign http://ppa.launchpad.net quantal/main Translation-en_US                                                                                                                                                 
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US                                                                                                                                  
Ign http://ppa.launchpad.net quantal/main Translation-en                                                                                                                                                    
Err http://ppa.launchpad.net quantal/main amd64 Packages                                                                                                                                                    
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages                                                                                                                                                     
  404  Not Found
```Thanks for the help! :)

---

### Post by Cavsfan on 2012-08-02
Well, I gave up and downloaded the daily iso but, it got an error during installation so I DLed the alpha 3 version again.
This time I backed up the software sources and edited them commenting out all of the source repos.
Got all of the updates and all is better. :D

---

### Post by jbicha on 2012-08-02
Those two PPAs (tualatrix & ubuntu-x-swat) don't have any packages built for Quantal yet. You can see this by going to [https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa) and looking in the "Published in" dropdown.

---

### Post by Cavsfan on 2012-08-03
> **jbicha said:**
> Those two PPAs (tualatrix & ubuntu-x-swat) don't have any packages built for Quantal yet. You can see this by going to [https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa) and looking in the "Published in" dropdown.

Thanks! I don't have them any more. I just went with standard stuff when I re-installed.
Guess I better keep it simple for now.

---

