---
title: "How can I make wifi work in 14.04?"
date: 2014-03-18
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-03-18
Does it work for you?
I have 2 wifi adapters.
In the liveusb the ralink works.
The older PCI MN730 broadcom I would like to get it working.

I did an update this am, and the RAlink does connect now in the installed os.

The MN 730 light flashes, it sees the wireless router, but never connects.

---

### Post by sdowney717 on 2014-03-18
I first did this using legacy firmware
[http://www.howopensource.com/2012/10/install-broadcom-b43-legacy-wireless-driver-in-ubuntu-12-10-12-04/](http://www.howopensource.com/2012/10/install-broadcom-b43-legacy-wireless-driver-in-ubuntu-12-10-12-04/)

That did not work although it saw the networks.

I then did this
[http://www.howopensource.com/2012/10/install-broadcom-sta-wireless-driver-in-ubuntu-12-10-12-04/](http://www.howopensource.com/2012/10/install-broadcom-sta-wireless-driver-in-ubuntu-12-10-12-04/)
Which caused it to not see any networks.

So I totally uninstalled that STA driver and rebooted.

Then It agains sees all the wireless networks

And I was able to connect one using the mn 730!?

So I have no idea what is what or why what happened to make it connect but it is.
However at a very slow speed of 11mb/sec and the router is only7 feet away from the PC? Wireless router is set to g speeds only.

when the RALink connects, it is 48mb/sec.

---

### Post by sdowney717 on 2014-03-18
something very odd about mn 730 broadcom driver. I disconnect and reconnect and speed now is 1 mb/sec.

I moved antenna to a foot away from router.

---

### Post by sdowney717 on 2014-03-18
plugged in the usb thingy and speed is 54 mb/s
speed on the mn 730 is at 11 mb/sec now,

I will give up on the mn730 for now. Some reason it has locked the pc up twice, num lock cant unlock, so it is locked it hard.
IMO a driver issue becuase until I installed the broacom stuff, nothing odd happened.

any ideas?

---

