---
title: "Outdated system information on login being displayed"
date: 2010-10-13
forum: Server Platforms
---

### Post by emgee3 on 2010-10-13
When I log onto my Ubuntu Server 10.04.1, the system information from several boots ago is showing still. The updated current message is shown as well. It's not the end of the world, but it would be nice to fix this. Any ideas? I've included below what it looks like:

```
Linux proxy 2.6.32-25-generic-pae #44-Ubuntu SMP Fri Sep 17 21:57:48 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Thu Oct 14 01:03:25 UTC 2010

  System load:  0.31              Processes:           84
  Usage of /:   14.2% of 8.96GB   Users logged in:     1
  Memory usage: 36%               IP address for eth0: 172.16.10.254
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/

Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Wed Oct 13 04:31:47 UTC 2010

  System load: 1.5               Memory usage: 26%   Processes:       70
  Usage of /:  10.1% of 8.96GB   Swap usage:   0%    Users logged in: 1

  Graph this data and manage this system at https://landscape.canonical.com/

174 packages can be updated.
30 updates are security updates.

*** System restart required ***
Last login: Thu Oct 14 01:01:41 2010 from 172.16.10.20

```

---

### Post by emgee3 on 2010-10-14
Blanking out /etc/motd.tail resolved this problem, per this post: [http://ubuntuforums.org/showthread.php?t=1593161](http://ubuntuforums.org/showthread.php?t=1593161)

---

