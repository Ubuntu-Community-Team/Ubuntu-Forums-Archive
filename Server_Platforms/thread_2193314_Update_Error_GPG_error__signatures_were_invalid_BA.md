---
title: "Update Error: GPG error:  signatures were invalid: BADSIG 40976EAF437D05B5"
date: 2013-12-12
forum: Server Platforms
---

### Post by upendrasahu20 on 2013-12-12
Hi 
I am Getting this error on freshly installed Ubuntu 12.04 LTS server

Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources                                                                                                                                  
  404  Not Found [IP: 91.189.92.200 80]
100% [286 Translation-en gzip 3595 kB]W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Its a open Network, No proxy is required.
I tried few solutions from other thread as well but issue is still there
I tried: 

"[FONT=Ubuntu Mono]sudo apt-get clean[/FONT]
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean [FONT=Ubuntu Mono]sudo apt-get update[/FONT]"

also tried:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5



even tried:

"[COLOR=#333333][FONT=Ubuntu]sudo fuser -vvv /var/lib/dpkg/lock[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]sudo rm /var/lib/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]apt/lists/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]lock[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]sudo cp -arf /var/lib/dpkg /var/lib/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]dpkg.backup[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]sudo cp /var/lib/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]dpkg/status-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]old /var/lib/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]dpkg/status[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]sudo cp /var/lib/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]dpkg/available-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]old /var/lib/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]dpkg/available[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]sudo rm -rf /var/lib/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]dpkg/updates/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]*[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]sudo rm -rf /var/lib/apt/lists[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]sudo rm /var/cache/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]apt/*.bin[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]sudo mkdir /var/lib/apt/lists[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]sudo mkdir /var/lib/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]apt/lists/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]partial[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]LANG=C;sudo apt-get clean[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]LANG=C;sudo apt-get autoclean[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]LANG=C;sudo apt-get --purge autoremove[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]LANG=C;sudo apt-get update -o APT::Cache-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Limit=25165824[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]sudo dpkg --clear-avail[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]sudo dpkg --configure -a[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]LANG=C;sudo apt-get -f install[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]LANG=C;sudo apt-get --fix-missing install[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]LANG=C;sudo apt-get update -o APT::Cache-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Limit=25165824 && sudo apt-get dist-upgrade[/FONT][/COLOR]"

but same issue.

complete apt-get update o/p:
$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release.gpg [198 B]             
Get:3 [http://ubuntu-cloud.archive.canonical.com](http://ubuntu-cloud.archive.canonical.com) precise-updates/grizzly Release.gpg [543 B]
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release.gpg [198 B]      
Get:5 [http://ubuntu-cloud.archive.canonical.com](http://ubuntu-cloud.archive.canonical.com) precise-updates/grizzly Release [5515 B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]      
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release.gpg [198 B]    
Get:8 [http://ubuntu-cloud.archive.canonical.com](http://ubuntu-cloud.archive.canonical.com) precise-updates/grizzly/main i386 Packages [49.7 kB]     
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release [49.6 kB]                                
Ign [http://ubuntu-cloud.archive.canonical.com](http://ubuntu-cloud.archive.canonical.com) precise-updates/grizzly/main TranslationIndex
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [93.9 kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2494 B]               
100% [11 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers] [Waiting for headers]      
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [30.0 kB]                
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1792 B]               
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [367 kB]               
Ign [http://ubuntu-cloud.archive.canonical.com](http://ubuntu-cloud.archive.canonical.com) precise-updates/grizzly/main Translation-en
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release [49.6 kB]        
Get:16 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:17 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:18 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:19 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:20 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:21 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:22 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:23 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:24 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:25 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:26 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:27 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:28 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:29 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:30 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:31 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:32 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:33 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:34 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:35 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:36 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:37 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:38 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:39 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:40 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:41 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [367 kB]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release                         
100% [41 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers]    
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


Get:42 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Sources [934 kB]       
Get:43 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4620 B]                                                                                                         
Get:44 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [89.6 kB]                                                                                                          
Get:45 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Sources [934 kB]                                                                                                                            
Get:46 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Sources [934 kB]                                                                                                                            
Get:47 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2642 B]                                                                                                         
99% [47 Packages bzip2 0 B] [46 Sources 910 kB/934 kB 97%]                                                                                                                        124 kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


Get:48 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]                                                                                                              
Get:49 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Sources [934 kB]                                                                                                                            
Get:50 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Sources [934 kB]                                                                                                                            
Get:51 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Sources [934 kB]                                                                                                                            
Get:52 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Sources [934 kB]                                                                                                                            
Get:53 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Sources [934 kB]                                                                                                                            
Get:54 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Sources [934 kB]                                                                                                                            
Get:55 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Sources [934 kB]                                                                                                                            
Get:56 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [72 B]                                                                                                        
Get:57 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Sources [934 kB]                                                                                                                            
Get:58 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]                                                                                                        
Get:59 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources [5470 B]                                                                                                                      
100% [57 Sources bzip2 0 B] [59 Sources 536 B/5470 B 10%] [Waiting for headers]                                                                                                   124 kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


