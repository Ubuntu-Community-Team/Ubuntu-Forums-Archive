---
title: "VMware WinXP virtual machine kills keyboard and mouse on Ubuntu host"
date: 2010-05-03
forum: Virtualisation
---

### Post by relic70 on 2010-05-03
I have VMware Player 3.0 installed on Ubuntu 10.04 with a Windows XP virtual machine.

During the boot process of the Windows VM the keyboard and mouse lock up and are no longer functional on host or guest. The Caps Lock and Scroll Lock lights on the keyboard are flashing.

This behavior began after I upgraded to 10.04 this week.

The same VM on VMware Player 3.0 worked perfectly on the Ubuntu 9.10 host.

I've seen somewhat similar problems posted, but they all appeared to occur on Windows or Mac hosts.

Any insights would be appreciated.

---

### Post by dcstar on 2010-05-05
> **relic70 said:**
> I have VMware Player 3.0 installed on Ubuntu 10.04 with a Windows XP virtual machine.

During the boot process of the Windows VM the keyboard and mouse lock up and are no longer functional on host or guest. The Caps Lock and Scroll Lock lights on the keyboard are flashing.

This behavior began after I upgraded to 10.04 this week.

The same VM on VMware Player 3.0 worked perfectly on the Ubuntu 9.10 host.

I've seen somewhat similar problems posted, but they all appeared to occur on Windows or Mac hosts.

Any insights would be appreciated.

Get Player 3.1

---

### Post by relic70 on 2010-05-05
> **dcstar said:**
> Get Player 3.1

The latest version is 3.0.1, which I have.

I was able to take a new Win XP image and successfully get it installed and running with Player 3.0.1 on Lucid. So, back in business again, after a bit of a hassle to redo my previous work.

That still doesn't answer why the other vm didn't transfer smoothly from Karmic to Lucid.

---

### Post by relic70 on 2010-05-07
Thanks to posts by "calc" and "TJet1.8" in this forum post

[http://ubuntuforums.org/showthread.php?t=1469854](http://ubuntuforums.org/showthread.php?t=1469854)

I was able to restore Player and the Windows XP VM operability after a kernel update in Lucid the other day.

The simple command from "calc" was

sudo vmware-modconfig --console --install-all

to update the kernels manually that Player apparently does not accomplish as it indicates after a new kernel install. 

"TJet1.8" added the caveat that one must have your build environment set first which I apparently did. He gives instructions on how to do so.

---

### Post by dcstar on 2010-05-09
> **relic70 said:**
> The latest version is 3.0.1, which I have.
........
No, the latest version is 3.1.0 build-256557 which is specifically stated by VMware to be 10.04 compatible, the others are not.

---

