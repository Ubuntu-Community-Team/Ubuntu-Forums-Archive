---
title: "Ubuntu Server on Live USB with Persistent Storage?"
date: 2013-09-01
forum: Server Platforms
---

### Post by MACscr on 2013-09-01
Id like to run Ubuntu Server 12.04 LTS off an USB flash drive, but I really want it to pretty much run from memory. Id also prefer to have some persistent storage for obviously apps that are installed and configurations, etc. This type of thing appears to be really easy to do with the desktop version, but not the server edition that I obviously want to be as minimal as possible so I can just build off it. Suggestions?

---

### Post by ibjsb4 on 2013-09-01
You could just do a standard server install to your flash drive and use ext2 file system so your flash will last longer (not as many calls to it).

Why do you want a server install on flash?  If you want a minimal install you should look at the mini.iso and maybe do a terminal only install.  The mini.iso is a 27M download compared to 600+MB server download.

The mini.iso can also be installed to flash drive using [Unetbootin]("http://unetbootin.sourceforge.net/#other").

---

### Post by MACscr on 2013-09-01
Thanks for the reply, but not the direction I am looking for.

Its pretty standard these days to run the OS for storage servers (nas/san) on flash drives. Each node is going to be for a Ceph cluster and all standard hard drives are going to be used for that purpose.

---

### Post by MACscr on 2013-09-01
> **ibjsb4 said:**
> You could just do a standard server install to your flash drive and use ext2 file system so your flash will last longer (not as many calls to it).

Why do you want a server install on flash?  If you want a minimal install you should look at the mini.iso and maybe do a terminal only install.  The mini.iso is a 27M download compared to 600+MB server download.

The mini.iso can also be installed to flash drive using [Unetbootin]("http://unetbootin.sourceforge.net/#other").

Will the mini iso do live boot?

---

### Post by sudodus on 2013-09-02
Yes, from the 13.04 version, see [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073") and [this link]("http://ubuntuforums.org/showthread.php?t=2155713&p=12698910#post12698910") where it is described.

---

### Post by MACscr on 2013-09-02
Unfortunately that wont work either as I need to use 12.04 LTS.

---

### Post by sudodus on 2013-09-02
> **MACscr said:**
> Thanks for the reply, but not the direction I am looking for.

Its pretty standard these days to run the OS for storage servers (nas/san) on flash drives. Each node is going to be for a Ceph cluster and all standard hard drives are going to be used for that purpose.

Maybe this link will help you using RAM

[http://ubuntuforums.org/showthread.php?t=1499338](http://ubuntuforums.org/showthread.php?t=1499338)

---

### Post by sudodus on 2013-09-02
> **MACscr said:**
> Unfortunately that wont work either as I need to use 12.04 LTS.

I can understand that you want to use an LTS, but why do you ***need*** it?

---

### Post by nerdtron on 2013-09-02
> **MACscr said:**
> Thanks for the reply, but not the direction I am looking for.

Its pretty standard these days to run the OS for storage servers (nas/san) on flash drives. Each node is going to be for a Ceph cluster and all standard hard drives are going to be used for that purpose.

I have 3 ceph nodes and 3 OSD each, I installed the FULL OS on a SanDisk Cruzer Fit 8GB and it works as expected. Just remove remove the swap during installation and "noatime" and "nodiratime".
Same setup was also done on OpenNebula nodes. OS on the flash drive. No internal hard drives.

---

### Post by MACscr on 2013-09-02
Thanks nerdtron. How long have you been running it in production?

sodus, yes, I have to use the LTS version based on the the fact that Ceph is the most tested on 12.04 LTS. Thanks for the idea though.

---

### Post by nerdtron on 2013-09-02
Just about 3 months. I think you are worried about the read/write cycles in flash drives? That is where the "noatime" and "nodiratime" helps to lower the read/write operations in the flash drives. But then again, flash drives will not last longer than hard drives.

---

### Post by MACscr on 2013-09-02
Nerd, so I followed your advice and just did a normal install with those options that you mentioned, but im wondering how I can set the logs to use buffer memory versus disk for storage. I already have rsyslog setup to do remote, but it still does local, right? If so, how do i make sure the local is only written to memory until shutdown, etc?

---

### Post by nerdtron on 2013-09-02
I had the idea to mount a CephFS or RBD image in the /var/log directory. I didn't implemented it though, but you can try if you want too. I'm don't mind about the short life span of flash drives, it's a ceph cluster after all. If a node goes down due to a dead flash drive, I can get another one and add it to the cluster, then remove the dead one.

---

