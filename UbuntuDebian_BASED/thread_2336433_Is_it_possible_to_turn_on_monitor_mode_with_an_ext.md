---
title: "Is it possible to turn on monitor mode with an external wifi connector"
date: 2016-09-08
forum: Ubuntu/Debian BASED
---

### Post by dcpifhq on 2016-09-08
Hi,
(I'm new to this forum so please don't judge me if I did something unregulary here...)

I'm experiencing some issues while trying to enable monitor mode on a Broadcom wireless card.
Here's what I typed in the terminal after some searches (and the errors):
```

root@kali:~# ifconfig wlan0 down
root@kali:~# sudo iwconfig wlan0 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
```


And after some more searching, I realized that Broadcom wireless cards don't support monitor mode.

So my question here is: If I buy an external wifi connector (You know, the one which you have to plug it in manually to your PC),
will I be able to switch to monitor mode, when I buy that?

Any answers would really help!

P.S. As you have probably noticed, I am using Kali Linux.

---

### Post by howefield on 2016-09-14
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

