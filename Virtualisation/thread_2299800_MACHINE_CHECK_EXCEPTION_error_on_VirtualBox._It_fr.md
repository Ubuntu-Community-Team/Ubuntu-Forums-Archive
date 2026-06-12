---
title: "MACHINE_CHECK_EXCEPTION error on VirtualBox. It freezes randomly and needs to reboot."
date: 2015-10-21
forum: Virtualisation
---

### Post by javier47 on 2015-10-21
Hello!
I cant understand why, but I have installed Ubuntu with VirtualBox and it freezes randomly.
Then, the PC gives me a MACHINE_CHECK_EXCEPTION error and I have to shutdown my computer, because it doesn't reboot.
> Your PC ran into a problem and needs to restart. We're just collecting some error info, and then we'll restart for you (100% complete).
If you'd like to know more, you can search online later for this error: MACHINE_CHECK_EXCEPTION  

I have installed GuestAddition Tools, verilog, grive, chrome, nvidia drivers (I think)
My specs are:

> [MSI GP62 Leopard Pro]
Intel Core i7-5700HQ CPU
[COLOR=#333333][FONT=Arial] RAM 8GB DDR3 SODIMM (1x8GB)
[/FONT][/COLOR][COLOR=#333333][FONT=Arial]1TB (7200 rpm S-ATA)+ 128GB SSD (M.2 SATA)
[/FONT][/COLOR][COLOR=#333333][FONT=Arial]Nvidia GeForce GTX950M 2GB GDDR3
[/FONT][/COLOR]OS: Windows 10 Education

Thank you for your help.

---

### Post by ajgreeny on 2015-10-21
Seems to be an MSI problem which I found following a search, with this thread giving a possible solution.
[http://ubuntuforums.org/showthread.php?t=2284315](http://ubuntuforums.org/showthread.php?t=2284315)

I haven't read all the thread but it may of some help to you.
Good luck!

---

### Post by Doug S on 2015-10-22
See also [this]("https://bugzilla.kernel.org/show_bug.cgi?id=103351").

---

### Post by javier47 on 2016-01-09
> **Doug S said:**
> See also [this]("https://bugzilla.kernel.org/show_bug.cgi?id=103351").

Yeeep, I think that worked for me. I will update if it fails again, but the installation was successful and no BSOD for the moment.
THANK YOU SO MUCH! I was annoyed with that, I needed to save my work every 2 minutes and I think that I finally can work with calm with Ubuntu.

This seems to be a problem with **[COLOR=#666666][FONT=Helvetica][/FONT][/COLOR][FONT=Helvetica][SIZE=4]Intel i5-5675C, i7-5775C, and i7-5700HQ[/SIZE][/FONT]**[COLOR=#666666][FONT=Helvetica]  [/FONT][/COLOR]processors. Some manufacturers have uploaded a BIOS update, so If you have this problem, check for BIOS updates first.
To solve this problem I followed [this instructions]("https://github.com/bgw/bdw-ucode-update-tool"). Please, read carefully all of that.

Thank you all so much :D

---

### Post by evgeny13 on 2016-02-06
> **javier47 said:**
> Yeeep, I think that worked for me. I will update if it fails again, but the installation was successful and no BSOD for the moment.
THANK YOU SO MUCH! I was annoyed with that, I needed to save my work every 2 minutes and I think that I finally can work with calm with Ubuntu.

This seems to be a problem with **[FONT=Helvetica][SIZE=4]Intel i5-5675C, i7-5775C, and i7-5700HQ[/SIZE][/FONT]**processors. Some manufacturers have uploaded a BIOS update, so If you have this problem, check for BIOS updates first.
To solve this problem I followed [this instructions]("https://github.com/bgw/bdw-ucode-update-tool"). Please, read carefully all of that.

Thank you all so much :D

Hi Can you please explain hopw did you apply the patch i have same setup. cpu 5775 and running ubuntu14.04 in virtualbox.
i am unable to apply this patch and i cannot see microcode in /proc/cpuinfo
also is there a way to make it pesistant?
thank you.

---

