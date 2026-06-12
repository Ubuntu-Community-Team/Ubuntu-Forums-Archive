---
title: "Can't download updates! Help"
date: 2009-07-20
forum: Server Platforms
---

### Post by pogztimz on 2009-07-20
hello everyone, i was wondering why i can't update my server. my internet connection is working fine. here is my problem..

```
To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
root@complab:~# apt-get update
Err http://archive.canonical.com hardy Release.gpg                                                                
  Could not resolve 'archive.canonical.com'
Err http://archive.canonical.com hardy/partner Translation-en_PH                                                  
  Could not resolve 'archive.canonical.com'
Err http://ph.archive.ubuntu.com hardy Release.gpg                                                                
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy/main Translation-en_PH               
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy/restricted Translation-en_PH         
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy/universe Translation-en_PH           
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy/multiverse Translation-en_PH         
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-updates Release.gpg                  
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-updates/main Translation-en_PH       
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-updates/restricted Translation-en_PH 
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-updates/universe Translation-en_PH   
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-updates/multiverse Translation-en_PH 
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-backports Release.gpg                
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-backports/main Translation-en_PH     
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-backports/restricted Translation-en_PH
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-backports/universe Translation-en_PH 
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-backports/multiverse Translation-en_PH
  Could not resolve 'ph.archive.ubuntu.com'
Err http://security.ubuntu.com hardy-security Release.gpg                   
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/main Translation-en_PH        
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/restricted Translation-en_PH  
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/universe Translation-en_PH    
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_PH  
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done                                               
W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release.gpg  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_PH.bz2  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_PH.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_PH.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_PH.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_PH.bz2  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
root@complab:~# 

```
 can u guys pls help me.... tnx

---

### Post by spynappels on 2009-07-20
It looks like a DNS rsolution issue. To test this, try to ping [www.google.com](www.google.com) and if this does not work, try pinging 209.85.227.103 and if this works, you need to look at your resolv.conf file.

---

### Post by Avinash.Rao on 2009-07-20
Are u accessing internet through proxy? In that case edit /etc/apt/apt.conf and make the following entry.

Acquire::http::Proxy "http://yourproxyservername:port no"; 

Eg: 

Acquire::http::Proxy "http://ubuntuserver:8088"; 

The smile is :P

> **pogztimz said:**
> hello everyone, i was wondering why i can't update my server. my internet connection is working fine. here is my problem..

```
To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
root@complab:~# apt-get update
Err http://archive.canonical.com hardy Release.gpg                                                                
  Could not resolve 'archive.canonical.com'
Err http://archive.canonical.com hardy/partner Translation-en_PH                                                  
  Could not resolve 'archive.canonical.com'
Err http://ph.archive.ubuntu.com hardy Release.gpg                                                                
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy/main Translation-en_PH               
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy/restricted Translation-en_PH         
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy/universe Translation-en_PH           
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy/multiverse Translation-en_PH         
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-updates Release.gpg                  
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-updates/main Translation-en_PH       
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-updates/restricted Translation-en_PH 
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-updates/universe Translation-en_PH   
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-updates/multiverse Translation-en_PH 
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-backports Release.gpg                
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-backports/main Translation-en_PH     
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-backports/restricted Translation-en_PH
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-backports/universe Translation-en_PH 
  Could not resolve 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com hardy-backports/multiverse Translation-en_PH
  Could not resolve 'ph.archive.ubuntu.com'
Err http://security.ubuntu.com hardy-security Release.gpg                   
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/main Translation-en_PH        
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/restricted Translation-en_PH  
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/universe Translation-en_PH    
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_PH  
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done                                               
W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release.gpg  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/i18n/Translation-en_PH.bz2  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_PH.bz2  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_PH.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_PH.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_PH.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_PH.bz2  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
root@complab:~# 

```
 can u guys pls help me.... tnx

---

### Post by willmsbrt1 on 2009-07-20
Could you post your sources list and what type pc and version ? 

see below for a dell mini 9 , all are factory but medibuntu and launchpad 

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse #Added by software-properties

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) hardy main

---

### Post by willmsbrt1 on 2009-07-20
woops , server:D

---

### Post by wojox on 2009-07-20
Try:

```
sudo apt-get dist-upgrade
```

---

### Post by David_River on 2009-09-01
Help... Help.... Help...

Hello, got the same problem too... Can't use the pidgin, can't use the internet and can't update ubuntu. I already try the solutions above but nothing works except to the solution given by Avinash.Rao that is ...

"Are u accessing internet through proxy? In that case edit /etc/apt/apt.conf and make the following entry. Acquire::http::razz:roxy "http://yourproxyservername:razz:ort no"; 
Eg: Acquire::http::razz:roxy "http://ubuntuserver:8088"; 
The smile is :razz:"

don't know how to do it need help about it. (newbie using ubuntu)

This is the message I always got after a few attempts in updating the Ubuntu using Update Manager.

An error occurred:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://ph.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_PH.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_PH.bz2)  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_PH.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_PH.bz2)  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_PH.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_PH.bz2)  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_PH.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_PH.bz2)  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_PH.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_PH.bz2)  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_PH.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_PH.bz2)  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_PH.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_PH.bz2)  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_PH.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_PH.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_PH.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_PH.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_PH.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_PH.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_PH.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_PH.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.



I also done the code below in the Terminal but i says 0 installations and updates.
sudo apt-get dist-upgrade

---

### Post by David_River on 2009-09-01
> **Avinash.Rao said:**
> Are u accessing internet through proxy? In that case edit /etc/apt/apt.conf and make the following entry.

Acquire::http::Proxy "http://yourproxyservername:port no"; 

Eg: 

Acquire::http::Proxy "http://ubuntuserver:8088"; 

The smile is :P
No idea on how to do your solution...
Are u accessing internet through proxy? In that case edit /etc/apt/apt.conf and make the following entry.

Acquire::http::razz:roxy "http://yourproxyservername:razz:ort no"; 

Eg: 

Acquire::http::razz:roxy "http://ubuntuserver:8088"; 

The smile is :razz:

Need help on how to execute this solution. Thank you

---

### Post by Avinash.Rao on 2009-09-03
There is an option called "Network Proxy" under Preferences menu. Add your proxy server address in this and check by executing #apt-get update

Avinash

---

