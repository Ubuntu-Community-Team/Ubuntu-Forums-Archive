---
title: "important security updates grayed out"
date: 2011-04-05
forum: Security
---

### Post by 55tptag on 2011-04-05
Hello,

I saw the that "Update Manager" had updates but they were grayed out.  See picture.  

Why are they grayed out?

My PC:
```
$ uname -a
Linux xps 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011 x86_64 GNU/Linux

```

Thank you.

Updated: 4/6/11 Problem resolved itself

---

### Post by sanguinoso on 2011-04-05
Can you run from a terminal (Applications -> Accessories -> Terminal) ```
sudo apt-get update
``` Then run ```
sudo apt-get upgrade
``` And please post the output from the second command here.

---

### Post by TiloBunt on 2011-04-06
same with me,

last cmd:
```

tilo@t-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ffmpeg libavdevice52 libavfilter0 libavformat52 libpostproc51 libswscale0
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
tilo@t-laptop:~$
```

both cmd:
```

tilo@t-laptop:~$ sudo apt-get update
[sudo] password for tilo: 
Hit http://download.virtualbox.org lucid Release.gpg
Hit http://linux.dropbox.com lucid Release.gpg                                 
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_CA              
Ign http://download.virtualbox.org/virtualbox/debian/ lucid/non-free Translation-en_CA
Hit http://linux.dropbox.com lucid Release                                     
Hit http://download.virtualbox.org lucid Release                               
Hit http://linux.dropbox.com lucid/main Packages                               
Hit http://ca.archive.ubuntu.com lucid Release.gpg                             
Hit http://ca.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_CA          
Hit http://ca.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_CA    
Hit http://badgerports.org lucid Release.gpg                                   
Get:1 http://dl.google.com stable Release.gpg [197B]                           
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_CA       
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_CA   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_CA
Hit http://download.virtualbox.org lucid/non-free Packages                     
Hit http://packages.medibuntu.org lucid Release.gpg                            
Hit http://deb.torproject.org lucid Release.gpg                                
Ign http://deb.torproject.org/torproject.org/ lucid/main Translation-en_CA     
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/ lucid/main Translation-en_CA
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Hit http://ca.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_CA      
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_CA    
Hit http://ca.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_CA  
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_CA
Hit http://archive.canonical.com lucid Release                                 
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_CA
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://ca.archive.ubuntu.com lucid Release                                 
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_CA   
Ign http://ppa.launchpad.net/gnome-media-player-development/development/ubuntu/ lucid/main Translation-en_CA
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/ lucid/main Translation-en_CA
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ lucid/main Translation-en_CA
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/pkg-games/ppa/ubuntu/ lucid/main Translation-en_CA
Hit http://deb.torproject.org lucid Release                                    
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Hit http://archive.canonical.com lucid/partner Packages                        
Ign http://badgerports.org/ lucid/main Translation-en_CA                       
Hit http://ca.archive.ubuntu.com lucid-updates Release                         
Hit http://security.ubuntu.com lucid-security/main Packages                    
Ign http://packages.medibuntu.org/ lucid/free Translation-en_CA                
Ign http://ppa.launchpad.net/sevenmachines/flash/ubuntu/ lucid/main Translation-en_CA
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_CA
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Ign http://deb.torproject.org lucid/main Packages                              
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ca.archive.ubuntu.com lucid/main Packages                           
Hit http://ca.archive.ubuntu.com lucid/restricted Packages                     
Hit http://ca.archive.ubuntu.com lucid/main Sources                            
Hit http://ca.archive.ubuntu.com lucid/restricted Sources                      
Hit http://ca.archive.ubuntu.com lucid/universe Packages                       
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/main Sources                     
Hit http://security.ubuntu.com lucid-security/restricted Sources               
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://security.ubuntu.com lucid-security/universe Sources                 
Hit http://security.ubuntu.com lucid-security/multiverse Packages              
Hit http://ppa.launchpad.net lucid Release                                     
Get:2 http://dl.google.com stable Release [1,347B]                             
Ign http://deb.torproject.org lucid/main Packages                              
Hit http://ca.archive.ubuntu.com lucid/universe Sources                        
Hit http://ca.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://badgerports.org lucid Release                                       
Hit http://ca.archive.ubuntu.com lucid/multiverse Sources                      
Hit http://ca.archive.ubuntu.com lucid-updates/main Packages                   
Hit http://ca.archive.ubuntu.com lucid-updates/restricted Packages             
Hit http://ca.archive.ubuntu.com lucid-updates/main Sources                    
Hit http://ca.archive.ubuntu.com lucid-updates/restricted Sources              
Hit http://ca.archive.ubuntu.com lucid-updates/universe Packages               
Hit http://security.ubuntu.com lucid-security/multiverse Sources               
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_CA            
Hit http://deb.torproject.org lucid/main Packages                              
Hit http://ca.archive.ubuntu.com lucid-updates/universe Sources                
Hit http://ca.archive.ubuntu.com lucid-updates/multiverse Packages             
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ca.archive.ubuntu.com lucid-updates/multiverse Sources              
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://badgerports.org lucid/main Packages                                 
Hit http://packages.medibuntu.org lucid Release                                
Hit http://ppa.launchpad.net lucid/main Packages                        
Hit http://packages.medibuntu.org lucid/free Packages                          
Get:3 http://dl.google.com stable/main Packages [761B]
Hit http://packages.medibuntu.org lucid/non-free Packages                      
Fetched 2,305B in 2s (1,053B/s)                           
Reading package lists... Done
tilo@t-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ffmpeg libavdevice52 libavfilter0 libavformat52 libpostproc51 libswscale0
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
tilo@t-laptop:~$ 

```

---

### Post by cariboo on 2011-04-06
I'd suggest using synaptic to install the updates, as it will tell you why a package can't be installed.

---

### Post by TiloBunt on 2011-04-07
solved, as it just worked today =)

---

### Post by sanguinoso on 2011-04-08
This could be the reason as to why this occurs: 
[http://www.debian-administration.org/articles/69](http://www.debian-administration.org/articles/69)

In any case its not a security problem with ubuntu. As you can force the update to those packages it just won't do it automatically if it has to install new packages to satisfy dependencies.

---

