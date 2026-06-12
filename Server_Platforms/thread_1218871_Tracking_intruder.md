---
title: "Tracking intruder"
date: 2009-07-21
forum: Server Platforms
---

### Post by dragos2 on 2009-07-21
I discovered an intruder on one server, I got his ip address but may be a proxy, I will start a tcpdump and let it run a few days maybe I can track him further.

Any suggestions of what else to do? The server is firewalled, only 22 opened, patched to day,
the passwords are not easy to break so I am wondering how did he got in.

This server is not important and does not contain sensible information so I am not worrying to much
but I want to track him down.

Any other suggestions?

---

### Post by druhboruch on 2009-07-21
I run into similar problem recently. I only had mysecureshell on this box.
Please, post back if you find out something.

---

### Post by shredkingj on 2009-07-21
Try taking a look in your auth.log file to see if they were brute forcing a login.  Something I always do for internet facing servers that need SSH running is to install Fail2ban (there are other similar packages).  It will detect failed login attempts, and after a certain number of times, perform an action (usually an iptables rule to deny their IP address for a period of time).

---

### Post by dragos2 on 2009-07-21
> **shredkingj said:**
> Try taking a look in your auth.log file to see if they were brute forcing a login.  Something I always do for internet facing servers that need SSH running is to install Fail2ban (there are other similar packages).  It will detect failed login attempts, and after a certain number of times, perform an action (usually an iptables rule to deny their IP address for a period of time).


The logs were tainted. He deleted his tracks.

I will investigate further but I am afraid of an undisclosed remote exploit.

---

### Post by cariboo on 2009-07-21
The people that are writing root kits are getting pretty smart. This past weekend one of the forum members posted a link to a web site that offered the free download of a rootkit with source code (don't go looking for it, as the thread has been jailed) I accessed the site using Jaunty in a vm and downloaded the code and ran it on one of my test systems. As I installed it, right before my eyes, it got rid of all it's files, included the tar I downloaded, and removed it self from all the logs.

I tried all the recommend tools, chkrootkit rkhunter and tiger, none of them even detected it. The only way you could tell it was running, is that it was listening on port 11111.

I did find some tracks, but they were encrypted, and not knowing the encryption method, it was pretty hard to tell what was going on.

I am in the process of reinstalling the os, as I couldn't find a way to get rid of it.

---

### Post by shredkingj on 2009-07-21
> The logs were tainted. He deleted his tracks.

The intruder must have gotten elevated privileges somehow.  Who knows what else they did, probably would be best to just reinstall.

---

### Post by dragos2 on 2009-07-22
> **cariboo907 said:**
> The people that are writing root kits are getting pretty smart. This past weekend one of the forum members posted a link to a web site that offered the free download of a rootkit with source code (don't go looking for it, as the thread has been jailed) I accessed the site using Jaunty in a vm and downloaded the code and ran it on one of my test systems. As I installed it, right before my eyes, it got rid of all it's files, included the tar I downloaded, and removed it self from all the logs.

I tried all the recommend tools, chkrootkit rkhunter and tiger, none of them even detected it. The only way you could tell it was running, is that it was listening on port 11111.

I did find some tracks, but they were encrypted, and not knowing the encryption method, it was pretty hard to tell what was going on.

I am in the process of reinstalling the os, as I couldn't find a way to get rid of it.

chkrootkit and company are a little outdated, unfortunately. 
It seems that some of these rootkits can hide files in a similar way that ADS works for NTFS.
And combined with encription there is nothing that we can do.

I am still waiting for tcdump to catch something.

---

