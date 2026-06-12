---
title: "index issue"
date: 2011-11-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by raja.genupula on 2011-11-06
Ubuntu Version:12:04 Xubuntu
1.... i have done changing my server to main server and server to india , but both are not given any solution to this issue .
 
2...removed all things in lists at apt & updated  but not worked .

3...i know one more thing is unchecking check boxes at update manager --> settings --> other software tab ...but i dont want to do that because i want that webupd8 ppa to install themes for my gnome-shell(i have installed). 

Help me guys ! i did all what i know 

```
assassin@raju-xubuntu:~$ sudo apt-get update
[sudo] password for assassin: 
Ign http://in.archive.ubuntu.com precise InRelease
Ign http://in.archive.ubuntu.com precise-updates InRelease                     
Ign http://in.archive.ubuntu.com precise-backports InRelease                   
Ign http://deb.opera.com stable InRelease                                      
Ign http://dl.google.com stable InRelease                                      
Ign http://in.archive.ubuntu.com precise-security InRelease                    
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:1 http://in.archive.ubuntu.com precise Release.gpg [198 B]                 
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://deb.opera.com stable Release.gpg                                    
Hit http://in.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://in.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Ign http://extras.ubuntu.com precise Release.gpg                               
Hit http://deb.opera.com stable Release                                        
Hit http://in.archive.ubuntu.com precise-security Release.gpg                  
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Ign http://extras.ubuntu.com precise Release                                   
Get:2 http://in.archive.ubuntu.com precise Release [49.6 kB]                   
Ign http://ppa.launchpad.net precise Release.gpg                               
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:3 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://in.archive.ubuntu.com precise-updates Release                       
Hit http://in.archive.ubuntu.com precise-backports Release                     
Hit http://in.archive.ubuntu.com precise-security Release                      
Get:4 http://in.archive.ubuntu.com precise/main Sources [899 kB]               
Err http://extras.ubuntu.com precise/main Sources                              
  404  Not Found
Get:5 http://dl.google.com stable Release [1,347 B]                            
Err http://extras.ubuntu.com precise/main i386 Packages                        
  404  Not Found
Ign http://deb.opera.com stable/non-free Translation-en_IN                     
Ign http://extras.ubuntu.com precise/main Translation-en_IN                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://deb.opera.com stable/non-free Translation-en                        
Err http://ppa.launchpad.net precise/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages                        
  404  Not Found
Ign http://ppa.launchpad.net oneiric/main Translation-en_IN                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_IN                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                     
Get:6 http://dl.google.com stable/main i386 Packages [1,221 B]               
Ign http://ppa.launchpad.net precise/main Translation-en_IN                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://dl.google.com stable/main Translation-en_IN                         
Ign http://dl.google.com stable/main Translation-en                            
Get:7 http://in.archive.ubuntu.com precise/restricted Sources [5,338 B]        
Get:8 http://in.archive.ubuntu.com precise/universe Sources [4,894 kB]         
Get:9 http://in.archive.ubuntu.com precise/multiverse Sources [158 kB]         
Get:10 http://in.archive.ubuntu.com precise/main i386 Packages [1,255 kB]      
Get:11 http://in.archive.ubuntu.com precise/restricted i386 Packages [8,212 B] 
Get:12 http://in.archive.ubuntu.com precise/universe i386 Packages [4,611 kB]  
Get:13 http://in.archive.ubuntu.com precise/multiverse i386 Packages [124 kB]  
Get:14 http://in.archive.ubuntu.com precise/main TranslationIndex [74 B]       
Get:15 http://in.archive.ubuntu.com precise/multiverse TranslationIndex [73 B] 
Get:16 http://in.archive.ubuntu.com precise/restricted TranslationIndex [72 B] 
Get:17 http://in.archive.ubuntu.com precise/universe TranslationIndex [75 B]   
Hit http://in.archive.ubuntu.com precise-updates/main Sources                  
Hit http://in.archive.ubuntu.com precise-updates/restricted Sources            
Hit http://in.archive.ubuntu.com precise-updates/universe Sources              
Hit http://in.archive.ubuntu.com precise-updates/multiverse Sources            
Hit http://in.archive.ubuntu.com precise-updates/main i386 Packages            
Hit http://in.archive.ubuntu.com precise-updates/restricted i386 Packages      
Hit http://in.archive.ubuntu.com precise-updates/universe i386 Packages        
Hit http://in.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Hit http://in.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://in.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://in.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://in.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://in.archive.ubuntu.com precise-backports/main Sources                
Hit http://in.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://in.archive.ubuntu.com precise-backports/universe Sources            
Hit http://in.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://in.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://in.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://in.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://in.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://in.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://in.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://in.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://in.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://in.archive.ubuntu.com precise-security/main Sources                 
Hit http://in.archive.ubuntu.com precise-security/restricted Sources           
Hit http://in.archive.ubuntu.com precise-security/universe Sources             
Hit http://in.archive.ubuntu.com precise-security/multiverse Sources           
Hit http://in.archive.ubuntu.com precise-security/main i386 Packages           
Hit http://in.archive.ubuntu.com precise-security/restricted i386 Packages     
Hit http://in.archive.ubuntu.com precise-security/universe i386 Packages       
Hit http://in.archive.ubuntu.com precise-security/multiverse i386 Packages     
Hit http://in.archive.ubuntu.com precise-security/main TranslationIndex        
Hit http://in.archive.ubuntu.com precise-security/multiverse TranslationIndex  
Hit http://in.archive.ubuntu.com precise-security/restricted TranslationIndex  
Hit http://in.archive.ubuntu.com precise-security/universe TranslationIndex    
Hit http://in.archive.ubuntu.com precise/main Translation-en                   
Hit http://in.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://in.archive.ubuntu.com precise/restricted Translation-en             
Hit http://in.archive.ubuntu.com precise/universe Translation-en               
Hit http://in.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://in.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://in.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://in.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://in.archive.ubuntu.com precise-backports/main Translation-en
Hit http://in.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://in.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://in.archive.ubuntu.com precise-backports/universe Translation-en
Hit http://in.archive.ubuntu.com precise-security/main Translation-en
Hit http://in.archive.ubuntu.com precise-security/multiverse Translation-en
Hit http://in.archive.ubuntu.com precise-security/restricted Translation-en
Hit http://in.archive.ubuntu.com precise-security/universe Translation-en
Fetched 12.0 MB in 3min 27s (57.9 kB/s)
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/webupd8team/themes/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/webupd8team/themes/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
assassin@raju-xubuntu:~$ 

```

