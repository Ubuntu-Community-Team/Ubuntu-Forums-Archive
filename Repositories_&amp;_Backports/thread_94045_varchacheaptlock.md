---
title: "/var/chache/apt/lock"
date: 2005-11-23
forum: Repositories &amp; Backports
---

### Post by buddhagui on 2005-11-23
Hello friends in Ubuntu! I need help. I deleted /var/chache/apt/lock and /var/chache/apt/archives, now I can no longer use apt! Someone please help! I did it because I was in a hurry and had to get something else out of there for lack of space. Now I don't know what's going on. An easy fix?

Thanks in advance

---

### Post by adwait on 2005-11-23
The lock file can be deleted without a problem. The /var/cache/apt/archives folder just stores the deb files that have been previously downloaded and installed.......so deleting them shouldn't theoratically cause a problem. What error are you getting when you try to run apt?

---

### Post by buddhagui on 2005-11-23
chris@ip62:~/The Producers$ sudo apt-get update
E: Archive directory /var/cache/apt/archives/partial is missing.

and the following error when running apt-get upgrade:
chris@ip62:~/The Producers$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
The following packages will be upgraded:
  libnetpbm10 libnetpbm9 linux-386 linux-restricted-modules-common netpbm
5 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
E: Could not open lock file /var/cache/apt/archives/lock - open (2 No such file or directory)
E: Unable to lock the download directory


Please HELP! Thanks,
chris

---

### Post by buddhagui on 2005-11-23
Thanks for the help. I ended up fixing it by recreating the directories and the lock file. Just putting in blank ones is enough and apt does the rest. Again, Thank you for the help.

---

### Post by MikeyXX on 2005-11-23
Thanks for posting your fix.

---

### Post by bfonseca on 2005-11-28
[QUOTE=buddhagui]Thanks for the help. I ended up fixing it by recreating the directories and the lock file. Just putting in blank ones is enough and apt does the rest. Again, Thank you for the help.[/QUOTE]

Hi can you please help me with the problem you had..I have the same problem and I am totally new so I dont understand what you mean by all that.. Can you please give me a step by step fix.. 
Thank you
Brian

---

### Post by towsonu2003 on 2005-11-28
[QUOTE=bfonseca]Hi can you please help me with the problem you had..I have the same problem and I am totally new so I dont understand what you mean by all that.. Can you please give me a step by step fix.. 
Thank you
Brian[/QUOTE]

"Thanks for the help. I ended up fixing it by recreating the directories and the lock file. Just putting in blank ones is enough and apt does the rest. Again, Thank you for the help."

it seems like he did the following in a terminal (applications>accessories>terminal):
```

sudo mkdir /var/cache/apt/archives
sudo touch /var/cache/apt/archives/lock
sudo mkdir /var/cache/apt/archives/partial
sudo apt-get update

```

I hope this will fix it...

---

### Post by atropus on 2005-12-15
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/aptitude/lock
sudo rm /var/lib/dpkg/lock
sudo rm /var/lib/apt/lists/lock
sudo dpkg --configure -a

---

### Post by andrewsomething on 2007-06-15
> **atropus said:**
> sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/aptitude/lock
sudo rm /var/lib/dpkg/lock
sudo rm /var/lib/apt/lists/lock
sudo dpkg --configure -a

I had the same issue. I accidentally deleted the files due to some bad advise concerning a different issue. Running the above commands fixed it for me. Thanks!

(I just wanted to put that on the record so people like me who might stumble upon this page googling the error message know this works.)

---

### Post by frozenjim on 2008-06-28
Confirmed again.

I (foolishly) deleted my cached files because I had (foolishly) created my partition at only 2.5 GB.  Two days later, disk was 100% and I was stuck in the middle of an upgrade.

Followed the advice and I'm back in business - ready to apt-get gparted and resize some partitions.

Thanks.

---

