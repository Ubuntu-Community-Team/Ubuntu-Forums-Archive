---
title: "Duplicate Repositories"
date: 2007-01-06
forum: Repositories &amp; Backports
---

### Post by benjjo on 2007-01-06
Can anyone point me in  the right direction? Why do i get this 
> W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_edgy-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_edgy-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_edgy-updates_multiverse_binary-i386_Packages)
And this
> [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.bz2:) Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages - open (2 No such file or directory)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
Here's my source list
> deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse

## Bleeding edge wine repository for Dapper
## only uncomment it if you need it
##deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
##deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

## skype
## only uncomment it if you need it
##deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free


And here's what i get when i apt-get update
> benjo@laptop:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main Translation-en_AU
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restricted Translation-en_AU               
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates Release.gpg [191B]                                                                 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/main Translation-en_AU                                                                             
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/restricted Translation-en_AU                                                                                  
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                                                                                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_AU                                                                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_AU                                       
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/universe Translation-en_AU                              
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_AU                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_AU                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_AU                                       
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_AU                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_AU
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_AU  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/multiverse Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_AU                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_AU                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_AU                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_AU                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_AU       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_AU         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_AU       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_AU         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_AU       
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/main Translation-en_AU            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_AU       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_AU                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                                                  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/restricted Translation-en_AU                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                                                      
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/universe Translation-en_AU                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages               
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/multiverse Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                                       
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [20.2kB]                             
Get:7 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy Release.gpg [191B]                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources                                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources                                                      
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Translation-en_AU                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages                                              
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages [2223B]                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages            
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [20.2kB]   
90% [Waiting for headers] [9 Packages 2869/20.2kB 14%] [Waiting for headers]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages              
  Sub-process bzip2 returned an error code (2)
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates Release                                            
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages [2223B]                                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources                                 
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [20.2kB]                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources                                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy Release                                                        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/main Packages                                                                                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/restricted Packages                                                                                           
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages [2223B]                                                                                 
99% [Connecting to au.archive.ubuntu.com (211.29.132.173)]                                                                                       33.4kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                                                                                              
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages - open (2 No such file or directory)
99% [Connecting to au.archive.ubuntu.com (211.29.132.173)]                                                                                       33.4kB/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                                                                                            
  Sub-process bzip2 returned an error code (2)
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/universe Packages                                                                                             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/multiverse Packages                                                                                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/main Packages                                                                                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/restricted Packages                                                                                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/universe Packages                                                                                             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/multiverse Packages                                                                                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Packages                                                                                                     
Fetched 65.1kB in 7s (9100B/s)                                                                                                                              
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.bz2)  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages - open (2 No such file or directory)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_edgy-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_edgy-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_edgy-updates_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
I'm quite lost, any help???

---

### Post by Koybe on 2007-01-07
Could you post this :

```
 ls -l /etc/apt
ls -l /etc/apt/sources.list.d
grep -r au.archive.ubuntu.com /etc/apt
```And you can also try 

```
 sudo apt-get clean
sudo apt-get check
```

and see if it helps.

---

### Post by benjjo on 2007-01-08
Sorry for the late reply, guess we're on a different time zone...
Anyway thanx for your interest and here's what you requested:

> benjo@laptop:~$ ls -l /etc/apt
total 52
-rw-r--r-- 1 root root   30 2006-12-18 07:31 apt.conf
drwxr-xr-x 2 root root 4096 2007-01-07 14:36 apt.conf.d
-rw------- 1 root root    0 2006-08-06 09:20 secring.gpg
-rw-r--r-- 1 root root 2160 2007-01-07 13:49 sources.list
-rw-r--r-- 1 root root 2074 2007-01-07 13:49 sources.list~
-rw-r--r-- 1 root root 1933 2006-12-21 15:18 sources.list_backup
drwxr-xr-x 2 root root 4096 2007-01-07 15:18 sources.list.d
-rw-r--r-- 1 root root 2098 2007-01-07 13:49 sources.list.distUpgrade
-rw-r--r-- 1 root root 2252 2007-01-05 18:40 sources.list.save
-rw------- 1 root root 1200 2006-12-19 16:46 trustdb.gpg
-rw-r--r-- 1 root root 4122 2006-12-19 16:46 trusted.gpg
-rw-r--r-- 1 root root 4122 2006-12-19 16:46 trusted.gpg~
and:
> benjo@laptop:~$ ls -l /etc/apt/sources.list.d
total 40
-rw-r--r-- 1 root root 183 2007-01-07 13:49 dapper-commercial.list
-rw-r--r-- 1 root root 181 2007-01-07 13:49 dapper-commercial.list.distUpgrade
-rw-r--r-- 1 root root 181 2007-01-05 18:40 dapper-commercial.list.save
-rw-r--r-- 1 root root 251 2007-01-07 13:49 dapper-multiverse.list
-rw-r--r-- 1 root root 255 2007-01-07 13:49 dapper-multiverse.list.distUpgrade
-rw-r--r-- 1 root root 255 2007-01-05 18:40 dapper-multiverse.list.save
-rw-r--r-- 1 root root 251 2007-01-07 13:49 dapper-universe.list
-rw-r--r-- 1 root root 255 2007-01-07 13:49 dapper-universe.list.distUpgrade
-rw-r--r-- 1 root root 255 2007-01-05 18:40 dapper-universe.list.save
-rw-r--r-- 1 root root 128 2007-01-07 15:18 edgy-universe.list
And:
> benjo@laptop:~$ sudo grep -r au.archive.ubuntu.com /etc/apt
/etc/apt/sources.list.d/dapper-multiverse.list:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
/etc/apt/sources.list.d/dapper-universe.list:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
/etc/apt/sources.list.d/dapper-multiverse.list.save:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
/etc/apt/sources.list.d/dapper-universe.list.save:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
/etc/apt/sources.list.d/dapper-multiverse.list.distUpgrade:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
/etc/apt/sources.list.d/dapper-universe.list.distUpgrade:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
/etc/apt/sources.list.d/edgy-universe.list:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
/etc/apt/sources.list_backup:deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
/etc/apt/sources.list_backup:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
/etc/apt/sources.list_backup:deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
/etc/apt/sources.list_backup:deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper universe multiverse
/etc/apt/sources.list_backup:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
/etc/apt/sources.list_backup:deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

