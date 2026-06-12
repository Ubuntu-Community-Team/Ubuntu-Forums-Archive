---
title: "unable to update in ubuntu 14.04 virtual box platform"
date: 2015-06-19
forum: Virtualisation
---

### Post by msr2 on 2015-06-19
internet is working fine but unable to update&install  software


```
msr@msr-VirtualBox:~$ sudo apt-get update
[sudo] password for msr: 
0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.a0% [Connecting to archive.ubuntu.com (91.189.92.201)] [Connecting to in.aErr [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease 
Ign mirror://mirrors.ubuntu.com precise InRelease                              
Ign mirror://mirrors.ubuntu.com precise-updates InRelease                      
Ign mirror://mirrors.ubuntu.com precise-backports InRelease                    
Ign mirror://mirrors.ubuntu.com precise-security InRelease                     
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
  Cannot initiate the connection to extras.ubuntu.com:80 (2001:67c:1360:8c01::23). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8c01::23 80]
Ign mirror://mirrors.ubuntu.com precise Release.gpg                            
Ign mirror://mirrors.ubuntu.com precise-updates Release.gpg                    
Ign mirror://mirrors.ubuntu.com precise-backports Release.gpg                  
Ign mirror://mirrors.ubuntu.com precise-security Release.gpg                   
Ign mirror://mirrors.ubuntu.com precise Release                                
Ign mirror://mirrors.ubuntu.com precise-updates Release                        
Ign mirror://mirrors.ubuntu.com precise-backports Release                      
Ign mirror://mirrors.ubuntu.com precise-security Release                       
Err mirror://mirrors.ubuntu.com precise/main amd64 Packages                    
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise/restricted amd64 Packages              
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise/universe amd64 Packages                
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise/multiverse amd64 Packages              
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise/main i386 Packages                     
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise/restricted i386 Packages               
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise/universe i386 Packages                 
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise/multiverse i386 Packages               
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Ign mirror://mirrors.ubuntu.com precise/main Translation-en_IN                 
Ign mirror://mirrors.ubuntu.com precise/main Translation-en                    
Ign mirror://mirrors.ubuntu.com precise/multiverse Translation-en_IN           
Ign mirror://mirrors.ubuntu.com precise/multiverse Translation-en              
Ign mirror://mirrors.ubuntu.com precise/restricted Translation-en_IN           
Ign mirror://mirrors.ubuntu.com precise/restricted Translation-en              
Ign mirror://mirrors.ubuntu.com precise/universe Translation-en_IN             
Ign mirror://mirrors.ubuntu.com precise/universe Translation-en                
Err mirror://mirrors.ubuntu.com precise-updates/main amd64 Packages            
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-updates/restricted amd64 Packages      
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-updates/universe amd64 Packages        
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-updates/multiverse amd64 Packages      
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-updates/main i386 Packages             
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-updates/restricted i386 Packages       
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-updates/universe i386 Packages         
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-updates/multiverse i386 Packages       
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Ign mirror://mirrors.ubuntu.com precise-updates/main Translation-en_IN         
Ign mirror://mirrors.ubuntu.com precise-updates/main Translation-en            
Ign mirror://mirrors.ubuntu.com precise-updates/multiverse Translation-en_IN   
Ign mirror://mirrors.ubuntu.com precise-updates/multiverse Translation-en      
Ign mirror://mirrors.ubuntu.com precise-updates/restricted Translation-en_IN   
Ign mirror://mirrors.ubuntu.com precise-updates/restricted Translation-en      
Ign mirror://mirrors.ubuntu.com precise-updates/universe Translation-en_IN     
Ign mirror://mirrors.ubuntu.com precise-updates/universe Translation-en        
Err mirror://mirrors.ubuntu.com precise-backports/main amd64 Packages          
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-backports/restricted amd64 Packages    
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-backports/universe amd64 Packages      
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-backports/multiverse amd64 Packages    
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-backports/main i386 Packages           
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-backports/restricted i386 Packages     
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-backports/universe i386 Packages       
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-backports/multiverse i386 Packages     
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Ign mirror://mirrors.ubuntu.com precise-backports/main Translation-en_IN       
Ign mirror://mirrors.ubuntu.com precise-backports/main Translation-en          
Ign mirror://mirrors.ubuntu.com precise-backports/multiverse Translation-en_IN 
Ign mirror://mirrors.ubuntu.com precise-backports/multiverse Translation-en    
Ign mirror://mirrors.ubuntu.com precise-backports/restricted Translation-en_IN 
Ign mirror://mirrors.ubuntu.com precise-backports/restricted Translation-en    
Ign mirror://mirrors.ubuntu.com precise-backports/universe Translation-en_IN   
Ign mirror://mirrors.ubuntu.com precise-backports/universe Translation-en      
Err mirror://mirrors.ubuntu.com precise-security/main amd64 Packages           
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-security/restricted amd64 Packages     
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-security/universe amd64 Packages       
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-security/multiverse amd64 Packages     
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-security/main i386 Packages            
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-security/restricted i386 Packages      
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-security/universe i386 Packages        
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-security/multiverse i386 Packages      
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Ign mirror://mirrors.ubuntu.com precise-security/main Translation-en_IN        
Ign mirror://mirrors.ubuntu.com precise-security/main Translation-en           
Ign mirror://mirrors.ubuntu.com precise-security/multiverse Translation-en_IN  
Ign mirror://mirrors.ubuntu.com precise-security/multiverse Translation-en     
Ign mirror://mirrors.ubuntu.com precise-security/restricted Translation-en_IN  
Ign mirror://mirrors.ubuntu.com precise-security/restricted Translation-en     
Ign mirror://mirrors.ubuntu.com precise-security/universe Translation-en_IN    
Ign mirror://mirrors.ubuntu.com precise-security/universe Translation-en       
Err [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease 
Err [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
  Cannot initiate the connection to archive.canonical.com:80 (2001:67c:1360:8c01::1b). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8c01::1b 80]
32% [Connecting to archive.ubuntu.com (91.189.91.24)] [Connecting to in.archive
```

---

### Post by howefield on 2015-06-19
Thread moved to the "*Virtualisation*" forum.

---

### Post by slickymaster on 2015-06-19
Hi msr2, welcome to the forums.

I've edit your post, adding code tags to it, because output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

---

