---
title: "Update Manager reports &quot;last updated 12 days ago&quot;"
date: 2012-02-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by shamusl on 2012-02-11
Update manager since updates last night now reports "last updated 12 days ago" even though I just updated the system. I tried rechecking for updates but that didn't change it. As a result, a system notification keeps bugging me telling me some of my sources don't work and to check my Internet connection.

---

### Post by bluexrider on 2012-02-11
could you post the output of this please ```
sudo apt-get update
```

---

### Post by shamusl on 2012-02-11
> **bluexrider said:**
> could you post the output of this please ```
sudo apt-get update
```

```
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://us.archive.ubuntu.com precise InRelease                             
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Get:2 http://dl.google.com stable Release [1,349 B]                            
Ign http://security.ubuntu.com precise-security InRelease                      
Get:3 http://dl.google.com stable/main i386 Packages [645 B]                   
Hit http://extras.ubuntu.com precise Release.gpg                               
Ign http://ppa.launchpad.net precise Release.gpg                               
Ign http://us.archive.ubuntu.com precise-proposed InRelease                    
Get:4 http://us.archive.ubuntu.com precise Release.gpg [198 B]                 
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                   
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://extras.ubuntu.com precise Release                                   
Get:5 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://security.ubuntu.com precise-security Release                        
Hit http://extras.ubuntu.com precise/main Sources                              
Ign http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise-proposed Release.gpg                  
Get:6 http://us.archive.ubuntu.com precise Release [49.6 kB]                   
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise Release                                   
Ign http://ppa.launchpad.net precise Release                                   
Hit http://security.ubuntu.com precise-security/main Sources                   
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://security.ubuntu.com precise-security/restricted Sources             
Hit http://security.ubuntu.com precise-security/universe Sources               
Hit http://security.ubuntu.com precise-security/multiverse Sources             
Hit http://security.ubuntu.com precise-security/main i386 Packages             
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex                    
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex              
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://security.ubuntu.com precise-security/universe i386 Packages         
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://us.archive.ubuntu.com precise-updates Release                       
Hit http://us.archive.ubuntu.com precise-backports Release                     
Hit http://us.archive.ubuntu.com precise-proposed Release                      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Get:7 http://us.archive.ubuntu.com precise/main Sources [921 kB]               
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Err http://ppa.launchpad.net precise/main Sources                              
  404  Not Found
Ign http://extras.ubuntu.com precise/main Translation-en                     
Err http://ppa.launchpad.net precise/main i386 Packages                      
  404  Not Found
Ign http://ppa.launchpad.net precise/main Translation-en_US                  
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Get:8 http://us.archive.ubuntu.com precise/restricted Sources [5,134 B]        
Get:9 http://us.archive.ubuntu.com precise/universe Sources [5,011 kB]         
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:10 http://us.archive.ubuntu.com precise/multiverse Sources [159 kB]        
Get:11 http://us.archive.ubuntu.com precise/main i386 Packages [1,292 kB]     
Get:12 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,304 B]
Get:13 http://us.archive.ubuntu.com precise/universe i386 Packages [4,782 kB]
Ign http://dl.google.com stable/main Translation-en_US                       
Ign http://dl.google.com stable/main Translation-en                          
Get:14 http://us.archive.ubuntu.com precise/multiverse i386 Packages [125 kB]
Get:15 http://us.archive.ubuntu.com precise/main TranslationIndex [3,570 B]
Get:16 http://us.archive.ubuntu.com precise/multiverse TranslationIndex [2,540 B]
Get:17 http://us.archive.ubuntu.com precise/restricted TranslationIndex [2,464 B]
Get:18 http://us.archive.ubuntu.com precise/universe TranslationIndex [2,784 B]
Hit http://us.archive.ubuntu.com precise-updates/main Sources    
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources
Hit http://us.archive.ubuntu.com precise-updates/universe Sources
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise-proposed/restricted i386 Packages     
Hit http://us.archive.ubuntu.com precise-proposed/main i386 Packages           
Hit http://us.archive.ubuntu.com precise-proposed/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com precise-proposed/universe i386 Packages       
Hit http://us.archive.ubuntu.com precise-proposed/main TranslationIndex        
Hit http://us.archive.ubuntu.com precise-proposed/multiverse TranslationIndex  
Hit http://us.archive.ubuntu.com precise-proposed/restricted TranslationIndex  
Hit http://us.archive.ubuntu.com precise-proposed/universe TranslationIndex    
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Hit http://us.archive.ubuntu.com precise-proposed/main Translation-en          
Hit http://us.archive.ubuntu.com precise-proposed/multiverse Translation-en    
Hit http://us.archive.ubuntu.com precise-proposed/restricted Translation-en    
Hit http://us.archive.ubuntu.com precise-proposed/universe Translation-en      
Fetched 12.4 MB in 9s (1,373 kB/s)                                             
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E9205C51236960C
W: Failed to fetch http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by savanna on 2012-02-11
Then try "sudo aptitude safe-upgrade".

---

### Post by shamusl on 2012-02-11
> **savanna said:**
> Then try "sudo aptitude safe-upgrade".

Command not found.

---

### Post by bluexrider on 2012-02-11
The repository for 
[http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/precise/main/source/Sources)

DOES NOT EXIST 
it is a oneiric repository and has no listing for precise.

That is why you are getting the errors
W: Failed to fetch [http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/precise/main/source/Sources)  404  Not Found  
W: Failed to fetch [http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

You can edit the software sources and un-check the repository or edit it by hand.

For the GPG error 
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E9205C51236960C
```

Then ```
sudo apt-get update
```

---

### Post by cariboo on 2012-02-11
If you read the output you quoted, the errors you are getting are for ppa's, I suggest you remove them, and try again. 

One suggestion I'd make is to install both aptitude and synaptic, as they are both valuable tools, that help quite a bit during the times when a development release breaks like this.

---

### Post by shamusl on 2012-02-11
> **bluexrider said:**
> The repository for 
[http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/precise/main/source/Sources)

DOES NOT EXIST 
it is a oneiric repository and has no listing for precise.

That is why you are getting the errors
W: Failed to fetch [http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/precise/main/source/Sources)  404  Not Found  
W: Failed to fetch [http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

You can edit the software sources and un-check the repository or edit it by hand.

For the GPG error 
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E9205C51236960C
```

Then ```
sudo apt-get update
```

I understand that, that has been an issue for my system since I installed Precise, however that wasn't the bug I was reporting. Update Manager still reports 12 days since last update, even with those removed.

---

### Post by cariboo on 2012-02-11
Update-manager has always been a source of problems during a development release. If you manually update and upgrade, do you still get the notification?

I personally disable update-manager every time I do a fresh install, as I've never liked it.

---

### Post by shamusl on 2012-02-11
Manually updating through the Terminal stops the notifications but the update manager is still off. No big deal I guess.

---

### Post by grahammechanical on 2012-02-12
Over the weeks I have seen a few updates to either Synaptic, Software Centre or Update manager. In fact, a few days ago an update removed Software Centre. I have just checked what packages are due to be downloaded today and I think that afterwards I might be able to re-install Software Centre.

My point is that it seems that a lot of work is taking place regarding the updating/installing part of the 12.04 distribution. So, as long as we have an alternative means of updating that works. Then these issues are no big deal for me.

Regards.

---