Thanks in advance

---

### Post by effenberg0x0 on 2011-11-07
**Copy&Paste Solution (into terminal window):**

sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup && sudo sed -i 's|[http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources|http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources|g]("http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources%7Chttp://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources%7Cg")' /etc/apt/sources.list && sudo sed -i 's|[http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages|http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages|g]("http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages%7Chttp://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages%7Cg")' /etc/apt/sources.list && sudo sed -i 's|[http://ppa.launchpad.net/webupd8team/themes/ubuntu/dists/precise/main/binary-i386/Packages|http://ppa.launchpad.net/webupd8team/themes/ubuntu/dists/precise/main/binary-i386/Packages|g]("http://ppa.launchpad.net/webupd8team/themes/ubuntu/dists/precise/main/binary-i386/Packages%7Chttp://ppa.launchpad.net/webupd8team/themes/ubuntu/dists/precise/main/binary-i386/Packages%7Cg")' /etc/apt/sources.list && sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade

There are no extras sources or binaries for Precise. webupd8team does not have a Precise repository. These lines are changed to use the Oneiric tree, using the command above. 

To debug this yourself in the future, use a browser.

Point to the address you see in apt error, say: 
```
http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources
```You'll get the same 404 error apt got.
Go up some levels: 
```
http://extras.ubuntu.com/ubuntu/dists/
```You'll see there's no Precise directory.

---

### Post by raja.genupula on 2011-11-07
> **effenberg0x0 said:**
> sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup && sudo sed -i 's|[http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources|http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources|g]("http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources%7Chttp://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources%7Cg")' /etc/apt/sources.list && sudo sed -i 's|[http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages|http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages|g]("http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages%7Chttp://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages%7Cg")' /etc/apt/sources.list && sudo sed -i 's|[http://ppa.launchpad.net/webupd8team/themes/ubuntu/dists/precise/main/binary-i386/Packages|http://ppa.launchpad.net/webupd8team/themes/ubuntu/dists/precise/main/binary-i386/Packages|g]("http://ppa.launchpad.net/webupd8team/themes/ubuntu/dists/precise/main/binary-i386/Packages%7Chttp://ppa.launchpad.net/webupd8team/themes/ubuntu/dists/precise/main/binary-i386/Packages%7Cg")' /etc/apt/sources.list && sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade

