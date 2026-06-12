---
title: "Be carefull about using Software Updater: 1 package held back in 13.10."
date: 2013-04-26
forum: Ubuntu Development Version
---

### Post by kevpan815 on 2013-04-26
LibColumbus held back in 13.10. So don't use Software Updater in 13.10 or else it will offer you a Partial Upgrade!

---

### Post by Frogs Hair on 2013-04-26
If you have updated your repositories to 13.10 you may to see many partial upgrades over the next six months , it's just part of testing . I didn't see this in 13.04 though.

---

### Post by Mathor on 2013-04-26
I wouldn't recommend using software-updater at all to update during a development release. Sudo apt-get dist-upgrade is a better choice!

---

### Post by deadflowr on 2013-04-26
> **Frogs Hair said:**
> If you have updated your repositories to 13.10 you may to see many partial upgrades over the next six months , it's just part of testing . I didn't see this in 13.04 though.

It's probably caused by the packages in the repos not being synced(?) right. If you wait a little while all the packages should be uploaded right.
At least that's what I've found.

> **Mathor said:**
> I wouldn't recommend using software-updater at all to update during a development release. Sudo apt-get dist-upgrade is a better choice!

So we're not suppose to test a major package?

---

### Post by Mathor on 2013-04-26
> **deadflowr said:**
> 

So we're not suppose to test a major package?

It just has rarely cooperated in past cycles.

---

### Post by serdotlinecho on 2013-04-26
Seriously...up until now, I never use or open Software Updater to uprade my Ubuntu+1, never bother to click the new "A" icon!

```
serdotlinecho@samalander:~$ date ; sudo apt-get dist-upgrade
Sat Apr 27 10:20:07 MYT 2013
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libboost-date-time1.53.0
The following packages will be upgraded:
  cpp cpp-4.8 g++ g++-4.8 gcc gcc-4.8 gcc-4.8-base glib-networking glib-networking-common
  glib-networking-services libasan0 libatomic1 libcmis-0.3-3 **libcolumbus0-0 libcolumbus0-0-common**
  libgcc-4.8-dev libgcc1 libgomp1 libitm1 libquadmath0 libstdc++-4.8-dev libstdc++6 linux-libc-dev vim
  vim-common vim-runtime vim-tiny
27 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 33.2 MB of archives.
After this operation, 176 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
```

---

### Post by kevpan815 on 2013-04-27
> **deadflowr said:**
> It's probably caused by the packages in the repos not being synced(?) right. If you wait a little while all the packages should be uploaded right.
At least that's what I've found.



So we're not suppose to test a major package?

Software Updater usually does NOT work at all during Alpha/Beta, and when it does work, it will usually offer you a Partial Upgrade. sudo apt-get update && sudo apt-get dist-upgrade is the better choice. P.S. See Cariboo907's comments regarding Partial Upgrades in the above Sticky.

---

### Post by kevpan815 on 2013-04-27
> **Mathor said:**
> It just has rarely cooperated in past cycles.

I agree with you 100% on that statement, though it looks like they are at least finally trying to fix the problems with it.

---

### Post by deadflowr on 2013-04-27
> **Mathor said:**
> It just has rarely cooperated in past cycles.

My point is , that shouldn't be an excuse not to help test and fix it.

If it is not tested in the development stage, then what about the users who install it in stable and the program goes bonkers.

It's in this stage the we can help prevent that.

---

### Post by kevpan815 on 2013-04-27
> **deadflowr said:**
> It's probably caused by the packages in the repos not being synced(?) right. If you wait a little while all the packages should be uploaded right.
At least that's what I've found.



So we're not suppose to test a major package?

By the way, deadflowr, are you helping us test Ubuntu + 1 right now? Since you Signature says that you are on 12.04? Those of us who are actually testing Ubuntu + 1 usually change our Profile so it says Ubuntu Developmental Release in our Profile. If you are just using Software Updater in 12.04.2 you should have no problems at all, as long as it does NOT Lock Up your System. But if you are actually helping us test 13.10 by putting in Ventrical's 3 Command's in 13.04, you should instead use sudo apt-get update && sudo apt-get dist-upgrade. Just to let you know. P.S. Software Updater has Locked Up all of my 3 Computers before, so use caution about actually using it, Just to let you know.

---

### Post by kevpan815 on 2013-04-27
> **deadflowr said:**
> My point is , that shouldn't be an excuse not to help test and fix it.

If it is not tested in the development stage, then what about the users who install it in stable and the program goes bonkers.

It's in this stage the we can help prevent that.

