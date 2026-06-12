---
title: "Ubuntu 15.10 host, Ubuntu Server 16.04 Client using Virtualbox - Crashing"
date: 2016-05-10
forum: Virtualisation
---

### Post by ktz84 on 2016-05-10
I'm able to install the OS without any issue. I am able to get all the services and everything setup fine however about 40 mins the virtualbox sessions just stops. My other VMs continue to run so it's not virtualbox itself that is stopping but something to do with this particular setup. I've set up an owncloud server on it. At setup I chose and OpenSSH server & Mail Server and then owncloud installed Apache, PHP7 and I installed mariadb. I've had 3 servers now running 16.04 and all do the same thing. Two owncloud servers (trashed the first one and started again to see if that resolved issues but same problem on the new) one and a gitlab server. I have a 4 core AMD cpu with 16GB of RAM of which 2GB was given to each of the two VM and 2 cores. I increased the RAM on the owncloud one to 4GB and the CPU cores to 3 however that made no difference either. Both have hardware  acceleration enabled, and this worked without issue under 14.04 clients. I have pae enable and disabled and that made no difference. I reduced the usb from 3.0 to 2.0 and then 1.1 still crashes.

Anybody else experience this. Basically what happens is the server stops serving requests. You go to the virtualbox screen and the screen is black and doesn't respond to keypresses or mouse clicks and is clearly dead so I power it off and restart. Same thing.

The version of virtualbox running on the host is the one from the Ubuntu Repositories and not the oracle respositories. I cannot upgrade my host to 16.04 as I'm stuck on 15.10 until AMD releases drivers for 16.04 as the open source drivers do not work with my dual monitor setup.

---

### Post by QDR06VV9 on 2016-05-10
> **ktz84 said:**
> I'm able to install the OS without any issue. I am able to get all the services and everything setup fine however about 40 mins the virtualbox sessions just stops. My other VMs continue to run so it's not virtualbox itself that is stopping but something to do with this particular setup. I've set up an owncloud server on it. At setup I chose and OpenSSH server & Mail Server and then owncloud installed Apache, PHP7 and I installed mariadb. I've had 3 servers now running 16.04 and all do the same thing. Two owncloud servers (trashed the first one and started again to see if that resolved issues but same problem on the new) one and a gitlab server. I have a 4 core AMD cpu with 16GB of RAM of which 2GB was given to each of the two VM and 2 cores. I increased the RAM on the owncloud one to 4GB and the CPU cores to 3 however that made no difference either. Both have hardware  acceleration enabled, and this worked without issue under 14.04 clients. I have pae enable and disabled and that made no difference. I reduced the usb from 3.0 to 2.0 and then 1.1 still crashes.

Anybody else experience this. Basically what happens is the server stops serving requests. You go to the virtualbox screen and the screen is black and doesn't respond to keypresses or mouse clicks and is clearly dead so I power it off and restart. Same thing.

The version of virtualbox running on the host is the one from the Ubuntu Repositories and not the oracle respositories. I cannot upgrade my host to 16.04 as I'm stuck on 15.10 until AMD releases drivers for 16.04 as the open source drivers do not work with my dual monitor setup.
See if this is relevant: [https://forums.virtualbox.org/viewtopic.php?f=3&t=69075](https://forums.virtualbox.org/viewtopic.php?f=3&t=69075)

---

### Post by ktz84 on 2016-05-10
Hi Runrickus. Things now seem to have settled. Both gitlab and owncloud servers are staying up a the minute. I have owncloud on 3 cores still but gitlab on 2 cores so no convinced on the 2 core theory but I'll see how things pan out first. Finger crossed.

---

### Post by QDR06VV9 on 2016-05-10
Indeed Finger's crossed.
I know in my case 1 cpu was the solution. But that dose not mean it will be the same for you.
Keep us posted though.
Kind regards

---

