---
title: "Ubuntu 20.04 'GNU GRUB' appear after updates and then unable to boot with  5.4.0-37"
date: 2020-06-10
forum: Ubuntu Development Version
---

### Post by dprevost on 2020-06-10
Yesterday, I launch the software update which updates everything and on reboot, I was presented the "GNU GRUB 2.04" command line.

I had to follow[ those instruction ]("https://askubuntu.com/questions/883992/stuck-at-grub-command-line")to help me boot ubuntu. I even had to use the [boot-repair tool]("https://help.ubuntu.com/community/Boot-Repair") else, the "GNU GRUB 2.04" command line was always reappearing at each reboot.

And even at that step, it was not booting sucessfully, I had to go to the advance menu to select an old kernel version **5.4.0-34** or** 5.4.0-32** to be able to boot because version **5.4.0-37** was always stalling to the second line of the log something like "Loading in memory"

Does anyone encounter those problems?
Does anyone knows problems with **5.4.0-37?**
How can I stop loading by default the **5.4.0-37 **so my laptop can boot sucessfully?
If anyone knows how to fix this with **5.4.0-37 **would be the best option.

Thanks

---

### Post by dino99 on 2020-06-10
If the previous kernels are well booting, but not the last one, then the problem is about that kernel.
Be sure linux-generic / build-essential are first installed. Then purge that last kernel (2 headers + 2 modules + image) and reinstall it for testing with the next reboot.

---

### Post by dprevost on 2020-06-10
Hi dino99 thanks for you reply,

- Be sure linux-generic / build-essential are first installed. --> I will check
- Then purge that last kernel (2 headers + 2 modules + image)  --> I'm not a mega ubuntu user.... do you mean some king of sudo apt-get remove XXX???
- and reinstall it for testing with the next reboot. --> I image the software update tool will do so for me!

---

### Post by dprevost on 2020-06-11
I remove 5.4.0-37 but after software update it then used 5.4.0-38 and everything is fine now.

Thanks for you help [COLOR=#000000]dino99[/COLOR]

---

