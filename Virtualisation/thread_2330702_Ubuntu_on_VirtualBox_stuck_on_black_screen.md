---
title: "Ubuntu on VirtualBox stuck on black screen"
date: 2016-07-13
forum: Virtualisation
---

### Post by roshenam on 2016-07-13
I'm very new to Ubuntu and have tried to get it running on a virtualbox virtual machine. I created a new machine, downloaded ubunto 16.04 iso, then loaded that onto the machine and installed it. It then told me I needed to restart the machine after it finished installing and I clicked ok. It then turned black and then displayed the message "intel_rap rapl domains found in package Oalized - upgrade BIOS or use force_addr=Oxaddr" as shown in the attached image. It has been stuck there for 15 minutes now. I would really appreciate any help you guys could give me. Thanks!

** Edit: solved! Thanks

[ATTACH=CONFIG]270094[/ATTACH]

---

### Post by QDR06VV9 on 2016-07-13
I see the same...It might take a little time to populate the first boot.
But Mine dose not take 15 mins maybe 3 or 4 mins.
What is the Host Machine?

---

### Post by QIII on 2016-07-13
Hello!

For the sake of the next person, would you please tell us how you solved the issue?

---

### Post by &amp;KyT$0P# on 2016-07-13
I see the exact same thing.  Nothing really to be "solved" - just wait for the virtual CD to eject, then Power Off the virtual machine and start it again.
(It's a [known bug]("https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes#Known_issues").)

---

### Post by ajgreeny on 2016-07-14
I have seen that same  "intel_rap rapl domains found in package O" error repeated several times on booting any debian based OSs in VBox for a very long time, however it does not cause any delay in the boot process and I get to a full GUI in about 90 seconds or less.

I have never been too concerned about it as the VMs all work perfectly, and boot at normal speed so it seems likely that ypour problem is not related to that error message but something more fundamental.  Have you checked the iso file you used to install Ubuntu VM with the hashes at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) ?

---

