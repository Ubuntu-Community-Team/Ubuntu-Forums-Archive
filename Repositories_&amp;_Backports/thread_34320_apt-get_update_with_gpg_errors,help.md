---
title: "apt-get update with gpg errors,help"
date: 2005-05-14
forum: Repositories &amp; Backports
---

### Post by lof on 2005-05-14
at the end of the apt-get update process ;

W: GPG error: [http://archive.ubuntu.org.cn](http://archive.ubuntu.org.cn) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.org.cn](http://archive.ubuntu.org.cn) hoary-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.org.cn](http://archive.ubuntu.org.cn) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I am not English,
who can help me with some simple words ?
thx :)

---

### Post by Xian on 2005-05-14
Have you enabled the hoary-updates and hoary-security repositories.

Add these lines to your /etc/apt/sources.list file:

```
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
```

---

### Post by lof on 2005-05-14
yes ,I do 
but I use the fallowing instead:


deb [http://archive.ubuntu.org.cn/ubuntu](http://archive.ubuntu.org.cn/ubuntu) hoary main restricted universe multiverse
deb [http://archive.ubuntu.org.cn/ubuntu](http://archive.ubuntu.org.cn/ubuntu) hoary-security main restricted universe multiverse
deb [http://archive.ubuntu.org.cn/ubuntu](http://archive.ubuntu.org.cn/ubuntu) hoary-updates main restricted universe multiverse

ubuntun.org.cn is a mirror of the ubuntun.com
It is faster for me

---

### Post by Xian on 2005-05-14
I don't have this issue you are describing. 
Backup your current sources.list and then use mine in its place.

It would be good to see if my config will work on your box.
After saving my config run your apt update:

sudo apt-get update

```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted universe

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
deb http://archive.ubuntu.com/ubuntu/ hoary universe main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

#Security Repositories
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# Backport Repositories
#deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
#deb http://manno.name/debian/ breezy cvs

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe

```

---

### Post by lof on 2005-05-14
ok,I will try 
but maybe I can't get the result today .
I post message here  through a proxy ,
so if I use your sources.list ,I must through a proxy to test it.

but ,there is no time for me ,the electirc will be turn down soon.
..............

however, thank you Tian !
I will be back tommorrow !
Good night! (maybe you are on day time  :razz: but I find your name is like to be a chinese charactor)

---

### Post by lof on 2005-05-15
AHAH,
I am back ,
Xian:
I tried your sources.list,the errors disappeared :)
thx!

I guessed that because of one of the repostories in my sources,list,
then I use my sources.list and comment the  respostory from CD,
It works well now:)

sorry for my poor English and even print your nickname wrongly :grin:

---

### Post by pnix on 2005-05-16
mine still got error with  hoary-updates. below is come from my sources.list 

Fetched 717kB in 48s (14.9kB/s)
Reading package lists... Done
W: GPG error: [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

if I replace it with Xian sources.list. I get...

Fetched 3770kB in 4m29s (14.0kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz)  MD5Sum mismatch
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

 ](*,)  ](*,)

---

