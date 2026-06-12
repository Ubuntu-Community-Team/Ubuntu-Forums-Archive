---
title: "Unable to update Intrepid"
date: 2008-11-04
forum: Security
---

### Post by hornetster on 2008-11-04
Have upgraded to the release version of x86 Intrepid, and all is basically working fairly well, except for the Update Manager. I 'think' it did a small update immediately after installation (I did a fresh install), but since then, whenever I try and check for updates, I get:

[I]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.[/I]

or similar... I initially posted in the Installation and Upgrades forum, ([http://ubuntuforums.org/showthread.php?t=964894](http://ubuntuforums.org/showthread.php?t=964894)) but unable to get a resolution there.
Yes, I have done all the basic stuff like trying different servers, including the main server and others in Oz etc, etc.
I think I need to basically do a 'fresh install' of the update server stuff, but what components do I need and how do I get rid of the current (possibly corrupted) configuration. I have installed Intrepid in a VMware box, and it has updated many programs...
Thanks for all help!

---

### Post by prshah on 2008-11-04
> **hornetster said:**
> 
]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.

Before anything else, update the index files; open a terminal (Applications-Accessories-Terminal) and give the command```
sudo apt-get update
``` Wait for it to complete; you may have to run it twice if you get any errors. If the errors persist even after running it twice, post back the error messages. It will also be better if you change to the main server software source before running this.

---

### Post by hornetster on 2008-11-04
Thanks for the reply, prshah.
Have tried running several times, with the following results (2 runs):
[I]john@boss:~$ sudo apt-get update
[sudo] password for john: 
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028.2) intrepid/main Translation-en_AU
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028.2) intrepid/restricted Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_AU               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_AU          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_AU        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_AU   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_AU     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_AU  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_AU       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_AU
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release [65.9kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                           
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages [4542kB]            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages             
Fetched 4608kB in 3min17s (23.3kB/s)
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
john@boss:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028.2) intrepid/main Translation-en_AU
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028.2) intrepid/restricted Translation-en_AU
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg [189B]                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_AU             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_AU           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_AU                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg                                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_AU   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_AU      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_AU
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release [65.9kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_AU    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages                                                                                                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages                                                                                                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages                                                                                                                                            
Fetched 190B in 7s (27B/s)                                                                                                                                                                                    
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems[/I]

Keep getting the same error when it runs...
Main server is set to "Main Server"

If I set the server to the Australian one I get:
[I]john@boss:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028.2) intrepid/main Translation-en_AU
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028.2) intrepid/restricted Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid Release.gpg                                       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid/main Translation-en_AU            
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid/universe Translation-en_AU          
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid/restricted Translation-en_AU        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-updates Release.gpg                 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-updates/universe Translation-en_AU  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-updates/main Translation-en_AU      
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-updates/restricted Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-updates Release                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid/main Packages                       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid/universe Packages                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid/restricted Packages                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-updates/universe Packages           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-updates/main Packages               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-updates/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Reading package lists... Done[/I]

but still get no updates....? (and still get lots of "failed"s as when checking for updates...
   John.

---

### Post by cdenley on 2008-11-04
So the main repo had a bad key, but what was the problem with the Australian repo? I don't see any errors or "failed" in the output you posted. It looks to me like your package index files were updated.

---

### Post by mpoconnor2 on 2008-11-04
All, I am having similar upgrade failure problems going from 8.04 to 8.10.
Eacg upgrade attempt fails with an error message similar to this:

W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  Unable to find expected entry  mulriverse/binary-i386/Packages in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

I tried the above suggestions:

coachmickey@coachmickey-desktop:~$ sudo apt-get update
sudo: unable to resolve host coachmickey-desktop
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US          
Hit [http://dl.google.com](http://dl.google.com) stable Release                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                  
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/mulriverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg                   
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Translation-en_US        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Sources                  
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Sources              
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Packages
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  mulriverse/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas for the next step to a successful upgrade? I really don't want to do a clean install...
Thanks!

---

### Post by MJWitter on 2008-11-04
To OP:  Try the following(worked for a few others and myself):
```
sudo apt-get update -o Acquire::http::No-Cache=true 
```

Not sure about mpoconnor2's problem, it looks to me like a seperate issue.

---

### Post by hornetster on 2008-11-05
Good stuff! Looks like that fixed it...
Actually, I'm sure I ran that (on somebody elses suggestion...) a few days ago, but maybe there was a problem with the sources at the time as well...
Who knows, anyway, hopefully it's fixed!

Thanks a heap,
    John.

---

