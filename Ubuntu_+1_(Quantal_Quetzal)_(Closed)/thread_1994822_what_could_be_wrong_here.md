---
title: "what could be wrong here?"
date: 2012-06-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kuvanito on 2012-06-03
ari@Ari:~$ sudo apt-get update
```
[sudo] password for ari: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports InRelease                   
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release.gpg                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release.gpg                   
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [769 B]                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release.gpg                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease                      
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe i386 Packages                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse TranslationIndex   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources
  404  Not Found
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages
  404  Not Found
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en
Fetched 2,314 B in 1s (1,158 B/s)
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
ari@Ari:~$

is it me or quantal quetzal?
```

---

### Post by cariboo on 2012-06-03
There aren't quantal repositories for extras yet, edit your /etc/apt/sources.list, to point to the precise repositories for now. You can also use software sources in the software centre or synaptic too.

---

### Post by zika on 2012-06-03
> **kuvanito said:**
> ari@Ari:~$ sudo apt-get update
[sudo] password for ari: 
...
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources
  404  Not Found
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages
  404  Not Found
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en
Fetched 2,314 B in 1s (1,158 B/s)
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
ari@Ari:~$

is it me or quantal quetzal?
No Quantal branch yet in extras...
You could disable it or use Precise ... It's Your choice...

---

### Post by xeddog on 2012-06-03
I, for one, know that if I change this to Precise I would most likely never change it back to Quantal unless there was some sort of notification.  How would I know that the Quantal repositories have become available?  

Thanks,

Wayne

---

### Post by zika on 2012-06-03
> **xeddog said:**
> I, for one, know that if I change this to Precise I would most likely never change it back to Quantal unless there was some sort of notification.  How would I know that the Quantal repositories have become available?  

Thanks,

WayneThere is an answer somewhere here to my same question. I think that script/app is {checklp,repostory}...
Here it is:
If I manage to find it I'll post it here... [http://ubuntuforums.org/showthread.php?t=1976156](http://ubuntuforums.org/showthread.php?t=1976156)

---

### Post by jerrylamos on 2012-06-03
> **xeddog said:**
> I, for one, know that if I change this to Precise I would most likely never change it back to Quantal unless there was some sort of notification.  How would I know that the Quantal repositories have become available?  

Thanks,

Wayne
For development "unstable" .iso's I usually run several partitions, example a couple quantal's alternating installs with new daily builds, a precise, perhaps an ocelot, then usually a meerkat and/or lucid.  10 GB for each on the 100 GB hard drives and up, 6 GB each on the 40 GB hard drive in a USB case.

Jerry

---

### Post by kuvanito on 2012-06-03
> **jerrylamos said:**
> For development "unstable" .iso's I usually run several partitions, example a couple quantal's alternating installs with new daily builds, a precise, perhaps an ocelot, then usually a meerkat and/or lucid.  10 GB for each on the 100 GB hard drives and up, 6 GB each on the 40 GB hard drive in a USB case.

Jerry

jerry i do just about the same but i use a kingwing bay Model: KF-1000-BK so i can change hd as if i was changing briefs,still i love to test and try things out b4 they come out to the public and at the same time help with testing for the dev team. :D

---

