---
title: "PowerPC Backport Repositories"
date: 2005-10-23
forum: Ubuntu Backports
---

### Post by Freddie on 2005-10-23
Hi, I have just added the new official backports repositories to my sources.list file. However, when I do an apt-get update I get this:
```

freddie@macserv:~$ sudo apt-get update
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]             
Get:2 http://security.ubuntu.com hoary-security Release [16.9kB]               
Get:3 http://archive.ubuntu.com hoary Release.gpg [189B]                       
Get:4 http://archive.ubuntu.com hoary Release [26.2kB]                         
Get:5 http://archive.ubuntu.com hoary/multiverse Packages [76.8kB]             
Get:6 http://security.ubuntu.com hoary-security/main Packages [73.2kB]         
Get:7 http://us.archive.ubuntu.com hoary Release.gpg [189B]                    
Get:8 http://us.archive.ubuntu.com breezy Release.gpg [189B]                   
Get:9 http://us.archive.ubuntu.com hoary-updates Release.gpg [189B]            
Get:10 http://us.archive.ubuntu.com breezy-updates Release.gpg [189B]          
Get:11 http://archive.ubuntu.com hoary/multiverse Sources [48.4kB]             
Get:12 http://security.ubuntu.com hoary-security/restricted Packages [14B]     
Get:13 http://security.ubuntu.com hoary-security/main Sources [16.4kB]         
Get:14 http://security.ubuntu.com hoary-security/restricted Sources [14B]      
Get:15 http://security.ubuntu.com hoary-security/universe Packages [49.0kB]    
Get:16 http://security.ubuntu.com hoary-security/universe Sources [7121B]      
Hit http://us.archive.ubuntu.com hoary Release                                 
Hit http://us.archive.ubuntu.com breezy Release                                
Get:17 http://us.archive.ubuntu.com hoary-updates Release [16.8kB]             
Get:18 http://us.archive.ubuntu.com breezy-updates Release [19.6kB]            
Hit http://us.archive.ubuntu.com hoary/main Packages                           
Ign http://mirror.brianpuccio.net hoary-backports Release.gpg                  
Ign http://mirror.brianpuccio.net hoary-extras Release.gpg                     
Hit http://us.archive.ubuntu.com hoary/restricted Packages                     
Get:19 http://us.archive.ubuntu.com hoary/universe Packages [2110kB]           
Ign http://mirror.brianpuccio.net hoary-backports Release                      
Ign http://mirror.brianpuccio.net hoary-extras Release                         
Ign http://mirror.brianpuccio.net hoary-backports/main Packages                
Ign http://mirror.brianpuccio.net hoary-backports/universe Packages            
Ign http://mirror.brianpuccio.net hoary-backports/multiverse Packages          
Ign http://mirror.brianpuccio.net hoary-backports/restricted Packages          
Ign http://mirror.brianpuccio.net hoary-extras/main Packages                   
Ign http://mirror.brianpuccio.net hoary-extras/universe Packages               
Ign http://mirror.brianpuccio.net hoary-extras/multiverse Packages             
Ign http://mirror.brianpuccio.net hoary-extras/restricted Packages             
Err http://mirror.brianpuccio.net hoary-backports/main Packages                
  404 Not Found
Err http://mirror.brianpuccio.net hoary-backports/universe Packages            
  404 Not Found
Err http://mirror.brianpuccio.net hoary-backports/multiverse Packages          
  404 Not Found
Err http://mirror.brianpuccio.net hoary-backports/restricted Packages          
  404 Not Found
Get:20 http://mirror.brianpuccio.net hoary-extras/main Packages [33B]          
Get:21 http://mirror.brianpuccio.net hoary-extras/universe Packages [592B]     
Get:22 http://mirror.brianpuccio.net hoary-extras/multiverse Packages [33B]    
Get:23 http://mirror.brianpuccio.net hoary-extras/restricted Packages [1080B]  
Get:24 http://us.archive.ubuntu.com hoary/universe Sources [857kB]             
Hit http://us.archive.ubuntu.com breezy/main Sources                           
Hit http://us.archive.ubuntu.com breezy/restricted Sources                     
Hit http://us.archive.ubuntu.com hoary-updates/main Packages                   
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages             
Hit http://us.archive.ubuntu.com breezy-updates/main Sources                   
Hit http://us.archive.ubuntu.com breezy-updates/restricted Sources             
Fetched 3320kB in 41s (80.7kB/s)                                               
Failed to fetch http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/main/binary-powerpc/Packages.gz  404 Not Found
Failed to fetch http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/universe/binary-powerpc/Packages.gz  404 Not Found
Failed to fetch http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/multiverse/binary-powerpc/Packages.gz  404 Not Found
Failed to fetch http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/restricted/binary-powerpc/Packages.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
Can anyone help me?

---

### Post by grinias on 2005-10-23
backport repositories aren't yet ready. We 've got to wait a little...

---

