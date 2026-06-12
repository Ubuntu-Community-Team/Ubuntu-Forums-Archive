---
title: "Apt-get Errors Ubuntu 12.0.4 Server"
date: 2012-09-05
forum: Virtualisation
---

### Post by kcars on 2012-09-05
When I run 'sudo apt-get update' command I'm getting some errors (see below). It is returning 'Unable to connect' errors and 'Failed to Fetch' errors however I am able to ping these servers no problem. Could someone please shine some light on this issue. Cheers

```

Err http://security.ubuntu.com precise-security InRelease
  
Err http://security.ubuntu.com precise-security Release.gpg
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err http://au.archive.ubuntu.com precise InRelease
  
Err http://au.archive.ubuntu.com precise-updates InRelease
  
Err http://au.archive.ubuntu.com precise-backports InRelease
  
Err http://au.archive.ubuntu.com precise Release.gpg
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com precise-updates Release.gpg
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com precise-backports Release.gpg
  Unable to connect to au.archive.ubuntu.com:http:
Reading package lists... Done
W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/precise/InRelease  

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease  

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg  Unable to connect to au.archive.ubuntu.com:http:

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by NikTh on 2012-09-05
Hello , 

possible server error (temporally unavailable) . 

Wait and try to update later 

or

change server from Update Manager > Settings > Ubuntu Software > Download From : and replace it with main server. 

Thanks

---

### Post by inventsekar on 2012-09-05
As said above, possible server, internet connection issue or something... you are able to browse? i mean internet is working??

---

### Post by kcars on 2012-09-05
Hi Nik, I just gave it another shot this morning and unfortunately I'm getting the same errors. I forgot to mention in the first post that I am accessing this box over ssh.  Could you please explain how I replace it with the main server on command line? Does it involve editing the /etc/apt/sources.list file? What is the main server address?

Thanks

---

### Post by NikTh on 2012-09-07
> **kcars said:**
> Hi Nik, I just gave it another shot this morning and unfortunately I'm getting the same errors. I forgot to mention in the first post that I am accessing this box over ssh.  Could you please explain how I replace it with the main server on command line? Does it involve editing the /etc/apt/sources.list file? What is the main server address?

Thanks

Hello , 
Unfortunately I don't occupy this sport (Servers - ssh etc) . Wait for a user who knows. 

Thanks

---

### Post by kcars on 2012-09-07
Hi,
Unfortunately, I am still having issues could someone please give me some ideas on how to troubleshoot this problem.  The strange thing is that I can ping the servers 'apt-get update' is having trouble connecting to. I have also successfully downloaded packages using 'wget' from the archives in question. Is there something in my configuration that could be restricting the apt-get from connecting to outside archives.

Thanks.

---

### Post by wojox on 2012-09-07
What does this file look like:
```
cat /etc/apt/sources.list
```

---

### Post by kcars on 2012-09-08
Hi, Thanks for the reply here is the contents of my sources.list file

```

# 

# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ precise main restricted

#deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/main/binary-i386/
#deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/restricted/binary-i386/
#deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://au.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ precise main restricted

deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://au.archive.ubuntu.com/ubuntu/ precise universe
deb http://au.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://au.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main


```

---

### Post by kcars on 2012-09-10
> **wojox said:**
> What does this file look like:
```
cat /etc/apt/sources.list
```
Hey wojox,  I have posted my sources.list file. could you please have a look and let me know if there is anything wrong here.

Cheers.

---

### Post by wojox on 2012-09-10
> **kcars said:**
> Hey wojox,  I have posted my sources.list file. could you please have a look and let me know if there is anything wrong here.

Cheers.

Looks good. :p

Try:
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.bk
```
```
sudo apt-get update
```

---

### Post by kcars on 2012-09-10
> **wojox said:**
> Looks good. :p

Try:
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.bk
```
```
sudo apt-get update
```
Thanks for the quick reply, however I thought 'apt-get update's inability to contact the archive servers was also the reason I am also having trouble using 'apt-get install' to install anything. I have also been trying to use 'apt-get install' to install nmap and I am still getting each time I try a "E: Unable to locate package nmap" error. Do you know why this error is occurring.

Thanks.

---

### Post by wojox on 2012-09-10
is this a vm or you behind a proxy?

---

### Post by kcars on 2012-09-10
> **wojox said:**
> is this a vm or you behind a proxy?
Its both. However it seems to be able to navigate the proxy as I was able to download packages straight from the archives using 'wget'. I also added the following lines to the .bashrc file to make sure it could authenticate. However this has had no effect.

```

http_proxy=http://myUserName:password@proxy.uowa.edu.au:8080
export http_proxy

```

Thanks.

---

### Post by wojox on 2012-09-10
> **kcars said:**
> However it seems to be able to navigate the proxy as I was able to download packages straight from the archives using 'wget'.
Thanks.

True, I don't have much vm experience though. I'll try and have this moved to the vm section. :)

---

### Post by dcstar on 2012-09-11
> **wojox said:**
> True, I don't have much vm experience though. I'll try and have this moved to the vm section. :)

Without ANY information about what VM platform this is on and if the VM networking is Bridged or whatever then the OP is not going to get much help at all.

---

