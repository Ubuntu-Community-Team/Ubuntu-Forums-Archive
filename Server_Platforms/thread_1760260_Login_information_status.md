---
title: "Login information status"
date: 2011-05-16
forum: Server Platforms
---

### Post by moonpup on 2011-05-16
Why is it, that when you login to Ubuntu server it shows the system status information twice? What the system is currently doing and what it did when it booted the first time? Is this normal as I see this stuff twice every time I login?

See below example...

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Mon May 16 19:02:51 EDT 2011

  System load:    0.04              Processes:           102
  Usage of /home: 0.2% of 75.25GB   Users logged in:     0
  Memory usage:   7%                IP address for eth0: 192.168.xxx.xxx
  Swap usage:     0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Mon May 16 18:39:04 EDT 2011

  System load:    0.22              Processes:           104
  Usage of /home: 0.2% of 75.25GB   Users logged in:     0
  Memory usage:   7%                IP address for eth0: 192.168.xxx.xxx
  Swap usage:     0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

44 packages can be updated.
22 updates are security updates.

Last login: Mon May 16 18:58:06 2011

---

### Post by volkswagner on 2011-05-16
This is a bug.  There is a [thread about this]("http://ubuntuforums.org/showthread.php?t=1472327").

I really wish the Ubuntu forum search worked better.  Best to use Google and reference Ubuntu forum with key words.

You can solve issue by deleting or zero out the file.


```
sudo cp /dev/null /etc/motd.tail
```

---

### Post by moonpup on 2011-05-16
Thanks, that fixed it. I did try searching for it but came up empty. Appreciate the help :)

---

