---
title: "Upgrade 11.10 to 12.04 beta reboot issue!"
date: 2012-04-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by antisomnic on 2012-04-12
I just installed ubuntu 11.10 through wubi and then through software update updated to 12.04. It got to the end and asked me to reboot and when I did my computer just perpetually restarts when I choose ubuntu in the boot menu. I can't get into it at all. Has anyone else run into this problem? Do I have to install it all over again?

---

### Post by cariboo on 2012-04-12
Can you get into recovery mode?

---

### Post by antisomnic on 2012-04-12
i'm not sure there's enough time before it reboots but what key do I press? I have used ubuntu in the past but never had to do recovery mode.

---

### Post by cariboo on 2012-04-13
Hold down the shift, while the system is going through post, you should see the grub menu, where you can select recovery mode.  Once at the menu, select ***Network***, this should enable the network, then select root. Once at the prompt type:

```
sudo apt-get -f install
```

The above command should fix any broken packages, and allow you to boot to a desktop.

---

