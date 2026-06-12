---
title: "root login message"
date: 2011-06-23
forum: Server Platforms
---

### Post by geohei on 2011-06-23
Hi.

When logging in as root using ssh to my 10.04.2 server, I get:
```
Linux vm-90 2.6.32-21-generic-pae #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Thu Jun 23 12:17:34 CEST 2011

  System load: 0.2               Memory usage: 17%   Processes:       74
  Usage of /:  16.3% of 7.49GB   Swap usage:   0%    Users logged in: 1

  Graph this data and manage this system at https://landscape.canonical.com/

8 packages can be updated.
6 updates are security updates.

Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Sun May 15 11:07:45 CEST 2011

  System load: 0.2               Memory usage: 40%   Processes:       77
  Usage of /:  15.6% of 7.49GB   Swap usage:   0%    Users logged in: 1

  Graph this data and manage this system at https://landscape.canonical.com/

33 packages can be updated.
15 updates are security updates.

Last login: Wed Jun 22 12:46:04 2011
```
1. There are 2 similar "blocks" of information. Why two of them?

2. It shows on both "blocks" that there are updates (packages and security). However "apt-get update" followed by "apt-get upgrade" doesn't update. How can I see which packages need updates and how can I finally uzpdate them?

BTW ... [https://help.ubuntu.com](https://help.ubuntu.com) didn't help.

Thanks,

---

### Post by volkswagner on 2011-06-23
This is a known bug.

Check out [this post]("http://ubuntuforums.org/showpost.php?p=10825039&postcount=2") for a simple solution.

---

### Post by geohei on 2011-06-23
Thanks a lot!

---

### Post by geohei on 2012-11-21
Is this "bug" (?) still present?

```
login as: root
root@192.168.1.90's password:
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-23-generic-pae i686)

 * Documentation:  https://help.ubuntu.com/

  System information as of Mon Nov 19 14:12:01 CET 2012

  System load:  0.27              Processes:           67
  Usage of /:   53.5% of 7.47GB   Users logged in:     0
  Memory usage: 41%               IP address for eth0: 192.168.1.90
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/

3 packages can be updated.
3 updates are security updates.

Last login: Sun Nov 18 13:20:18 2012 from susi.fritz.box
root@vm-90:~# apt-get update
Ign http://security.ubuntu.com precise-security InRelease
Hit http://security.ubuntu.com precise-security Release.gpg
...
Reading package lists... Done
root@vm-90:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-generic-pae linux-image-generic-pae
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```
I login and I get the message that 3 packages can be updates.
I update && upgrade and 0 are upgraded but 2 not.

???

Why aren't they upgraded and why only 2 (i.s.o.) not?

Thanks,

---

### Post by Cheesemill on 2012-11-21
Apt-get update only updates packages that are currently on your system. As kernel updates are new packages instead of updates to existing packages you need to use the command:
```
sudo apt-get dist-upgrade
```

---

### Post by geohei on 2012-11-21
Hmmm ... strange.

I logged in to test your suggestion. It showed ...
```
...
4 packages can be updated.
4 updates are security updates.
...
```
... at login. I did update && upgrade again and now all packages seem to be updated (no updates are shown at login).

How come?

Referring to your previous answer ... you say that my initial 3 updates were "kernel" updates.
How do you see this from the code block I posted that the updates were kernel related?

Thanks,

---

