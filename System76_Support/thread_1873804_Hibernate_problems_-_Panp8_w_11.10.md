---
title: "Hibernate problems - Panp8 w/ 11.10"
date: 2011-11-01
forum: System76 Support
---

### Post by werewolves on 2011-11-01
I'm having a couple of issues with my brand new Pangolin.  Suspend works like a charm (thank God), but hibernate does not.  The system acts like it is going to hibernate, but when I power back on, it goes to the login screen as though I had shut down.

The other problem I have is that about half of the time when I unplug from power, I get a warning that I have low battery (even though it was at 100%), and it will hibernate (which of course basically means it has shut down because of issue #1).

Frankly, I can live without hibernate, but the other issue is really annoying.  Is there a way to set it to "do nothing" on critical battery?  It isn't an option in the dropdown...

Thanks

---

### Post by werewolves on 2011-11-01
OK, for anyone looking for a solution to part #2 above:
[http://ubuntuforums.org/showthread.php?t=1866533](http://ubuntuforums.org/showthread.php?t=1866533)

Still wonder why it won't hibernate...

---

### Post by isantop on 2011-11-03
Can you check the size of your swap partition versus your RAM? You can look this up in the resources tab of System Monitor.

---

### Post by werewolves on 2011-11-03
I'll look up the exact numbers when I get home, but they are approximately the same.  Around 6GB each.

---

### Post by werewolves on 2011-11-03
Memory: 6030MB
Swap: 5480MB

Is that enough difference to cause an issue?

---

### Post by werewolves on 2011-11-04
Bump

---

### Post by dFlyer on 2011-11-04
My guess is yes if your using all your ram and it needs to be written to the swap space there is not enough room.

---

### Post by werewolves on 2011-11-05
Nope, increasing the swap so that it is larger than the memory does not help.  Still can't return from hibernate.

Any other ideas?

---

### Post by werewolves on 2011-11-07
Hey System76 guys, any thoughts?  Thanks.

---

### Post by isantop on 2011-11-08
The swap being too small was causing your problems earlier. 

How did you go about increasing the swap size? What are the sizes at now?

---

### Post by ruediger.kupper on 2011-12-09
I have the same problem as werewolves: My Thinkpad writes hibernation data, but at next startup, this data is not restored. Actually, the boot.log reads:

```
swapon: /dev/sda6: software suspend data detected. Rewriting the swap signature.

```So there **is** a hibernation image, but it is never restored, just deleted and then a normal boot is performed.

Any idea why this (not) happens?

Regards,
Rüdiger

---

### Post by isantop on 2011-12-12
I know there are some things in our BIOSes that ensure Hibernate works. I'm not very familiar with ThinkPads, so I can't verify that for you. Have you checked your swap sizes?

---

### Post by ruediger.kupper on 2011-12-12
Yes, swap size is larger than physical memory.

---

### Post by isantop on 2011-12-13
Unfortunately, I'm not really sure what would cause that then.

---