The problem is that Software Updater will quite often offer us a Partial Upgrade during the Development Cycle. Partial Upgrades are usually a NO-NO! That's actually what the main problem is about using it during a Development Release Cycle. Ask any one else in this Sub-Forum that same Question, most of them will tell you the same answer that I am giving you right now.

---

### Post by deadflowr on 2013-04-27
> **kevpan815 said:**
> The problem is that Software Updater will quite often offer us a Partial Upgrade during the Development Cycle. Partial Upgrades are usually a NO-NO! That's actually what the main problem is about using it during a Development Release Cycle. Ask any one else in this Sub-Forum that same Question, most of them will tell you the same answer that I am giving you right now.


Partial Upgrades are partial upgrades and have no bearing on whether to run updates through the software updater or not.
If you get a partial upgrade request, and don't feel like running it, then cancel it.
If it's persistent then report it.
If you have problems like the OP has, then yes run a cli to try to see if it'll fix things.
But don't avoid something out of fear.
You are running a development release, after all. 
Be intrepid.

---

### Post by jppr on 2013-04-27
When you use the Synaptic updates so the update is the least problems. Synaptic is the best tool for the update because it does not ever provide a partial upgrade but left without upgrading those packages which have dependencies does not update right now. Update-manager does not do that, but offers a partial upgrade that makes the application of that part of the users that is not "dangerous".

I don´t  understand why the Update-manager is even a tool to update the Synaptic is 10 times better, easier, and smarter upgrades and otherwise as the update-manager.

Users that is not part of the update-manager is indeed dangerous to update tool and when something goes wrong, or, in the worst case, the whole system breaks down then here in the forum to cry and complain.

---

### Post by roly33 on 2013-04-27
> **serdotlinecho said:**
> Seriously...up until now, I never use or open Software Updater to uprade my Ubuntu+1, never bother to click the new "A" icon!

```
serdotlinecho@samalander:~$ date ; sudo apt-get dist-upgrade
Sat Apr 27 10:20:07 MYT 2013
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libboost-date-time1.53.0
The following packages will be upgraded:
  cpp cpp-4.8 g++ g++-4.8 gcc gcc-4.8 gcc-4.8-base glib-networking glib-networking-common
  glib-networking-services libasan0 libatomic1 libcmis-0.3-3 **libcolumbus0-0 libcolumbus0-0-common**
  libgcc-4.8-dev libgcc1 libgomp1 libitm1 libquadmath0 libstdc++-4.8-dev libstdc++6 linux-libc-dev vim
  vim-common vim-runtime vim-tiny
27 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 33.2 MB of archives.
After this operation, 176 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
```

How did you get those updates?

I've run [COLOR=#000000]sudo apt-get update && sudo apt-get dist-upgrade and all I get is

