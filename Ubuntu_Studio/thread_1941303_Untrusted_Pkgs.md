---
title: "Untrusted Pkgs???"
date: 2012-03-15
forum: Ubuntu Studio
---

### Post by hbnmgr on 2012-03-15
When Update Window appears, selecting any pkgs gets the response.

**"Requires Installation of Untrusted Packages"**

I only have Canonical Sources checked under Software Sources.

Any suggestions?

Thanks!

---

### Post by 2F4U on 2012-03-15
What version of Ubuntu are you using? Do you get the same result when you do the updates from a terminal using apt-get?
Here is one solved forum post with other solutions you might wish to try:

[http://ubuntuforums.org/showthread.php?t=1878602](http://ubuntuforums.org/showthread.php?t=1878602)

---

### Post by hbnmgr on 2012-03-16
Running the latest version of Ubuntu Studio.

Here is output from your recommended page (see Errors)

```

stephen@Linus2us:~$ sudo apt-get update
[sudo] password for stephen: 
Ign http://archive.canonical.com oneiric InRelease
Ign http://archive.ubuntu.com oneiric InRelease                     
Ign http://us.archive.ubuntu.com oneiric InRelease                   
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://security.ubuntu.com oneiric-security InRelease                      
Get:1 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]       
Get:2 http://archive.canonical.com oneiric Release.gpg [198 B]       
Get:3 http://archive.ubuntu.com oneiric Release.gpg [198 B]          
Get:4 http://security.ubuntu.com oneiric-security Release.gpg [198 B]          
Get:5 http://us.archive.ubuntu.com oneiric-updates Release.gpg [198 B]
Hit http://archive.ubuntu.com oneiric Release                        
Get:6 http://archive.canonical.com oneiric Release [5,922 B]         
Get:7 http://security.ubuntu.com oneiric-security Release [40.8 kB]            
Ign http://archive.ubuntu.com oneiric Release                                  
Hit http://us.archive.ubuntu.com oneiric Release                               
Ign http://us.archive.ubuntu.com oneiric Release                               
Ign http://archive.canonical.com oneiric Release                               
Ign http://archive.ubuntu.com oneiric/restricted Sources/DiffIndex             
Get:8 http://us.archive.ubuntu.com oneiric-updates Release [40.8 kB]           
Ign http://archive.canonical.com oneiric/partner Sources/DiffIndex             
Ign http://archive.ubuntu.com oneiric/main Sources/DiffIndex                   
Ign http://archive.ubuntu.com oneiric/multiverse Sources/DiffIndex             
Ign http://archive.canonical.com oneiric/partner i386 Packages/DiffIndex       
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://archive.ubuntu.com oneiric/restricted Sources                       
Hit http://archive.ubuntu.com oneiric/main Sources                             
Get:9 http://archive.canonical.com oneiric/partner Sources [2,279 B]           
Ign http://security.ubuntu.com oneiric-security Release                        
Hit http://archive.ubuntu.com oneiric/multiverse Sources                       
Ign http://us.archive.ubuntu.com oneiric-updates Release                       
Get:10 http://archive.canonical.com oneiric/partner i386 Packages [3,941 B]
Ign http://security.ubuntu.com oneiric-security/main Sources/DiffIndex         
Ign http://us.archive.ubuntu.com oneiric/main Sources/DiffIndex      
Ign http://us.archive.ubuntu.com oneiric/main i386 Packages/DiffIndex
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex       
Ign http://security.ubuntu.com oneiric-security/main i386 Packages/DiffIndex
Get:11 http://security.ubuntu.com oneiric-security/main TranslationIndex [73 B]
Ign http://us.archive.ubuntu.com oneiric-updates/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-updates/main i386 Packages/DiffIndex
Get:12 http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]
Hit http://us.archive.ubuntu.com oneiric/main Sources                
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages          
Get:13 http://security.ubuntu.com oneiric-security/main Sources [34.5 kB]
Hit http://us.archive.ubuntu.com oneiric/main Translation-en                   
Get:14 http://us.archive.ubuntu.com oneiric-updates/main Sources [130 kB]      
Get:15 http://security.ubuntu.com oneiric-security/main i386 Packages [90.4 kB]
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Get:16 http://us.archive.ubuntu.com oneiric-updates/main i386 Packages [300 kB]
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Ign http://archive.canonical.com oneiric/partner Translation-en                
Get:17 http://us.archive.ubuntu.com oneiric-updates/main Translation-en [141 kB]
Fetched 790 kB in 4s (185 kB/s)                              
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://us.archive.ubuntu.com oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.canonical.com oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://security.ubuntu.com oneiric-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://us.archive.ubuntu.com oneiric-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)

```

Any Help Appreciated
Thanks!

---

### Post by jerrrys on 2012-03-16
Here's what I have

[http://askubuntu.com/questions/1877/what-is-the-easiest-way-to-resolve-apt-get-badsig-gpg-errors](http://askubuntu.com/questions/1877/what-is-the-easiest-way-to-resolve-apt-get-badsig-gpg-errors)

[http://ubuntuforums.org/showthread.php?p=11662785#post11662785](http://ubuntuforums.org/showthread.php?p=11662785#post11662785)

[http://ubuntuforums.org/showthread.php?t=1904845](http://ubuntuforums.org/showthread.php?t=1904845)

---

### Post by hbnmgr on 2012-03-19
Because the GPG Error was NO_PUBKEY, I ran the following (showing results);

```

root@Linus2us:/var/lib/apt# apt-get clean
root@Linus2us:/var/lib/apt# mv lists lists.old
root@Linus2us:/var/lib/apt# apt-get clean
root@Linus2us:/var/lib/apt# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.bewoCdXOzF --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: public key "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
root@Linus2us:/var/lib/apt# apt-get update
Ign http://archive.ubuntu.com oneiric InRelease
Ign http://security.ubuntu.com oneiric-security InRelease           
Ign http://us.archive.ubuntu.com oneiric InRelease                  
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://archive.canonical.com oneiric InRelease                             
Get:1 http://security.ubuntu.com oneiric-security Release.gpg [198 B]
Get:2 http://archive.ubuntu.com oneiric Release.gpg [198 B]          
Get:3 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]                 
Get:4 http://archive.canonical.com oneiric Release.gpg [198 B]       
Get:5 http://security.ubuntu.com oneiric-security Release [40.8 kB]  
Get:6 http://archive.ubuntu.com oneiric Release [40.8 kB]                      
Get:7 http://us.archive.ubuntu.com oneiric-updates Release.gpg [198 B]         
Get:8 http://archive.canonical.com oneiric Release [5,922 B]                   
Get:9 http://us.archive.ubuntu.com oneiric Release [40.8 kB]                   
Get:10 http://archive.canonical.com oneiric/partner Sources [2,279 B]          
Get:11 http://archive.canonical.com oneiric/partner i386 Packages [3,941 B]    
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Get:12 http://security.ubuntu.com oneiric-security/main Sources [34.5 kB]      
Get:13 http://archive.ubuntu.com oneiric/restricted Sources [5,351 B]          
Get:14 http://archive.ubuntu.com oneiric/main Sources [877 kB]                 
Get:15 http://us.archive.ubuntu.com oneiric-updates Release [40.8 kB]          
Get:16 http://security.ubuntu.com oneiric-security/main i386 Packages [90.4 kB]
Get:17 http://us.archive.ubuntu.com oneiric/main Sources [877 kB]              
Get:18 http://security.ubuntu.com oneiric-security/main TranslationIndex [73 B]
Get:19 http://security.ubuntu.com oneiric-security/main Translation-en [50.7 kB]
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://archive.canonical.com oneiric/partner Translation-en                
Get:20 http://archive.ubuntu.com oneiric/multiverse Sources [149 kB]           
Get:21 http://us.archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]      
Get:22 http://us.archive.ubuntu.com oneiric/main TranslationIndex [3,289 B]
Get:23 http://us.archive.ubuntu.com oneiric-updates/main Sources [130 kB]
Get:24 http://us.archive.ubuntu.com oneiric-updates/main i386 Packages [300 kB]
Get:25 http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]
Get:26 http://us.archive.ubuntu.com oneiric/main Translation-en [701 kB]
Get:27 http://us.archive.ubuntu.com oneiric-updates/main Translation-en [141 kB]
Fetched 4,762 kB in 8s (547 kB/s)                                              
Reading package lists... Done

```

UPDATE MGR now Updating !!!

Thanks Guys - Problem Solved

---

