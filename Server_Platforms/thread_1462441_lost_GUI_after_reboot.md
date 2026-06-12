---
title: "lost GUI after reboot"
date: 2010-04-25
forum: Server Platforms
---

### Post by adellalin on 2010-04-25
Hi I was using Ubuntu 9.10 and was using fireftp ( firefox plugin ) to do some ftp operation. And then I noticed firfox is fozen so I reboot my pc by switching off the power ( restart doesn't work ). When I turn it back on again, no GUI anymore. I was taken to ttyl login commend.

I tried to fix it with Ubuntu 9.10 on CD, it didn't help. 

Please help me ! I need my computer back!

---

### Post by lavinog on 2010-06-07
Are you still having this problem?

Are there any messages saying why the gui isn't starting?
you might be able to check the logs.
From the console:
```

cd /var/log
less Xorg.0.log

less messages

```
Scroll to the bottom of Xorg.0.log and see if it gives any sort of error.
Same with messages.

---

### Post by BobVila on 2010-06-08
It's also worth looking at /var/log/messages to see if anything relevant is in there. Sure sounds like a corrupted xorg.conf file to me, though.

---

### Post by lavinog on 2010-06-08
> **BobVila said:**
> Sure sounds like a corrupted xorg.conf file to me, though.

There shouldn't be a xorg.conf file in a default install.

---