[/COLOR]```
roland@steelers:~$ sudo apt-get update && sudo apt-get dist-upgrade[sudo] password for roland: 
Ign http://extras.ubuntu.com saucy Release.gpg                                                                                                 
Get:1 http://security.ubuntu.com saucy-security Release.gpg [933 B]                                                                            
Get:2 http://gb.archive.ubuntu.com saucy Release.gpg [933 B]                                                                                   
Hit http://archive.canonical.com saucy Release.gpg                                                                                             
Ign http://extras.ubuntu.com saucy Release                                                                                                     
Get:3 http://security.ubuntu.com saucy-security Release [40.8 kB]                                                                              
Hit http://dl.google.com stable Release.gpg                                                                                                    
Get:4 http://gb.archive.ubuntu.com saucy-updates Release.gpg [933 B]                                                                           
Hit http://archive.canonical.com saucy Release                                                                                                 
Get:5 http://gb.archive.ubuntu.com saucy-backports Release.gpg [933 B]                                                                         
Hit http://dl.google.com stable Release.gpg                                                                                                    
Hit http://archive.canonical.com saucy/partner Sources                                                                                         
Get:6 http://gb.archive.ubuntu.com saucy Release [40.8 kB]                                                                                     
Hit http://dl.google.com stable Release                                                                                                        
Hit http://archive.canonical.com saucy/partner amd64 Packages                                                                                  
Hit http://archive.ubuntu.com saucy Release.gpg                                                                                                
Hit http://archive.canonical.com saucy/partner i386 Packages                                                                                   
Hit http://dl.google.com stable Release                                                                                                        
Get:7 http://security.ubuntu.com saucy-security/main Sources [14 B]                                                                            
Hit http://dl.google.com stable/main amd64 Packages                                                                                            
Get:8 http://gb.archive.ubuntu.com saucy-updates Release [40.8 kB]                                                                             
Hit http://archive.ubuntu.com saucy Release                                                                                                    
Get:9 http://security.ubuntu.com saucy-security/restricted Sources [14 B]                                                                      
Hit http://dl.google.com stable/main i386 Packages                                                                                             
Get:10 http://security.ubuntu.com saucy-security/multiverse Sources [14 B]                                                                     
Get:11 http://gb.archive.ubuntu.com saucy-backports Release [40.8 kB]                                                                          
Get:12 http://security.ubuntu.com saucy-security/universe Sources [14 B]                                                                       
Get:13 http://security.ubuntu.com saucy-security/main amd64 Packages [14 B]                                                                    
Hit http://archive.ubuntu.com saucy/main Sources                                                                                               
Get:14 http://security.ubuntu.com saucy-security/restricted amd64 Packages [14 B]                                                              
Get:15 http://security.ubuntu.com saucy-security/universe amd64 Packages [14 B]                                                                
Get:16 http://security.ubuntu.com saucy-security/multiverse amd64 Packages [14 B]                                                              
Ign http://archive.canonical.com saucy/partner Translation-en_GB                                                                               
Get:17 http://security.ubuntu.com saucy-security/main i386 Packages [14 B]                                                                     
Hit http://archive.ubuntu.com saucy/restricted Sources                                                                                         
Ign http://archive.canonical.com saucy/partner Translation-en                                                                                  
Get:18 http://gb.archive.ubuntu.com saucy/main Sources [966 kB]                                                                                
Get:19 http://security.ubuntu.com saucy-security/restricted i386 Packages [14 B]                                                               
Get:20 http://security.ubuntu.com saucy-security/universe i386 Packages [14 B]                                                                 
Get:21 http://security.ubuntu.com saucy-security/multiverse i386 Packages [14 B]                                                               
Hit http://security.ubuntu.com saucy-security/main Translation-en                                                                              
Hit http://dl.google.com stable/main amd64 Packages                                                                                            
Hit http://dl.google.com stable/main i386 Packages                                                                                             
Err http://extras.ubuntu.com saucy/main Sources                                                                                                
  404  Not Found [IP: 91.189.88.33 80]
Err http://extras.ubuntu.com saucy/main amd64 Packages                                                                                         
  404  Not Found [IP: 91.189.88.33 80]
Hit http://security.ubuntu.com saucy-security/multiverse Translation-en                                                                        
Err http://extras.ubuntu.com saucy/main i386 Packages                                                                                          
  404  Not Found [IP: 91.189.88.33 80]
Ign http://extras.ubuntu.com saucy/main Translation-en_GB                                                                                      
Hit http://security.ubuntu.com saucy-security/restricted Translation-en                                                                        
Ign http://extras.ubuntu.com saucy/main Translation-en                                                                                         
Hit http://security.ubuntu.com saucy-security/universe Translation-en                                                                          
Get:22 http://gb.archive.ubuntu.com saucy/restricted Sources [5,987 B]                                                                         
Get:23 http://gb.archive.ubuntu.com saucy/multiverse Sources [171 kB]                                                                          
Get:24 http://gb.archive.ubuntu.com saucy/universe Sources [5,843 kB]                                                                          
Ign http://security.ubuntu.com saucy-security/main Translation-en_GB                                                                           
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_GB                                                                     
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_GB                                                                     
Ign http://dl.google.com stable/main Translation-en_GB                                                                                         
Ign http://security.ubuntu.com saucy-security/universe Translation-en_GB                                                                       
Ign http://dl.google.com stable/main Translation-en                                                                                            
Ign http://dl.google.com stable/main Translation-en_GB                                                                                         
Ign http://dl.google.com stable/main Translation-en                                                                                            
Get:25 http://gb.archive.ubuntu.com saucy/main amd64 Packages [1,190 kB]                                                                       
Get:26 http://gb.archive.ubuntu.com saucy/restricted amd64 Packages [9,651 B]                                                                  
Get:27 http://gb.archive.ubuntu.com saucy/universe amd64 Packages [5,407 kB]                                                                   
Hit http://ppa.launchpad.net raring Release.gpg                                                                                                
Hit http://ppa.launchpad.net raring Release.gpg                                                                                                
Hit http://ppa.launchpad.net raring Release                                                                                                    
Hit http://ppa.launchpad.net raring Release                                                                                                    
Hit http://ppa.launchpad.net raring/main Sources                                                                                               
Hit http://ppa.launchpad.net raring/main amd64 Packages                                                                                        
Hit http://ppa.launchpad.net raring/main i386 Packages                                                                                         
Hit http://ppa.launchpad.net raring/main Sources                                                                                               
Hit http://ppa.launchpad.net raring/main amd64 Packages                                                                                        
Hit http://ppa.launchpad.net raring/main i386 Packages                                                                                         
Hit https://private-ppa.launchpad.net raring Release.gpg                                                                                       
Hit https://private-ppa.launchpad.net raring Release.gpg                                                                               
Hit https://private-ppa.launchpad.net raring Release                                                                                   
Hit https://private-ppa.launchpad.net raring Release                                                                                           
Ign http://ppa.launchpad.net raring/main Translation-en_GB                                                                                     
Ign http://ppa.launchpad.net raring/main Translation-en                                                                                
Ign http://ppa.launchpad.net raring/main Translation-en_GB                                                                             
Ign http://ppa.launchpad.net raring/main Translation-en                                                                                
Hit https://private-ppa.launchpad.net raring/main amd64 Packages                                                                               
Hit https://private-ppa.launchpad.net raring/main i386 Packages                                                                                
Hit https://private-ppa.launchpad.net raring/main amd64 Packages                                                                               
Hit https://private-ppa.launchpad.net raring/main i386 Packages                                                                                
Get:28 http://gb.archive.ubuntu.com saucy/multiverse amd64 Packages [129 kB]                                                                   
Get:29 http://gb.archive.ubuntu.com saucy/main i386 Packages [1,186 kB]                                                                        
Hit http://deb.playonlinux.com precise Release.gpg                                                                                             
Get:30 http://gb.archive.ubuntu.com saucy/restricted i386 Packages [9,632 B]                                                                   
Hit http://deb.playonlinux.com precise Release                                                                                                 
Hit http://deb.playonlinux.com precise/main amd64 Packages                                                                                     
Get:31 http://gb.archive.ubuntu.com saucy/universe i386 Packages [5,416 kB]                                                                    
Hit http://deb.playonlinux.com precise/main i386 Packages                                                                                      
Ign http://deb.playonlinux.com precise/main Translation-en_GB                                                                                  
Ign http://deb.playonlinux.com precise/main Translation-en                                                                                     
Err http://repo.steampowered.com precise Release.gpg                                                                                           
  Something wicked happened resolving 'repo.steampowered.com:http' (-11 - System error)
Ign https://private-ppa.launchpad.net raring/main Translation-en_GB                                                                            
Ign https://private-ppa.launchpad.net raring/main Translation-en                                                                               
Ign https://private-ppa.launchpad.net raring/main Translation-en_GB                                                                            
Get:32 http://gb.archive.ubuntu.com saucy/multiverse i386 Packages [131 kB]                                                                    
Ign https://private-ppa.launchpad.net raring/main Translation-en                                                                               
Hit http://gb.archive.ubuntu.com saucy/main Translation-en_GB                                                                                  
Hit http://gb.archive.ubuntu.com saucy/main Translation-en                                                                                     
Hit http://gb.archive.ubuntu.com saucy/multiverse Translation-en_GB                                                                            
Hit http://gb.archive.ubuntu.com saucy/multiverse Translation-en                                                                               
Hit http://gb.archive.ubuntu.com saucy/restricted Translation-en_GB                                                                            
Hit http://gb.archive.ubuntu.com saucy/restricted Translation-en                                                                               
Hit http://gb.archive.ubuntu.com saucy/universe Translation-en_GB                                                                              
Hit http://gb.archive.ubuntu.com saucy/universe Translation-en                                                                                 
Get:33 http://gb.archive.ubuntu.com saucy-updates/main Sources [14 B]                                                                          
Get:34 http://gb.archive.ubuntu.com saucy-updates/restricted Sources [14 B]                                                                    
Get:35 http://gb.archive.ubuntu.com saucy-updates/multiverse Sources [14 B]                                                                    
Get:36 http://gb.archive.ubuntu.com saucy-updates/universe Sources [14 B]                                                                      
Get:37 http://gb.archive.ubuntu.com saucy-updates/main amd64 Packages [14 B]                                                                   
Get:38 http://gb.archive.ubuntu.com saucy-updates/restricted amd64 Packages [14 B]                                                             
Get:39 http://gb.archive.ubuntu.com saucy-updates/universe amd64 Packages [14 B]                                                               
Get:40 http://gb.archive.ubuntu.com saucy-updates/multiverse amd64 Packages [14 B]                                                             
Get:41 http://gb.archive.ubuntu.com saucy-updates/main i386 Packages [14 B]                                                                    
Get:42 http://gb.archive.ubuntu.com saucy-updates/restricted i386 Packages [14 B]                                                              
Get:43 http://gb.archive.ubuntu.com saucy-updates/universe i386 Packages [14 B]                                                                
Get:44 http://gb.archive.ubuntu.com saucy-updates/multiverse i386 Packages [14 B]                                                              
Hit http://gb.archive.ubuntu.com saucy-updates/main Translation-en                                                                             
Hit http://gb.archive.ubuntu.com saucy-updates/multiverse Translation-en                                                                       
Hit http://gb.archive.ubuntu.com saucy-updates/restricted Translation-en                                                                       
Hit http://gb.archive.ubuntu.com saucy-updates/universe Translation-en                                                                         
Get:45 http://gb.archive.ubuntu.com saucy-backports/main Sources [14 B]                                                                        
Get:46 http://gb.archive.ubuntu.com saucy-backports/restricted Sources [14 B]                                                                  
Get:47 http://gb.archive.ubuntu.com saucy-backports/universe Sources [14 B]                                                                    
Get:48 http://gb.archive.ubuntu.com saucy-backports/multiverse Sources [14 B]                                                                  
Get:49 http://gb.archive.ubuntu.com saucy-backports/main amd64 Packages [14 B]                                                                 
Get:50 http://gb.archive.ubuntu.com saucy-backports/restricted amd64 Packages [14 B]                                                           
Get:51 http://gb.archive.ubuntu.com saucy-backports/universe amd64 Packages [14 B]                                                             
Get:52 http://gb.archive.ubuntu.com saucy-backports/multiverse amd64 Packages [14 B]                                                           
Get:53 http://gb.archive.ubuntu.com saucy-backports/main i386 Packages [14 B]                                                                  
Get:54 http://gb.archive.ubuntu.com saucy-backports/restricted i386 Packages [14 B]                                                            
Get:55 http://gb.archive.ubuntu.com saucy-backports/universe i386 Packages [14 B]                                                              
Get:56 http://gb.archive.ubuntu.com saucy-backports/multiverse i386 Packages [14 B]                                                            
Hit http://gb.archive.ubuntu.com saucy-backports/main Translation-en                                                                           
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en                                                                     
Hit http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en                                                                     
Hit http://gb.archive.ubuntu.com saucy-backports/universe Translation-en                                                                       
Ign http://gb.archive.ubuntu.com saucy-updates/main Translation-en_GB                                                                          
Ign http://gb.archive.ubuntu.com saucy-updates/multiverse Translation-en_GB                                                                    
Ign http://gb.archive.ubuntu.com saucy-updates/restricted Translation-en_GB                                                                    
Ign http://gb.archive.ubuntu.com saucy-updates/universe Translation-en_GB                                                                      
Ign http://gb.archive.ubuntu.com saucy-backports/main Translation-en_GB                                                                        
Ign http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en_GB                                                                  
Ign http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en_GB                                                                  
Ign http://gb.archive.ubuntu.com saucy-backports/universe Translation-en_GB                                                                    
Hit http://repo.steampowered.com precise Release                                                                                               
Ign http://repo.steampowered.com precise/steam Sources/DiffIndex
Ign http://repo.steampowered.com precise/steam amd64 Packages/DiffIndex
Ign http://repo.steampowered.com precise/steam i386 Packages/DiffIndex
Hit http://repo.steampowered.com precise/steam Sources
Hit http://repo.steampowered.com precise/steam amd64 Packages
Hit http://repo.steampowered.com precise/steam i386 Packages
Ign http://repo.steampowered.com precise/steam Translation-en_GB
Ign http://repo.steampowered.com precise/steam Translation-en
Fetched 20.6 MB in 53s (387 kB/s)
W: Failed to fetch http://repo.steampowered.com/steam/dists/precise/Release.gpg  Something wicked happened resolving 'repo.steampowered.com:http' (-11 - System error)


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/saucy/main/source/Sources  404  Not Found [IP: 91.189.88.33 80]


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/saucy/main/binary-amd64/Packages  404  Not Found [IP: 91.189.88.33 80]


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/saucy/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.33 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.
roland@steelers:~$ 



```
[COLOR=#000000]
Roland
[/COLOR]

---

### Post by dino99 on 2013-04-27
Testers here know and trust the main server. Why that dl.google.com ?

---

### Post by roly33 on 2013-04-27
> **dino99 said:**
> Testers here know and trust the main server. Why that dl.google.com ?

Ether Google Chrome or Play Music Manager.

Roland

---

