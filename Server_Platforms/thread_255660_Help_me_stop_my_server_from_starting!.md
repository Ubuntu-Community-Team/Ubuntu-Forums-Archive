---
title: "Help me stop my server from starting!"
date: 2006-09-11
forum: Server Platforms
---

### Post by panthera on 2006-09-11
Every day (at the same time) my server starts up. I have it ready to go, but we don't want it up yet. I have to (every day) shut down (shutdown -h) the computer. Is there a reason why it's starting up? How do I stop it? Thanks!!

---

### Post by Frogger on 2006-09-11
Check your bios for an indicated boot time.
If not, see if another computer is sending a WOL request.

---

### Post by panthera on 2006-09-11
How do I check the BIOS? 
I don't have the computer hooked up to the internet, so it's definitely starting on it's own...

---

### Post by max.diems on 2006-09-11
You have a server not connected to the internet?

---

### Post by panthera on 2006-09-11
Yep. It's not connected to the internet. We were almost set to put it up, but we are not ready yet, so it's not hooked up to the internet. Still, at 8pm exactly, it turns itself on every night. :(

---

### Post by panthera on 2006-09-11
I see nothing in the BIOS that has anything to do with the system starting -- since I'm sorta new at dealing with the BIOS, I could be missing it, but I looked through everything.

The system did not have this problem when I installed redhat on it (an old version which I overwrote with Ubuntu).

---

### Post by paul.maddox on 2006-09-12
[IMG]http://www.wealddown.co.uk/images%20shop/480%20Broad%20Axe.jpg[/IMG] ?

---

### Post by rastilin on 2006-09-12
Might be easier to just leave the problem alone and unplug the server.

---

### Post by Iowan on 2006-09-12
Try unplugging the LAN cable (as opposed to the power cable).  See if it still turns itself on.
Yes: BIOS
No: WOL

---

### Post by Trackieman on 2006-09-12
[QUOTE=panthera;1488721]Every day (at the same time) my server starts up.

Some Motherboards have a setting in the BIOS that allow you to specify a time
for the Motherboard to power on. I have a cheapy Gigabyte SiS chipset
motherboard here that has a setting for this.
Press the Delete key as you power up your server to get into the BIOS
Look under Power management.
Look for a setting called Resume by alarm.

---

### Post by panthera on 2006-09-12
It's not connected to ANY other computers... 
where would it be in the BIOS? Please help me on this!! It started only after Ubuntu was installed, so that MUST have done something to the system....

---

### Post by panthera on 2006-09-12
ok. there is no "power management":

System Time
System Date
Diskette Drive A:

System Memory
Video Memory
CPU Information (which has bus speed, processor, clock speed)

Boot Sequence
Hard Disk Drive Sequence

Integrated Devices
PCI IRQ Assignment

System Security
Keyboard NumLock
Report Keyboard Errors

Asset Tag.

that's all there is..
and I think it's resetting to the hour when I installed Ubuntu..
(not like I think that helps much).

---

### Post by WagnerVaz on 2006-09-12
man, I starting to think is better you call an Priest o0

Do you make the default ubuntu instalation?
or did you removed/installed packages.
if yes what.

did you complile the kernel?
if yes, show the output of lsmod

What kind of server is?

---

### Post by WagnerVaz on 2006-09-12
On bios try to find something like it:
Wake/Power up on external modem
Wake/Power up by PS/2 Keyboard
Wake/Power up by PS/2 Mouse
Power up on pci device
Automatic Power UP

Maybe can be too the Bios batery, try to change for one with full of charge.

At last try to update the Bios, some Bios has these option.

---

### Post by panthera on 2006-09-12
I gave you all the options from my bios... 
and power up/wake is not one of them.
Is there a way to get a list of packages? I can try to remember them all, but I might forget one.

I did the standard LAMP installation, then removed PHP.. added telnet (inetd) and an ftp program (proftpd). 

I didnt' change the kernel.

---

### Post by panthera on 2006-09-12
Oh, and it's a Dell poweredge 1400 sc.

---

### Post by WagnerVaz on 2006-09-12
Try to reset bios (removing the batery for 5 minutes) and configure the bios again, if it still with problem, trade the batery for one full of charge.

---

### Post by Trackieman on 2007-06-01
> **panthera said:**
> Oh, and it's a Dell poweredge 1400 sc.

Ah, the option then is probably not in the BIOS. It's the bit that comes after relating to your Network card configuration, PXE booting and all that goodness. It's usually a CTRL and (some letter on the left of the keyboard, cant be more precise sorry) - combo.

---

