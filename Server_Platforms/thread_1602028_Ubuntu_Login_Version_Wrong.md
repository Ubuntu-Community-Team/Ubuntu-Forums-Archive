---
title: "Ubuntu Login Version Wrong?"
date: 2010-10-20
forum: Server Platforms
---

### Post by cabbrick1243 on 2010-10-20
This is just a slightly irritating problem, and not of great importance, but for some reason, after upgrading to ubuntu server 10.10 after 10.04, every time I login, the main message shows wrong information.
It reads:

> Linux ******** 2.6.35-22-generic-pae #35-Ubuntu SMP Sat Oct 16 22:16:51 UTC 2010 i686 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Wed Oct 20 22:25:01 EDT 2010

  System load:  0.04                Temperature:         50 C
  Usage of /:   26.0% of 105.52GB   Processes:           92
  Memory usage: 5%                  Users logged in:     0
  Swap usage:   0%                  IP address for eth0: ***.***.***.***

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Mon Oct 11 21:58:41 EDT 2010

  System load:  0.04                Temperature:         50 C
  Usage of /:   29.1% of 105.52GB   Processes:           98
  Memory usage: 49%                 Users logged in:     0
  Swap usage:   0%                  IP address for eth0: ***.***.***.***

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

13 packages can be updated.
8 updates are security updates.

Last login: Wed Oct 20 22:04:15 2010 from *********************.net

Ubuntu 10.04.1? And sudo apt get update or upgrade both report no available updates, 
The output from lsb_release -a reads:
> No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick

Knowing me there is probably something obvious that I am overlooking.

---

### Post by bmathis on 2010-10-20
The file was probably merged instead of written over. Edit /etc/motd, delete the 10.04 info, and add anything else you might want.

---

### Post by Irregular Joe on 2010-10-21
Use the commands:

sudo rm /etc/motd.tail
sudo touch /etc/motd.tail

That will solve it.

---

### Post by Xenomorph on 2011-05-13
> **Irregular Joe said:**
> Use the commands:

sudo rm /etc/motd.tail
sudo touch /etc/motd.tail

That will solve it.

I apologize for bumping an old thread, but this helped fix an issue on our server.

On every login, it would say "*** System restart required ***" - turns out it was just old info in the /etc/motd.tail file!

---

