---
title: "Failed upgrade from Lubuntu 13.04 to 13.10"
date: 2013-04-30
forum: Ubuntu Development Version
---

### Post by epikvision on 2013-04-30
Hello,

Today, I have a small, old laptop that I plan to use for testing lubuntu.  It's on 13.04 and runs really well, but I wanted to install the daily build straight from upgrading, not another fresh install. 

I tried ```
$ update-manager -d 
```, but it failed.  

I also tried the commands.

```
 
john@jkimtux:~$ sudo sed -i 's/raring/saucy/g' /etc/apt/sources.list
john@jkimtux:~$ sudo apt-get update && sudo apt-get dist-upgrade
Get:1 http://linux.dropbox.com precise Release.gpg [489 B]
Get:2 http://linux.dropbox.com precise Release [2,603 B]                       
Get:3 http://linux.dropbox.com precise/main i386 Packages [1,148 B]            
Get:4 http://us.archive.ubuntu.com saucy Release.gpg [933 B]                   
Get:5 http://security.ubuntu.com saucy-security Release.gpg [933 B]            
Get:6 http://us.archive.ubuntu.com saucy-updates Release.gpg [933 B]           
Ign http://extras.ubuntu.com saucy Release.gpg                                 
Get:7 http://us.archive.ubuntu.com saucy-backports Release.gpg [933 B]         
Get:8 http://security.ubuntu.com saucy-security Release [40.8 kB]              
Get:9 http://archive.canonical.com saucy Release.gpg [933 B]                   
Ign http://extras.ubuntu.com saucy Release                                     
Get:10 http://us.archive.ubuntu.com saucy-proposed Release.gpg [933 B]         
Ign http://linux.dropbox.com precise/main Translation-en_US                    
Ign http://linux.dropbox.com precise/main Translation-en                       
Get:11 http://us.archive.ubuntu.com saucy Release [40.8 kB]                    
Get:12 http://archive.canonical.com saucy Release [5,916 B]                    
Get:13 http://security.ubuntu.com saucy-security/main Sources [14 B]           
Get:14 http://us.archive.ubuntu.com saucy-updates Release [40.8 kB]            
Get:15 http://archive.canonical.com saucy/partner i386 Packages [1,137 B]      
Get:16 http://security.ubuntu.com saucy-security/restricted Sources [14 B]     
Get:17 http://security.ubuntu.com saucy-security/universe Sources [14 B]       
Get:18 http://us.archive.ubuntu.com saucy-backports Release [40.8 kB]          
Get:19 http://security.ubuntu.com saucy-security/multiverse Sources [14 B]     
Get:20 http://us.archive.ubuntu.com saucy-proposed Release [40.8 kB]           
Get:21 http://security.ubuntu.com saucy-security/main i386 Packages [14 B]     
Get:22 http://us.archive.ubuntu.com saucy/main Sources [966 kB]                
Get:23 http://security.ubuntu.com saucy-security/restricted i386 Packages [14 B]
Get:24 http://security.ubuntu.com saucy-security/universe i386 Packages [14 B] 
Get:25 http://security.ubuntu.com saucy-security/multiverse i386 Packages [14 B]
Get:26 http://security.ubuntu.com saucy-security/main Translation-en [14 B]    
Ign http://archive.canonical.com saucy/partner Translation-en_US               
Get:27 http://security.ubuntu.com saucy-security/multiverse Translation-en [14 B]
Ign http://archive.canonical.com saucy/partner Translation-en                  
Get:28 http://security.ubuntu.com saucy-security/restricted Translation-en [14 B]
Get:29 http://security.ubuntu.com saucy-security/universe Translation-en [14 B]
Err http://extras.ubuntu.com saucy/main Sources                                
  404  Not Found [IP: 91.189.88.33 80]
Err http://extras.ubuntu.com saucy/main i386 Packages                         
  404  Not Found [IP: 91.189.88.33 80]
Get:30 http://us.archive.ubuntu.com saucy/restricted Sources [5,987 B] 
Ign http://extras.ubuntu.com saucy/main Translation-en_US                      
Get:31 http://us.archive.ubuntu.com saucy/universe Sources [5,962 kB]          
Ign http://extras.ubuntu.com saucy/main Translation-en                         
Ign http://security.ubuntu.com saucy-security/main Translation-en_US           
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com saucy-security/universe Translation-en_US       
Get:32 http://us.archive.ubuntu.com saucy/multiverse Sources [173 kB]          
Get:33 http://us.archive.ubuntu.com saucy/main i386 Packages [1,186 kB]        
Get:34 http://us.archive.ubuntu.com saucy/restricted i386 Packages [9,632 B]   
Get:35 http://us.archive.ubuntu.com saucy/universe i386 Packages [5,494 kB]    
Get:36 http://us.archive.ubuntu.com saucy/multiverse i386 Packages [133 kB]    
Get:37 http://us.archive.ubuntu.com saucy/main Translation-en [684 kB]         
Get:38 http://us.archive.ubuntu.com saucy/multiverse Translation-en [99.7 kB]  
Get:39 http://us.archive.ubuntu.com saucy/restricted Translation-en [2,767 B]  
Get:40 http://us.archive.ubuntu.com saucy/universe Translation-en [3,797 kB]   
Get:41 http://us.archive.ubuntu.com saucy-updates/main Sources [14 B]          
Get:42 http://us.archive.ubuntu.com saucy-updates/restricted Sources [14 B]    
Get:43 http://us.archive.ubuntu.com saucy-updates/universe Sources [14 B]      
Get:44 http://us.archive.ubuntu.com saucy-updates/multiverse Sources [14 B]    
Get:45 http://us.archive.ubuntu.com saucy-updates/main i386 Packages [14 B]    
Get:46 http://us.archive.ubuntu.com saucy-updates/restricted i386 Packages [14 B]
Get:47 http://us.archive.ubuntu.com saucy-updates/universe i386 Packages [14 B]
Get:48 http://us.archive.ubuntu.com saucy-updates/multiverse i386 Packages [14 B]
Get:49 http://us.archive.ubuntu.com saucy-updates/main Translation-en [14 B]   
Get:50 http://us.archive.ubuntu.com saucy-updates/multiverse Translation-en [14 B]
Get:51 http://us.archive.ubuntu.com saucy-updates/restricted Translation-en [14 B]
Get:52 http://us.archive.ubuntu.com saucy-updates/universe Translation-en [14 B]
Get:53 http://us.archive.ubuntu.com saucy-backports/main Sources [14 B]        
Get:54 http://us.archive.ubuntu.com saucy-backports/restricted Sources [14 B]  
Get:55 http://us.archive.ubuntu.com saucy-backports/universe Sources [14 B]    
Get:56 http://us.archive.ubuntu.com saucy-backports/multiverse Sources [14 B]  
Get:57 http://us.archive.ubuntu.com saucy-backports/main i386 Packages [14 B]  
Get:58 http://us.archive.ubuntu.com saucy-backports/restricted i386 Packages [14 B]
Get:59 http://us.archive.ubuntu.com saucy-backports/universe i386 Packages [14 B]
Get:60 http://us.archive.ubuntu.com saucy-backports/multiverse i386 Packages [14 B]
Get:61 http://us.archive.ubuntu.com saucy-backports/main Translation-en [14 B] 
Get:62 http://us.archive.ubuntu.com saucy-backports/multiverse Translation-en [14 B]
Get:63 http://us.archive.ubuntu.com saucy-backports/restricted Translation-en [14 B]
Get:64 http://us.archive.ubuntu.com saucy-backports/universe Translation-en [14 B]
Get:65 http://us.archive.ubuntu.com saucy-proposed/main i386 Packages [3,175 B]
Get:66 http://us.archive.ubuntu.com saucy-proposed/multiverse i386 Packages [1,034 B]
Get:67 http://us.archive.ubuntu.com saucy-proposed/universe i386 Packages [26.5 kB]
Get:68 http://us.archive.ubuntu.com saucy-proposed/restricted i386 Packages [14 B]
Get:69 http://us.archive.ubuntu.com saucy-proposed/main Translation-en [3,046 B]
Get:70 http://us.archive.ubuntu.com saucy-proposed/multiverse Translation-en [634 B]
Get:71 http://us.archive.ubuntu.com saucy-proposed/restricted Translation-en [14 B]
Get:72 http://us.archive.ubuntu.com saucy-proposed/universe Translation-en [18.5 kB]
Ign http://us.archive.ubuntu.com saucy/main Translation-en_US                  
Ign http://us.archive.ubuntu.com saucy/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com saucy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com saucy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com saucy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com saucy-updates/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com saucy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com saucy-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com saucy-backports/main Translation-en_US        
Ign http://us.archive.ubuntu.com saucy-backports/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com saucy-backports/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com saucy-backports/universe Translation-en_US    
Ign http://us.archive.ubuntu.com saucy-proposed/main Translation-en_US         
Ign http://us.archive.ubuntu.com saucy-proposed/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com saucy-proposed/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com saucy-proposed/universe Translation-en_US     
Fetched 18.8 MB in 45s (409 kB/s)                                              
**W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/saucy/main/source/Sources  404  Not Found [IP: 91.189.88.33 80]**

**W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/saucy/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.33 80]**

**E: Some index files failed to download. They have been ignored, or old ones used instead.**

```

I bolded where I thought was most important.  Surely, the software upgrade should've proceeded normally, but instead, the error is that the Sources are 404'ed.  

Are there any workarounds so I may install at ease?  Thanks.

---

### Post by Elfy on 2013-04-30
Edit sources list and comment out the extras repos for the time being.

---

### Post by grahammechanical on 2013-04-30
As has been mentioned in a couple of other threads in Ubuntu+1 those extras repositories do not yet exist. This is the situation at this stage of development for every new development cycle. In fact 13.10 does not yet exist. All we have done is change the URLs of the repositories and now we wait for the developers to develop and the maintainers to merge the new code into the repositories. Sometimes, it is just as good or perhaps better to wait until the first 13.10 daily ISO image is put on qa.ubuntu. Then we can download and put in a fresh install.

You will notice that this error is preventing Software Sources/Software & Updates/Synaptic Settings from working but Software Updater will run an update as will Synaptic and the Terminal.

Regards.

---

