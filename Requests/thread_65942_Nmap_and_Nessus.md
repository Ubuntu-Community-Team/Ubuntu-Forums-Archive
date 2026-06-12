---
title: "Nmap and Nessus?"
date: 2005-09-15
forum: Requests
---

### Post by kag3musha on 2005-09-15
I like to use Ubuntu as a security testing platform because of its ease of use.

Yeah, yeah I can "roll my own" but quite frankly that is a pain in the arse.

Anyway we can get the latest versions of Nmap and Nessus?

---

### Post by evilghost on 2005-09-15
Am I missing something?

```

luser@400sc:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

## Backports Staging
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

#WINE
#deb http://wine.sourceforge.net/apt/ binary/
#deb-src http://wine.sourceforge.net/apt/ source/
luser@400sc:~$

```

```

luser@400sc:~$ sudo apt-get install nmap
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  nmap
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 575kB of archives.
After unpacking 1933kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  nmap
Install these packages without verification [y/N]? y
Get:1 http://ubuntu-backports.mirrormax.net hoary-backports-staging/universe nma p 3.81-2build1~5.04ubp1 [575kB]
Fetched 575kB in 11s (50.0kB/s)

Preconfiguring packages ...
Selecting previously deselected package nmap.
(Reading database ... 94075 files and directories currently installed.)
Unpacking nmap (from .../nmap_3.81-2build1~5.04ubp1_i386.deb) ...
Setting up nmap (3.81-2build1~5.04ubp1) ...

luser@400sc:~$ sudo apt-get install nessus
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libgd-gif1 libnessus2
Suggested packages:
  nessusd
The following NEW packages will be installed:
  libgd-gif1 libnessus2 nessus
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 400kB of archives.
After unpacking 1233kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hoary/main libgd-gif1 1.3-5 [62.8kB]
Get:2 http://us.archive.ubuntu.com hoary/main libnessus2 2.2.3-1 [93.5kB]
Get:3 http://us.archive.ubuntu.com hoary/main nessus 2.2.3-3 [244kB]
Fetched 400kB in 4s (92.0kB/s)

Preconfiguring packages ...
Selecting previously deselected package libgd-gif1.
(Reading database ... 94097 files and directories currently installed.)
Unpacking libgd-gif1 (from .../libgd-gif1_1.3-5_i386.deb) ...
Selecting previously deselected package libnessus2.
Unpacking libnessus2 (from .../libnessus2_2.2.3-1_i386.deb) ...
Selecting previously deselected package nessus.
Unpacking nessus (from .../nessus_2.2.3-3_i386.deb) ...
Setting up libgd-gif1 (1.3-5) ...

Setting up libnessus2 (2.2.3-1) ...

Setting up nessus (2.2.3-3) ...

luser@400sc:~$

```

---

### Post by kag3musha on 2005-09-21
Perhaps I am wrong..maybe I should have said "updated versions"?

Again I am new here and may have stated my request incorrectly.

Nessus is currently at: 2.2.5
Nmap is currenty at: 3.90

Both versions available via apt-get or Synaptic are old versions.

---

### Post by Technoviking on 2005-09-21
[QUOTE=kag3musha]
Nessus is currently at: 2.2.5
Nmap is currenty at: 3.90
[/QUOTE]

Nmap 3.81 is the latest version in Breezy, I will make a backport for 3.90 once it makes it into Breezy.

I will check on Nessus.

Mike

---

### Post by Technoviking on 2005-09-21
I have made debs for nessus 2.2.4, which is the latest in Breezy. I will try to get them uploaded later.

Mike

---

### Post by N8MAN1068 on 2005-10-05
any luck on the debs?
I'm trying to install Nessus 2.2.5 using the .sh file, and it does not want to install...or even start to install.

is there an extra repository that I should add? I did a clean install of Breezy.

---

### Post by zamroot on 2005-11-26
hi..

this is my first post here..i'm really interested to use nessus in ubuntu becoz it is simple and very user friendly..but the main problems is out dated..

i have the same problem like N8MAN1068 when installing nessus 2.2.6 from .sh file..problem with openssl header..

another problem is about nessusclient..anyone have success experience  installing this program on ubuntu?

the latest nessus version --> 2.2.6
nessusclient version --> 1.0.0

tq

p/s: sory for my bad english :smile:

---

### Post by arphe_el on 2005-11-30
hello!

is there any default set-up for the nessus to run? 

the following questions I have in mind are the following
nessusd host: (in my case its 192.168.1.102)
port: 1241 (is there any port information and their uses)
login: given
passwd: given

then when i click on login "could not open a connection" 

any information or set-up that i need to know? thank you and GODspeed!

---

### Post by sjoeboo on 2005-12-01
both jsut backported fine for me.

nmap version: 3.93
nessus version: 2.2.5

will notify john/list.

---

### Post by strikeforce on 2005-12-01
Your repo's are I believe incorrect.  There is no extra's I believe.  If there is I haven't used em.

Get rid of your backports line and insert this one.

```

## Backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

```

---

### Post by sysmin on 2005-12-13
[QUOTE=zamroot]
another problem is about nessusclient..anyone have success experience  installing this program on ubuntu?

the latest nessus version --> 2.2.6
nessusclient version --> 1.0.0

[/QUOTE]
I have installed the NessusClient with no problems. I have the development libraries installed and I running a custom vanilla kernel 2.6.14.3, so I am not sure if there would be any problems using a machine with a standard kernel image. 

Another point, I have not tried to connect the NessusClient to any version other than Nessus 3.0, so I am not sure if that would work.

[QUOTE=arphe_el]hello!

is there any default set-up for the nessus to run? 

the following questions I have in mind are the following
nessusd host: (in my case its 192.168.1.102)
port: 1241 (is there any port information and their uses)
login: given
passwd: given

then when i click on login "could not open a connection" 

any information or set-up that i need to know? 
[/QUOTE]

This may be a stupid question but did you go through and create a user for use in Nessus? Also, if you have done that are you getting the Digital Certificate screen where it is asking you to accept the certificate? Run 'man nessusd' for some more information.

---