hi thanks for reply

could please provide me that information in a good-manner please man its look very much confuse to me

---

### Post by effenberg0x0 on 2011-11-07
I'm sorry, I can't.

---

### Post by raja.genupula on 2011-11-07
its ok man , thanks for picking up.I need solution because i wanna get some themes to my gnome-shell.

---

### Post by dino99 on 2011-11-07
you dont need those lines ending with "sources" (deb-scr lines into /etc/apt/sources.list, comment them out and update again)

---

### Post by raja.genupula on 2011-11-11
problem not yet solved and i am still getting few more things ...

```
assassin@raju-xubuntu:~$ sudo apt-get upgrade
[sudo] password for assassin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  banshee banshee-extension-soundmenu conky-all flex gir1.2-webkit-3.0
  gnome-online-accounts libgoa-1.0-0 libwebkitgtk-1.0-0 libwebkitgtk-3.0-0
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
assassin@raju-xubuntu:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://deb.opera.com stable InRelease                                      
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://mirror.switch.ch precise InRelease                                  
Ign http://extras.ubuntu.com precise Release.gpg                               
Get:2 http://deb.opera.com stable Release.gpg [189 B]                          
Get:3 http://dl.google.com stable Release [1,347 B]                  
Get:4 http://ppa.launchpad.net oneiric Release.gpg [316 B]                     
Ign http://mirror.switch.ch precise-updates InRelease                          
Ign http://extras.ubuntu.com precise Release                                   
Ign http://mirror.switch.ch precise-backports InRelease                        
Hit http://deb.opera.com stable Release                                        
Get:5 http://dl.google.com stable/main i386 Packages [1,208 B]                 
Err http://deb.opera.com stable Release                                        
  
Get:6 http://ppa.launchpad.net oneiric Release.gpg [316 B]                     
Ign http://mirror.switch.ch precise-security InRelease                         
Get:7 http://mirror.switch.ch precise Release.gpg [198 B]            
Ign http://ppa.launchpad.net precise Release.gpg                               
Get:8 http://mirror.switch.ch precise-updates Release.gpg [198 B]              
Get:9 http://mirror.switch.ch precise-backports Release.gpg [198 B]            
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://mirror.switch.ch precise-security Release.gpg                       
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://ppa.launchpad.net oneiric Release                                   
Get:10 http://mirror.switch.ch precise Release [49.6 kB]                       
Ign http://ppa.launchpad.net precise Release                                   
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex                    
Ign http://ppa.launchpad.net oneiric/main i386 Packages/DiffIndex              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex                    
Ign http://ppa.launchpad.net oneiric/main i386 Packages/DiffIndex              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Err http://extras.ubuntu.com precise/main i386 Packages                        
  404  Not Found
Hit http://mirror.switch.ch precise-updates Release                            
Hit http://mirror.switch.ch precise-backports Release                          
Hit http://mirror.switch.ch precise-security Release                           
Ign http://mirror.switch.ch precise-updates Release                            
Ign http://mirror.switch.ch precise-backports Release                          
Ign http://dl.google.com stable/main TranslationIndex                          
Get:11 http://mirror.switch.ch precise/main Sources [901 kB]                   
Ign http://extras.ubuntu.com precise/main Translation-en_IN              
Ign http://extras.ubuntu.com precise/main Translation-en                 
Err http://ppa.launchpad.net precise/main Sources      
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net oneiric/main Translation-en_IN                  
Ign http://ppa.launchpad.net oneiric/main Translation-en                     
Ign http://ppa.launchpad.net oneiric/main Translation-en_IN                  
Ign http://ppa.launchpad.net oneiric/main Translation-en                     
Ign http://ppa.launchpad.net precise/main Translation-en_IN                  
Ign http://ppa.launchpad.net precise/main Translation-en                     
Ign http://dl.google.com stable/main Translation-en_IN                         
Ign http://dl.google.com stable/main Translation-en                            
Get:12 http://mirror.switch.ch precise/restricted Sources [5,358 B]            
Get:13 http://mirror.switch.ch precise/universe Sources [4,914 kB]             
Get:14 http://mirror.switch.ch precise/multiverse Sources [159 kB]             
Get:15 http://mirror.switch.ch precise/main i386 Packages [1,260 kB]           
Get:16 http://mirror.switch.ch precise/restricted i386 Packages [8,218 B]      
Get:17 http://mirror.switch.ch precise/universe i386 Packages [4,639 kB]       
Get:18 http://mirror.switch.ch precise/multiverse i386 Packages [124 kB]       
Get:19 http://mirror.switch.ch precise/main TranslationIndex [74 B]            
Get:20 http://mirror.switch.ch precise/multiverse TranslationIndex [73 B]      
Get:21 http://mirror.switch.ch precise/restricted TranslationIndex [72 B]      
Get:22 http://mirror.switch.ch precise/universe TranslationIndex [75 B]        
Ign http://mirror.switch.ch precise-updates/main Sources/DiffIndex             
Ign http://mirror.switch.ch precise-updates/restricted Sources/DiffIndex       
Ign http://mirror.switch.ch precise-updates/universe Sources/DiffIndex         
Ign http://mirror.switch.ch precise-updates/multiverse Sources/DiffIndex       
Ign http://mirror.switch.ch precise-updates/main i386 Packages/DiffIndex       
Ign http://mirror.switch.ch precise-updates/restricted i386 Packages/DiffIndex 
Ign http://mirror.switch.ch precise-updates/universe i386 Packages/DiffIndex   
Ign http://mirror.switch.ch precise-updates/multiverse i386 Packages/DiffIndex 
Hit http://mirror.switch.ch precise-updates/main TranslationIndex              
Hit http://mirror.switch.ch precise-updates/multiverse TranslationIndex        
Hit http://mirror.switch.ch precise-updates/restricted TranslationIndex        
Hit http://mirror.switch.ch precise-updates/universe TranslationIndex          
Ign http://mirror.switch.ch precise-backports/main Sources/DiffIndex           
Ign http://mirror.switch.ch precise-backports/restricted Sources/DiffIndex     
Ign http://mirror.switch.ch precise-backports/universe Sources/DiffIndex       
Ign http://mirror.switch.ch precise-backports/multiverse Sources/DiffIndex     
Ign http://mirror.switch.ch precise-backports/main i386 Packages/DiffIndex     
Ign http://mirror.switch.ch precise-backports/restricted i386 Packages/DiffIndex
Ign http://mirror.switch.ch precise-backports/universe i386 Packages/DiffIndex 
Ign http://mirror.switch.ch precise-backports/multiverse i386 Packages/DiffIndex
Hit http://mirror.switch.ch precise-backports/main TranslationIndex            
Hit http://mirror.switch.ch precise-backports/multiverse TranslationIndex      
Hit http://mirror.switch.ch precise-backports/restricted TranslationIndex      
Hit http://mirror.switch.ch precise-backports/universe TranslationIndex        
Hit http://mirror.switch.ch precise-security/main Sources                      
Hit http://mirror.switch.ch precise-security/restricted Sources                
Hit http://mirror.switch.ch precise-security/universe Sources
Hit http://mirror.switch.ch precise-security/multiverse Sources
Hit http://mirror.switch.ch precise-security/main i386 Packages
Hit http://mirror.switch.ch precise-security/restricted i386 Packages
Hit http://mirror.switch.ch precise-security/universe i386 Packages
Hit http://mirror.switch.ch precise-security/multiverse i386 Packages
Hit http://mirror.switch.ch precise-security/main TranslationIndex
Hit http://mirror.switch.ch precise-security/multiverse TranslationIndex
Hit http://mirror.switch.ch precise-security/restricted TranslationIndex
Hit http://mirror.switch.ch precise-security/universe TranslationIndex
Get:23 http://mirror.switch.ch precise/main Translation-en [717 kB]
Hit http://mirror.switch.ch precise/multiverse Translation-en                  
Hit http://mirror.switch.ch precise/restricted Translation-en                  
Get:24 http://mirror.switch.ch precise/universe Translation-en [3,278 kB]      
Hit http://mirror.switch.ch precise-updates/main Sources                       
Hit http://mirror.switch.ch precise-updates/restricted Sources                 
Hit http://mirror.switch.ch precise-updates/universe Sources                   
Hit http://mirror.switch.ch precise-updates/multiverse Sources                 
Hit http://mirror.switch.ch precise-updates/main i386 Packages                 
Hit http://mirror.switch.ch precise-updates/restricted i386 Packages           
Hit http://mirror.switch.ch precise-updates/universe i386 Packages             
Hit http://mirror.switch.ch precise-updates/multiverse i386 Packages           
Hit http://mirror.switch.ch precise-updates/main Translation-en                
Hit http://mirror.switch.ch precise-updates/multiverse Translation-en          
Hit http://mirror.switch.ch precise-updates/restricted Translation-en          
Hit http://mirror.switch.ch precise-updates/universe Translation-en            
Hit http://mirror.switch.ch precise-backports/main Sources                     
Hit http://mirror.switch.ch precise-backports/restricted Sources               
Hit http://mirror.switch.ch precise-backports/universe Sources                 
Hit http://mirror.switch.ch precise-backports/multiverse Sources               
Hit http://mirror.switch.ch precise-backports/main i386 Packages               
Hit http://mirror.switch.ch precise-backports/restricted i386 Packages         
Hit http://mirror.switch.ch precise-backports/universe i386 Packages           
Hit http://mirror.switch.ch precise-backports/multiverse i386 Packages         
Hit http://mirror.switch.ch precise-backports/main Translation-en              
Hit http://mirror.switch.ch precise-backports/multiverse Translation-en        
Hit http://mirror.switch.ch precise-backports/restricted Translation-en        
Hit http://mirror.switch.ch precise-backports/universe Translation-en          
Hit http://mirror.switch.ch precise-security/main Translation-en               
Hit http://mirror.switch.ch precise-security/multiverse Translation-en         
Hit http://mirror.switch.ch precise-security/restricted Translation-en         
Hit http://mirror.switch.ch precise-security/universe Translation-en           
Fetched 16.1 MB in 4min 51s (55.0 kB/s)                                        
Reading package lists... Done
[B]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://deb.opera.com stable Release: The following signatures were invalid: BADSIG A2019EA84E7532C8 Opera Software Archive Automatic Signing Key 2011 <packager@opera.com>

W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG D834D91FA49CCDDB Launchpad PPA for System Load Indicator developers
W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG 8C851674F96FD737 Launchpad PPA for Paul Gevers
W: GPG error: http://mirror.switch.ch precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://mirror.switch.ch precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release  
[/B]
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/webupd8team/themes/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/webupd8team/themes/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

W: Some index files failed to download. They have been ignored, or old ones used instead.
assassin@raju-xubuntu:~$ 

```

