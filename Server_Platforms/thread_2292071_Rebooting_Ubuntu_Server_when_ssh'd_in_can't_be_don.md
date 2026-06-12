---
title: "Rebooting Ubuntu Server when ssh'd in can't be done"
date: 2015-08-24
forum: Server Platforms
---

### Post by fizgig on 2015-08-24
Fresh install of 64bit vivid server.  Got a LAMP stack installed and openssh.

**Scenario 1:  No monitor, I'm only ssh'd in**
When I try to do a "sudo reboot", my ssh tession is terminated and am quickly not able to ping the server anymore as expected - but it doesn't reboot.  It just stays disconnected from the network with the power light still on.  If I hold the power button down long enough, the computer turns off and I'm then able to power it back on again and it boots fine.  Before hard powering it off when it's stuck, I try plugging in a monitor but nothing is shown on the screen.

**Scenario 2:  Monitor Connected, I'm logged in at the keyboard, I'm also ssh'd in**
If I try rebooting via ssh again with the monitor plugged in to see if I can see anything, I do see the shutdown sequence (the blinking dots) and then the bios is shown for awhile and then it's just black.  I can't alt-f3 or anything into another terminal and no network connectivity.  It's stuck just as above.

[B]Scenario 3:  Monitor Connected, I'm logged in at the keyboard, no ssh involved
[/B]I try rebooting from the connected keyboard and terminal.  Everything works fine!
Anyone have any suggestions as to how to troubleshoot this?

---

### Post by TheFu on 2015-08-25
Wow!  I've never seen this.

Some BIOS require both the monitor and keyboard connected to boot. There is often a setting "boot with keyboard error" that has to be enabled. Could that be it?  

Besides that, I haven't a clue. reboot via ssh or console shouldn't matter.

---

### Post by fizgig on 2015-08-25
> **TheFu said:**
> Wow!  I've never seen this.

Some BIOS require both the monitor and keyboard connected to boot. There is often a setting "boot with keyboard error" that has to be enabled. Could that be it?  

Besides that, I haven't a clue. reboot via ssh or console shouldn't matter.

Yeah, I've run into the need for a monitor as well.  The flaw in that theory is that it can cold boot without the monitor just fine.  It's just re-booting without the monitor that fails.

---

### Post by cariboo on 2015-08-25
Check the BIOS to see if it is set to halt on all errors. If it is change to ignore any errors.

---

### Post by TheFu on 2015-08-25
Cariboo's idea is good. 

If that isn't it, might help if we knew the motherboard details - be as specific as possible - model, version, current bios, age.  I've seen some show strange issues when the cmos battery died too.

---

### Post by fizgig on 2015-08-25
Ok.  The BIOS is iBTMx-DS R1.02.

This BIOS looks very bare bones - not a ton of options in it compared to others I've seen.  In the boot menu, there's a quiet boot mode which is disabled, numlock state, etc... Nothing too interesting.

---

### Post by fizgig on 2015-08-25
Well, I noticed in the BIOS that the boot devices listed two items - some flash thing I don't recognize and the normal disk drive.  I made the normal disk drive the default drive and I can't get the reboot to fail anymore.  Not sure where that setting came from and why it didn't matter when the monitor was plugged in but there you go.

Thanks everyone for the help!

---

