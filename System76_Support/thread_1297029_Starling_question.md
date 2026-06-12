---
title: "Starling question"
date: 2009-10-21
forum: System76 Support
---

### Post by vttay03 on 2009-10-21
The wireless on my Starling has been acting funny....it seems to be very intermittent and lots of times it will say that's connected but when I go to use the internet it times out waiting for a page to load.  It almost never reconnects when I come out of suspend and I find myself running the following command from the shell to get it up and running:

```

sudo /etc/init.d/NetworkManager restart

```

I haven't done anything to the configuration since I received the netbook (only had it for a week or so).  I assumed the System76 driver had already been in use during factory testing and I didn't need to reinstall/rerun it.  However, is there still something I need to do to activate the System76 driver for better wireless connectivity?  If that isn't it, then what else may be going on?  Any help is appreciated.  I plan on updating to the Karmic Netbook Remix when it and the System76 driver are released.  However, I figured I'd try to look into this in the meantime.

---

### Post by thomasaaron on 2009-10-21
Please establish a wired Internet connection. Then run your system76 driver (Administration > System76 Driver > Install (tab) > Install (button)). When the driver is finished, reboot your computer.

---

### Post by vttay03 on 2009-10-21
Thanks I wasn't sure if I needed to do this or not...after I installed the driver it seems to be significantly better.  Still seems to have some issues coming out of suspend, but in general, it's much more reliable.  Maybe I was confused about the initial setup...was the computer shipped without the System76 driver installed?  For some reason I was under the impression that the driver had been installed at the factory.

---