Get:60 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]                                                                                                          
Get:61 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources [5470 B]                                                                                                                      
Get:62 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources [5470 B]                                                                                                                      
Get:63 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources [5470 B]                                                                                                                      
Get:64 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources [5470 B]                                                                                                                      
Get:65 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources [5470 B]                                                                                                                      
Get:66 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources [5470 B]                                                                                                                      
Get:67 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources [5470 B]                                                                                                                      
Get:68 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources [5470 B]                                                                                                                      
Get:69 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources [5470 B]                                                                                                                      
Get:70 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources [5470 B]                                                                                                                      
100% [70 Sources bzip2 0 B] [Waiting for headers] [11 Sources bzip2 551 B]                                                                                                        124 kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


Get:71 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe Sources [5019 kB]                                                                                                                       
Get:72 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe Sources [5019 kB]                                                                                                                       
Get:73 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Sources [155 kB]                                                                                                                      
Get:74 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main i386 Packages [1274 kB]                                                                                                                     
Get:75 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main i386 Packages [1274 kB]                                                                                                                     
Get:76 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages [8431 B]                                                                                                                
Get:77 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages [8431 B]                                                                                                                
Get:78 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages [8431 B]                                                                                                                
Get:79 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages [8431 B]                                                                                                                
Get:80 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages [8431 B]                                                                                                                
Get:81 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages [8431 B]                                                                                                                
Get:82 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages [8431 B]                                                                                                                
Get:83 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages [8431 B]                                                                                                                
Get:84 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages [8431 B]                                                                                                                
Get:85 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages [8431 B]                                                                                                                
Get:86 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages [8431 B]                                                                                                                
Get:87 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages [8431 B]                                                                                                                
Get:88 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages [8431 B]                                                                                                                
Get:89 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages [8431 B]                                                                                                                
Get:90 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages [8431 B]                                                                                                                
Get:91 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages [8431 B]                                                                                                                
Get:92 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe i386 Packages [4796 kB]                                                                                                                 
74% [72 Sources bzip2 0 B] [92 Packages 1468 kB/4796 kB 31%]                                                                                                                      979 kB/s 3s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


100% [75 Packages bzip2 0 B] [92 Packages 4757 kB/4796 kB 99%]                                                                                                                    979 kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


100% [91 Packages bzip2 0 B] [92 Packages 4757 kB/4796 kB 99%]                                                                                                                    979 kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


