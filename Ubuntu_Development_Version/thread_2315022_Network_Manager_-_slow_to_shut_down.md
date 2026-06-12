---
title: "Network Manager - slow to shut down"
date: 2016-02-25
forum: Ubuntu Development Version
---

### Post by sammiev on 2016-02-25
On Feb 20/16 I noticed shutting down times on Ubuntu-gnome 16.04 went from 1 second to 8 seconds.

I installed a few other flavors of Ubuntu 16.04 and all had the same problem.

With Xubuntu and Ubuntu-gnome 16.04 shutting down the Internet connection first before shutting down the computer fixes the problem for shutting down.

Anyone else notice this?

Thanks

---

### Post by MikeMecanic on 2016-02-26
i always disable the network switch before I shut down, but I confirm that it takes about the same time here to shut down with the network switch enable.  Otherwise, it shut down instantly.  Ubuntu today's build. 

Made another observation regarding the network switch, if i close it before shutting down there is only Ubuntu the keeps the previous state on startup.  All other flavors will enable the network switch even if I disable it on startup.  So, they don't keep or memorize the previous state.

Regards,

---

### Post by QDR06VV9 on 2016-02-26
> **sammiev said:**
> On Feb 20/16 I noticed shutting down times on Ubuntu-gnome 16.04 went from 1 second to 8 seconds.

I installed a few other flavors of Ubuntu 16.04 and all had the same problem.

With Xubuntu and Ubuntu-gnome 16.04 shutting down the Internet connection first before shutting down the computer fixes the problem for shutting down.

Anyone else notice this?

Thanks
Yep!   About the same as you notice it.
I think this was the same for about a week with wily when it was in the development stage.(At Least for me)

---

### Post by sammiev on 2016-02-26
Tried most of the 16.04 flavors and they are all the same.

Hope they get this fixed before the release date. :)

Many thanks

---

### Post by Doug S on 2016-02-28
Yes, as of updates of two days ago I am noticing a significant increase in shutdown time. I have also had kernel crash a couple of times during shutdown, but likely related to putting some apparmor profiles into complain mode, as there were 3  that were not working (one was fixed in yesterdays updates). I haven't had the kernel crash issue since putting "/usr/sbin/named" back into enforce mode, and just living with the issue. Note I also tried going back to kernel 4.4.0-7-generic from 4.4.0-8-generic, but it still has the slow shutdown.

My version of Ubuntu is server 64 bit. (I am a few days behind updating my desktop test computer).

---

### Post by sammiev on 2016-02-28
I have been running 4.4.2 since Feb17 with no issues till Feb20. I noticed the problem after updates to net-manager and bind9. Both updates came together the same day.

---

### Post by sammiev on 2016-03-17
There was an update today that corrected this problem.

---

