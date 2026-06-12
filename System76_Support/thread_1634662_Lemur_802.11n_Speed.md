---
title: "Lemur 802.11n Speed"
date: 2010-11-30
forum: System76 Support
---

### Post by rokstar on 2010-11-30
I recently upgraded my router to an 802.11n.  The maximum speed that shows in network manager is 54Mb/s.  My router supports speeds of 300Mb/s.  Is there a way to increase the network throughput? My signal strength is strong, so is there some configuration issue that I haven't taken into account?  Thanks for any help!

---

### Post by isantop on 2010-12-01
Do you have the stock wireless card or the Intel Upgrade?

---

### Post by rokstar on 2010-12-01
I think I do.  lspci shows this:

Network controller: Intel Corporation Ultimate N WiFi Link 5300

---

### Post by isantop on 2010-12-01
That would bee it then. Currently, Intel WiFi cards don't support N-mode on Ubuntu, and the router/card are falling back to G mode, which runs at 54 Mbps. I expect they'll have the kinks with N mode worked out by 11.04 next April, though I can't make any guarantees. (It's Intel who's currently working on it.)

---

### Post by rokstar on 2010-12-01
Thanks for the info!

---