Get:93 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe i386 Packages [4796 kB]                                                                                                                 
Get:94 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe i386 Packages [4796 kB]                                                                                                                 
Get:95 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                                
Get:96 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                                
Get:97 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                                
Get:98 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                                
Get:99 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                                
Get:100 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:101 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:102 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:103 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:104 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:105 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:106 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:107 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:108 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:109 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:110 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:111 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:112 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:113 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:114 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:115 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:116 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:117 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:118 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:119 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:120 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:121 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:122 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:123 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:124 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:125 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:126 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                                               
Get:127 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main TranslationIndex [3706 B]                                                                                                                  
Get:128 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main TranslationIndex [3706 B]                                                                                                                  
Get:129 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main TranslationIndex [3706 B]                                                                                                                  
Get:130 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main TranslationIndex [3706 B]                                                                                                                  
Get:131 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main TranslationIndex [3706 B]                                                                                                                  
Get:132 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main TranslationIndex [3706 B]                                                                                                                  
Get:133 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main TranslationIndex [3706 B]                                                                                                                  
Get:134 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse TranslationIndex [2676 B]                                                                                                            
Get:135 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse TranslationIndex [2676 B]                                                                                                            
Get:136 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse TranslationIndex [2676 B]                                                                                                            
Get:137 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse TranslationIndex [2676 B]                                                                                                            
Get:138 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse TranslationIndex [2676 B]                                                                                                            
Get:139 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted TranslationIndex [2596 B]                                                                                                            
Get:140 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted TranslationIndex [2596 B]                                                                                                            
100% [94 Packages bzip2 0 B] [140 TranslationIndex 1071 B/2596 B 41%]                                                                                                            1027 kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


100% [126 Packages bzip2 0 B] [140 TranslationIndex 1071 B/2596 B 41%]                                                                                                           1027 kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


Get:141 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted TranslationIndex [2596 B]                                                                                                            
Get:142 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted TranslationIndex [2596 B]                                                                                                            
Get:143 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted TranslationIndex [2596 B]                                                                                                            
Get:144 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe TranslationIndex [2922 B]                                                                                                              
Get:145 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe TranslationIndex [2922 B]                                                                                                              
Get:146 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe TranslationIndex [2922 B]                                                                                                              
Get:147 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe TranslationIndex [2922 B]                                                                                                              
Get:148 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe TranslationIndex [2922 B]                                                                                                              
Get:149 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe TranslationIndex [2922 B]                                                                                                              
Get:150 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Sources [428 kB]                                                                                                                   
Get:151 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Sources [428 kB]                                                                                                                   
Get:152 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Sources [428 kB]                                                                                                                   
Get:153 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Sources [428 kB]                                                                                                                   
Get:154 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Sources [428 kB]                                                                                                                   
Get:155 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Sources [428 kB]                                                                                                                   
Get:156 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Sources [428 kB]                                                                                                                   
Get:157 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Sources [428 kB]                                                                                                                   
100% [157 Sources bzip2 0 B]                                                                                                                                                     19.8 kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


Get:158 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted Sources [7006 B]                                                                                                             
Get:159 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe Sources [101 kB]                                                                                                               
Get:160 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse Sources [8807 B]                                                                                                             
Get:161 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main i386 Packages [737 kB]                                                                                                             
Get:162 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB]                                                                                                      
Get:163 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe i386 Packages [229 kB]                                                                                                         
Get:164 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.4 kB]                                                                                                      
Get:165 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main TranslationIndex [3564 B]                                                                                                          
Get:166 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main TranslationIndex [3564 B]                                                                                                          
Get:167 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main TranslationIndex [3564 B]                                                                                                          
Get:168 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main TranslationIndex [3564 B]                                                                                                          
Get:169 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main TranslationIndex [3564 B]                                                                                                          
Get:170 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main TranslationIndex [3564 B]                                                                                                          
Get:171 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main TranslationIndex [3564 B]                                                                                                          
Get:172 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2605 B]                                                                                                    
Get:173 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2605 B]                                                                                                    
Get:174 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2605 B]                                                                                                    
Get:175 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2605 B]                                                                                                    
Get:176 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2605 B]                                                                                                    
Get:177 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2461 B]                                                                                                    
Get:178 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2461 B]                                                                                                    
Get:179 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2461 B]                                                                                                    
Get:180 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2461 B]                                                                                                    
Get:181 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2461 B]                                                                                                    
Get:182 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe TranslationIndex [2850 B]                                                                                                      
Get:183 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe TranslationIndex [2850 B]                                                                                                      
Get:184 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe TranslationIndex [2850 B]                                                                                                      
Get:185 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe TranslationIndex [2850 B]                                                                                                      
Get:186 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe TranslationIndex [2850 B]                                                                                                      
Get:187 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe TranslationIndex [2850 B]                                                                                                      
Get:188 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Sources [4225 B]                                                                                                                 
Get:189 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Sources [4225 B]                                                                                                                 
Get:190 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Sources [4225 B]                                                                                                                 
Get:191 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Sources [4225 B]                                                                                                                 
Get:192 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Sources [4225 B]                                                                                                                 
Get:193 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Sources [4225 B]                                                                                                                 
Get:194 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Sources [4225 B]                                                                                                                 
Get:195 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Sources [4225 B]                                                                                                                 
100% [195 Sources bzip2 0 B]                                                                                                                                                      181 kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


