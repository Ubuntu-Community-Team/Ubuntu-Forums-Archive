---
title: "PanP5: &quot;Networking disabled&quot; after hard shutdown"
date: 2010-10-16
forum: System76 Support
---

### Post by tlroche on 2010-10-16
I've got a model=panp5 running vanilla GNOME Ubuntu 10.04.1 LTS with kernel=2.6.32-25. It was up-to-date as of yesterday, and was running fine until an hour or 2 ago, when I suspended it to do other stuff. Later I heard its fan running loud, and noticed the leftmost status LED was on continuously, not strobing. Apparently the PanP5 had not slept, but the video would not come back on either, despite some typing and mouse fiddling. So I held down the power button until it shutdown.

The panp5 restarted to disk check, which it completed without apparent problem. However, after I logged into Ubuntu, I noticed that, in the panel, NetworkManager had the red '!', and hovering or right-clicking it showed "Network disabled"--i.e. both wire and wireless down.

I tried hitting Fn-F11, but no change in NetworkManager. I did

```
sudo lshw -C network
```

which showed both interfaces disabled. I tried restarting: no change. How to fix?

thankful that my GF's star1 still works, Tom Roche [Tom_Roche@pobox.com]

---

### Post by riseringseeker on 2010-10-17
Two things you could try, one right click the network icon, and see if you can reenable the network there.  The other is you could try "sudo /etc/init.d/networking restart" in a terminal.

Let me know if either of those work.

---

### Post by tlroche on 2010-10-17
> **riseringseeker said:**
> Two things you could try, one right click the network icon, and see if you can reenable the network there.

Already tried that:

> **tlroche said:**
> I noticed that, in the panel, NetworkManager had the red '!', and hovering or right-clicking it showed "Network disabled"

I.e., the only item in the dropdown, when I right-clicked NetworkManager, was "Network disabled"

> **riseringseeker said:**
> The other is you could try "sudo /etc/init.d/networking restart" in a terminal.

That worked! Thanks.

---

