---
title: "Why is this download showing up?"
date: 2015-05-14
forum: Server Platforms
---

### Post by reswob on 2015-05-14
It's been a few years since I've used or built an Ubuntu server.  I recently installed the latest version, used just about all the defaults, chose the SSH install and set it up as a syslog-ng server.  The HD is about 750 GB which should be plenty of space for what I'm doing as the logs I'm collecting grow by about 1 MB per day.  The other day I came in and the server was out of space.  Upon investigation, I found I had a large file that had showed up.  I deleted it, since I had not configured the server to download it.  But it showed up again and locked my machine.  

-rw-r--r-- 1 root   root   789129572352 May 13 06:27 /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_vivid-security_main_source_Sources.bz2

So it looks like it's some kind of security update?  But since I had not configured this for automatic updates, why is it downloading this and why is it so big?

Thanks.

BTW, searching for that string through the forums really doesn't work, so if this has been answered before, please just point me to the post.

---

### Post by SeijiSensei on 2015-05-14
Does "latest version" mean 15.04 or 14.04LTS?  I strongly recommend using only LTS versions on any production server.  Something is obviously very wrong with the installation you have now.  The uncompressed version of the equivalent file on 14.04 is 396K.

---

### Post by reswob on 2015-05-15
15.04

If I have to I'll reinstall, it's easy enough to export and import the syslog-ng config.  But I figured I'd check to see if there was a solution for this first.

---

### Post by harold-fritz on 2015-05-25
I have a similar problem with Ubuntu Server 15.04: 
When I execute  "apt-get update" begin to download the file  /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_vivid-security_main_source_Sources.bz2,  and never stop to grow, inclusive use the whole file system (520GB): is  it a error of ubuntu or I have a bad setting in my server?? [-o

---

### Post by SeijiSensei on 2015-05-25
I cannot seem to reproduce this problem.  I installed 15.04 Server in a VirtualBox virtual machine, then ran "update" and "dist-upgrade" and everything worked correctly.  I have no files in /var/lib/apt/lists/partial.  Maybe try deleting everything in that directory and running the upgrade again?

---

### Post by harold-fritz on 2015-05-25
Many Thansk SeijiSensei, I deleted the folder and the lock file and all is working good again!!!! \\:D/\\:D/=d>=d>=d>

> **SeijiSensei said:**
> I cannot seem to reproduce this problem.  I installed 15.04 Server in a VirtualBox virtual machine, then ran "update" and "dist-upgrade" and everything worked correctly.  I have no files in /var/lib/apt/lists/partial.  Maybe try deleting everything in that directory and running the upgrade again?

---

### Post by SeijiSensei on 2015-05-25
Well, I think you need to restore the folder.
```
sudo mkdir /var/lib/apt/lists/partial
```

Glad the fix worked.  I was just guessing!

---