Get:196 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted Sources [14 B]                                                                                                             
Get:197 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources [36.4 kB]                                                                                                            
Get:198 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources [36.4 kB]                                                                                                            
Get:199 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources [36.4 kB]                                                                                                            
Get:200 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources [36.4 kB]                                                                                                            
Get:201 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources [36.4 kB]                                                                                                            
Get:202 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources [36.4 kB]                                                                                                            
Get:203 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources [36.4 kB]                                                                                                            
Get:204 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources [36.4 kB]                                                                                                            
Get:205 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources [36.4 kB]                                                                                                            
Get:206 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources [36.4 kB]                                                                                                            
Get:207 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources [36.4 kB]                                                                                                            
Get:208 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources [36.4 kB]                                                                                                            
Get:209 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources [36.4 kB]                                                                                                            
Get:210 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources [36.4 kB]                                                                                                            
Get:211 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources [36.4 kB]                                                                                                            
100% [211 Sources bzip2 0 B]                                                                                                                                                      181 kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


Get:212 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Sources [5311 B]                                                                                                           
Get:213 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Sources [5311 B]                                                                                                           
Get:214 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Sources [5311 B]                                                                                                           
Get:215 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Sources [5311 B]                                                                                                           
Get:216 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Sources [5311 B]                                                                                                           
Get:217 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Sources [5311 B]                                                                                                           
Get:218 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Sources [5311 B]                                                                                                           
Get:219 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Sources [5311 B]                                                                                                           
Get:220 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Sources [5311 B]                                                                                                           
Get:221 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Sources [5311 B]                                                                                                           
100% [221 Sources bzip2 0 B]                                                                                                                                                      181 kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


Get:222 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main i386 Packages [4809 B]                                                                                                           
Get:223 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main i386 Packages [4809 B]                                                                                                           
Get:224 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main i386 Packages [4809 B]                                                                                                           
Get:225 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main i386 Packages [4809 B]                                                                                                           
Get:226 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main i386 Packages [4809 B]                                                                                                           
Get:227 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main i386 Packages [4809 B]                                                                                                           
Get:228 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main i386 Packages [4809 B]                                                                                                           
Get:229 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main i386 Packages [4809 B]                                                                                                           
Get:230 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main i386 Packages [4809 B]                                                                                                           
100% [230 Packages bzip2 0 B]                                                                                                                                                     7976 B/s 1s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


Get:231 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]                                                                                                       
Get:232 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]                                                                                                      
Get:233 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]                                                                                                      
Get:234 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]                                                                                                      
Get:235 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]                                                                                                      
Get:236 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]                                                                                                      
Get:237 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]                                                                                                      
Get:238 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]                                                                                                      
Get:239 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]                                                                                                      
Get:240 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]                                                                                                      
Get:241 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]                                                                                                      
Get:242 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]                                                                                                      
Get:243 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]                                                                                                      
Get:244 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]                                                                                                      
Get:245 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]                                                                                                      
Get:246 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]                                                                                                      
Get:247 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]                                                                                                      
Get:248 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]                                                                                                      
Get:249 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]                                                                                                      
100% [249 Packages bzip2 0 B]                                                                                                                                                     7976 B/s 1s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


Get:250 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5178 B]                                                                                                     
Get:251 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5178 B]                                                                                                     
Get:252 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5178 B]                                                                                                     
Get:253 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5178 B]                                                                                                     
Get:254 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5178 B]                                                                                                     
Get:255 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5178 B]                                                                                                     
Get:256 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5178 B]                                                                                                     
Get:257 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5178 B]                                                                                                     
Get:258 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5178 B]                                                                                                     
Get:259 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5178 B]                                                                                                     
100% [259 Packages bzip2 0 B]                                                                                                                                                     7976 B/s 1s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


