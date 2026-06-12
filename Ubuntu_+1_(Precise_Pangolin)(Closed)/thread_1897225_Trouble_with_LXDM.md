---
title: "Trouble with LXDM"
date: 2011-12-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Sworddragon on 2011-12-18
Since libglib2.0-0 got an update from version 2.30 to 2.31 lxdm-binary is using 100% cpu time of one core on my system after a reboot. A solution is to downgrade libglib2.0-0 to version 2.30. I thought somebody else has this issue too and I will see here a thread for this. Has somebody else with LXDM this problem too?

I have already made a bugreport for this: [https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/901407](https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/901407)

I hope the bug will be fixed fast because downgrading libglib2.0-0 will break a lot of packages.

---

### Post by MG&amp;TL on 2011-12-18
I think LXDM is being replaced:


[http://lubuntublog.blogspot.com/2011/07/lightdm-on-lubuntu.html]("http://lubuntublog.blogspot.com/2011/07/lightdm-on-lubuntu.html")

so shouldn't need to.

---

### Post by Sworddragon on 2011-12-18
I'm not really using Lubuntu. It's originally from an Ubuntu CD - I installed just the packages that I wanted afterwards. I don't know if I want to use LightDM (Will LXDM still be available in the repository?) so I should try to find a solution for this problem. My system was running now for 10 days and it seems that a downgrade doesn't work anymore because the screen is black if LXDM starts.


Edit: I tried a SIGSTOP on the process and this is working. I can't logout anymore until I use a SIGCONT but this is acceptable for a workaround.

---