And i tried " sudo apt-get clean, sudo apt-get check" before i posted your requests.
Is it the BACKUP that's causing the difficulties? I really don't understand this whole repository concept.

---

### Post by Koybe on 2007-01-08
Yes we're in different time zone ;-) It's gonna be harder.

As I see it looks like a mess. You got source both from dapper and edgy. Are you sure this is ok? It seems not to me.

Make a backup of the files in /etc/apt/sources.list.d then remove them all.

```
tar zvcf ~/sources.tar.gz /etc/apt/sources.list.d/*
sudo rm /etc/apt/sources.list.d/*
sudo apt-get update

```If it works try to upgrade to see if everything runs fine
```
sudo apt-get upgrade
```

---

### Post by benjjo on 2007-01-08
> As I see it looks like a mess. You got source both from dapper and edgy. Are you sure this is ok? It seems not to me.
Let me assure you that i am positive that I have NO IDEA.

But on the plus side, I think i'm getting somewhere now. 
I don't seem to be getting any errors now when i apt-get update so i think this is a good sign.
I will post everything here if you could be so kind as to double check things.
**ls -l /etc/apt**
```
total 48
-rw-r--r-- 1 root root   30 2006-12-18 07:31 apt.conf
drwxr-xr-x 2 root root 4096 2007-01-07 14:36 apt.conf.d
-rw------- 1 root root    0 2006-08-06 09:20 secring.gpg
-rw-r--r-- 1 root root 1436 2007-01-09 14:05 sources.list
-rw-r--r-- 1 root root  200 2007-01-09 13:08 sources.list~
-rw-r--r-- 1 root root 2161 2007-01-09 13:03 sources.list_backup
drwxr-xr-x 2 root root 4096 2007-01-09 13:02 sources.list.d
-rw-r--r-- 1 root root  194 2007-01-09 13:08 sources.list.save
-rw------- 1 root root 1200 2006-12-19 16:46 trustdb.gpg
-rw-r--r-- 1 root root 4122 2006-12-19 16:46 trusted.gpg
-rw-r--r-- 1 root root 4122 2006-12-19 16:46 trusted.gpg~
```
**ls -l /etc/apt/sources.list.d**
```
total 0
```
**grep -r au.archive.ubuntu.com /etc/apt**
```

/etc/apt/sources.list~:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
/etc/apt/sources.list~:deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted #Added by software-properties

```
**Sources.list**
```

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse




```


Thank you so very much for giving me your time. One truly thankful nerd way down here.

---

### Post by Koybe on 2007-01-09
Nice to see this is helping you.

Everything looks ok for me now. Maybe you can change your /etc/apt/sources.list (and not /etc/apt/sources.list~) to match your country. The goal is to dowload from a mirror near you.

archive.ubuntu.com is the general repo. And you can change all in your sources.list by au.archive.ubuntu.com.
Copy it before.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.working
```

**/etc/apt/sources.list**
```

## Uncomment the following two lines to fetch updated software from the network
deb [http://au.archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") edgy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://au.archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") edgy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") edgy universe
deb-src [http://au.archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") edgy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://au.archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") edgy multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") edgy multiverse
deb [http://au.archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") edgy-backports main restricted universe multiverse 
```

Then sudo apt-get update again to check if it is ok. If not go back to the one that is ok.

You can also try to sudo apt-get upgrade to be sure everything is up to date and working correctly.

---

### Post by benjjo on 2007-01-09
It's like this tremendous weight has lifted off my shoulders. I've been battling with this problem for weeks now. I've put the Australian repos in and they work like a charm. Thank you for your help, if your ever in Melbourne i will have to shout you a beer (although Australian beer may be a bit of an insult compared to the Belgium brew).
Cheers.

---

### Post by Koybe on 2007-01-09
Hehe I'll think about it ;-)

Have a nice day.

---

