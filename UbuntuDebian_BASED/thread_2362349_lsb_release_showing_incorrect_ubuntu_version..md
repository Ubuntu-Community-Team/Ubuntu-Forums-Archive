---
title: "lsb_release showing incorrect ubuntu version."
date: 2017-05-27
forum: Ubuntu/Debian BASED
---

### Post by shridhar-kapshikar on 2017-05-27
Hi,

I have successfullly upgraded ubuntu 14.04 --> ubuntu 16.04 using 

```

apt-get upgrade

then

apt-get dist-upgrade

then

do-release-upgrade




```

but still when i execute the command,

```

root@shridhar:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty
root@shridhar:~# 





```

Please suggest am I missing something here.

---

### Post by howefield on 2017-05-27
Could be the base-files package is out of date, what's the output of

```
apt-cache policy base-files
```

---

### Post by vasa1 on 2017-05-27
Side issue: rather than run as root, stay as a normal user and use sudo whenever you want elevated privileges.

---

### Post by shridhar-kapshikar on 2017-05-28
here is requested command output,
```

shridhar@shridhar:~$ sudo apt-cache policy base-files 
base-files:
  Installed: 9.9.sparky
  Candidate: 9.9.sparky
  Version table:
 *** 9.9.sparky 100
        100 /var/lib/dpkg/status
     9.4ubuntu4.4 500
        500 http://in.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
     9.4ubuntu4 500
        500 http://in.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
shridhar@shridhar:~$ 


```

sure, I will make sure to use normal user and use sudo all the time.
Thank you.

---

### Post by howefield on 2017-05-28
Not what I'd expect.

What's the output of 

```
cat /etc/*-release
```

---

### Post by vasa1 on 2017-05-28
OP seems to be using Sparky Linux :???:

From: [https://sparkylinux.org/repo/](https://sparkylinux.org/repo/)
```
...
Packages in Sparky testing repository:
A
acidrip 0.14-0.2ubuntu7
awesome-theme-sparky 0.1.0
B
base-files 9.9.sparky
blue-sky-sparky 0.1.4
bluegriffon 2.3.1
boot-repair 4ppa40
boot-sav 4ppa40
boot-sav-extra 4ppa40
#budgie-desktop 10.2.9-1
C
calamares 3.1-sparky11
cde-desktop 2.2.4-1
ceni 2017.04.08
custom-iso-builder 0.1.14
...
```

Or OP could have added something from [https://sparkylinux.org/sparky-aptus-on-debian-and-ubuntu/](https://sparkylinux.org/sparky-aptus-on-debian-and-ubuntu/) at some time?

---

### Post by howefield on 2017-05-28
Yep, which hopefully the *-release output will illuminate.

---

### Post by vasa1 on 2017-05-28
And maybe this:```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/* | nl
```

---

### Post by shridhar-kapshikar on 2017-05-28
Hi,

Here are requested commands output as below,

```

shridhar@shridhar:~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.4 LTS"
PRETTY_NAME="SparkyLinux 4 (tyche)"
NAME="SparkyLinux"
VERSION_ID="4"
VERSION="4 (tyche)"
ID=debian
HOME_URL="https://sparkylinux.org/"
SUPPORT_URL="https://sparkylinux.org/forum/"
BUG_REPORT_URL="https://sourceforge.net/p/sparkylinux/tickets"
shridhar@shridhar:~$ 

```


2nd command

```

shridhar@shridhar:~$ grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/* | nl
     1    /etc/apt/sources.list:deb http://in.archive.ubuntu.com/ubuntu/ xenial main restricted
     2    /etc/apt/sources.list:deb http://in.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
     3    /etc/apt/sources.list:deb http://in.archive.ubuntu.com/ubuntu/ xenial universe
     4    /etc/apt/sources.list:deb http://in.archive.ubuntu.com/ubuntu/ xenial-updates universe
     5    /etc/apt/sources.list:deb http://in.archive.ubuntu.com/ubuntu/ xenial multiverse
     6    /etc/apt/sources.list:deb http://in.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
     7    /etc/apt/sources.list:deb http://in.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
     8    /etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security main restricted
     9    /etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security universe
    10    /etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security multiverse
    11    /etc/apt/sources.list:deb http://archive.canonical.com/ubuntu xenial partner
    12    /etc/apt/sources.list.d/google-chrome.list.save:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
shridhar@shridhar:~$ 


```

On Login page, it shows Ubuntu 16.04 LTS.[ATTACH=CONFIG]275338[/ATTACH]

---

### Post by howefield on 2017-05-28
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by vasa1 on 2017-05-28
> **shridhar-kapshikar said:**
> Hi,

I have successfullly upgraded ubuntu 14.04 --> ubuntu 16.04 using 
...
Please suggest am I missing something here.
From the data you've provided, it appears that whatever you upgraded from wasn't actually Ubuntu 14.04, *per se*, but a related distro, Sparky Linux. So even though you feel you've successfully upgraded to Ubuntu 16.04, it's just possible that vestiges of the last distro may cause unexpected issues.

Keep in mind that even several experienced users of "pure" Ubuntu prefer to do a "clean" install rather than upgrade.

---

### Post by howefield on 2017-05-28
> **shridhar-kapshikar said:**
> 
```
PRETTY_NAME="SparkyLinux 4 (tyche)"
```

How exactly did you actually carry out the upgrade ?

Sorry to ask you another question but you have an odd situation, what's the output from.. 

```
cat /var/log/installer/media-info
```

Might tell you what the installation media originally used was.

If all appears to be working then you might leave it, but a fresh and clean install would probably be a good bet.

---

### Post by shridhar-kapshikar on 2017-05-30
Thank you for your respond.

Yesterday , I had installed fresh Ubuntu server 16.04 on my laptop. For now, all looks good.

Thank you for your suggestions.

---

### Post by howefield on 2017-05-30
> **shridhar-kapshikar said:**
> Yesterday , I had installed fresh Ubuntu server 16.04 on my laptop. For now, all looks good.

Sounds like the best plan and thanks for marking as solved.

---

