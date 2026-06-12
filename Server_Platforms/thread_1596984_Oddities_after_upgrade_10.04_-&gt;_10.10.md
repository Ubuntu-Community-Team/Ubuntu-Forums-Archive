---
title: "Oddities after upgrade 10.04 -&gt; 10.10"
date: 2010-10-14
forum: Server Platforms
---

### Post by ahhyes on 2010-10-14
Hi Guys,

I followed the instructions to upgrade my Ubuntu server from 10.04 to 10.10 (using the dist upgrade command).

At the end of the process it reported there were no errors and a reboot was required. Rebooted. Logged in as root and I see some inconsistencies:

> Linux server 2.6.35.6-server #1 SMP PREEMPT Wed Sep 29 10:05:02 EST 2010 x86_64                            GNU/Linux
Ubuntu 10.10

Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)

  System information as of Fri Oct 15 10:47:55 EST 2010

  System load:  0.0                 Processes:           112
  Usage of /:   11.1% of 269.51GB   Users logged in:     1
  Memory usage: 20%                 IP address for eth0: 172.16.0.245
  Swap usage:   0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

Ubuntu 10.04.1 LTS

Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)

  System information as of Thu Oct 14 17:57:00 EST 2010

  System load:  0.08                Processes:           123
  Usage of /:   11.0% of 269.51GB   Users logged in:     2
  Memory usage: 25%                 IP address for eth0: 172.16.0.245
  Swap usage:   0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

5 packages can be updated.
0 updates are security updates.

*** System restart required ***

> root@server:~# /usr/lib/update-notifier/apt-check --human-readable
0 packages can be updated.
0 updates are security updates.Something is borked with the motd updating.

It looks like something is updating the motd twice, the second update contains incorrect information. Any ideas?

---

### Post by ahhyes on 2010-10-15
*bump*

---

### Post by Dragonsong on 2010-10-15
It's not just you, I have the same problem.

---

### Post by James78 on 2010-10-16
I had that problem awhile ago, and fixed it. Go into the file /etc/motd.tail, delete everything in it, and the problem will be fixed. ;)

---

### Post by ahhyes on 2010-10-16
> **James78 said:**
> I had that problem awhile ago, and fixed it. Go into the file /etc/motd.tail, and delete everything in it, and the problem will be 100% fixed (1st message will still update, etc etc, everything back to normal). ;)

That's done the trick! Fixed :) thanks man :)
:guitar:

---

### Post by mansonthomas on 2010-10-16
Get the same issue,

emptying the /etc/motd.tail as James78 told fix the problem !

Thanks James78 !

---

### Post by webappl on 2010-11-08
> **mansonthomas said:**
> Get the same issue,

emptying the /etc/motd.tail as James78 told fix the problem !

Thanks James78 !

I had the same issue. However, there was not a /etc/motd.tail file on my computer.
Strangely, the problem fixed automatically.

---

