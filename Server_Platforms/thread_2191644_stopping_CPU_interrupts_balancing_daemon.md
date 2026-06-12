---
title: "stopping CPU interrupts balancing daemon"
date: 2013-12-03
forum: Server Platforms
---

### Post by Laszlo_Danielisz on 2013-12-03
I have an Ubuntu 12.04.3 LTS server.
Suddenly restarted and when it boots I have the following error:
[B]*Stopping CPU interrupts balancing daemon [ok]

[/B]Do you have any idea how can I solve this?
I'd really appreciate if somebody could help, thank you!

---

### Post by tgalati4 on 2013-12-03
Check the power management settings in the BIOS.  If you have any suspend or sleep settings (say after 1 hour) try turning them off and see if that helps.

Go through dmesg and see if there are any other errors:

```
dmesg | more
```

and 

```
 more /var/log/syslog
```

---

### Post by Laszlo_Danielisz on 2013-12-04
I did that, nothing abnormally appears there. By the way, I have this running on a ESXi 5.1.

---

### Post by tgalati4 on 2013-12-04
What is the hardware that this virtual machine is running?  Are the virtual machine features enabled in the BIOS?  It's possible that it is a bug in how vmware handles stopping of processes before switching to another vm.  This may be an informational message.  Does it continue to boot or does it require you to hit "return" to acknowledge?

---

### Post by Laszlo_Danielisz on 2013-12-04
It is a 2GHz dual core CPU with 700MB allocated RAM and 700GB HDD.
I can't take a look right now at the computer to check the BIOS but I'll do it later on today. For what exactly shall I look?

No it doesn't continue to boot, not even hitting return or ctrl+c, so right now I have no access to all of my data stored in that machine which makes me very sad.

---

### Post by tgalati4 on 2013-12-04
So (if I understand this correctly) the host machine running vmware is OK, it is just the LTS server vm that is not booting?  And you can't access the data on this vm because it won't boot correctly?

You would look for HyperV and related virtual-machine-related features on the motherboard.  I presume that they are already enabled, but depending on the motherboard and processor, hardware support for virtual machines may be limited and that may contribute to strange vm behavior.

Was this server running for a long time and all of a sudden it stopped working?  

Without log messages from the vm, it's difficult to troubleshoot.

---

### Post by Laszlo_Danielisz on 2013-12-04
Thank you for your help tgalati4!

Actually I haven't done yet BUT I managed to attach the vmdk to another Linux machine and mount everything from there, so I have all of my data and nothing is lost :)

---

### Post by tgalati4 on 2013-12-05
If you can attach to the vm, then look through the log files (/var/log) and see what other errors are happening during vm boot.

---

### Post by Laszlo_Danielisz on 2013-12-05
good idea, I'm going to take a look

---

