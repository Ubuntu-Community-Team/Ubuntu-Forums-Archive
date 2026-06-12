---
title: "Ubuntu 8.04 Server and Adaptec AIC-9410 RAID issues"
date: 2009-06-16
forum: Server Platforms
---

### Post by spoolzer on 2009-06-16
Hi all,

I have been searching about my issue for quite some time and I have given up and decided to finally post on the forums for some help. On a side note, I would like to say how helpful these forums have been for me in the past. I usually always find my answer without even having to post anything. In fact, I think this is my first post on the forums! So many thanks to all those who contribute!

Anyways, let's get down to business. We recently obtained and installed Ubuntu 8.04 Server on a [_*SuperMicro 6025B-3B*_]("http://www.supermicro.com/products/system/2U/6025/SYS-6025B-3.cfm"). While installing, we noticed that the RAID controller wasn't detected. So we decided to just use the Ubuntu Software RAID. We found out the hard way that it wasn't the best choice, as our server went down last week, and resulted in having to re-install. 

Now, upon doing my research, I am aware that SuperMicro doesn't support Ubuntu, but has drivers for both Suse and RedHat distros. I have also seen on other posts, that there is a driver available for the SAS controller and can be copied into the /lib/firmware directory when installing. My question is this. If I already have a clean install of Ubuntu, is there a way that I can install the SAS controller driver, setup a RAID 1, put in a new drive, and have the controller build the RAID on the new drive (IE copy everything from the current drive to the new drive thus creating the RAID 1)? The idea is to get the RAID 1 running without having to re-install.

At the same time, is there anyone who can confirm that this driver will work for us? Here is the link to the post and driver that I found:
[http://ubuntuforums.org/showthread.php?t=581462]("http://ubuntuforums.org/showthread.php?t=581462")

Thanks in advance to anyone who can help us through this difficult problem.

---

### Post by spoolzer on 2009-06-30
anyone?

---

