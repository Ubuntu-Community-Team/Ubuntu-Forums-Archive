---
title: "[SOLVED] Fixing a friends Windows machine: i'd like a little help."
date: 2008-01-06
forum: Windows
---

### Post by coolen on 2008-01-06
Hey guys. I'm fixing a friend's computer. It's a Windows machine, and she's not particularly interested in Linux. Here's what I've got so far:

The computer turns on, and I get to the screen where it asks what configuration I want to boot with (safe modes, normal, and last good configuration). Whichever option I choose, I get a quick message. Something about VGA BIOS. This led me to think it's a problem with the graphics card.
After confirming that none of the modes worked, I put in an old Xubuntu disc (Dapper), which booted successfully to a graphical enviornment. This computer has a Nvidia graphics card, GeForce2 GTS/Pro according to lspci.
I've confirmed that X is using the nv driver.

Correct me if I'm wrong, but I've drawn the conclusion that the graphics card has nothing physically wrong with it.

So, I'm thinking a driver issue in Windows. Any thoughts/suggestions?

---

### Post by Sef on 2008-01-06
Moved to Windows Discussions.

> Hey guys. I'm fixing a friend's computer. It's a Windows machine, and she's not particularly interested in Linux. Here's what I've got so far:

The computer turns on, and I get to the screen where it asks what configuration I want to boot with (safe modes, normal, and last good configuration). Whichever option I choose, I get a quick message. Something about VGA BIOS. This led me to think it's a problem with the graphics card.
After confirming that none of the modes worked, I put in an old Xubuntu disc (Dapper), which booted successfully to a graphical enviornment. This computer has a Nvidia graphics card, GeForce2 GTS/Pro according to lspci.
I've confirmed that X is using the nv driver.

Correct me if I'm wrong, but I've drawn the conclusion that the graphics card has nothing physically wrong with it.

So, I'm thinking a driver issue in Windows. Any thoughts/suggestions?

I agree it is a Windows driver issue.  If the card was bad, Xubuntu would come up the same as XP.  Since you get the error about VGA BIOS, go into the BIOS and if changing a setting is needed.   Has she changed monitors or done any other changes recently?

---

### Post by kamaboko on 2008-01-06
You have to make a boot CD with the VGA Bios (which you download from the card manufacture site) and the eeprom flashing program (e.g., awdflash).

---

### Post by Vince4Amy on 2008-01-07
I think it's a Driver Issue, since I had the same problem with an ATI Graphics card on Windows. Though it may be the chipset drivers as well as the Graphics Card Drivers.

---

### Post by bufsabre666 on 2008-01-08
if its during boot theres the error id bank more on ram then vga, ram errors in windows are commonly displayed as being other things ((once had a ram error tell my usbport.sys was invalid))

if you have other ram switch and try it

if thats not it try this

boot off a windows disk
go into the recovery console
go into your windows partition
type:
FIXBOOT
FIXMBR
EXIT

it should reboot and it might work from there
ive had similar things happen to me in the past so this might work

---

### Post by Pevichaey5 on 2008-01-08
using fix boot is absolutely fine, however, you might want to backup all the stuff before doing a fix mbr, as i did this once, and it corrupted my entire hard drive, be very causous

---

### Post by bufsabre666 on 2008-01-08
> **thexero said:**
> using fix boot is absolutely fine, however, you might want to backup all the stuff before doing a fix mbr, as i did this once, and it corrupted my entire hard drive, be very causous

i had this problem on windows 98se with fat32, ive done it on ntfs 3-4 times and never had this problem but given windows track record i would put it past this, so backing up inportant data would prolly be a good choice

---

### Post by coolen on 2008-01-08
Ahh, thank you! It was the RAM.
I was going to try fixmbr (as it occured to me that the message about VGA RAM may be purely informational), but unfortunately the CD I used never got to that point.

I did back up all of her data, once on my machine, and then on a second partition I created for her. Just seems irresponsible not to have one.

Thank you everyone for your input.

---