thanks in advance

EDIT : ok i did this 

```

assassin@raju-xubuntu:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A2019EA84E7532C8
[sudo] password for assassin: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.X5MH6gCrd9 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys A2019EA84E7532C8
gpg: requesting key 4E7532C8 from hkp server keyserver.ubuntu.com
gpg: key 4E7532C8: "Opera Software Archive Automatic Signing Key 2011 <packager@opera.com>" 2 new signatures
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:         new signatures: 2
assassin@raju-xubuntu:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D834D91FA49CCDDB
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.cGjJ8huZnO --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys D834D91FA49CCDDB
gpg: requesting key A49CCDDB from hkp server keyserver.ubuntu.com
gpg: key A49CCDDB: "Launchpad PPA for System Load Indicator developers" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
assassin@raju-xubuntu:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8C851674F96FD737
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.jJ9TgrcygK --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 8C851674F96FD737
gpg: requesting key F96FD737 from hkp server keyserver.ubuntu.com
gpg: key F96FD737: "Launchpad PPA for Paul Gevers" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
assassin@raju-xubuntu:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.n6yuMvuB2w --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" 22 new signatures
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:         new signatures: 22
assassin@raju-xubuntu:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.IKOCfX8Mwd --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
assassin@raju-xubuntu:~$ 

```

