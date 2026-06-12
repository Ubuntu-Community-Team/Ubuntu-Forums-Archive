---
title: "Network usage with no apparent source - a cause for concern?"
date: 2009-10-20
forum: Security
---

### Post by david- on 2009-10-20
Hi,
 
I posted this in the Networking/Wireless section but got no response, so I am re-posting it here.

I have noticed that my system has been sluggish lately. I have had Jaunty 9.04 for a few months now.

When I click on my system monitor, there is a continuous network usage of about 175 KiB/s sending and 5 KiB/s receiving. I don't have any programs open, and the process list indicates all processes as sleeping except for the system monitor.  netstat does not indicate any open connections.

Is this sort of background network usage normal, or is it something to be concerned about in any way?

Thanks,
David

---

### Post by cariboo on 2009-10-20
I would be concerned. Open a terminal and type:

```
netstat -tunlp
```

To check network activity.

---

### Post by cdenley on 2009-10-20
> **cariboo907 said:**
> I would be concerned. Open a terminal and type:

```
netstat -tunlp
```

To check network activity.

I would try that with "sudo", so you can get process names, then I would check the non-listening processes as well.
```

sudo netstat -tunlp
sudo netstat -tunp

```

---

### Post by juancarlospaco on 2009-10-20
[I]Layer 3 Broadcasts, Layer 2 ARP, 
SMB protocol spamm, Seahorse daemon sharing your publick keys, Avahi.[/I]

---

