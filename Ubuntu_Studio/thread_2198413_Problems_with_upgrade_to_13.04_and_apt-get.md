---
title: "Problems with upgrade to 13.04 and apt-get"
date: 2014-01-08
forum: Ubuntu Studio
---

### Post by dmtparker on 2014-01-08
I just upgraded to Ubuntu Studio 13.10. When trying to get an update, apt-get crashes. When I run apt-get update manually I get the following:

```
mark@mark-Inspiron-M5110:~$ sudo apt-get update
[sudo] password for mark: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release     
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy InRelease                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports InRelease               
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security InRelease
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy Release 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release.gpg                      
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release.gpg [933 B]    
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy/partner amd64 Packages                  
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports Release.gpg [933 B]  
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy/partner i386 Packages                   
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security Release.gpg [933 B]    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release                                    
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release [49.6 kB]                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en                         
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en_US               
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en                  
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports Release [49.6 kB]              
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security Release [49.6 kB]               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main amd64 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe amd64 Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main i386 Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe i386 Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Translation-en                    
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Sources [61.4 kB]           
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Sources [14 B]        
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Sources [41.8 kB]       
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Sources [1,353 B]    
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main amd64 Packages [181 kB]    
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted amd64 Packages [14 B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe amd64 Packages [123 kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse amd64 Packages [1,566 B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main i386 Packages [180 kB]     
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted i386 Packages [14 B] 
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe i386 Packages [124 kB] 
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse i386 Packages [1,776 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Translation-en            
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main Sources [14 B]           
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted Sources [14 B]     
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe Sources [2,107 B]    
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse Sources [834 B]    
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main amd64 Packages [14 B]    
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted amd64 Packages [14 B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe amd64 Packages [2,321 B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse amd64 Packages [14 B]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main i386 Packages [14 B]     
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted i386 Packages [14 B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe i386 Packages [2,329 B]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse i386 Packages [709 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe Translation-en          
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Sources [21.6 kB]         
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Sources [14 B]      
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Sources [6,669 B]     
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Sources [701 B]     
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main amd64 Packages [62.9 kB]  
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted amd64 Packages [14 B]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe amd64 Packages [24.1 kB]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse amd64 Packages [1,149 B]
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main i386 Packages [62.6 kB]   
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted i386 Packages [14 B]
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe i386 Packages [24.4 kB]
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse i386 Packages [1,388 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Translation-en           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Translation-en_US
Fetched 1,081 kB in 1min 12s (14.8 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy-security_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
mark@mark-Inspiron-M5110:~$
```


Sorry for the long post, but I figured it might help

---

### Post by dmtparker on 2014-01-08
This is for anyone with similar problems.
I am not an IT guy and have no formal training in Linux, but I've been using it since before Fedora was born, so I have acquired a bit of knowledge "the hard way." In this case, it appeared that the problem was with the file: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy-security_main_i18n_Translation-en, so let's open it and see what it says! I use gedit and if you do NOT do it with sudo, the file will open as read-only and you cannot do much harm. So I did. The file was complete garbage with no recognizable characters. Now this MIGHT mean it was a machine language file of some sort, but in my experience, in linux, usually files of this type are ASKI. So let's try just deleting it. Not being stupid (been there done that) I first copy the file to *.old, THEN delete it (all must be done as root : sudo cp... then sudo rm...). Now run sudo apt-get update again and all is well. Problem solved, or at least I think it is. The automated update is working and so far no crashes. And, yes, the file (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy-security_main_i18n_Translation-en) is a normal ASKI file again. 
No idea why this happened. If it is a bug or just my luck, but if you run into the same thing, this quick trick works.

---

### Post by mörgæs on 2014-01-08
Good, please mark the thread 'solved'.

By the way, it's ASCII not ASKI.

---

