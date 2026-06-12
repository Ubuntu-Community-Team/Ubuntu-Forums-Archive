---
title: "Yet an Another Chkrootkit output..."
date: 2005-01-06
forum: Server Platforms
---

### Post by Malifice on 2005-01-06
I've made a chkrootkit and found that warning:

> 
Checking `lkm'... You have    17 process hidden for readdir command
You have    17 process hidden for ps command
Warning: Possible LKM Trojan installed


I'am using the linux-image-2.6.8.1-3-k7 package, installed using aptitude.
There is my source list:

> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main


And I am sure I had any weird source when I installed the new kernel.
I'm really not good  regarding security issues, so if someonde can give me a hint ^^.

Thanks.

---

### Post by nocturn on 2005-01-06
[QUOTE=Malifice]I've made a chkrootkit and found that warning:



I'am using the linux-image-2.6.8.1-3-k7 package, installed using aptitude.
There is my source list:



And I am sure I had any weird source when I installed the new kernel.
I'm really not good  regarding security issues, so if someonde can give me a hint ^^.

Thanks.[/QUOTE]

You could try rkhunter (IMO better then chkrootkit), see if that comes up with any identied malware.  The page is [www.rootkit.nl](www.rootkit.nl).

---

### Post by jdong on 2005-01-06
I backported a newer chkrootkit (0.44) to Warty. This one doesn't complain, so I suppose it's a false positive.

---

### Post by ubuntu_demon on 2005-01-06
[QUOTE=Malifice]I've made a chkrootkit and found that warning:



I'am using the linux-image-2.6.8.1-3-k7 package, installed using aptitude.
There is my source list:



And I am sure I had any weird source when I installed the new kernel.
I'm really not good  regarding security issues, so if someonde can give me a hint ^^.

Thanks.[/QUOTE]
 You have nothing to worry about. These are probably shortliving processes. This is common.

---

### Post by Malifice on 2005-01-06
Ok, thanks you all for your help ^^

---

