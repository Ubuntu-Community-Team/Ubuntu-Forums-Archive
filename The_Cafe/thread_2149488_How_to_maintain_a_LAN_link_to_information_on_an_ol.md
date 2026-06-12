---
title: "How to maintain a LAN link to information on an old, semi-retired family PC?"
date: 2013-05-28
forum: The Cafe
---

### Post by Plumtreed on 2013-05-28
I have pretty much retired an old PC that labours under less 1GB RAM and an older CPU.......it contains 2 HDD that contain a fair amount of important, at least to me, information and photos. There is also a fair amount of space that might be handy as additional storage. It is happily running Ubuntu 10.04LTS. It has a wireless connection to our LAN but could be easily linked via Ethernet.

I would like to link to it periodically to look at and exchange files..........all of our home/LAN PCs run on Ubuntu....no Windows.

I'm looking for suggestions as to the best way to maintain a link that would provide access to these HDDs............I think the RAM available would be too weak for a server application?

---

### Post by mastablasta on 2013-05-29
how much ram does it have then? and what kind of older CPU?

i am running a desktop on 256MB, 1,2Ghz CPU

for simple server 512MB is plenty.

---

### Post by mips on 2013-05-29
Any server app would be fine. You can use ftp, nfs, samba etc

---

### Post by lykwydchykyn on 2013-05-29
SSH would be simplest to set up.  Most file browsers can connect to a remote computer over ssh/sftp.

Just install openssh-server on the old system.  Done.

---

### Post by Plumtreed on 2013-05-29
@mastablasta.............circa 2001, 512mb Ram and 1.2GHZ Celeron......do you use Ubuntu Server?

@mips..........thanks!

@lykwydchykyn..........It does sound like the simplest way to go but implications are that it may have inherent security problems?

---

### Post by CharlesA on 2013-05-29
I'd probably run debian minimal (no GUI) on it as ubuntu server might be too heavy for it.

As long as you use a strong password for ssh, you should be "OK"

---

### Post by lykwydchykyn on 2013-05-29
> **Plumtreed said:**
> 
@lykwydchykyn..........It does sound like the simplest way to go but implications are that it may have inherent security problems?

Not sure where you got that idea from; ssh is as secure (if not moreso) than other file sharing systems.

---

### Post by CharlesA on 2013-05-29
> **lykwydchykyn said:**
> Not sure where you got that idea from; ssh is as secure (if not moreso) than other file sharing systems.

Encryption is awesome. ;)

SSH is susceptible to brute force attacks, but if you are just using it internally, that shouldn't be a problem.

---

### Post by Plumtreed on 2013-05-30
Thanks, I'm using SSH and it does the job as suggested.............and Is really pretty staight forward. I guess I was hoping there would be something more intuitive for other family members to use. Most are not interested in things 'IT'!

---

### Post by mastablasta on 2013-05-30
> **Plumtreed said:**
> @mastablasta.............circa 2001, 512mb Ram and 1.2GHZ Celeron......do you use Ubuntu Server?


I use chrunchbang with XFCE desktop (based on debian 6 = old stable). you tube videos in full screen are a bit laggy but in enlarged size are ok. just enough for my kid to watch some cartoons and heavy maschinery at work ;-)
.
> **Plumtreed said:**
> Thanks, I'm using SSH and it does the job as suggested.............and Is really pretty staight forward. I guess I was hoping there would be something more intuitive for other family members to use. Most are not interested in things 'IT'!

i use SSH with key. i think user in this case needs to have a copy of the key and password. nut sure if brute force is easy on these...

anyway - you need a FTP server or rather sFTP. then you will be drag and drop the files to the server. Filezilla is one choice. maybe someone knows something lighter on resoruces.

to administer the server from another mashcine via browser you can use webmin.

---

### Post by CharlesA on 2013-05-30
> **Plumtreed said:**
> Thanks, I'm using SSH and it does the job as suggested.............and Is really pretty staight forward. I guess I was hoping there would be something more intuitive for other family members to use. Most are not interested in things 'IT'!

Check out NFS: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

It'll probably be easier to drag and drop than SSH (unless you use sshfs).

---

### Post by lykwydchykyn on 2013-05-30
> **Plumtreed said:**
> Thanks, I'm using SSH and it does the job as suggested.............and Is really pretty staight forward. I guess I was hoping there would be something more intuitive for other family members to use. Most are not interested in things 'IT'!

Depending on which desktops you are using, you should be able to set up network locations in the file managers of the other computers to easily access the shares.  

Let me ask this: how would you envision a friendly file-sharing service to look?  Because there are tons of options, from raw file-sharing protocols to fancy browser-based Dropbox-like solutions.

---

### Post by Plumtreed on 2013-05-30
Has anybody tried or is using Mosh?

---

### Post by Plumtreed on 2013-05-30
> **lykwydchykyn said:**
> Depending on which desktops you are using, you should be able to set up network locations in the file managers of the other computers to easily access the shares.  

Let me ask this: how would you envision a friendly file-sharing service to look?  Because there are tons of options, from raw file-sharing protocols to fancy browser-based Dropbox-like solutions.

I guess I picture a 'setup' that can be accessed as simply as if the files are freely available as any on the 'client' machine......with little or no terminal use, 

Say, once set up, browse to a location, drag&drop, flexible integration of the 'server'.

---

### Post by lykwydchykyn on 2013-05-30
OK, there should be *no terminal use required* for someone to browse the computer over ssh.  If the clients are using Nautilus or Thunar or PCManFM, they can enter "ssh://addressofserver" as the location, and be able browse the filesystem on the server.  In dolphin, it's "fish://addressofserver".  If you have the ability to resolve hostnames on your LAN (some routers do this automatically), even better.

I use dolphin on my system, so I don't know what this looks like under other file browsers, but under "Places" I can click "Network" and there's a wizard that guides me through setting up a shortcut to a network share using WebDAV, FTP, Samba, or SSH.  All very simple, no terminal required.  I'm assuming Nautilus and others have a similar feature.

---

### Post by Plumtreed on 2013-05-30
Many thanks for your help and patience regarding a 'project' that now appears to be so easy and obvious.

Nautilus does the job in very easy to follow steps and is simple enough to use in 12.04LTS......we can use SSH, SFTP and FTP without making any drastic changes.

.....your help is very much appreciated!

---

