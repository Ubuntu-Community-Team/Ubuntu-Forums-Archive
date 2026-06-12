---
title: "ubuntu wants to be updated and restarted after every reboot"
date: 2011-05-19
forum: Server Platforms
---

### Post by MarisO on 2011-05-19
Every time I reboot my ubuntu server it shows this:

[FONT=Lucida Console]Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

38 packages can be updated.
21 updates are security updates.

***** System restart required *****[/FONT]


I did:
[FONT=Lucida Console]apt-get update
apt-get dist-upgrade
reboot[/FONT]

But it still shows *** System restart required ***
There is nothing to upgrade:
[FONT=Lucida Console]
~/ $ sudo apt-get upgrade       [/FONT]                                                                        

[FONT=Lucida Console]Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/FONT]

---

### Post by moonpup on 2011-05-20
I had the same issue and found out it is a bug. Just sudo cp /dev/null > /etc/motd.tail

This will clear out that file and then when you login it should show the updated and current status.

---

### Post by MarisO on 2011-05-20
$ sudo cp /dev/null > /etc/motd.tail
bash: /etc/motd.tail: Permission denied

---

### Post by moonpup on 2011-05-21
My mistake, take the > out of the line.

---

### Post by CharlesA on 2011-05-21
Delete /etc/motd.tail

There was a bug where the motd wasn't being updated properly.

---

