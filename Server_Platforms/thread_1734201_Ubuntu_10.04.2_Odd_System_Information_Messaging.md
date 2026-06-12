---
title: "Ubuntu 10.04.2 Odd System Information Messaging"
date: 2011-04-20
forum: Server Platforms
---

### Post by cdnjay on 2011-04-20
I'm not sure why but after tonights updates:

> dhcp3-client 3.1.3-2ubuntu3.2
dhcp3-common 3.1.3-2ubuntu3.2
initscripts 2.87dsf-4ubuntu17.1
krb5-multidev 1.8.1+dfsg-2ubuntu0.9
libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.9
libgssrpc4 1.8.1+dfsg-2ubuntu0.9
libk5crypto3 1.8.1+dfsg-2ubuntu0.9
libkadm5clnt-mit7 1.8.1+dfsg-2ubuntu0.9
libkadm5srv-mit7 1.8.1+dfsg-2ubuntu0.9
libkdb5-4 1.8.1+dfsg-2ubuntu0.9
libkrb5-3 1.8.1+dfsg-2ubuntu0.9
libkrb5-dev 1.8.1+dfsg-2ubuntu0.9
libkrb5support0 1.8.1+dfsg-2ubuntu0.9
libpolkit-gobject-1-0 0.96-2ubuntu0.1
linux-firmware 1.34.7
logrotate 3.7.8-4ubuntu2.1
sysv-rc 2.87dsf-4ubuntu17.1
sysvinit-utils 2.87dsf-4ubuntu17.1

The system information that prints when I logon with SSH prints twice.  The current version and the version that was current when the updates were applied.  I'm not sure which of these updates might have caused this to occur but it happened on 3 Ubuntu 10.04.2 servers that I applied updates to.

> Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Tue Apr 19 23:02:36 CST 2011

  System load:  1.03               Temperature:          37 C
  Usage of /:   11.9% of 17.41GB   Processes:            85
  Memory usage: 34%                Users logged in:      0
  Swap usage:   4%                 IP address for bond0: ##.#.#.#

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Tue Apr 19 19:34:35 CST 2011

  System load:  0.93               Temperature:          37 C
  Usage of /:   11.9% of 17.41GB   Processes:            83
  Memory usage: 19%                Users logged in:      0
  Swap usage:   0%                 IP address for bond0: ##.#.#.#

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

5 packages can be updated.
0 updates are security updates.

Last login: Tue Apr 19 22:55:59 2011 from 10.0.1.2

Any thoughts?

Thanks,

Jason

---

### Post by johandicap on 2011-04-20
I get a similar message when logging in via ssh! Mine only mentions system load etc. once though.


```

Linux minerva 2.6.32-30-generic-pae #59-Ubuntu SMP Tue Mar 1 23:01:33 UTC 2011 i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

 System information disabled due to load higher than 1

Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Wed Apr 20 11:56:41 CEST 2011

  System load:  0.08               Processes:           71
  Usage of /:   92.0% of 35.14GB   Users logged in:     0
  Memory usage: 14%                IP address for eth0: x.x.x.x
  Swap usage:   0%

  => / is using 92.0% of 35.14GB

  Graph this data and manage this system at https://landscape.canonical.com/

12 packages can be updated.
7 updates are security updates.

Last login: Wed Apr 20 12:01:43 2011 from x.x.x.x

```

---

### Post by cdnjay on 2011-04-21
I deleted /etc/motd.tail and it seems to be acting properly again.

> sudo rm /etc/motd.tail

Or, if you want to play it safe.

> sudo mv /etc/motd.tail /etc/motd.tail.old2

Jason

---

### Post by johandicap on 2011-04-21
Perfect, thanks cdnjay!

(I wonder why this file was created/updated during the update..? :)

---

### Post by dgermann on 2011-04-23
cdnjay--

Thanks! Worked for me today. Now we'll see if it generates a new message when there are updates.

---

### Post by bdoe on 2011-05-05
I had this problem as well on my server. The funny thing was, I did a wipe and clean reinstall because I transferred my server to new hardware, and I guess whatever update caused this issue just happened to be pushed at the same time, so I thought it was something *I* had managed to screw up!

Your solution fixed the problem, and saved what's left of my hair!

---

