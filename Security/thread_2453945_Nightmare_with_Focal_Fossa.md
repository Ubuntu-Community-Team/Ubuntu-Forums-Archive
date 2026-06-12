---
title: "Nightmare with Focal Fossa"
date: 2020-11-19
forum: Security
---

### Post by adagio on 2020-11-19
About a week ago I upgraded from 18.04 to 20.04.1. Worked OK for a week, some strange phenomena, double letters typed in a Gmail emails when only pressing one key at one point, the categories on the snap store disappeared at one point as well (returned later), a search that returned tens of results in the snap store returned only three results for some reason when rerun (again went back to all results later).

However, yesterday I started to get a dummy dialog, asking for the password to unlock the keyring, appearing on boot up. That is booting up offline and online. Tried reinstalling on the basis that I might have installed a rogue application, but this time the dialog appeared as soon as I ran the software updates after installing and rebooting (an offline install).

Tried running rkhunter and various other tools, only result and from the former of interest was that it pointed out there were two large applications using shared memory, firefox and snap-store, these being the two applications showing signs of being hacked.

There is another dimension to this.  I logged into my online banking four days ago using firefox without any issues, tried yesterday, it got to the screen asking for my security code to log in, and the input box would not accept any characters being typed into it, I typed but nothing appeared in the box.  Tried chromium, Windows 10 / Edge, safari on my iPhone with both wifi and mobile data connections (my mobile operator and wifi are the same company, Virgin), booting from the Focal Fossa install CD as well.  I also tried with a VPN.  Got a friend in another locality to try with another ISP and it worked fine.  Not sure what is going on here but it's something fishy.

Reinstalled 18.04 after this, but I could do to get 20.04.1 working as it will run 64 bit virtualbox VMs, and I have a 64 bit Windows 10 partition.

[Edit] Correction, it is possible to run 64 bit VMs on Bionic Beaver, the BIOS was not set up for VT-x usage.  There isn't that much urgency to upgrade now.

---

### Post by EuclideanCoffee on 2020-11-19
Yes, that's very odd. Keep us posted. I don't think there is anything inherit to 20.04 LTS that would cause these issues. Perhaps your quarrel is with snap-store?

---

