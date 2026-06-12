---
title: "PanP5 on Lucid: wireless is disabled"
date: 2010-04-30
forum: System76 Support
---

### Post by lnxguit on 2010-04-30
I upgraded my PanP5 from Karmic to Lucid (64 bit) last night, and it seems like everything is working so far.
However, I am unable to use the function keys Fn+F11 to turn on the wireless.
Is there a command-line method to enable wireless?

---

### Post by thomasaaron on 2010-04-30
We're getting that on the shop Pangolin too. But the wireless is enabled... just the Fn-F11 isn't really working.

Did you try right-clicking on network manager and enabling wireless?

If that doesn't work, try...
```

sudo modprobe iwlagn
```

---

### Post by lnxguit on 2010-04-30
I did "sudo modprobe iwlagn" and then "lsmod"
iwlagn,iwlcore & mac80211 are all loaded - however, I cannot enable wireless.
Any other ideas?

---

### Post by thomasaaron on 2010-04-30
Please go to System > Admin > Software Sources > Updates (tab) and make sure Proposed and Backports are enabled. Then run your updates and reboot. 

Does that fix it?

---

### Post by lnxguit on 2010-05-01
Thanks - I enabled Proposed and Backports and can now turn on wireless!
Unfortunately, it looks like I'm running into a different bug - my wireless is VERY slow. (went from ~10 megabits/second down to 1 megabit/second.
I am experiencing the same problem on a desktop running Lucid, and haven't solved it yet.

---

### Post by lnxguit on 2010-05-02
hmmm, for some reason my wireless has sped up to normal?
well, I'll call that "solved" even if I don't know why!

---

### Post by thomasaaron on 2010-05-03
Could have been a problem with your access point, then. If it occurs again, I'd try resetting the AP and see if that solves it.

---

### Post by lnxguit on 2010-05-04
Thanks for your help. Yes, my panp5 is working great with Lucid!

---

