---
title: "Default to Older Kernel (Hidden in Submenu)"
date: 2011-09-06
forum: Server Platforms
---

### Post by rickatnight11 on 2011-09-06
Because my RocketRaid 2680 drivers won't run on anything newer than 2.6.38-8, I haven't been able to use newer kernels.  The only way to boot from this kernel version, however, is to manually select the Previous Versions menu from Grub and select the kernel from there.  This means that I'm screwed, if I need to reboot the server remotely.

How can I have grub automatically boot from 2.6.38-8 (after the 5-second timeout)?

---

### Post by drs305 on 2011-09-06
I'm presuming you are asking how to set an entry in a submenu as the default?

I wrote a guide about how to use the new submenu structure in Grub 1.99:
[http://ubuntuforums.org/showthread.php?p=10720316#post10720316]("http://ubuntuforums.org/showthread.php?p=10720316#post10720316")

---

### Post by rickatnight11 on 2011-09-06
Fantastic guide.  All I had to do was update */etc/default/grub* with:
```
...
GRUB_DEFAULT="Previous Linux versions>Ubuntu, with Linux 2.6.38-8-server"
...
```

...and run [FONT="Courier New"]sudo update-grub[/FONT] to commit the changes.  Thanks so much for the help!

---

### Post by drs305 on 2011-09-06
The Grub 1.99 submenu feature is going to give users a bit of a problem until it's use becomes more commonplace. 

I like the submenu structure, which makes things simple for users who want a 'clean' menu but don't want to get under the hood to tweak things. For the rest of us, we just have to do a bit of learning.

Please mark this SOLVED via the 'Thread Tools' link at the top right of the original post if you have no further issues.

Happy Ubuntu-ing !

---

