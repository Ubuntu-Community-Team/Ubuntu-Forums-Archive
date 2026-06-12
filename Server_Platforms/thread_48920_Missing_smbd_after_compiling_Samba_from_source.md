---
title: "Missing smbd after compiling Samba from source"
date: 2005-07-14
forum: Server Platforms
---

### Post by etanizar on 2005-07-14
Folks: 

I've been trying to install latest Samba (samba-3.0.14a) on a fresh Ubuntu Hoary, but could not find the smbd, nmbd in /usr/local/samba/bin folder. Other tools such as findsmb, smbclient, and smbstatus are compiled and built properly in that folder.

I have apt-get install build-essential to get the build tools before I started.
Then I extracted samba-latest.tar.gz to ./tmp, run configure, make, and make install with no arguments.

I have tried this a few times, but still cannot find the daemon programs.

Any help is appreaciated. Thanks.

---

### Post by LordHunter317 on 2005-07-14
Without build parmaters, it's hard to tell where it'll be, but it's likely it's /usr/local/samba/sbin, not bin.

And why?  Unless you really must have something it provides, use the packages.

---

### Post by etanizar on 2005-07-14
I cannot find /usr/local/samba/sbin, and even doing find from / does not return smbd.

I tried installing samba from apt-get, but kept getting this error:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.3.6-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.3.6-1_i386.deb)  MD5Sum mismatch

Any suggestions? Thanks.

---

### Post by etanizar on 2005-07-14
Apologies.

Found the folder that you mentioned.
Many thanks ... :)

---

