---
title: "another error updating sources..."
date: 2005-07-03
forum: Repositories &amp; Backports
---

### Post by robertobech on 2005-07-03
I saw some post of problems similar to mine, but nothing is working to fix my problem. Since I'm not really a Linux pro, maybe it's a good idea to ask around the forums...

When updating my sources I always get this error:
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

How can I solve it? Here is my sources.list

```

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


#deb http://sg.archive.ubuntu.com/ubuntu hoary main restricted
#deb-src http://sg.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb http://sg.archive.ubuntu.com/ubuntu hoary-updates main restricted
#deb-src http://sg.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
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

#deb ftp://ftp.nerim.net/debian-marillat stable main
#deb ftp://ftp.nerim.net/debian-marillat unstable main
#deb ftp://ftp.nerim.net/debian-marillat testing main

```

---

### Post by pwab on 2005-07-06
I've got the exact same problem. Found a solution yet?

p!

---

### Post by n6mod on 2005-07-06
Looks like something got corrupted. I'm seeing the same thing here:

```
W: GPG error: http://us.archive.ubuntu.com hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
``` 

Also, I'm getting MD5sum failures trying to install libdts-dev:

```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdts/libdts-dev_0.0.2-svn-1_amd64.deb  MD5Sum mismatch
```

---

