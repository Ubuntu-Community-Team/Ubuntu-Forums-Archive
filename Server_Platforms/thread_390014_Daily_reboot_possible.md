---
title: "Daily reboot possible?"
date: 2007-03-21
forum: Server Platforms
---

### Post by elyask87 on 2007-03-21
Hello,

I have currently installed Ubuntu 6.10 Edgy server on a pretty old PC lying around. However it seems that after a few days of running the system sort of hangs and I need to do a cold boot. This problem isn't really annoying, but I'm just worried that the constant hard reboots might mess up things since it is isn't going down as it should like a shutdown command.

Is there some way I could set a cron or something similar that would reboot the server daily?

Thanks

---

### Post by Brazen on 2007-03-21
put a file in /etc/cron.daily/ with this in it:```
#!/bin/bash
reboot
```

---

### Post by elyask87 on 2007-03-21
Thanks, hopefully this will keep my server up on a daily basis :)

---

### Post by MJN on 2007-03-21
I'd suggest treating the cause rather than the masking the symptom might be a good idea!

Mathew

---

### Post by markusfarkus on 2007-03-22
Sounds like there is a more serious problem going on there.  Ubuntu shouldn't be totally freezing on you like that.  Linux by nature is designed not to freeze like that, and designed so that you shouldn't have to reboot.

---

### Post by Brazen on 2007-03-22
It sounded like a hardware problem to me, possibly bad RAM.  So unless he wants to spend money on this, addressing the root cause probably isn't an option or even really necessary in this case.

---

### Post by elyask87 on 2007-05-03
No idea what the problem was but now my system has been up for over a month (apart from the shutdown while traveling ;) ).

---