---

### Post by raja.genupula on 2011-11-11
again i did update guys but no use still getting signature errors .......... give me a solution....but i want that webupd8 PPA for my gnome-shell themes.

Thanks to all

---

### Post by ronacc on 2011-11-11
in your /etc/apt/sources.list change precise to oneiric for the webupd8 ppa ONLY  and update again .

edit: or manualy download the themes and install with dpkg .

---

### Post by effenberg0x0 on 2011-11-12
If you want to understand what you are doing, what is Ubuntu, what are repositories, or anything like that, you should read this very good and simples documents people wrote in hopes of ever being used by those in your exact situation:

1) Introduction to repositories:
[https://help.ubuntu.com/community/Repositories/](https://help.ubuntu.com/community/Repositories/)

2) Managing repositories via GUI and command-line:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

If you just want an easy answer without having to actually think for a second:

1) Go here and get a new sources.list from the third-part unofficial sources.list generator for the version of Ubuntu you are running. [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) 
Leave this browser window open.
 
2) Open a terminal using the Ubuntu dash. In the terminal, type these commands:

3) The following command will backup the current list of sources.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.screwed
```4) The following command will open a text-editor so you can edit your current sources.list
```
sudo gedit /etc/apt/sources.list
```5) Inside the text-editor, delete all the contents, everything, you see inside.

6) Now go back to the browser window where you had the new list of sources, select them with your mouse, copy them, and paste them inside the text-editor. Click the "save" button in the text editor and close it.

7) In the terminal, run the following command:
```
sudo apt-get update && sudo apt-get upgrade
```8) If you still have the same problems, it means it is necessary to clear your cache. If this is the case, run the following commands, one by one:
```

cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
 
```9) Now try to run this command again:
```
sudo apt-get update && sudo apt-get upgrade
```The commands above are standards, known to work, and they will work there. You will end up with a clean / default sources list. This will give you back the ability to update/upgrade the operating system. 

At this point, you will have to manually add any alternative repository you want to.

---

### Post by raja.genupula on 2011-11-12
> **ronacc said:**
> in your /etc/apt/sources.list change precise to oneiric for the webupd8 ppa ONLY  and update again .

edit: or manualy download the themes and install with dpkg .

hi man thanks for the info , i dont have that webdp8 PPA  in my source list 
```
# deb cdrom:[Xubuntu 11.10 _Oneiric Ocelot_ - Alpha i386 (20110705)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ precise main restricted
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ precise-updates main restricted
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ precise universe
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ precise universe
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ precise-updates universe
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ precise multiverse
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ precise multiverse
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ precise-updates multiverse
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ precise-backports main restricted universe multiverse

deb http://mirror.switch.ch/ftp/mirror/ubuntu/ precise-security main restricted
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ precise-security main restricted
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ precise-security universe
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ precise-security universe
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ precise-security multiverse
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
## deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main
```

now how can i go

---

### Post by raja.genupula on 2011-11-12
Hi man thanks for the info & actually the link given by you is upto for 11.10 but i am using 12.04...but thanks for the other links .:D

---

### Post by lemino on 2011-11-20
I understand the concept of the solution you're offering, I think, but I don't get the command to work. When I look at 

/etc/apt/sources.list

 I can't find any file named that. What I have is instead a library called 

/etc/apt/sources.list.d

What can I do about this? I guess the reason why there are no extras for Precise is because it's still in development, and I'm of course fine with installing without them.

Thanks for all tips!

---

### Post by effenberg0x0 on 2011-11-20
**/etc/apt/sources.list.d is directory**, not a library, in which files are automatically created inside when you add alternative PPAs to your system. You'll only have anything inside there if you add a PPA. you can use the following commands to check if anything is in there:
```

cd /etc/apt/sources.list.d/
ls -la

```**/etc/apt/sources.list is a default file**, mandatory to any install, that is used by many applications. It informs them where on the Internet are Ubuntu repositories of files. Without this file, you won't be able to use apt-get, update-manager, synaptic, Ubuntu Software Center, aptitude, etc. It's basically a broken setup. You can't not escape from having this file, you need it. Check if you have this vital file using the following command:
```

ls -la /etc/apt/sources.list

```If you really deleted this file, you need to recreate it. At a terminal, type:

```
sudo gedit /etc/apt/sources.list 
```Copy the following content inside of gedit:

[B]If you are running Oneiric Ocelot:
[/B]```
deb http://archive.ubuntu.com/ubuntu oneiric main restricted universe
deb-src http://archive.ubuntu.com/ubuntu oneiric main restricted universe
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://archive.canonical.com/ubuntu oneiric partner
```[B]If you are running Precise Pangolin:
[/B]```
deb http://archive.ubuntu.com/ubuntu precise main restricted universe
deb-src http://archive.ubuntu.com/ubuntu precise main restricted universe
```Save, exit gedit, get back to the terminal.
Now run the following commands to update your cache, access the default repositories we just added and update your system:

```

