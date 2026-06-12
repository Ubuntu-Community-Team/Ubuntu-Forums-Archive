---
title: "Never seen a number this low on login: 1 package can be updated."
date: 2015-06-04
forum: Security
---

### Post by Lido on 2015-06-04
I've got two 12.04 LTS servers on similar hardware that I set up at the same time a few years ago. I just updated both a few days ago and one of them (one with more packages installed), is saying "1 package can be updated." on the login welcome screen while the other one has 12 that can be updated. Normally there's a lot held back so that number has never been lower than 10 from what I can remember. Of course my security paranoia has been triggered. Any suggestions?

```
Welcome to Ubuntu 12.04.5 LTS (GNU/Linux 3.2.0-29-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Thu Jun  4 09:21:46 PDT 2015

  System load:  0.09               Processes:           82
  Usage of /:   5.6% of 145.61GB   Users logged in:     0
  Memory usage: 8%                 IP address for eth1: 192.168.1.138
  Swap usage:   0%

  Graph this data and manage this system at:
    https://landscape.canonical.com/

12 packages can be updated.
9 updates are security updates.

New release '14.04.1 LTS' available.
Run 'do-release-upgrade' to upgrade to it.
```

```
Welcome to Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-33-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Thu Jun  4 09:22:04 PDT 2015

  System load:  0.01               Processes:           186
  Usage of /:   4.1% of 914.55GB   Users logged in:     0
  Memory usage: 50%                IP address for eth1: 192.168.1.129
  Swap usage:   0%                 IP address for eth0: 192.168.1.130

  Graph this data and manage this system at:
    https://landscape.canonical.com/

1 package can be updated.
1 update is a security update.

New release '14.04.1 LTS' available.
Run 'do-release-upgrade' to upgrade to it.


Your Hardware Enablement Stack (HWE) is supported until April 2017.
```

This machine is behind a firewall, but is a web/mail server so the following ports are open:

```
$ netstat -an | grep LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:465             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.130:1009      0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.129:443       0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.129:993       0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.130:9988      0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:389             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     
tcp6       0      0 :::389                  :::*                    LISTEN  
```

---

### Post by cariboo on 2015-06-04
There's nothing wrong from the info you've given us. What you are seeing happens quite often with my home server.

---

### Post by Lido on 2015-06-04
Ok, thanks. I've just never seen the number of files that need to be updated so low.

---

### Post by cariboo on 2015-06-04
Here a screenshot of when I logged into my server a couple of minutes ago, I'm running 14.04, but the principal is the same.

---

### Post by vasa1 on 2015-06-04
> **cariboo said:**
> Here a screenshot of when I logged into my server a couple of minutes ago, I'm running 14.04, but the principal is the same.

Hi, is there a way for desktop *buntu users to get the same (or similar) screen output without using **ssh**? I'm particularly interested in the line with ***** System restart required *****?

---

### Post by cariboo on 2015-06-04
Ssh client is installed by default on Ubuntu and derivatives, so the quickest and easiest way to view the motd is to:

```
ssh localhost
```

The output from the command looks like this:

```
Welcome to Ubuntu Wily Werewolf (development branch) (GNU/Linux 3.19.0-20-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

Last login: Thu Jun  4 20:47:34 2015 from localhost
```

The scripts that create the motd are located in /etc/update=motd.d

---

### Post by Lido on 2015-06-05
> **cariboo said:**
> Here a screenshot of when I logged into my server a couple of minutes ago, I'm running 14.04, but the principal is the same.

Thanks. Weird. I don't think I've ever seen zero at all.

---

### Post by fugu2 on 2015-06-06
> **vasa1 said:**
> I'm particularly interested in the line with ***** System restart required *****?
```

$ cat /etc/apt/apt.conf.d/50unattended-upgrades | head -n 49 | tail -n 2
// Automatically reboot *WITHOUT CONFIRMATION*
//  if the file /var/run/reboot-required is found after the upgrade 

```

---

