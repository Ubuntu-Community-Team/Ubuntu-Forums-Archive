---
title: "Not shutdown only reset"
date: 2014-02-04
forum: System76 Support
---

### Post by dmery on 2014-02-04
I  have a Galapago Ultrabook Pro. I bought it one month ago. Now when I tried to shutdown only reset my computer.
Thanks in advance for helping me
Danmery

---

### Post by krishna.988 on 2014-02-06
Can you elaborate a bit? you are unable to shutdown is that what you mean?

---

### Post by Erik1984 on 2014-02-07
What if you try it from the terminal?
```
sudo shutdown -h now
```

---

### Post by ahlgren on 2014-02-12
I have an older System76 netbook with 5 or 6 users and if another user forgets to logout, shutdown will reboot instead.  That might be what is happening with your system.

---

### Post by Buster95 on 2014-02-20
Same problem here, only using a 32 bit desktop running Linux Mint 15 Cinnamon.
Shutdown and restart produce a restart. Sudo shutdown -v or sudo shutdown -h produces the same restart. I can only "crash-stop" my system by holding down the power button during the inevitable restart.

My problem seemed to start after an upgrade to the latest stable LibreOffice, which seemed to trigger a kernel update to 3.8.0.35.53. The logs don't show anything amiss that I can recognise.

I have since reverted the LibreOffice, which had no positive effect. I have yet to pluck up the courage to revert the kernel to 3.8.0-19.30 which was the previous kernel (I think). I'm a bit afraid to dig the hole a little deeper.

---

### Post by dmery on 2014-02-21
Yes I am unable to shutdown, computer only reset. I am the only user on my laptop. Sometimes, when i shutdown it,  the computer is off but 1 minute after that computer is on again.
Thanks,

---

### Post by thewizardz on 2014-02-26
hi,

I have the galago as well, and it happens to me sometimes too. I'm the only one using the laptop, so is definitely not what ahlgreen mentioned. but I noticed that it only happens when I have the charger plugged in, so if I'm on battery it doesn't happen. Anyway, in my case, is only from time to time, so is not so annoying, but it raises even more questions as of why is not a persistent issue. dmary, does your restart happens all the time? can you try when you run on batteries?

---

### Post by Matt12334 on 2014-03-10
This is a BIOS issue, and System76 sent me a fix which took about 10 minutes to install. You'll likely need to contact support for them to send you the necessary fix, but I can confirm that it worked perfectly :)

---