sudo chmod 644 /etc/apt/sources.list
sudo chown root:root /etc/apt/sources.list
cd /var/lib/apt
sudo mv lists lists.old.1
sudo mkdir -p lists/partial
cd
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```[B]OBS: 
[/B]- If you have alternate PPAs added to /etc/sources.list.d/ , the state of your machine is unpredictable since we don't know what is added and, anyway, it is not PP supported software. The command to properly remove an alternate PPA and uninstall it's software is 
```
sudo apt-get install ppa-purge
sudo apt-purge ppa:repository_name/directory
```You will have to update and upgrade again after removing any ppa. ```
sudo apt-get update && sudo apt-get upgrade
```- Same thing if you keep previous entries in /etc/sources.list file which are not default ones (official repositories).

---

### Post by fdrake on 2011-11-20
i remember once someone from India had the same problem as you. The solution was to try a different server source from a country close to him. Just an suggestion. It may not be the repository list the problem. I don't run Oneiric so I cannot compare it with mine . Hope some one else does.

---

### Post by raja.genupula on 2011-11-21
Thanks for the all reply's , but I am sorry 
My 12.04 not booting even  and right now i am looking for a fix to that .
 
So i will be back to here after fixing that problem .
 
I am really sorry to say this. :(:(.
 
Thank you.

---

### Post by dino99 on 2011-11-21
hi,
i've already said you need to clean your /etc/apt/sources.list, but you dont have done it, so why still whining then ?

here is a working /etc/apt/sources.list:


  
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-proposed main universe restricted multiverse

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric free non-free


if you enter something else (non genuine third entries) it supposed you understand what you are doing.

---

### Post by raja.genupula on 2011-11-21
@dino99 , Thanks man 

But i'm unable to do any ....

right now my system got freeze at login screen   , any of things keyboard and Mouse are not responding .

So now i am looking for a fix to that .its really making me OFF man . 
Hmm i am in tense that will it be ok ? 
I already posted a thread in Forums about that and soon i hope it will be with a solution .

---

### Post by dino99 on 2011-11-21
you should be able to  go ahead if you boot in recovery mode (hold "shift" key down at bios end process to get the grub menu on a single OS installation)

---

### Post by effenberg0x0 on 2011-11-21
@Raja

In order for us to be able to help you, please follow the steps below and provide the requested information:

**1)** Reset your PC while holding the shift key. That will show you the Grub Menu.


**2) **Select the "Recovery Mode" option (generally the second one). See the screenshot.
[ATTACH]207686[/ATTACH]

**3)** It will boot until it asks you what you want to do. You will select the option "Remount". See screenshot.
[ATTACH]207687[/ATTACH]

**4)** After remounting, it will ask you to press ENTER and another screen will show. In this screen, select "Drop to root shell prompt with networking". See screenshot.
[ATTACH]207688[/ATTACH]

**5)** You will see a prompt. Type the following commands in this prompt:
a) If you connect to the Internet using a cable, type the following command and take note of the name your ethernet card (probably eth0)
ifconfig

b) If you connect to the Internet using wireless, type the following command and take note of the name your wireless card (probably wlan0)
iwconfig

Now activate an Internet connection using the card name you detected above, using the command dhclient <name>.

Example 1: You connect using a network cable and your network card name is eth0:
dhclient eth0

Example 2: You connect using wireless and your wireless cared is named wlan0:
dhclient wlan0

**6)** Test the connection, with the following command:
ping ubuntu.com

You should see a reply, like this:
$ ping ubuntu.com
PING ubuntu.com (91.189.94.156) 56(84) bytes of data.
64 bytes from vostok.canonical.com (91.189.94.156): icmp_req=1 ttl=45 time=370 ms

**7)** Follow the instructions at: [http://ubuntuforums.org/showpost.php?p=11474806&postcount=14](http://ubuntuforums.org/showpost.php?p=11474806&postcount=14)

**ADVICE: I STRONGLY recommend that you install Oneiric Oncelot as you are clearly trying to learn to use Linux. You will benefit from mushc more increased support (see the General Help section - there are much more people there, many helpers, etc). This version (Precise Pangolin) is in Alpha stage. IT WILL BREAK CONTINUOUSLY until is released. EVERY UPDATE IS RISKY AND LIKELY TO BREAK THE SETUP. The really reason to use it, it to test and report bugs. In order to do so, one must have some level of comprehension on Ubuntu and Linux. People in this forum section are not focused at support. We are here to test PP.**

---

### Post by raja.genupula on 2011-11-21
I am sorry guys , i did a stupid thing . I just formatted that .

But my big thanks to all of you. 

Now i am here to ask one question . Because I wanna know that .
What the things i shouldn't do while Using a development release.

Once again Thank you very much Friends.

---

### Post by effenberg0x0 on 2011-11-21
> **raja.genupula said:**
> I am sorry guys , i did a stupid thing . I just formatted that .

But my big thanks to all of you. 

Now i am here to ask one question . Because I wanna know that .
What the things i shouldn't do while Using a development release.

Once again Thank you very much Friends.

- The development release, at this point, has virtually no difference from the stable one, from an end-user point of view. So there's no advantage whatsoever in using it.
- During the development, many shared libraries are updated (to support new features or fix programs bugs in the future). But every time one library is updated, many other libraries and the programs that use them may (probably will) become unusable. Either they won't function correctly or won't work at all, until these are also updated. It all happens asynchronously.
- Testing versions of libraries and programs are published for testing. Meaning that their behavior is unpredictable. It can be perfect, it can be usable, it can make your PC unusable.

It's expected that testers can spot something wrong, track the package and possibly the exact problem, and report it to developers. Developers have absolutely no concern, during development stage, to provide usable releases - they are not to be used for anything else than testing. There's no support, etc.

So I can't think of a reason someone would want to use the development version, if not to test, find problems and report them.
So, unless someone voluntarily wants to have an unusable PC day in day out, there's no point.

---

### Post by raja.genupula on 2011-11-21
So I am using in a right way i think . Installing all what i need and using them . If i have problem then reporting that with launchpad .

Thanks man . you spend a lot of time for me. Thank you  very much.

I reinstall 12.04 ...in evening .

Thanks man .

I am making this.

---

### Post by cariboo on 2011-11-21
Remember to follow the instructions [here]("https://help.ubuntu.com/community/ReportingBugs"), there are to many bugs reported, that are either duplicates or, there isn't enough information to help the devs solve the problem.

---

### Post by raja.genupula on 2011-11-22
Hi cariboo907 
                    I need this link too. i think it can help me to report the with essential information need to the dev's to solve the reporting BUG's in launchpad .Now i am on it , 

                                                        Thank you man.:D

---

### Post by raja.genupula on 2011-11-22
> **effenberg0x0 said:**
> **/etc/apt/sources.list.d is directory**, not a library, in which files are automatically created inside when you add alternative PPAs to your system. You'll only have anything inside there if you add a PPA. you can use the following commands to check if anything is in there:
```

