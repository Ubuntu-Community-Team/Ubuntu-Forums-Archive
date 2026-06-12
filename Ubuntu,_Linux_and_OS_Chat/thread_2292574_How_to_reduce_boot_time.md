---
title: "How to reduce boot time"
date: 2015-08-29
forum: Ubuntu, Linux and OS Chat
---

### Post by semofa on 2015-08-29
Hi,
I have Ubuntu installed on my PC. I need only a ordinary things like network and XWindow. I want reduce boot time to 5 sec. is it possible? if so, can you people help me how to do that,please?

thanks in advance

---

### Post by oldfred on 2015-08-29
Fast SSD with new UEFI system.

My last entry in dmesg shows timestamp of under 5 sec. My SSD is not the fastest available.

[    4.993590] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

But I do set a 3 sec delay in UEFI boot, so I can get into UEFI if needed. Otherwise if issues you may have trouble getting into UEFI to boot flash drive to fix things.
And I put a 3 sec delay in grub as I also boot other Ubuntu installs.

Full shutdown to reset even with the delays is under 20 sec.

---

### Post by semofa on 2015-08-29
thanks,
but I don't have SSD. I have HDD. can you point me some guide to reduce boot time as far as possible?

---

### Post by Bucky Ball on 2015-08-29
Switch off start up applications that aren't needed. Install a lighter flavour like Xubuntu or Lubuntu. Better still, do a minimal install and install only the meagre apps/software you want/need.

---

### Post by ajgreeny on 2015-08-29
With even a fast HDD I very much doubt that you can get the boot time of a Linux system with some sort of GUI, either a full DE or even just a WM, to boot from the point you press the power-button to a login-screen in 5 seconds, not to mention starting the DE or WM itself after that.  The POST may even take longer than that depending on your m/b and hardware; it certainly does on mine.

The best you can probably do within the *ubuntu family is use the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") to install either a lubuntu-core system or even just a command line system to which you add openbox or other window-manager.

---

### Post by Bucky Ball on 2015-08-29
*Thread moved to **Ubuntu, Linux & OS Chat***.

My HP Stream 11 boots in about 10-15 seconds with a mini install. But that is running from an eMMC card which is very fast so doesn't count I guess.

---

### Post by tgalati4 on 2015-08-29
Why can't you use sleep?  To wake up from sleep can take 3 to 8 seconds, depending on the machine.

---

### Post by v3.xx on 2015-08-29
sysv-rc-conf can still be installed.

A dated post so things have changed, but gives you the idea.  Looks insane; I like it :biggrin:

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

other hits

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=improve+boot+time&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=improve+boot+time&sa=Search&cof=FORID:9)

---

### Post by monkeybrain20122 on 2015-08-29
> **Bucky Ball said:**
> Switch off start up applications that aren't needed. Install a lighter flavour like Xubuntu or Lubuntu. Better still, do a minimal install and install only the meagre apps/software you want/need.

Not sure if "lighter" DEs have anything to do with boot time (from turning computer on to login screen), it may speed up login time (from login screen to desktop). I see no difference in boot time for any *buntu. All about 10 sec, fast enough for me (actually very little difference between login time either, in fact Ubuntu is a little faster than Xubuntu here) One thing I discovered that might speed up login time is to boot into the old kernel(s) once (advanced options in grub menu) then subsequent logins are a lot faster. Only need to do it once and then may be til the next kernel upgrade. Don't know why, but the trick always seem to work for me (tried on several computers with totally different specs)

---

### Post by chemist931 on 2015-09-12
Solid State Hybrid Drive!
SSHD's combine a normal mechanical HDD with a little bit of SSD (very technical language there).  Your boot stuff (more technical) is put on the SSD, and I can currently boot in 13 seconds with one in my laptop running Ubuntu and Unity.  *Almost* the speed of an SSD with *almost* the cost of an HDD.

---

