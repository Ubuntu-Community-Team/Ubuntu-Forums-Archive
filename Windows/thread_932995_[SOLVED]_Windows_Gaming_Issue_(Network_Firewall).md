---
title: "[SOLVED] Windows Gaming Issue (Network Firewall)"
date: 2008-09-29
forum: Windows
---

### Post by Keymaster on 2008-09-29
I'm not sure if the off topic area supports Windows discussions as well.  I have a somewhat unique problem.  My network is behind an ISA server
```

internet => linux router => ISA => gaming rig

```

When trying to play Company of Heroes I get NAT errors.  Any idea how to fix this without cutting out ISA? (Due to a major network configuration the ISA server performs a lot of important fuctions I don't have time to redistribute to other servers)  Thanks.

Moderators: Again if any Windows posts don't belong here, please just delete this, and PM me letting me know

---

### Post by Greyed on 2008-09-29
Er, not getting why it can't just be 

Internet -> Linux router -> Gaming rig.

I don't think it would be possible to answer your question without knowing your network topology and why the gaming rig needs to be behind ISA.

---

### Post by Keymaster on 2008-09-29
The ISA server provides site-to-site VPN connections for my office.  I probably could put the one machine outside the ISA server for gaming, but I do kind of enjoy it blocking all the ad servers when I browse the web ;)  Also I'm kind of curious as to how to do this.

---

### Post by K.Mandla on 2008-09-29
Moved to Windows Discussions. :)

---

### Post by Keymaster on 2008-09-29
> **K.Mandla said:**
> Moved to Windows Discussions. :)

Thanks.  I couldn't find that forum.

---

### Post by Greyed on 2008-09-29
> **Keymaster said:**
> The ISA server provides site-to-site VPN connections for my office.

Chances are you could get the linux router to do the VPN if needed.  Take a look at Openswan for most everything or vpnc for Cisco stuff.

> I probably could put the one machine outside the ISA server for gaming, but I do kind of enjoy it blocking all the ad servers when I browse the web ;)  Also I'm kind of curious as to how to do this.

Firefox + adblockplus works wonders.  Personally I have a Squid proxy plus Adzapper for the local network so the sites my wife and I both browse are a tad snappier.  Again, possible on the Linux box.  :)

---

### Post by Keymaster on 2008-09-29
I have found a workaround that  I am now using successfully.  I just set up a script to adjust which router my machine is using when I launch/exit company of heroes.

---

### Post by Greyed on 2008-09-29
Pardon me as I go perform a V-8-ectomy on my forehead for not thinking of that.  :)

---

### Post by Keymaster on 2008-09-29
lol I personally would prefer to get NAT working through both routers (linux, and isa) just because not knowing how to do stuff I once tried to do bugs me.  If anyone still wants to try this with me, I'm leaving the thread as unsolved right now.

---