cd /etc/apt/sources.list.d/
ls -la

```**/etc/apt/sources.list is a default file**, mandatory to any install, that is used by many applications. It informs them where on the Internet are Ubuntu repositories of files. Without this file, you won't be able to use apt-get, update-manager, synaptic, Ubuntu Software Center, aptitude, etc. It's basically a broken setup. You can't not escape from having this file, you need it. Check if you have this vital file using the following command:
```

ls -la /etc/apt/sources.list

```If you really deleted this file, you need to recreate it. At a terminal, type:

```
sudo gedit /etc/apt/sources.list 
```Copy the following content inside of gedit:

[B]If you are running Oneiric Ocelot:
[/B]```
deb http://archive.ubuntu.com/ubuntu oneiric main restricted universe
deb-src http://archive.ubuntu.com/ubuntu oneiric main restricted universe
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://archive.canonical.com/ubuntu oneiric partner
```[B]If you are running Precise Pangolin:
[/B]```
deb http://archive.ubuntu.com/ubuntu precise main restricted universe
deb-src http://archive.ubuntu.com/ubuntu precise main restricted universe
```Save, exit gedit, get back to the terminal.
Now run the following commands to update your cache, access the default repositories we just added and update your system:

```

sudo chmod 644 /etc/apt/sources.list
sudo chown root:root /etc/apt/sources.list
cd /var/lib/apt
sudo mv lists lists.old.1
sudo mkdir -p lists/partial
cd
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```[B]OBS: 
[/B]- If you have alternate PPAs added to /etc/sources.list.d/ , the state of your machine is unpredictable since we don't know what is added and, anyway, it is not PP supported software. The command to properly remove an alternate PPA and uninstall it's software is 
```
sudo apt-get install ppa-purge
sudo apt-purge ppa:repository_name/directory
```You will have to update and upgrade again after removing any ppa. ```
sudo apt-get update && sudo apt-get upgrade
```- Same thing if you keep previous entries in /etc/sources.list file which are not default ones (official repositories).

I have reinstalled XUbuntu 11.10 and turn it up as 12.04 and used this post .
as dino99 told me i have ## ed  those extra PPA and after as you said i did and got some error related to partial and with a message as hash mismatch or something .
so i did sudo m -rf /var/lib/apt/lists/partial/*
and updated again. Now this problem completely solved ,

Thank you once again.

---

