---
title: "Unable to install Clam AV in Ubunt 15.10"
date: 2016-03-02
forum: Security
---

### Post by danny_king on 2016-03-02
Hi All,

I recently installed Ubuntu 14.04 and then upgraded to 15.10. I am trying to install Clam AV but I am getting the below message in the terminal:

dannyking@Toshiba-L650:~$ sudo apt-get install clamav
[sudo] password for dannyking: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 clamav : Depends: clamav-freshclam (>= 0.98.7+dfsg) but it is not going to be installed or
                   clamav-data
          Depends: libclamav6 (>= 0.98.5~rc1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
dannyking@Toshiba-L650:~$ 

What needs to be done to fix the above?

---

### Post by oldos2er on 2016-03-02
Please post output of ```
cat /etc/apt/sources.list

ll /etc/apt/sources.list.d/
```

---

### Post by danny_king on 2016-03-03
> **oldos2er said:**
> Please post output of ```
cat /etc/apt/sources.list

ll /etc/apt/sources.list.d/
```

Here is the output from the terminal after inputting the command:

dannyking@Toshiba-L650:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main universe restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security main universe restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main universe restricted

dannyking@Toshiba-L650:~$ ll /etc/apt/sources.list.d/
total 16
drwxr-xr-x 2 root root 4096 Mar  1 17:08 ./
drwxr-xr-x 6 root root 4096 Mar  1 14:11 ../
-rw-r--r-- 1 root root  192 Mar  2 13:06 linrunner-ubuntu-tlp-wily.list
-rw-r--r-- 1 root root  126 Mar  2 13:06 linrunner-ubuntu-tlp-wily.list.save

---

### Post by oldos2er on 2016-03-03
You have both wily and trusty sources in your sources.list file, which is most likely causing the problem. Remove the trusty sources, run ```
sudo apt-get update
``` and retry the clamav install. If there are still errors, please post them.

---

### Post by danny_king on 2016-03-04
> **oldos2er said:**
> You have both wily and trusty sources in your sources.list file, which is most likely causing the problem. Remove the trusty sources, run ```
sudo apt-get update
``` and retry the clamav install. If there are still errors, please post them.

Is there a code for removing the trusty updates? 
I used the command for updating and then tried to install clam. I am still getting the original error message. Please see below:

dannyking@Toshiba-L650:~$ sudo apt-get update
[sudo] password for dannyking: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily InRelease                                   
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates InRelease [65.9 kB]               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                          
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-security InRelease [65.9 kB]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                                 
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease [65.9 kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [65.9 kB]           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/main Sources                                
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [430 kB]  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/universe Sources                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/main amd64 Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/universe amd64 Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/main i386 Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/universe i386 Packages                      
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [124 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/main Translation-en                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/universe Translation-en                     
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/main Sources [65.6 kB]            
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [13.0 kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [403 kB]   
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/universe Sources [19.1 kB]       
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/main amd64 Packages [188 kB]     
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [124 kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [235 kB] 
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [3,206 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [72.9 kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/universe amd64 Packages [82.9 kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/main i386 Packages [184 kB]      
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/universe i386 Packages [80.4 kB] 
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/main Translation-en [84.8 kB]    
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/universe Translation-en [48.6 kB]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-security/main Sources [39.0 kB]          
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-security/universe Sources [8,955 B]      
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-security/main amd64 Packages [127 kB]    
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-security/universe amd64 Packages [45.3 kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-security/main i386 Packages [125 kB]     
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-security/universe i386 Packages [45.2 kB]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-security/main Translation-en [61.5 kB]   
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-security/universe Translation-en [30.4 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg                               
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main amd64 Packages [712 kB]   
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe amd64 Packages [339 kB]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted amd64 Packages [15.9 kB]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [692 kB]    
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages [339 kB]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.6 kB]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en [360 kB]   
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en [3,699 B]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en [180 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main amd64 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe amd64 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_US                
Fetched 5,576 kB in 1min 36s (57.6 kB/s)                                       
Reading package lists... Done
dannyking@Toshiba-L650:~$ sudo apt-get install clamav
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 clamav : Depends: clamav-freshclam (>= 0.98.7+dfsg) but it is not going to be installed or
                   clamav-data
          Depends: libclamav6 (>= 0.98.5~rc1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
dannyking@Toshiba-L650:~$

---

### Post by oldos2er on 2016-03-04
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

sudo nano /etc/apt/sources.list
``` Add a hash mark # at the beginning of each line referencing trusty. Or if you're feeling confident, simply delete those lines. Then ```
sudo apt-get update
```

---

### Post by danny_king on 2016-03-04
> **oldos2er said:**
> ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

sudo nano /etc/apt/sources.list
``` Add a hash mark # at the beginning of each line referencing trusty. Or if you're feeling confident, simply delete those lines. Then ```
sudo apt-get update
```

Tried the instructions you mentioned, but still getting the same error:

The following packages have unmet dependencies:
 clamav : Depends: clamav-freshclam (>= 0.98.7+dfsg) but it is not going to be installed or
                   clamav-data
          Depends: libclamav6 (>= 0.98.5~rc1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
dannyking@Toshiba-L650:~$

---

### Post by oldos2er on 2016-03-05
Try ```
sudo apt-get install -f
```

---

### Post by danny_king on 2016-03-10
I did a fresh install. Right from the scratch. Installed clam as well. :)

---

