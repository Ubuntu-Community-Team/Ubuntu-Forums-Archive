---
title: "fingerprint problem with serval laptop"
date: 2011-10-12
forum: System76 Support
---

### Post by mahermali on 2011-10-12
Hi
I have Serval Laptop
I need to know if someone got success in running the fingerprint in this laptop

I've tried fprint but it didn't recognized the device.

Any suggestions?

Thanks

---

### Post by Toz on 2011-10-12
There is also fingerprint GUI and ThinkFinger (depending on your system). Have a look at: [https://launchpad.net/~fingerprint]("https://launchpad.net/~fingerprint") to see if your system is supported by one of these other solutions.

```
lsusb
```
will get you the device codes you need.

---

### Post by isantop on 2011-10-13
Are you using Ubuntu 11.04 or later? The fingerprint reader support is broken in these releases due to PAM issues, which we're shooting to have resolved in time for 12.04 LTS.

---

### Post by mahermali on 2011-10-18
I'll give it up
I have another problems when upgrading to Ubuntu 11.10
Thanks guys

---

