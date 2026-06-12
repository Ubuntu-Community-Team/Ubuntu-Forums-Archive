---
title: "zorin ubuntu software center problem"
date: 2015-04-11
forum: Ubuntu/Debian BASED
---

### Post by alexcoyle-alex on 2015-04-11
Hi, I'm having a major problem with my zorin currently 12.04 install as it won't update ,specifically with ubuntu software center opening and then crashing,along with system problem message's etc anyone else experienced this? any easy solution?

any help will be greatly appreciated.

thank's

---

### Post by coffeecat on 2015-04-11
*Thread moved to **Ubuntu/Debian BASED**.*

Zorin prefix added to thread title.

I have no experience of Zorin, but I suggest you post the output to these two terminal commands so that those with Zorin experience can help you.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by alexcoyle-alex on 2015-04-11
thank's here's what i got,seem's a skype issue? 
$ sudo apt-get upgrade
[sudo] password for admin2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package skype:i386 needs to be reinstalled, but I can't find an archive for it.

---

### Post by alexcoyle-alex on 2015-04-11
admin2@admin2-CQ3420AN:~$ sudo apt-get update
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) dists/trusty/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) dists/trusty/restricted/binary-i386/ Release.gpg                                                     
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) dists/trusty/main/binary-i386/ Release                                                               
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) dists/trusty/restricted/binary-i386/ Release                                                         
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) dists/trusty/main/binary-i386/ Packages/DiffIndex                                                    
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) dists/trusty/restricted/binary-i386/ Packages/DiffIndex                                              
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) dists/trusty/main/binary-i386/ Translation-en_US                                                     
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) dists/trusty/main/binary-i386/ Translation-en                                                        
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) dists/trusty/restricted/binary-i386/ Translation-en_US                                               
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) dists/trusty/restricted/binary-i386/ Translation-en                                                  
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main TranslationIndex                                                                         
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted TranslationIndex                                                                   
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en_US                                                                        
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en                                                                           
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en_US                                                                  
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en                                                                     
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                                                                                    
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                                                                                                                      
Get:2 [http://deb.opera.com](http://deb.opera.com) stable Release.gpg [819 B]                                                                                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                                                       
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]                                                                                  
Get:4 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                                                                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                                                     
Get:5 [http://deb.opera.com](http://deb.opera.com) stable Release [1,721 B]                                                                                                     
Err [http://deb.opera.com](http://deb.opera.com) stable Release                                                                                                                   
  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                     
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                                                 
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [54.3 kB]                                                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                                                                                                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                                                                                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                                                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                                 
Get:7 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                                                                                        
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                                                                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                                 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [126 kB]                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                                                                  
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                                        
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                     
Get:9 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,200 B]                                                                                         
Get:10 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,180 B]                                                                                          
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [3,759 B]                                                                           
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [34.2 kB]                                                     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,815 B]                                                                                    
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [498 kB]                                                   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                                                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                                                                 
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                                       
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed Release.gpg [198 B]                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                                     
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [196 kB]                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                                                                                                       
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [8,943 B]                                                                                         
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [109 kB]                                                                                            
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,463 B]                                                                                         
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [534 kB]                                                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                                                                                                                     
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed Release [196 kB]                                                                                                          
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [8,939 B]                                                                                          
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [116 kB]                                                                                             
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,652 B]                                                                                          
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [208 B]                                                                                               
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [199 B]                                                                                         
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [202 B]                                                                                         
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [205 B]                                                                                           
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [220 kB]                                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                                                                                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                                                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                                                                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                                                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                                                                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages                                                                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages                                                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages                                                                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                                                                                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                                                                                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en                                                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages                                                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                                                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages                                                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                                                                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex                                                                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex                                                                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex                                                                                                             
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [487 kB]                                                                                                      
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [66.7 kB]                                                                                           
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [7,981 B]                                                                                               
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [113 kB]                                                                                                  
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [9,417 B]                                                                                               
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [887 kB]                                                                                               
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                                                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                                                                                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                                                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                                                                                            
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                                                                                                                      
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                                                                                                                          
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [13.6 kB]                                                                                        
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [256 kB]                                                                                           
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages                                                                                                              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages                                                                                                               
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [16.4 kB]                                                                                        
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [928 kB]                                                                                                
Get:41 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex [361 B]                                                                                                 
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex                                                                                                            
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [13.6 kB]                                                                                         
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [265 kB]                                                                                            
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [16.6 kB]                                                                                         
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [10.6 kB]                                                                                            
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [7,613 B]                                                                                      
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [7,297 B]                                                                                      
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [8,333 B]                                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                                                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources                                                                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources                                                                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources                                                                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages                                                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages                                                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages                                                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages                                                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages                                                                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages                                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages                                                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages                                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex                                                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex                                                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex                                                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex                                                                                                   
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted amd64 Packages [1,140 B]                                                                                       
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main amd64 Packages [143 kB]                                                                                              
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US                                                                                                           
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse amd64 Packages [28 B]                                                                                          
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe amd64 Packages [8,008 B]                                                                                         
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted i386 Packages [1,138 B]                                                                                        
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main i386 Packages [176 kB]                                                                                               
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en                                                                                                              
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse i386 Packages [28 B]                                                                                           
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe i386 Packages [9,281 B]                                                                                          
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main TranslationIndex [10.6 kB]                                                                                           
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse TranslationIndex [7,613 B]                                                                                     
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted TranslationIndex [7,297 B]                                                                                     
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe TranslationIndex [8,333 B]                                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                                                                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en                                                                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en                                                                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en                                                                                                               
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [391 kB]                                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en                                                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en                                                                                                     
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [149 kB]                                                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en                                                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en                                                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en                                                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en                                                                                                     
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main Translation-en [36.4 kB]                                                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse Translation-en                                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted Translation-en                                                                                                    
Get:64 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe Translation-en [5,876 B]                                                                                         
Fetched 6,188 kB in 19s (319 kB/s)                                                                                                                                             
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 517590D9A8492E35


W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  


W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)/ trusty/main i386 Packages (/var/lib/apt/lists/Ubuntu%2014.04.1%20LTS%20%5fTrusty%20Tahr%5f%20-%20Release%20amd64%20(20140722.2)_dists_trusty_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)/ trusty/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2014.04.1%20LTS%20%5fTrusty%20Tahr%5f%20-%20Release%20amd64%20(20140722.2)_dists_trusty_restricted_binary-i386_Packages)
admin2@admin2-CQ3420AN:~$

---

