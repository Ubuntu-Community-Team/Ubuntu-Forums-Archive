---
title: "Probably issue with update?"
date: 2012-10-30
forum: Server Platforms
---

### Post by RETtrib on 2012-10-30
Hey guys

I'm trying to update my ubuntu server and I'm not sure what's going on since this is what ```
apt-get update
``` reports:

```
Ign http://gr.archive.ubuntu.com precise InRelease
Ign http://gr.archive.ubuntu.com precise-updates InRelease               
Ign http://gr.archive.ubuntu.com precise-backports InRelease             
Hit http://gr.archive.ubuntu.com precise Release.gpg                      
Get:1 http://gr.archive.ubuntu.com precise-updates Release.gpg [198 B]    
Ign http://security.ubuntu.com precise-security InRelease
Get:2 http://gr.archive.ubuntu.com precise-backports Release.gpg [198 B]
Hit http://gr.archive.ubuntu.com precise Release                               
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:4 http://gr.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://www.plexapp.com lucid InRelease                                   
Get:5 http://security.ubuntu.com precise-security Release [49.6 kB]            
Get:6 http://gr.archive.ubuntu.com precise-backports Release [49.6 kB]         
Hit http://www.plexapp.com lucid/main amd64 Packages                           
Hit http://gr.archive.ubuntu.com precise/main Sources                          
Hit http://gr.archive.ubuntu.com precise/restricted Sources                    
Hit http://gr.archive.ubuntu.com precise/universe Sources                      
Hit http://gr.archive.ubuntu.com precise/multiverse Sources                    
Hit http://gr.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://gr.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://gr.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://gr.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://gr.archive.ubuntu.com precise/main i386 Packages                    
Hit http://www.plexapp.com lucid/main i386 Packages                            
Ign http://www.plexapp.com lucid/main TranslationIndex                         
Hit http://gr.archive.ubuntu.com precise/restricted i386 Packages
Hit http://gr.archive.ubuntu.com precise/universe i386 Packages
Hit http://gr.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://gr.archive.ubuntu.com precise/main TranslationIndex
Hit http://gr.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://gr.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://gr.archive.ubuntu.com precise/universe TranslationIndex
Get:7 http://gr.archive.ubuntu.com precise-updates/main Sources [182 kB]
Get:8 http://security.ubuntu.com precise-security/main Sources [51.1 kB]
Get:9 http://gr.archive.ubuntu.com precise-updates/restricted Sources [4,395 B]
Get:10 http://gr.archive.ubuntu.com precise-updates/universe Sources [60.7 kB]
Get:11 http://gr.archive.ubuntu.com precise-updates/multiverse Sources [4,745 B]
Get:12 http://gr.archive.ubuntu.com precise-updates/main amd64 Packages [417 kB]
Get:13 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]
Get:14 http://security.ubuntu.com precise-security/universe Sources [14.5 kB]  
Get:15 http://security.ubuntu.com precise-security/multiverse Sources [1,379 B]
Get:16 http://security.ubuntu.com precise-security/main amd64 Packages [180 kB]
Get:17 http://gr.archive.ubuntu.com precise-updates/restricted amd64 Packages [8,215 B]
Get:18 http://gr.archive.ubuntu.com precise-updates/universe amd64 Packages [151 kB]
Get:19 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:20 http://security.ubuntu.com precise-security/universe amd64 Packages [48.6 kB]
Get:21 http://gr.archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,948 B]
Get:22 http://gr.archive.ubuntu.com precise-updates/main i386 Packages [425 kB]
Get:23 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,188 B]
Get:24 http://security.ubuntu.com precise-security/main i386 Packages [186 kB] 
Ign http://www.plexapp.com lucid/main Translation-en_US                        
Ign http://www.plexapp.com lucid/main Translation-en                           
Get:25 http://gr.archive.ubuntu.com precise-updates/restricted i386 Packages [8,218 B]
Get:26 http://gr.archive.ubuntu.com precise-updates/universe i386 Packages [151 kB]
Get:27 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:28 http://security.ubuntu.com precise-security/universe i386 Packages [48.7 kB]
Get:29 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,357 B]
Get:30 http://gr.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,930 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Get:31 http://gr.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:32 http://gr.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:33 http://gr.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:34 http://gr.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:35 http://gr.archive.ubuntu.com precise-backports/main Sources [2,422 B]   
Get:36 http://gr.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:37 http://gr.archive.ubuntu.com precise-backports/universe Sources [17.2 kB]
Get:38 http://gr.archive.ubuntu.com precise-backports/multiverse Sources [2,669 B]
Get:39 http://gr.archive.ubuntu.com precise-backports/main amd64 Packages [1,945 B]
Get:40 http://gr.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:41 http://gr.archive.ubuntu.com precise-backports/universe amd64 Packages [14.9 kB]
Get:42 http://gr.archive.ubuntu.com precise-backports/multiverse amd64 Packages [2,489 B]
Get:43 http://gr.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]
Get:44 http://gr.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Get:45 http://gr.archive.ubuntu.com precise-backports/universe i386 Packages [14.9 kB]
Get:46 http://gr.archive.ubuntu.com precise-backports/multiverse i386 Packages [2,504 B]
Get:47 http://gr.archive.ubuntu.com precise-backports/main TranslationIndex [72 B]
Get:48 http://gr.archive.ubuntu.com precise-backports/multiverse TranslationIndex [72 B]
Get:49 http://gr.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:50 http://gr.archive.ubuntu.com precise-backports/universe TranslationIndex [73 B]
Hit http://gr.archive.ubuntu.com precise/main Translation-en   
Hit http://gr.archive.ubuntu.com precise/multiverse Translation-en
Hit http://gr.archive.ubuntu.com precise/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://gr.archive.ubuntu.com precise/universe Translation-en
Hit http://gr.archive.ubuntu.com precise-updates/main Translation-en
Hit http://gr.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://gr.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://gr.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://gr.archive.ubuntu.com precise-backports/main Translation-en
Hit http://gr.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://gr.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://gr.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 2,199 kB in 5s (416 kB/s)
Reading package lists... Done
kingc@Server:~$ sudo apt-get update
Ign http://gr.archive.ubuntu.com precise InRelease
Ign http://gr.archive.ubuntu.com precise-updates InRelease               
Ign http://gr.archive.ubuntu.com precise-backports InRelease              
Hit http://gr.archive.ubuntu.com precise Release.gpg                      
Hit http://gr.archive.ubuntu.com precise-updates Release.gpg              
Ign http://security.ubuntu.com precise-security InRelease                 
Hit http://gr.archive.ubuntu.com precise-backports Release.gpg            
Hit http://gr.archive.ubuntu.com precise Release                          
Hit http://gr.archive.ubuntu.com precise-updates Release                       
Hit http://gr.archive.ubuntu.com precise-backports Release           
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://gr.archive.ubuntu.com precise/main Sources                
Hit http://gr.archive.ubuntu.com precise/restricted Sources
Hit http://gr.archive.ubuntu.com precise/universe Sources
Hit http://gr.archive.ubuntu.com precise/multiverse Sources          
Hit http://gr.archive.ubuntu.com precise/main amd64 Packages         
Hit http://gr.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://gr.archive.ubuntu.com precise/universe amd64 Packages     
Hit http://gr.archive.ubuntu.com precise/multiverse amd64 Packages   
Hit http://gr.archive.ubuntu.com precise/main i386 Packages
Hit http://gr.archive.ubuntu.com precise/restricted i386 Packages
Hit http://security.ubuntu.com precise-security Release              
Hit http://www.plexapp.com lucid InRelease                            
Hit http://gr.archive.ubuntu.com precise/universe i386 Packages         
Hit http://gr.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://gr.archive.ubuntu.com precise/main TranslationIndex
Hit http://gr.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://gr.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://gr.archive.ubuntu.com precise/universe TranslationIndex
Hit http://gr.archive.ubuntu.com precise-updates/main Sources
Hit http://gr.archive.ubuntu.com precise-updates/restricted Sources
Hit http://gr.archive.ubuntu.com precise-updates/universe Sources    
Hit http://gr.archive.ubuntu.com precise-updates/multiverse Sources  
Hit http://gr.archive.ubuntu.com precise-updates/main amd64 Packages 
Hit http://gr.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://gr.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://gr.archive.ubuntu.com precise-updates/multiverse amd64 Packages
Hit http://gr.archive.ubuntu.com precise-updates/main i386 Packages  
Hit http://gr.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://gr.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://security.ubuntu.com precise-security/main Sources         
Hit http://gr.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://gr.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://gr.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://gr.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://gr.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://gr.archive.ubuntu.com precise-backports/main Sources
Hit http://gr.archive.ubuntu.com precise-backports/restricted Sources
Hit http://gr.archive.ubuntu.com precise-backports/universe Sources
Hit http://gr.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://gr.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://gr.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/restricted Sources   
Hit http://security.ubuntu.com precise-security/universe Sources     
Hit http://security.ubuntu.com precise-security/multiverse Sources   
Hit http://security.ubuntu.com precise-security/main amd64 Packages  
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://gr.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://gr.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://www.plexapp.com lucid/main amd64 Packages                 
Hit http://gr.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://gr.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://gr.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://gr.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://gr.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://gr.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://gr.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://gr.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://gr.archive.ubuntu.com precise/main Translation-en         
Hit http://gr.archive.ubuntu.com precise/multiverse Translation-en   
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://security.ubuntu.com precise-security/main i386 Packages   
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://gr.archive.ubuntu.com precise/restricted Translation-en   
Hit http://gr.archive.ubuntu.com precise/universe Translation-en     
Hit http://gr.archive.ubuntu.com precise-updates/main Translation-en
Hit http://gr.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://gr.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://gr.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://gr.archive.ubuntu.com precise-backports/main Translation-en
Hit http://gr.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://gr.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://gr.archive.ubuntu.com precise-backports/universe Translation-en
Hit http://www.plexapp.com lucid/main i386 Packages
Ign http://www.plexapp.com lucid/main TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Ign http://www.plexapp.com lucid/main Translation-en_US
Ign http://www.plexapp.com lucid/main Translation-en
Reading package lists... Done
```

---

### Post by jrog on 2012-10-30
I hope I'm not just being dense... What is the problem?

---

### Post by Kaobear on 2012-10-30
> **RETtrib said:**
> Hey guys

I'm trying to update my ubuntu server and I'm not sure what's going on since this is what ```
apt-get update
``` reports:

```
Ign http://gr.archive.ubuntu.com precise InRelease
Ign http://gr.archive.ubuntu.com precise-updates InRelease               
Ign http://gr.archive.ubuntu.com precise-backports InRelease             
Hit http://gr.archive.ubuntu.com precise Release.gpg                      
Get:1 http://gr.archive.ubuntu.com precise-updates Release.gpg [198 B]    
Ign http://security.ubuntu.com precise-security InRelease
Get:2 http://gr.archive.ubuntu.com precise-backports Release.gpg [198 B]
Hit http://gr.archive.ubuntu.com precise Release                               
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:4 http://gr.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://www.plexapp.com lucid InRelease                                   
Get:5 http://security.ubuntu.com precise-security Release [49.6 kB]            
Get:6 http://gr.archive.ubuntu.com precise-backports Release [49.6 kB]         
Hit http://www.plexapp.com lucid/main amd64 Packages                           
Hit http://gr.archive.ubuntu.com precise/main Sources                          
Hit http://gr.archive.ubuntu.com precise/restricted Sources                    
Hit http://gr.archive.ubuntu.com precise/universe Sources                      
Hit http://gr.archive.ubuntu.com precise/multiverse Sources                    
Hit http://gr.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://gr.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://gr.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://gr.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://gr.archive.ubuntu.com precise/main i386 Packages                    
Hit http://www.plexapp.com lucid/main i386 Packages                            
Ign http://www.plexapp.com lucid/main TranslationIndex                         
Hit http://gr.archive.ubuntu.com precise/restricted i386 Packages
Hit http://gr.archive.ubuntu.com precise/universe i386 Packages
Hit http://gr.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://gr.archive.ubuntu.com precise/main TranslationIndex
Hit http://gr.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://gr.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://gr.archive.ubuntu.com precise/universe TranslationIndex
Get:7 http://gr.archive.ubuntu.com precise-updates/main Sources [182 kB]
Get:8 http://security.ubuntu.com precise-security/main Sources [51.1 kB]
Get:9 http://gr.archive.ubuntu.com precise-updates/restricted Sources [4,395 B]
Get:10 http://gr.archive.ubuntu.com precise-updates/universe Sources [60.7 kB]
Get:11 http://gr.archive.ubuntu.com precise-updates/multiverse Sources [4,745 B]
Get:12 http://gr.archive.ubuntu.com precise-updates/main amd64 Packages [417 kB]
Get:13 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]
Get:14 http://security.ubuntu.com precise-security/universe Sources [14.5 kB]  
Get:15 http://security.ubuntu.com precise-security/multiverse Sources [1,379 B]
Get:16 http://security.ubuntu.com precise-security/main amd64 Packages [180 kB]
Get:17 http://gr.archive.ubuntu.com precise-updates/restricted amd64 Packages [8,215 B]
Get:18 http://gr.archive.ubuntu.com precise-updates/universe amd64 Packages [151 kB]
Get:19 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:20 http://security.ubuntu.com precise-security/universe amd64 Packages [48.6 kB]
Get:21 http://gr.archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,948 B]
Get:22 http://gr.archive.ubuntu.com precise-updates/main i386 Packages [425 kB]
Get:23 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,188 B]
Get:24 http://security.ubuntu.com precise-security/main i386 Packages [186 kB] 
Ign http://www.plexapp.com lucid/main Translation-en_US                        
Ign http://www.plexapp.com lucid/main Translation-en                           
Get:25 http://gr.archive.ubuntu.com precise-updates/restricted i386 Packages [8,218 B]
Get:26 http://gr.archive.ubuntu.com precise-updates/universe i386 Packages [151 kB]
Get:27 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:28 http://security.ubuntu.com precise-security/universe i386 Packages [48.7 kB]
Get:29 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,357 B]
Get:30 http://gr.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,930 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Get:31 http://gr.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:32 http://gr.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:33 http://gr.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:34 http://gr.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:35 http://gr.archive.ubuntu.com precise-backports/main Sources [2,422 B]   
Get:36 http://gr.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:37 http://gr.archive.ubuntu.com precise-backports/universe Sources [17.2 kB]
Get:38 http://gr.archive.ubuntu.com precise-backports/multiverse Sources [2,669 B]
Get:39 http://gr.archive.ubuntu.com precise-backports/main amd64 Packages [1,945 B]
Get:40 http://gr.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:41 http://gr.archive.ubuntu.com precise-backports/universe amd64 Packages [14.9 kB]
Get:42 http://gr.archive.ubuntu.com precise-backports/multiverse amd64 Packages [2,489 B]
Get:43 http://gr.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]
Get:44 http://gr.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Get:45 http://gr.archive.ubuntu.com precise-backports/universe i386 Packages [14.9 kB]
Get:46 http://gr.archive.ubuntu.com precise-backports/multiverse i386 Packages [2,504 B]
Get:47 http://gr.archive.ubuntu.com precise-backports/main TranslationIndex [72 B]
Get:48 http://gr.archive.ubuntu.com precise-backports/multiverse TranslationIndex [72 B]
Get:49 http://gr.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:50 http://gr.archive.ubuntu.com precise-backports/universe TranslationIndex [73 B]
Hit http://gr.archive.ubuntu.com precise/main Translation-en   
Hit http://gr.archive.ubuntu.com precise/multiverse Translation-en
Hit http://gr.archive.ubuntu.com precise/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://gr.archive.ubuntu.com precise/universe Translation-en
Hit http://gr.archive.ubuntu.com precise-updates/main Translation-en
Hit http://gr.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://gr.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://gr.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://gr.archive.ubuntu.com precise-backports/main Translation-en
Hit http://gr.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://gr.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://gr.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 2,199 kB in 5s (416 kB/s)
Reading package lists... Done
kingc@Server:~$ sudo apt-get update
Ign http://gr.archive.ubuntu.com precise InRelease
Ign http://gr.archive.ubuntu.com precise-updates InRelease               
Ign http://gr.archive.ubuntu.com precise-backports InRelease              
Hit http://gr.archive.ubuntu.com precise Release.gpg                      
Hit http://gr.archive.ubuntu.com precise-updates Release.gpg              
Ign http://security.ubuntu.com precise-security InRelease                 
Hit http://gr.archive.ubuntu.com precise-backports Release.gpg            
Hit http://gr.archive.ubuntu.com precise Release                          
Hit http://gr.archive.ubuntu.com precise-updates Release                       
Hit http://gr.archive.ubuntu.com precise-backports Release           
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://gr.archive.ubuntu.com precise/main Sources                
Hit http://gr.archive.ubuntu.com precise/restricted Sources
Hit http://gr.archive.ubuntu.com precise/universe Sources
Hit http://gr.archive.ubuntu.com precise/multiverse Sources          
Hit http://gr.archive.ubuntu.com precise/main amd64 Packages         
Hit http://gr.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://gr.archive.ubuntu.com precise/universe amd64 Packages     
Hit http://gr.archive.ubuntu.com precise/multiverse amd64 Packages   
Hit http://gr.archive.ubuntu.com precise/main i386 Packages
Hit http://gr.archive.ubuntu.com precise/restricted i386 Packages
Hit http://security.ubuntu.com precise-security Release              
Hit http://www.plexapp.com lucid InRelease                            
Hit http://gr.archive.ubuntu.com precise/universe i386 Packages         
Hit http://gr.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://gr.archive.ubuntu.com precise/main TranslationIndex
Hit http://gr.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://gr.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://gr.archive.ubuntu.com precise/universe TranslationIndex
Hit http://gr.archive.ubuntu.com precise-updates/main Sources
Hit http://gr.archive.ubuntu.com precise-updates/restricted Sources
Hit http://gr.archive.ubuntu.com precise-updates/universe Sources    
Hit http://gr.archive.ubuntu.com precise-updates/multiverse Sources  
Hit http://gr.archive.ubuntu.com precise-updates/main amd64 Packages 
Hit http://gr.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://gr.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://gr.archive.ubuntu.com precise-updates/multiverse amd64 Packages
Hit http://gr.archive.ubuntu.com precise-updates/main i386 Packages  
Hit http://gr.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://gr.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://security.ubuntu.com precise-security/main Sources         
Hit http://gr.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://gr.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://gr.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://gr.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://gr.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://gr.archive.ubuntu.com precise-backports/main Sources
Hit http://gr.archive.ubuntu.com precise-backports/restricted Sources
Hit http://gr.archive.ubuntu.com precise-backports/universe Sources
Hit http://gr.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://gr.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://gr.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/restricted Sources   
Hit http://security.ubuntu.com precise-security/universe Sources     
Hit http://security.ubuntu.com precise-security/multiverse Sources   
Hit http://security.ubuntu.com precise-security/main amd64 Packages  
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://gr.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://gr.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://www.plexapp.com lucid/main amd64 Packages                 
Hit http://gr.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://gr.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://gr.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://gr.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://gr.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://gr.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://gr.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://gr.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://gr.archive.ubuntu.com precise/main Translation-en         
Hit http://gr.archive.ubuntu.com precise/multiverse Translation-en   
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://security.ubuntu.com precise-security/main i386 Packages   
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://gr.archive.ubuntu.com precise/restricted Translation-en   
Hit http://gr.archive.ubuntu.com precise/universe Translation-en     
Hit http://gr.archive.ubuntu.com precise-updates/main Translation-en
Hit http://gr.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://gr.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://gr.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://gr.archive.ubuntu.com precise-backports/main Translation-en
Hit http://gr.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://gr.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://gr.archive.ubuntu.com precise-backports/universe Translation-en
Hit http://www.plexapp.com lucid/main i386 Packages
Ign http://www.plexapp.com lucid/main TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Ign http://www.plexapp.com lucid/main Translation-en_US
Ign http://www.plexapp.com lucid/main Translation-en
Reading package lists... Done
```

```
sudo apt-get upgrade
```

That's what is next.

---

### Post by RETtrib on 2012-10-30
Oh. I for some reason believed that ```
 apt-get upgrade
``` upgraded Ubuntu to the next version, eg from 12 to 13 and that the update was supposed to do all the work.

Thanks guys

---