Get:260 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main TranslationIndex [72 B]                                                                                                          
Get:261 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse TranslationIndex [72 B]                                                                                                    
Get:262 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted TranslationIndex [70 B]                                                                                                    
Get:263 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe TranslationIndex [73 B]                                                                                                      
Get:264 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]                                                                                                                    
Get:265 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]                                                                                                                    
Get:266 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]                                                                                                                    
Get:267 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]                                                                                                                    
Get:268 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]                                                                                                                    
Get:269 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]                                                                                                                    
Get:270 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]                                                                                                                    
Get:271 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]                                                                                                                    
Get:272 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]                                                                                                                    
Get:273 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]
Get:274 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]
Get:275 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]
Get:276 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]
Get:277 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]
Get:278 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]
Get:279 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]
Get:280 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]
Get:281 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]
Get:282 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]
Get:283 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]
Get:284 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]
Get:285 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]
Get:286 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en [726 kB]
Get:287 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
99% [286 Translation-en bzip2 0 B] [287 Translation-en 2680 B/93.4 kB 3%]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


Get:288 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:289 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:290 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:291 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:292 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:293 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:294 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:295 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:296 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:297 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:298 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:299 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:300 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:301 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:302 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:303 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:304 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:305 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:306 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:307 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:308 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:309 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:310 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:311 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:312 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:313 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:314 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:315 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:316 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:317 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:318 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:319 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:320 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:321 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:322 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:323 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:324 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:325 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:326 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:327 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:328 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:329 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
100% [329 Translation-en bzip2 0 B]           
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


Get:330 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:331 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:332 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:333 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:334 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:335 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:336 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:337 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:338 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:339 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:340 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:341 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:342 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:343 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:344 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:345 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:346 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:347 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:348 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:349 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:350 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:351 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:352 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:353 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:354 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:355 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:356 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:357 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:358 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:359 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:360 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:361 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:362 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:363 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:364 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:365 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
Get:366 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [323 kB]                                                                                                            
100% [366 Translation-en bzip2 0 B]                                                                                                                                               127 kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)


It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.


You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources                                                                                                                                  
  404  Not Found [IP: 91.189.92.200 80]
100% [286 Translation-en gzip 3595 kB]W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
E: Unable to parse package file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en.decomp (1)
100% [329 Translation-en gzip 0 B]E: Unable to parse package file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en.decomp (1)
100% [366 Translation-en gzip 2695 kB]E: Unable to parse package file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en.decomp (1)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted Sources
  404  Not Found [IP: 91.189.92.200 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Fetched 1815 kB in 1min 21s (22.3 kB/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_restricted_source_Sources  Hash Sum mismatch


W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages  Hash Sum mismatch


W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages  Hash Sum mismatch


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Index](http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Index)  No sections in Release file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Index


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Index](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Index)  No sections in Release file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Index


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Index](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Index)  No sections in Release file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Index


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Index](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Index)  No sections in Release file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Index


W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise_main_source_Sources  Hash Sum mismatch


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  404  Not Found [IP: 91.189.92.200 80]


W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources  Hash Sum mismatch


W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages  Hash Sum mismatch


W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages  Hash Sum mismatch


W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  Hash Sum mismatch


W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages  Hash Sum mismatch


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Index)  


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Index)  


W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise-updates_main_source_Sources  Hash Sum mismatch


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Index)  


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Index)  


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Index)  


W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise-backports_main_source_Sources  Encountered a section with no Package: header


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.92.200 80]


W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_source_Sources  Encountered a section with no Package: header


W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_source_Sources  Encountered a section with no Package: header


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]


W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages  Encountered a section with no Package: header


W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-i386_Packages  Encountered a section with no Package: header


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Index)  No sections in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Index


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Index)  No sections in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Index


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Index)  No sections in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Index


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Index)  No sections in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Index


W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en  


W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en  


W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en  


E: Some index files failed to download. They have been ignored, or old ones used instead.

please help me solve this,

Upendra

---

