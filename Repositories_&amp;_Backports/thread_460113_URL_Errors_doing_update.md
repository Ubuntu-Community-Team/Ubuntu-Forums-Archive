---
title: "URL Errors doing update"
date: 2007-05-31
forum: Repositories &amp; Backports
---

### Post by @ndreX! on 2007-05-31
Well, i got many errors when i try to do sudo apt-get update here's the errors:

```

Get:1 http://archive.canonical.com edgy-commercial Release.gpg [191B]          
Get:2 http://archive.ubuntu.com edgy Release.gpg [191B]                        
Get:3 http://security.ubuntu.com edgy-security Release.gpg [191B]              
Ign http://archive.canonical.com edgy-commercial/main Translation-en_US        
Ign http://theli.free.fr edgy Release.gpg                                      
Get:4 http://medibuntu.sos-sts.com edgy Release.gpg [189B]                     
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Ign http://archive.ubuntu.com edgy/main Translation-en_US                      
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US                
Ign http://theli.free.fr edgy/listen Translation-en_US                         
Get:5 http://archive.canonical.com edgy-commercial Release [4874B]             
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US      
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US                
Ign http://archive.canonical.com edgy-commercial Release                       
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US        
Ign http://archive.ubuntu.com edgy/universe Translation-en_US                  
Ign http://theli.free.fr edgy Release                                          
Get:6 http://archive.canonical.com edgy-commercial/main Packages [1066B]       
Get:7 http://archive.ubuntu.com edgy-proposed Release.gpg [191B]               
Ign http://archive.ubuntu.com edgy-proposed/main Translation-en_US             
Ign http://theli.free.fr edgy/listen Packages                                  
Ign http://archive.ubuntu.com edgy-proposed/restricted Translation-en_US       
Ign http://archive.ubuntu.com edgy-proposed/multiverse Translation-en_US       
Err http://theli.free.fr edgy/listen Packages                                  
  301 Moved Permanently
Ign http://archive.ubuntu.com edgy-proposed/universe Translation-en_US         
Get:8 http://archive.ubuntu.com edgy-updates Release.gpg [191B]                
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US              
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US        
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US        
Get:9 http://security.ubuntu.com edgy-security Release [50.9kB]                
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US          
Get:10 http://archive.ubuntu.com edgy-backports Release.gpg [191B]             
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US            
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US      
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US      
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US        
Ign http://medibuntu.sos-sts.com edgy/free Translation-en_US                   
Get:11 http://security.ubuntu.com edgy-security/main Packages [83.7kB]         
Get:12 http://security.ubuntu.com edgy-security/restricted Packages [5678B]    
Ign http://security.ubuntu.com edgy-security/restricted Packages     
Ign http://medibuntu.sos-sts.com edgy/non-free Translation-en_US               
Hit http://medibuntu.sos-sts.com edgy Release                                  
Err http://medibuntu.sos-sts.com edgy Release                                  
  
Get:13 http://medibuntu.sos-sts.com edgy Release [7228B]                       
Hit http://security.ubuntu.com edgy-security/multiverse Packages               
Ign http://medibuntu.sos-sts.com edgy Release                                  
Hit http://medibuntu.sos-sts.com edgy/free Packages                            
Hit http://medibuntu.sos-sts.com edgy/non-free Packages                        
Hit http://security.ubuntu.com edgy-security/universe Packages                 
Get:14 http://medibuntu.sos-sts.com edgy/free Sources [1132B]                  
96% [14 Sources bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting f
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://medibuntu.sos-sts.com edgy/free Sources                             
  Sub-process bzip2 returned an error code (2)
Get:15 http://archive.ubuntu.com edgy Release [34.7kB]                         
Ign http://archive.ubuntu.com edgy Release                                     
Get:16 http://security.ubuntu.com edgy-security/main Sources [17.3kB]          
Get:17 http://medibuntu.sos-sts.com edgy/non-free Sources [1206B]              
Get:18 http://security.ubuntu.com edgy-security/restricted Sources [937B]      
97% [Waiting for headers] [Connecting to security.ubuntu.com (82.211.81.138)]  
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://security.ubuntu.com edgy-security/restricted Sources              
  Sub-process bzip2 returned an error code (2)
Get:19 http://security.ubuntu.com edgy-security/multiverse Sources [430B]      
97% [Waiting for headers] [Connecting to security.ubuntu.com (82.211.81.138)]  
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://security.ubuntu.com edgy-security/multiverse Sources              
  Sub-process bzip2 returned an error code (2)
Get:20 http://security.ubuntu.com edgy-security/universe Sources [4913B]       
Ign http://security.ubuntu.com edgy-security/universe Sources                  
Get:21 http://security.ubuntu.com edgy-security/restricted Packages [5709B]    
95% [21 Packages gzip 0] [Waiting for headers] [Waiting for headers]           
gzip: stdin: not in gzip format
Err http://security.ubuntu.com edgy-security/restricted Packages    
  Sub-process gzip returned an error code (1)
Get:22 http://security.ubuntu.com edgy-security/universe Sources [5046B]       
95% [22 Sources gzip 0] [Waiting for headers]                        932B/s 11s
gzip: stdin: not in gzip format
Err http://security.ubuntu.com edgy-security/universe Sources                  
  Sub-process gzip returned an error code (1)
Get:23 http://archive.ubuntu.com edgy-proposed Release [38.4kB]                
Get:24 http://archive.ubuntu.com edgy-updates Release [38.4kB]                 
Get:25 http://archive.ubuntu.com edgy-backports Release [44.6kB]               
Get:26 http://archive.ubuntu.com edgy/main Packages [940kB]                    
Get:27 http://archive.ubuntu.com edgy/restricted Packages [5974B]              
Ign http://archive.ubuntu.com edgy/restricted Packages                         
Get:28 http://archive.ubuntu.com edgy/multiverse Packages [126kB]              
Get:29 http://archive.ubuntu.com edgy/universe Packages [3559kB]               
Get:30 http://archive.ubuntu.com edgy/main Sources [274kB]                     
Get:31 http://archive.ubuntu.com edgy/restricted Sources [1436B]               
Get:32 http://archive.ubuntu.com edgy/multiverse Sources [45.0kB]              
Get:33 http://archive.ubuntu.com edgy/universe Sources [1068kB]                
Get:34 http://archive.ubuntu.com edgy-proposed/main Packages [88.0kB]          
Ign http://archive.ubuntu.com edgy-proposed/main Packages                      
Get:35 http://archive.ubuntu.com edgy-proposed/restricted Packages [14B]       
Get:36 http://archive.ubuntu.com edgy-proposed/multiverse Packages [3084B]     
Ign http://archive.ubuntu.com edgy-proposed/multiverse Packages                
Get:37 http://archive.ubuntu.com edgy-proposed/universe Packages [31.4kB]      
98% [35 Packages bzip2 0] [Waiting for headers]                      101kB/s 1s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com edgy-proposed/restricted Packages                
  Sub-process bzip2 returned an error code (2)
Get:38 http://archive.ubuntu.com edgy-updates/main Packages [81.1kB]           
Ign http://archive.ubuntu.com edgy-updates/main Packages                       
Get:39 http://archive.ubuntu.com edgy-updates/restricted Packages [14B]        
Get:40 http://archive.ubuntu.com edgy-updates/multiverse Packages [14B]        
Get:41 http://archive.ubuntu.com edgy-updates/universe Packages [24.2kB]       
Get:42 http://archive.ubuntu.com edgy-updates/main Sources [24.2kB]            
Get:43 http://archive.ubuntu.com edgy-updates/restricted Sources [14B]         
Get:44 http://archive.ubuntu.com edgy-updates/multiverse Sources [14B]         
Get:45 http://archive.ubuntu.com edgy-updates/universe Sources [4862B]         
Ign http://archive.ubuntu.com edgy-updates/universe Sources                    
Get:46 http://archive.ubuntu.com edgy-backports/main Packages [17.8kB]         
Get:47 http://archive.ubuntu.com edgy-backports/restricted Packages [14B]      
Get:48 http://archive.ubuntu.com edgy-backports/multiverse Packages [6087B]    
Ign http://archive.ubuntu.com edgy-backports/multiverse Packages               
Get:49 http://archive.ubuntu.com edgy-backports/universe Packages [41.3kB]     
Get:50 http://archive.ubuntu.com edgy-backports/main Sources [5594B]           
Ign http://archive.ubuntu.com edgy-backports/main Sources                      
Get:51 http://archive.ubuntu.com edgy-backports/restricted Sources [14B]       
Get:52 http://archive.ubuntu.com edgy-backports/multiverse Sources [2382B]     
Get:53 http://archive.ubuntu.com edgy-backports/universe Sources [14.6kB]      
Get:54 http://archive.ubuntu.com edgy/restricted Packages [6132B]              
96% [54 Packages gzip 0] [Waiting for headers]                     12.4kB/s 16s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com edgy/restricted Packages                         
  Sub-process gzip returned an error code (1)
Get:55 http://archive.ubuntu.com edgy-proposed/main Packages [113kB]           
96% [Connecting to archive.ubuntu.com (91.189.88.31)]              12.4kB/s 16s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com edgy-proposed/main Packages                      
  Sub-process gzip returned an error code (1)
Get:56 http://archive.ubuntu.com edgy-proposed/multiverse Packages [2802B]     
96% [Connecting to archive.ubuntu.com (91.189.88.31)]              12.4kB/s 16s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com edgy-proposed/multiverse Packages                
  Sub-process gzip returned an error code (1)
Get:57 http://archive.ubuntu.com edgy-updates/main Packages [103kB]            
97% [Connecting to archive.ubuntu.com (91.189.88.31)]              12.4kB/s 16s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com edgy-updates/main Packages                       
  Sub-process gzip returned an error code (1)
Get:58 http://archive.ubuntu.com edgy-updates/universe Sources [4864B]         
97% [58 Sources gzip 0] [Waiting for headers]                      12.4kB/s 16s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com edgy-updates/universe Sources                    
  Sub-process gzip returned an error code (1)
Get:59 http://archive.ubuntu.com edgy-backports/multiverse Packages [6081B]    
97% [59 Packages gzip 0] [Waiting for headers]                     12.4kB/s 16s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com edgy-backports/multiverse Packages               
  Sub-process gzip returned an error code (1)
Get:60 http://archive.ubuntu.com edgy-backports/main Sources [5806B]           
97% [Working]                                                      12.4kB/s 16s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com edgy-backports/main Sources                      
  Sub-process gzip returned an error code (1)
Fetched 6574kB in 1m13s (89.1kB/s)                                             
Failed to fetch http://theli.free.fr/packages/dists/edgy/listen/binary-i386/Packages.gz  301 Moved Permanently
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/edgy/free/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/multiverse/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: http://archive.canonical.com edgy-commercial Release: The following signatures were invalid: NODATA 2
W: GPG error: http://medibuntu.sos-sts.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://archive.ubuntu.com edgy Release: The following signatures were invalid: NODATA 2
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


```

I don't know if i have some lost in my sources-list by the way here's my list:

```

##deb http://us.archive.ubuntu.com/ubuntu/ edgy main universe multiverse
##deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main universe multiverse
##deb http://us.archive.ubuntu.com/ubuntu/ edgy-proposed main universe multiverse

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted multiverse universe

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted multiverse universe

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted multiverse universe

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted multiverse universe

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
deb http://theli.free.fr/packages/ edgy listen

```

I don't know if some body can give me goods repositories, however i have Edgy 6.10 and i don't want to upgrade my dist.

Thanks for your help.

Regards.

---

### Post by Spook27 on 2007-05-31
I have been having the same problem since at least last night.  I am running on Dapper (6.06).

---

### Post by ktraglin on 2007-06-02
I've been having similar problems for more than a week.  I thought it might be a problem that would be fixed within a couple of days, but I suppose not.

---

