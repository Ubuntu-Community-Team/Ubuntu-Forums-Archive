---
title: "Aptitude Segmentation Fault"
date: 2008-09-29
forum: Server Platforms
---

### Post by MagicBrain on 2008-09-29
Hi,

i made today a upgrade to one of my servers.
When i run aptitude update or upgrade, the result is this:
# aptitude update
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy Release.gpg
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/multiverse Translation-en_US                                              
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates Release.gpg                                                       
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/main Translation-en_US                                            
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/restricted Translation-en_US                                                            
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/universe Translation-en_US                                                              
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US                                                            
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports Release.gpg                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                                                                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US                                                                   
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/main Translation-en_US                                                                                
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/restricted Translation-en_US                                                                          
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/universe Translation-en_US                                                                            
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US                                                                          
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy Release                                                                                                         
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates Release                                                                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US                                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                                                                  
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                                        
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US                          
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                                
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/main Packages                                     
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/restricted Packages           
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/main Sources                  
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/restricted Sources            
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/universe Packages             
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/universe Sources              
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/multiverse Packages           
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/multiverse Sources            
Ign [http://download.webmin.com](http://download.webmin.com) sarge Release.gpg                     
Ign [http://download.webmin.com](http://download.webmin.com) sarge/contrib Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources                           
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                                    
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/main Packages                               
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/restricted Packages   
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/main Sources          
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/restricted Sources    
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/universe Packages     
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/universe Sources      
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/multiverse Packages   
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/multiverse Sources    
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/main Packages       
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/restricted Packages 
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/universe Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources                           
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                                     
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/multiverse Packages 
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/main Sources
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/multiverse Sources
**100% [Working]Segmentation fault**

**but, when i run apt-get update**

# apt-get update
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy Release.gpg
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/multiverse Translation-en_US                              
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates Release.gpg                                       
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/main Translation-en_US                            
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/restricted Translation-en_US                                            
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/universe Translation-en_US                                              
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US                                            
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports Release.gpg                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                                                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US                                             
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/main Translation-en_US                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                                                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US                                                       
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/restricted Translation-en_US                                          
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/universe Translation-en_US                      
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US                    
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy Release                                                   
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates Release                                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                                                                  
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports Release                                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages              
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/main Packages                 
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/restricted Packages           
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/main Sources                  
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/restricted Sources            
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/universe Packages             
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/universe Sources              
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/multiverse Packages           
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/multiverse Sources            
Ign [http://download.webmin.com](http://download.webmin.com) sarge Release.gpg                     
Ign [http://download.webmin.com](http://download.webmin.com) sarge/contrib Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources                           
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                                     
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/main Packages                               
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/restricted Packages   
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/main Sources          
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/restricted Sources    
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/universe Packages     
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/universe Sources      
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/multiverse Packages   
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/multiverse Sources    
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/main Packages       
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/restricted Packages 
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/universe Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources     
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/multiverse Packages 
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/main Sources
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-backports/multiverse Sources
Fetched 1B in 0s (1B/s)
Reading package lists... Done

Well, i think aptitude package is broken ... any ideas ?

Best regards,

Octávio Filipe Gonçalves

---

### Post by lykwydchykyn on 2008-09-29
apt-get install aptitude --reinstall

might fix it.  If not, I'd start checking the hardware for faults (run memtest86, badblocks, fsck, etc).

---

### Post by mattmill30 on 2009-07-15
Hi,

I know this is resurecting an old thread, but its top listed in google for aptitude segmentation fault, so if someone knows the fix, it'll help people more than me creating a new one.

Basically i have the same problem, however, its also a problem with apt-get.

I doubt its a hardware fault, because if it were a ram or hard drive fault, i'd expect it to make itself more prominent that just a little message in terminal when i try and run synaptic/aptitude/apt-get.

Anyone any ideas?

Thanks,

Matthew Millar

---

### Post by Axed on 2009-10-25
Just had this problem on my home server, and found this solution in another thread ([http://ubuntuforums.org/showthread.php?t=19563](http://ubuntuforums.org/showthread.php?t=19563)):
```
sudo rm /var/cache/apt/*.bin
```

I use apt-cacher-ng which may have contributed to the problem, but I also had some flaky ram in there for a while.

---

### Post by SemenSemenych on 2010-04-08
Thanks! That really helps! :)

---

