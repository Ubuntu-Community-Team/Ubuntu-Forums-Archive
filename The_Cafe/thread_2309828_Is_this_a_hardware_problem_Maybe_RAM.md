---
title: "Is this a hardware problem? Maybe RAM?"
date: 2016-01-13
forum: The Cafe
---

### Post by KayeNg on 2016-01-13
Hi guys.  

I have this dual boot system running windows 8.1 SL and Lubuntu.  It restarts randomly.  I used to think it was a windows bug because it would happen while I was using windows, but not when I'm using Lubuntu.  But now it's happening while I'm in Lubuntu as well.

Yesterday, it rebooted itself a few times while I was using Lubuntu, so I took out the RAM and moved it to the other slot.  It seemed to have solved the problem because I used the computer (lubuntu) for 2 or 3 hours without any problem.

Today however, as soon as I log into Lubuntu and start typing on the web browser, it reboots.  I has rebooted several times already, almost as soon as logging into the system.

Could RAM be the problem? If it's the RAM, can anyone tell me what type of ram it is? Here's the picture, not sure if you can see it though.

[ATTACH=CONFIG]266730[/ATTACH]

Does it look like [COLOR=#555555][FONT=Helvetica]4GB DDR3-1600 MHz ?[/FONT][/COLOR]

Thanks a lot!

---

### Post by 1clue on 2016-01-13
[LIST=1]
[*]Put your memory into the slots as recommended by your hardware manufacturer.  There IS a slot or bank of slots recommended for population first, or if all are full then that bank should have the fastest memory.
[*]Reboot into your BIOS
[*]Ensure that all 'fast boot' options are disabled, so that your system does a complete memory and hardware test.
[*]Pay very close attention to the boot process, even to the point of getting video of it so you don't have to keep rebooting.
[/LIST]

If everything passes, then do a filesystem check (fsck) on every Linux partitions and use whatever disk utility to check your Windows partitions.

---

### Post by KayeNg on 2016-01-14
It has gotten worse.  The computer doesn't even reach the lubuntu log in screen anymore; it just reboots over and over again.  I was also able to boot a memtest dvd but the test lasted for only a minute or so, because it rebooted during the test as well!  

(I booted a memtest dvd because there's no built-in memtest in my GRUB, probably has something to do with the fact that the lubuntu system is 64-bit? I don't know)

In other words, it reboots by itself when I'm trying to boot an operating system or if I'm already running the os, and it also reboots by itself even when I'm booting the memtest dvd (memtest would be interrupted because of reboot). 

By the way, if I shut down the computer for about 5 minutes, I could reach the lubuntu log in and I could actually log in the system.  But after a minute or so, it reboots.

Also, during the memtest, one of the things it showed is the cpu temperature which seems to be fluctuating.  Before it was interrupted due to the reboot, I noticed the temperature went as high as 45 degrees.  Is that normal?

So what do you think? Is it the RAM?

---

### Post by Shaun_Dixon on 2016-01-14
Is this a Desktop or laptop?  

If it is a desktop build then it may be worth doing some basic things like ensuring the RAM is seated correctly inside the correct slots as per the manufacturers guide.  While you have the PC open (ensuring it is powered down and disconnected from the power source) make sure there is a not a build up of dust inside your PC.  Overheating issues, which you mentioned with the CPU can be caused by dust.  

It could potentially be a hardware issue which could be a number of things, but doing some basic checks like ensuring the components are seated correctly inside the PC and that any power cables to devices are plugged in fully can sometimes resolve the issue.

---

### Post by KayeNg on 2016-01-14
Thanks Shaun_Dixon.

It is a branded desktop. Lenovo H530s I think. I have managed to make it a dual boot system:  Windows 8.1 SL and Lubuntu.

RAM is seated securely, I'm sure of that. There are two slots for the RAM; the desktop reboots itself regardless of where I put the RAM. 

> [COLOR=#000000]Overheating issues, which you mentioned with the CPU can be caused by dust. [/COLOR]

Are you confirming that the 45 degree temperature of cpu shown in memtest was indeed overheating?  

Incidentally I just cleaned the inside of the desktop with a powerful industrial blower about two weeks ago, it got rid of most of the dust.  I did it because of the reboots.  The desktop worked pretty well for a week and then the reboots started again.  

> [COLOR=#000000]....doing some basic checks like ensuring the components are seated correctly inside the PC and that any power cables to devices are plugged in fully can sometimes resolve the issue.[/COLOR]


What do you any power cables to devices? Like the monitor? Anyway I'm pretty sure everything was plugged in fully.

---

### Post by Dragonbite on 2016-01-14
If you boot to a Live USB and the issue doesn't persist then it may be something with the hard drive.
Keep a note on how long it lasts and how hard the system is working for heat build-up.
If you have 2 sticks of RAM maybe remove one and bootup and if it psersists change that one for the other stick and see if it happens with that one, in case one stick is bad.

---

### Post by Shaun_Dixon on 2016-01-14
Thank you for the information KayneNG.  

RE the overheating, 45 degrees is not an indication of overheating.  A lot of CPU's run at that level and the temp can fluctuate, so that is nothing to worry about.   

I was just saying if you were concerned about the potential overheating to ensure there was not a build up of dust.  But it is great that you have already checked that. I have had PC's in the past that suffered this kind of issue due to dust :)  

Is it just the one stick of RAM that you are using?  

I am not an expert with Linux but have had similar issues in the past with my windows machines, it can be a pain to diagnose the cause so I feel for you.

---

### Post by KayeNg on 2016-01-14
Dragonbite I'll try the live USB. Thank you.

Thanks Shaun for verifying the normal cpu temperature.  Yes the desktop has only one stick of RAM.  Regardless of where I put it, the computer reboots.

I'll try the live USB and I'll let you guys know. thanks!

---

### Post by 1clue on 2016-01-15
[LIST=1]
[*]Power the system off.
[*]Open the case.
[*]Take a picture of the inside of the computer so you can see where everything is right now.
[*]Remove every PCI card.
[*]Unplug all hard disk/cdrom/floppy cables, but do so from the board.
[*]Unplug every USB/external device which is not a keyboard or mouse.
[*]You should have only the RAM module in the system, in the default slot.
[*]Boot the system.
[LIST=1]
[*]You should get a POST message, and it should do a memory check before either trying a network boot or complaining of no startup disk.
[*]If you don't get one of these, then there may be something wrong with the motherboard, power supply or RAM.
[*]If you have a memory-related error on the screen then it's probably memory.
[/LIST]

[*]If your system got a message described by 7.1, then plug in the boot disk and reboot.
[*]If your system boots, then the problem is with one of the peripherals not connected.
[*]Repeat until you find something which causes the system to fail to boot or reboot  continuously like you're describing.
[*]Start with internal hardware like hard drives and PCI cards.
[*]You can install 2 or 3 things at a time if you have a lot of devices.  If you get a failure you can remove the ones most recently added until you know which one is failed.
[/LIST]

---

### Post by KayeNg on 2016-01-19
When you say PCI card, do you mean extension? Because the desktop Doesn't have that. As far as I can tell, the ones that can be removed are the hard disk, cdrom, and ram. I removed them except the ram. I got a message like "unable to find operating system". Forgot the exact words. 
I did not remove them from the board like you said though. I unplugged from the hard disk and the cdrom. But I checked the plug at the board, I re-plugged it real good. 
I'm thinking it's the ram because even running memtest by booting a memtest cd isn't spared from the random reboots. That's why I couldn't finish the memtest. Don't you think?

---

### Post by 1clue on 2016-01-19
Do you have the long memory check enabled?  Meaning, do you see a number on the screen rapidly changing?  You want the full memory test to take place, you'll need to check your bios for that.

Power down, remove the RAM and see if you still get reboots.  This could still be any number of things.

Removing the cables from the motherboard instead of from the device prevents a bad cable from causing a problem.

A PCI card is a circuit board which plugs into the motherboard.  Usually, if the motherboard is horizontal then the PCI card will be vertical.  Some compact systems use other arrangements.

---

### Post by KayeNg on 2016-01-20
> do you see a number on the screen rapidly changing?  You want the full  memory test to take place, you'll need to check your bios for that.
It doesn't show that, even if I disable the quick boot in BIOS.  It goes straight to the screen showing the lenovo logo, then to GRUB.  And I swear I've looked in BIOS several times for a way to show the memory test during boot up; cannot find it.  There seems to be no setting in BIOS for that.

Here's the thing that got me more confused.  I am now using the same desktop computer but with a different mouse, monitor, and UPS.  It's working fine, both in Lubuntu and windows.  I've been at it for over an hour now with no reboots.

Could it be the UPS? or even the PSU?  If I'm not mistaken, whenever I use the desktop with the above-mentioned devices, it doesn't seem to have reboot problems.  Then if I switch to the other workstation (with a different mouse, monitor, UPS), reboot problems start again.

PS.  I've just successfully installed MS Office in windows.  Still no problems.

---

### Post by 1clue on 2016-01-20
It absolutely positively could be the UPS.  Does it have a status display?  How old is it?

It could also be a loose plug in a socket, either the UPS to the wall or the computer to the UPS.  Or, if you boot from or depend on an external drive, any plug connecting that to the wall or your computer.

While I have never seen a bad keyboard or mouse cause reboots on PC hardware, I have seen an IBM AS/400 fail to boot because of a bad keyboard on the main terminal.

Using the new keyboard and mouse, try booting with the old UPS.

---

### Post by Dragonbite on 2016-01-20
> **1clue said:**
> While I have never seen a bad keyboard or mouse cause reboots on PC hardware, I have seen an IBM AS/400 fail to boot because of a bad keyboard on the main terminal.

> Keyboard not found
Hit F1 to continue
Hit F2 to go into settings

](*,):confused::lolflag:

---

### Post by 1clue on 2016-01-20
> **Dragonbite said:**
> ](*,):confused::lolflag:

That won't cause random reboots like the OP is experiencing.  Also, you can go to the BIOS and tell it to not fail if no keyboard is attached.

No keyboard attached is different from having a bad keyboard cause a reboot or even failure to boot.

---

### Post by michael337 on 2016-01-22
It sounds like the hard drive's controller board has a dead short in it, so try to either get a new controller board or a new hard drive on eBay, If you choose only to replace the controller board, BE SURE THAT IT'S FOR THE EXACT SAME MODEL FOR YOUR HARD DRIVE!!!

---

### Post by 1clue on 2016-01-22
If I understand the OP correctly, it still reboots when the hard disk is disconnected.

---

### Post by Christopher_Stayne on 2016-01-23
I have seen computer mice cause some rather odd issues.  One was where the system would randomly lock up hard and the only way to recover was to do a cold reset.  It wasnt rebooting like this, but it may be something to look into.  Try the old mouse again and see if the rebooting issues come back.

---

### Post by kurt18947 on 2016-01-24
> **KayeNg said:**
> 
.........................
Could it be the UPS? or even the PSU?  If I'm not mistaken, whenever I use the desktop with the above-mentioned devices, it doesn't seem to have reboot problems.  Then if I switch to the other workstation (with a different mouse, monitor, UPS), reboot problems start again.

PS.  I've just successfully installed MS Office in windows.  Still no problems.

I did have a desktop UPS cause power interruptions rather than prevent them. The frequency was nowhere near what you're experiencing though.

---

