---
title: "Home Server Security"
date: 2009-03-17
forum: Security
---

### Post by GriFF3n on 2009-03-17
I have all my parts ready to go for my home server as well as my DynDNS setup so I can access my files away from home, but I'm concerned about security. I have a couple of Windows boxes on my local network along with my Ubuntu box. I'm afraid that after I set everything up I will be open to attacks. My main purpose for my server is file sharing, accessing files away from home and torrents. Any help would be appreciated. Thanks!

GriFF

---

### Post by bodhi.zazen on 2009-03-17
I suggest you access the files, over the Internet, via ssh.

There is a nice client for Windows, winscp.


Only forward your ssh port.

See [AdvancedOpenSSH - Community Ubuntu Documentation]("https://help.ubuntu.com/community/AdvancedOpenSSH")

---

### Post by dot2kode on 2009-03-17
Look into Putty if you are looking for a ssh client to access your server...It has always treated me nicely ;)

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

---

### Post by GriFF3n on 2009-03-17
Thanks fellas, I know SSH is supposedly "secure", I'm just not sure how secure it truly is. Is there anything I should do to protect the Windows Boxes on my network? I have a firewall and antivirus, is that enough? Also, are there any SSH apps i can use on a jump drive? Thanks again for the help!

GriFF

---

### Post by brian_p on 2009-03-17
> **GriFF3n said:**
> Thanks fellas, I know SSH is supposedly "secure", I'm just not sure how secure it truly is.

Set up correctly (the default Ubuntu package is) and used sensibly  you will find ssh to be incredibly secure.

---

### Post by bodhi.zazen on 2009-03-17
> **GriFF3n said:**
> Thanks fellas, I know SSH is supposedly "secure", I'm just not sure how secure it truly is. Is there anything I should do to protect the Windows Boxes on my network? I have a firewall and antivirus, is that enough? Also, are there any SSH apps i can use on a jump drive? Thanks again for the help!

GriFF

yes.

You can use Winscp and putty from a usb or flash drive (they do not need to be installed).

Protect your windows boxes as you normally would.

And see the link I gave you for securing ssh (change the port, keys, etc ... )

---

### Post by GriFF3n on 2009-03-17
> **bodhi.zazen said:**
> yes.

You can use Winscp and putty from a usb or flash drive (they do not need to be installed).

Protect your windows boxes as you normally would.

And see the link I gave you for securing ssh (change the port, keys, etc ... )

Will do bodhi.zazen. One more question. I've set everything up so that I can access my home server over WAN through SSH, but I'd like to be able to manipulate files like an FTP program can through drag n drop. I logged in through Putty and it just gave me remote control of the home server. Anyway to do this securely? Thanks again for all your guys help. This is one of the main reasons I LOVE UBUNTU!!!

GriFF

---

### Post by bodhi.zazen on 2009-03-17
Use winscp on windows for a gui, ftp like interface (you can drag and drop).

From Linux, use sshfs (which will mount the share locally).

[http://winscp.net/eng/docs/screenshots](http://winscp.net/eng/docs/screenshots)

---

### Post by GriFF3n on 2009-03-17
> **bodhi.zazen said:**
> Use winscp on windows for a gui, ftp like interface (you can drag and drop).

From Linux, use sshfs (which will mount the share locally).

[http://winscp.net/eng/docs/screenshots](http://winscp.net/eng/docs/screenshots)

Was able to use FileZilla to SFTP into the box. So far so good. A little more configuring and she'll be set. Thanks a bunch for all the help bodhi.zazen. I wish these forums had REP points cause I'd give you a bunch ;)

GriFF

---

### Post by mayer213 on 2009-03-18
Well I think yo must first study your own connectivity device. If it's just a new type of a connectivity device it must have a guide on how to secure the computer that using it.

---

