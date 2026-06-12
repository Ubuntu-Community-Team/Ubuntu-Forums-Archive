---
title: "Netboot installation fails to download a file from my local mirror."
date: 2008-01-15
forum: Server Platforms
---

### Post by chris.zeman on 2008-01-15
I am working on a project that will entail a large number of computers to require an Ubuntu installation. The best way to do this in my case is to perform automated netboot installations. 

I can successfully (PXE) boot my test machine into the installer and proceed through the installation process. I have a mirror of archive.ubuntu.com on my server and it appears everything is all set, but it obviously isn't. I select the server as my mirror, but the installer is failing to download a file from the server. Is there any way to find out what file is failing to download?

Here is a copy of my mirror.list:
```
############# config ##################
#
# set base_path    /var/spool/apt-mirror
#
# if you change the base path you must create the directories below with write privlages
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
set nthreads     10
set tilde 0
#
############# end config ##############

deb http://archive.ubuntu.com/ubuntu gutsy main main/debian-installer restricted restricted/debian-installer
deb http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

clean http://archive.ubuntu.com/ubuntu
```

Thank you,
Chris

---

### Post by DATAndrews on 2008-01-18
The problem (as I found out after much agony) is that there is a debian-installer in gutsy-updates and gutsy-security.  What seems to work (so far!)  is the following mirrors.list file:

```

############# config ##################
#
# set base_path    /var/spool/apt-mirror
#
# if you change the base path you must create the directories below with write privlages
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
set nthreads     20
set _tilde 0
#
############# end config ##############

deb http://us.archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu gutsy-proposed main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu gutsy main/debian-installer restricted/debian-installer
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates main/debian-installer restricted/debian-installer
deb http://us.archive.ubuntu.com/ubuntu gutsy-security main/debian-installer
deb http://us.archive.ubuntu.com/ubuntu gutsy-backports main/debian-installer

clean http://us.archive.ubuntu.com/ubuntu

```

I hope this helps.

---

### Post by chris.zeman on 2008-02-21
Cool, thanks!

I forgot to subscribe to this thread and got sidetracked with other things. :)

Thank you,
Chris

---

### Post by hans_olo on 2008-03-04
Thank you, this saved may day (week?) :-)

Cheers, Stefan

---

### Post by olituks on 2008-03-24
Hello,

I have maked a PXE installer server. I use a kick installation file to pilot my unattended installation on my test wks. I have a apache 2 server to distribute the content of the alternate CD installation. 

My client boot normaly over a PXE, TFTP and apache2 but after 1 minute the installer block in a missing file.

Apparently my problem is the same.

Have you a documentation or procedure to avoid this strange problem ?

Thanks in advance and Ubuntu power :lolflag:

---

### Post by olituks on 2008-03-24
Hello, It's ok now.
My error is I use a script to make my mirror and not apt-mirror.
I modify my mirror.list with your addaptation and now all is ok. :guitar:

With the good tools you make a good work :KS

---

### Post by drink on 2008-05-02
This is a critical bug. Looks like Ubuntu is signing its own death warrants. You cannot set up a net installer from the CD alone. This is ridiculous. I hope this works properly in hardy. Someday I hope to go someplace with enough bandwidth to download it.

---

