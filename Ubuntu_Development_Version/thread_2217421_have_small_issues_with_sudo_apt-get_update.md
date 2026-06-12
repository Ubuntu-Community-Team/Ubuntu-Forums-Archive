---
title: "have small issues with sudo apt-get update"
date: 2014-04-17
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-04-17
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
  404  Not Found
the above???

The below I know about.
W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

Looks like related to when I added boot repair repo which has not been updated yet.
When will boot-repair get trusty support?

```
boat@boat-MS-7529:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://security.ubuntu.com trusty-security Release                         
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://us.archive.ubuntu.com trusty-updates Release.gpg                    
Ign http://dl.google.com stable InRelease                                      
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://security.ubuntu.com trusty-security/universe Sources                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty-updates Release                        
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://dl.google.com stable Release.gpg                                    
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Ign http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://dl.google.com stable Release                                        
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Ign http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Hit http://us.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages            
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Ign http://security.ubuntu.com trusty-security/main Translation-en_US          
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages             
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com trusty-security/universe Translation-en_US      
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en  
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/main Sources       
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://dl.google.com stable/main Translation-en_US               
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources   
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources 
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Ign http://dl.google.com stable/main Translation-en                  
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Err http://ppa.launchpad.net trusty/main amd64 Packages
  404  Not Found
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Ign http://us.archive.ubuntu.com trusty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/universe Translation-en_US
W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
boat@boat-MS-7529:~$ 

```

---

### Post by zika on 2014-04-17
Simply check, periodically, if maintainer has opened trusty branch...: [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/)

---

