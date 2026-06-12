---
title: "dont know how to fix this error message"
date: 2013-10-10
forum: Ubuntu Development Version
---

### Post by rburkartjo on 2013-10-10
ray@ray-Latitude-D630:~$ do-release-upgrade -d
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [198 B]                                                                                          
Get:2 Upgrade tool [1,140 kB]                                                                                                 
Fetched 1,140 kB in 0s (0 B/s)                                                                                                
authenticate 'saucy.tar.gz' against 'saucy.tar.gz.gpg' 
extracting 'saucy.tar.gz'
Can not run the upgrade
This usually is caused by a system where /tmp is mounted noexec. Please remount without noexec and run the upgrade again.
ray@ray-Latitude-D630:~$ 


tks just upgrading from 13.04 to 13.10. of course i have backed up first.

---

### Post by xc3RnbFO8P on 2013-10-10
This:
[http://ubuntuforums.org/showthread.php?t=1454863]("http://ubuntuforums.org/showthread.php?t=1454863")

---

### Post by rburkartjo on 2013-10-10
rin tks for the link still cant upgrade. appreciate the speedy reply.

---

### Post by ptn107 on 2013-10-11
How about
```
sudo do-release-upgrade -d
```

---

### Post by rburkartjo on 2013-10-11
i followed this 
Try this. Just press Ctrl+Alt+T on your keyboard to open Terminal. When it opens, run the command(s) below:

sudo sed -i 's/raring/saucy/' /etc/apt/sources.list
sudo apt-get update && apt-get dist-upgrade
I tried it, and it works.

ref this 
[http://askubuntu.com/questions/302762/upgrading-13-04-to-13-10](http://askubuntu.com/questions/302762/upgrading-13-04-to-13-10)

---

