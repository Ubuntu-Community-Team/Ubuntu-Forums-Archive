---
title: "[server] How to display start up message when running ?"
date: 2010-11-01
forum: Server Platforms
---

### Post by ponsfrilus on 2010-11-01
Hello,
   I'm looking for the way to display this message :

> 
Linux server 2.6.32-25-generic-pae #45-Ubuntu SMP Sat Oct 16 21:01:33 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Mon Nov  1 10:10:47 CET 2010

  System load:  0.0                Processes:           88
  Usage of /:   69.1% of 15.04GB   Users logged in:     1
  Memory usage: 43%                IP address for eth0: aaa.bbb.ccc.ddd
  Swap usage:   1%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

0 packages can be updated.
0 updates are security updates.

Last login: Fri Oct 29 09:54:17 2010 from xxx.yyy.com


which is the default when connecting through ssh on a server install. 

Thanks in advance!

---

### Post by erlendoos on 2010-11-26
You could make a shell script to generate the content and output it to /etc/motd, which stands for Message Of The Day.

Then make the script run as a service or via cron.

---

### Post by erlendoos on 2010-11-26
Perhaps this would be a perfect spot to start the script first time
[http://ubuntuforums.org/showpost.php?p=4937189&postcount=2](http://ubuntuforums.org/showpost.php?p=4937189&postcount=2)

---

### Post by ponsfrilus on 2010-11-26
> **erlendoos said:**
> /etc/motd, which stands for Message Of The Day.

This is exactly what I was looking for! 
Thank you very much erlendoos, these 5 stars are for you:
:KS:KS:KS:KS:KS

---

