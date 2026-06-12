---
title: "helping with root"
date: 2012-09-05
forum: Server Platforms
---

### Post by hiperflash on 2012-09-05
Hey its me again :)

i fixed my server i can connect to it from remote computer and now i have some problemi cant access to root user..

when i try to install this for gui look form remote computer..

sudo apt-get install tightvncserver

i get this error "E: Unable to locate package tightvncserver
"
[http://www.cyberciti.biz/faq/access-linux-from-windows-xp-system/](http://www.cyberciti.biz/faq/access-linux-from-windows-xp-system/)

even if try to log into with "su"

can someone help me? :/

and is there any better way to accesss linux server with no gui from other computer with gui access..

ty

---

### Post by kmyram on 2012-09-05
You would probably be better off logging in with SSH - but you need to do this as a "normal" user and then su (or better, sudo) for root-access.

/Kasper

---

### Post by drmrgd on 2012-09-05
That error doesn't suggest permissions problems.  It says that it couldn't locate the package in the repositories.  I do see the package in the repo using apt-cache:

```
sudo apt-cache showpkg tightvncserver
Package: tightvncserver
Versions: 
1.3.9-6.2ubuntu2 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages
                  MD5: 212aadc6932fc1ffc49df1c9619bc26a
 Description Language: en
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en
                  MD5: 212aadc6932fc1ffc49df1c9619bc26a


Reverse Depends: 
  tightvncserver:i386,tightvncserver
  tightvnc-java,tightvncserver
  xtightvncviewer,tightvncserver
  xrdp,tightvncserver
  x2vnc,tightvncserver
  vncsnapshot,tightvncserver
Dependencies: 
1.3.9-6.2ubuntu2 - libc6 (2 2.4) libjpeg8 (2 8c) libx11-6 (0 (null)) zlib1g (2 1:1.1.4) perl (0 (null)) x11-common (16 (null)) xserver-common (0 (null)) x11-utils (0 (null)) xauth (0 (null)) tightvnc-java (0 (null)) xfonts-base (0 (null)) x11-xserver-utils (0 (null)) tightvncserver:i386 (0 (null)) 
Provides: 
1.3.9-6.2ubuntu2 - xserver vnc-server 
Reverse Provides:
```

Are you positive you typed it correctly?

Also, if you can 'su' successfully, then I don't think it's permissions, but rather something amuck with your sources.  Do you have an internet connection on that server, and do you get any errors when you run:

```
sudo apt-get update
```

---

### Post by hiperflash on 2012-09-06
> **kmyram said:**
> You would probably be better off logging in with SSH - but you need to do this as a "normal" user and then su (or better, sudo) for root-access.

/Kasper

well im connected to server with putty! and i log into "admin" acc...

> **drmrgd said:**
> That error doesn't suggest permissions problems.  It says that it couldn't locate the package in the repositories.  I do see the package in the repo using apt-cache:

```
sudo apt-cache showpkg tightvncserver
Package: tightvncserver
Versions: 
1.3.9-6.2ubuntu2 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages
                  MD5: 212aadc6932fc1ffc49df1c9619bc26a
 Description Language: en
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en
                  MD5: 212aadc6932fc1ffc49df1c9619bc26a


Reverse Depends: 
  tightvncserver:i386,tightvncserver
  tightvnc-java,tightvncserver
  xtightvncviewer,tightvncserver
  xrdp,tightvncserver
  x2vnc,tightvncserver
  vncsnapshot,tightvncserver
Dependencies: 
1.3.9-6.2ubuntu2 - libc6 (2 2.4) libjpeg8 (2 8c) libx11-6 (0 (null)) zlib1g (2 1:1.1.4) perl (0 (null)) x11-common (16 (null)) xserver-common (0 (null)) x11-utils (0 (null)) xauth (0 (null)) tightvnc-java (0 (null)) xfonts-base (0 (null)) x11-xserver-utils (0 (null)) tightvncserver:i386 (0 (null)) 
Provides: 
1.3.9-6.2ubuntu2 - xserver vnc-server 
Reverse Provides:
```

Are you positive you typed it correctly?

Also, if you can 'su' successfully, then I don't think it's permissions, but rather something amuck with your sources.  Do you have an internet connection on that server, and do you get any errors when you run:

```
sudo apt-get update
```

yep im positive..

```
adminpapir@HomeServerPapir:~$ sudo apt-get install tightvncserver
[sudo] password for adminpapir:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package tightvncserver
adminpapir@HomeServerPapir:~$

```

after using this code : sudo apt-get update
its like this: 
```
adminpapir@HomeServerPapir:~$ sudo apt-get update
Err http://si.archive.ubuntu.com precise InRelease

Err http://security.ubuntu.com precise-security InRelease

Err http://si.archive.ubuntu.com precise-updates InRelease

Err http://security.ubuntu.com precise-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err http://si.archive.ubuntu.com precise-backports InRelease

Err http://si.archive.ubuntu.com precise Release.gpg
  Temporary failure resolving 'si.archive.ubuntu.com'
Err http://si.archive.ubuntu.com precise-updates Release.gpg
  Temporary failure resolving 'si.archive.ubuntu.com'
Err http://si.archive.ubuntu.com precise-backports Release.gpg
  Temporary failure resolving 'si.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://si.archive.ubuntu.com/ubuntu/dists/precise/InRelease

W: Failed to fetch http://si.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease

W: Failed to fetch http://si.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease

W: Failed to fetch http://si.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Temporary failure resolving 'si.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Temporary failure resolving 'security.ubuntu.com'

W: Failed to fetch http://si.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  Temporary failure resolving 'si.archive.ubuntu.com'

W: Failed to fetch http://si.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg  Temporary failure resolving 'si.archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.
adminpapir@HomeServerPapir:~$

```

---

### Post by drmrgd on 2012-09-06
Yes, it looks like you're suffering from a connection issue to the repositories, which is why you're getting the package not found error.  Can you confirm that there is a internet connection to that server?  Since you can connect to it by PuTTY, it is obviously on a network.  Perhaps, though there is no internet connection to that box, the port is blocked for one reason or another, you're behind a proxy that's messing things up, or you're using a bad repository mirror.  Are there any other Slovenia mirrors you could try instead of the default ones in the event that it's not an internet connection issue?

---

### Post by DJ_Max on 2012-09-06
Try pinging google from your server.

---

### Post by hiperflash on 2012-09-06
> **drmrgd said:**
> Yes, it looks like you're suffering from a connection issue to the repositories, which is why you're getting the package not found error.  Can you confirm that there is a internet connection to that server?  Since you can connect to it by PuTTY, it is obviously on a network.  Perhaps, though there is no internet connection to that box, the port is blocked for one reason or another, you're behind a proxy that's messing things up, or you're using a bad repository mirror.  Are there any other Slovenia mirrors you could try instead of the default ones in the event that it's not an internet connection issue?

this one looks like that is up to date.. 
[https://launchpad.net/ubuntu/+mirror/mirror.lihnidos.org-archive](https://launchpad.net/ubuntu/+mirror/mirror.lihnidos.org-archive)

but how can i change mirror servers?

edit:
hmmm...? 

ping: unknown host [www.google.com](www.google.com)

---

### Post by drmrgd on 2012-09-06
In case it's a DNS issue and to help narrow the problem down, maybe try pinging Google's IP address: 74.125.224.72.

This definitely sounds more like an internet connection problem that a repository mirror issue to me.

---

### Post by hiperflash on 2012-09-06
> **drmrgd said:**
> In case it's a DNS issue and to help narrow the problem down, maybe try pinging Google's IP address: 74.125.224.72.

This definitely sounds more like an internet connection problem that a repository mirror issue to me.

u think? :/
141 packets transmitted, 141 received, 0% packet loss, time 140192ms
rtt min/avg/max/mdev = 187.245/187.597/191.813/0.622 ms

---

### Post by drmrgd on 2012-09-06
OK, so to me (and I'm not where near anything close to a network guru), it looks like you have a DNS issue.  If you can ping the IP address OK, but can not ping the domain name, then that's what I would blame.  

I'm not sure how to fix it other than messing around with entries in /etc/resolv.conf.  But it's probably best to wait for someone who knows more about networking to help.  I think that once you get that resolved, you should be able to get the package you want from the repositories.

---

### Post by DJ_Max on 2012-09-06
Check your DNS settings. Make sure your nameservers are correct.

```
cat /etc/resolv.conf
nslookup www.google.com
dig www.google.com
```

---

### Post by hiperflash on 2012-09-07
> **DJ_Max said:**
> Check your DNS settings. Make sure your nameservers are correct.

```
cat /etc/resolv.conf
nslookup www.google.com
dig www.google.com
```

```
:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 84.255.254.1
adminpapir@HomeServerPapir:~$ nslookup www.google.com

;; connection timed out; no servers could be reached

```

crap.. so something is worng with conf packages?

---

### Post by HugoSerrano on 2012-09-07
add google dns into your /etc/resolv.conf

nameserver 8.8.8.8
nameserver 8.8.4.4

And test it. If it works, you need to change your dns settings, because, like it said on the file, the changes will be overwritten.

---

### Post by hiperflash on 2012-09-08
hua fixed it :) 

```

--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10143ms
rtt min/avg/max/mdev = 33.916/33.937/33.966/0.021 ms

```

thx all :))) 

now i need something else.. 

for normal users i would like to set up remote gui for server and i think tighvnc is to old.. any suggesting or ideas what else to do?

EDIT:
i know that i can install gnome desktop to server. but i dont want reduce performance of server. is there any other way?

---

### Post by DJ_Max on 2012-09-08
Installing any GUI will reduce performance, is there any reason you need a GUI over SSH?

---

