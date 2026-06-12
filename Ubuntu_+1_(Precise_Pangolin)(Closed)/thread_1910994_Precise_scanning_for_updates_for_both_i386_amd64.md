---
title: "Precise scanning for updates for both i386 amd64?"
date: 2012-01-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by NCLI on 2012-01-18
My Precise machine seems to be checking both the i386 archives and the amd64 archives for updates, is this normaal? I currently get a huge list of packages that have to be removed when I try to update, could this be the cause?
```
&#28961;&#35222; http://archive.ubuntu.com precise InRelease                                                                                                                                         
&#28961;&#35222; http://archive.ubuntu.com precise-updates InRelease                                                                                                                                 
&#28961;&#35222; http://archive.ubuntu.com precise-backports InRelease    
&#28961;&#35222; http://extras.ubuntu.com precise InRelease                                              
&#28961;&#35222; http://ppa.launchpad.net precise InRelease                                              
&#12498;&#12483;&#12488; http://extras.ubuntu.com precise Release.gpg            
&#12498;&#12483;&#12488; http://ppa.launchpad.net precise Release.gpg            
&#28961;&#35222; http://archive.ubuntu.com precise-security InRelease      
&#21462;&#24471;:1 http://archive.ubuntu.com precise Release.gpg [198 B]   
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates Release.gpg                                    
&#12498;&#12483;&#12488; http://extras.ubuntu.com precise Release                                              
&#12498;&#12483;&#12488; http://ppa.launchpad.net precise Release                                              
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports Release.gpg 
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security Release.gpg  
&#21462;&#24471;:2 http://archive.ubuntu.com precise Release [49.6 kB]                                   
&#12498;&#12483;&#12488; http://extras.ubuntu.com precise/main Sources                                         
&#12498;&#12483;&#12488; http://ppa.launchpad.net precise/main Sources                                         
&#12498;&#12483;&#12488; http://extras.ubuntu.com precise/main amd64 Packages      
&#12498;&#12483;&#12488; http://extras.ubuntu.com precise/main i386 Packages                                     
&#12498;&#12483;&#12488; http://ppa.launchpad.net precise/main amd64 Packages                                    
&#12498;&#12483;&#12488; http://ppa.launchpad.net precise/main i386 Packages                                     
&#28961;&#35222; http://ppa.launchpad.net precise/main TranslationIndex      
&#28961;&#35222; http://extras.ubuntu.com precise/main TranslationIndex      
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates Release                                
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports Release                              
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security Release                                                           
&#21462;&#24471;:3 http://archive.ubuntu.com precise/main Sources [921 kB]                                                      
&#28961;&#35222; http://ppa.launchpad.net precise/main Translation-ja_JP                                 
&#21462;&#24471;:4 http://archive.ubuntu.com precise/restricted Sources [5,064 B]                        
&#21462;&#24471;:5 http://archive.ubuntu.com precise/universe Sources [5,040 kB]
&#28961;&#35222; http://ppa.launchpad.net precise/main Translation-ja                                                            
&#28961;&#35222; http://extras.ubuntu.com precise/main Translation-ja_JP                                                         
&#28961;&#35222; http://ppa.launchpad.net precise/main Translation-en                                      
&#28961;&#35222; http://extras.ubuntu.com precise/main Translation-ja       
&#28961;&#35222; http://extras.ubuntu.com precise/main Translation-en                                                                                                                                                   
&#21462;&#24471;:6 http://archive.ubuntu.com precise/multiverse Sources [161 kB]                                                                                                                                        
&#21462;&#24471;:7 http://archive.ubuntu.com precise/main amd64 Packages [1,288 kB]                                                                                                                                     
&#21462;&#24471;:8 http://archive.ubuntu.com precise/restricted amd64 Packages [8,350 B]                                                                                                                                
&#21462;&#24471;:9 http://archive.ubuntu.com precise/universe amd64 Packages [4,758 kB]                                                                                                                                 
&#21462;&#24471;:10 http://archive.ubuntu.com precise/multiverse amd64 Packages [124 kB]                                                                                                                                
&#21462;&#24471;:11 http://archive.ubuntu.com precise/main i386 Packages [1,288 kB]                                                                                                                                     
&#21462;&#24471;:12 http://archive.ubuntu.com precise/restricted i386 Packages [8,270 B]                                                                                                                                
&#21462;&#24471;:13 http://archive.ubuntu.com precise/universe i386 Packages [4,769 kB]                                                                                                                                 
&#21462;&#24471;:14 http://archive.ubuntu.com precise/multiverse i386 Packages [126 kB]                                                                                                                                 
&#21462;&#24471;:15 http://archive.ubuntu.com precise/main TranslationIndex [3,502 B]                                                                                                                                   
&#21462;&#24471;:16 http://archive.ubuntu.com precise/multiverse TranslationIndex [2,472 B]                                                                                                                             
&#21462;&#24471;:17 http://archive.ubuntu.com precise/restricted TranslationIndex [2,464 B]                                                                                                                             
&#21462;&#24471;:18 http://archive.ubuntu.com precise/universe TranslationIndex [2,712 B]                                                                                                                               
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/main Sources                                                                                                                                               
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/restricted Sources                                                                                                                                         
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/universe Sources                                                                                                                                           
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/multiverse Sources                                                                                                                                         
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/main amd64 Packages                                                                                                                                        
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/restricted amd64 Packages                                                                                                                                  
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/universe amd64 Packages                                                                                                                                    
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/multiverse amd64 Packages                                                                                                                                  
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/main i386 Packages                                                                                                                                         
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/restricted i386 Packages                                                                                                                                   
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/universe i386 Packages                                                                                                                                     
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/multiverse i386 Packages                                                                                                                                   
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/main TranslationIndex                                                                                                                                      
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/multiverse TranslationIndex                                                                                                                                
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/restricted TranslationIndex                                                                                                                                
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/universe TranslationIndex                                                                                                                                  
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/main Sources                                                                                                                                             
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/restricted Sources                                                                                                                                       
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/universe Sources                                                                                                                                         
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/multiverse Sources                                                                                                                                       
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/main amd64 Packages                                                                                                                                      
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/restricted amd64 Packages                                                                                                                                
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/universe amd64 Packages                                                                                                                                  
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/multiverse amd64 Packages                                                                                                                                
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/main i386 Packages                                                                                                                                       
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/restricted i386 Packages                                                                                                                                 
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/universe i386 Packages                                                                                                                                   
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/multiverse i386 Packages                                                                                                                                 
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/main TranslationIndex                                                                                                                                    
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/multiverse TranslationIndex                                                                                                                              
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/restricted TranslationIndex                                                                                                                              
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/universe TranslationIndex                                                                                                                                
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/main Sources                                                                                                                                              
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/restricted Sources                                                                                                                                        
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/universe Sources                                                                                                                                          
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/multiverse Sources                                                                                                                                        
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/main amd64 Packages                                                                                                                                       
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/restricted amd64 Packages                                                                                                                                 
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/universe amd64 Packages                                                                                                                                   
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/multiverse amd64 Packages                                                                                                                                 
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/main i386 Packages                                                                                                                                        
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/restricted i386 Packages                                                                                                                                  
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/universe i386 Packages                                                                                                                                    
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/multiverse i386 Packages                                                                                                                                  
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/main TranslationIndex                                                                                                                                     
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/multiverse TranslationIndex                                                                                                                               
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/restricted TranslationIndex                                                                                                                               
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/universe TranslationIndex                                                                                                                                 
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise/main Translation-ja                                                                                                                                                
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise/main Translation-en                                                                                                                                                
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise/multiverse Translation-ja                                                                                                                                          
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise/multiverse Translation-en                                                                                                                                          
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise/restricted Translation-ja                                                                                                                                          
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise/restricted Translation-en                                                                                                                                          
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise/universe Translation-ja                                                                                                                                            
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise/universe Translation-en                                                                                                                                            
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/main Translation-en                                                                                                                                        
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/multiverse Translation-en                                                                                                                                  
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/restricted Translation-en                                                                                                                                  
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-updates/universe Translation-en                                                                                                                                    
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/main Translation-en                                                                                                                                      
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/multiverse Translation-en                                                                                                                                
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/restricted Translation-en                                                                                                                                
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-backports/universe Translation-en                                                                                                                                  
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/main Translation-en                                                                                                                                       
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/multiverse Translation-en                                                                                                                                 
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/restricted Translation-en                                                                                                                                 
&#12498;&#12483;&#12488; http://archive.ubuntu.com precise-security/universe Translation-en                                                                                                                                   

```

---

### Post by jbicha on 2012-01-18
It's called multiarch. If you have installed the amd64 version, your computer will also check the 32-bit repositories.

[https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes#A32-bit_compatibility_on_amd64_systems](https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes#A32-bit_compatibility_on_amd64_systems)

---

### Post by grahammechanical on 2012-01-18
The purpose is to make the running of 32bit applications on 64bit Ubuntu more efficient and easier for the user. See this link:

[https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes]("https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes")

under the heading: Ubuntu Common Infrastructure.

regards.

---

### Post by NCLI on 2012-01-19
Ah.... I guess my update problems stem from a different source then, thanks.

---

