---
title: "Recommedations for platform-independent secure cloud-storage"
date: 2014-10-31
forum: Security
---

### Post by johanm2 on 2014-10-31
Currently I am using Dropbox as platform-independent cloud-storage, but according to Snowden that is not good.
He recommends SpiderOak.
After doing some research I found the following platform-independent (Microsoft, Apple, Linux, iOS, Android), secure, cloud-storage providers:
[LIST]
[*]SpiderOak (free 2 GB)
[*]Wuala (5 GB $0.99)
[*]Mega (50 GB free)
[*]Tresorit (5 GB free)
[/LIST]
Which one do you recommend and why?

---

### Post by Habitual on 2014-10-31
Funny Snowden doesn't mention the common-sense approach...
I recommend encrypting your data (files) with a **strong password** *before* uploading.
You do that, then any of those service would be fine.

---

### Post by bashiergui on 2014-10-31
> **Habitual said:**
> Funny Snowden doesn't mention the common-sense approach...
I recommend encrypting your data (files) with a **strong password** *before* uploading.
You do that, then any of those service would be fine.
+1

---

### Post by CharlesA on 2014-11-01
Owncloud gets my vote, but I don't store any sensitive stuff on it and the syncing client leaves quite a bit to be desired.

---

### Post by Bucky Ball on 2014-11-01
I've just been looking at Mega. You might be interested in this:

[https://mega.co.nz/#about](https://mega.co.nz/#about)

I've never used a cloud before and it's the upload and download speeds that concern me. Specially with free clouds. Thoughts?

---

### Post by CharlesA on 2014-11-03
No experience with it myself, but I host my own stuff, and that's how I like it. There are probably better packages to use than owncloud, but it works for me.

As far as "Free cloud storage" goes - if you are going with a third party - be sure they support two factor auth and encryption.

---

### Post by mastablasta on 2014-11-04
spider oak uses keys, but their transmission is quite slow (at least for us in Europe). still to store a few small files for backup it is good enough.

owncloud has so many options but their client really is lame. only syncing, no backup/one way transfers and many other things missing.
but you need your own server for this so in that case there are also other options like WD cloud and such.

---

### Post by johanm2 on 2014-11-04
Which platform-independent encryption program do you recommend? Truecrypt, 7-zip, ...
Same for a password manager.

---

### Post by mastablasta on 2014-11-05
for password manager you have keepassx and keepass2. 
truecrypt is now dead, though still used and forked. : 
[https://truecrypt.ch/](https://truecrypt.ch/)
[https://veracrypt.codeplex.com/](https://veracrypt.codeplex.com/)

some difference between Ciphershed and veracrypt explaine by their devs: [https://forum.truecrypt.ch/t/veracrypt-or-ciphershed/449/3](https://forum.truecrypt.ch/t/veracrypt-or-ciphershed/449/3)


there are other programs that will do ecryption for you. for example aes crypt etc. : [https://www.aescrypt.com/linux_aes_crypt.html](https://www.aescrypt.com/linux_aes_crypt.html)

---

### Post by povlhp on 2014-11-05
I use 1password for passwords across iOS, Windows and Mac. No Linux version though.

And if I need something to be really secure a truecrypt container. You can mount them over the network using most types of filesystem emulators.

I used dropbox, and the free 50GB box.net (I was an initial user). Another solution is to get your own virtual server. $15/year brings you 128-256MB memory, 10-80GB of disk space, typicaly 100GB/traffic per month or thereabouts. Look at lowendbox.com for the good offers. They change all the time. You can use them for VPN, and you can export your truecrypt container using NFS, SMB, WebDAV etc.

---

