---
title: "Help me figure out this computer problem..."
date: 2009-06-05
forum: The Cafe
---

### Post by Roasted on 2009-06-05
Note - This is not an Ubuntu issue, despite me using an Ubuntu laptop to act as a Linux based server to run FOG open source imaging on it. It is a hardware issue at the BIOS level that I can't seem to troubleshoot, so I was not too sure where to place this thread as a result.

Situation:

Computer Lab.
30 Computers.
HP dc7100. All identical.
Operating System - Windows XP Professional SP3.

FOG Open Source Imaging Solution.
Network based. PXE boot. Linux server.

I imaged the entire lab in no time at all. But 3 of these 7100's acted weird. These 3 in particular did not have the "F12 Network Service Boot" option at the BIOS. I checked the BIOS, which is password protected, and network booting is enabled. Even after disabling and re-enabling it, it still didn't pop up.

Confused, I ended up using our time consuming hard drive cloner to just to a direct disk copy of the drives. So ultimately, these 3 problematic computers were cloned via hard drive cloner whereas the rest of the lab were cloned via FOG imaging software over PXE boot. And yes - These were all identical images. When I used the hard drive cloner, my "master" drive was one of the recently FOG'd computers.

Afterwards, the F12 Network Service Boot option appeared on the HP BIOS splash screen.

WTF?!!!!!?!?!?!?! At this point, the hard drive has no involvement. How is it possible that at the BIOS level of booting that the option magically pops back up? The only thing that changed was the image on the hard drive, but at this point the hard drive shouldn't have been a factor yet.

How is this possible?

---

### Post by Roasted on 2009-06-08
Nobody has any idea? I'm very confused by this...

I just always thought the boot screen was at the BIOS level.

How can a computer image change something at the BIOS level????

---

### Post by gn2 on 2009-06-08
Did the imaging affect the MBR?

What was the BIOS boot order of the 3 that wouldn't play, was it HDD before PXE?

Do they PXE boot now because the MBR got changed during the cloning?

Sorry for lack of answers, only questions ;)

---

### Post by Roasted on 2009-06-08
The imaging process before it starts says "backing up MBR................DONE" So I assume all is good in that department.

With the HP boot menu, I don't think that F12 Network Service Boot (PXE) is in the boot order because HP has a dedicated F12 key. I honestly don't think these machines can have the PXE option in the boot order...

I just don't get it because the boot order (including the F12 option at the HP splash screen) is a BIOS level setting. How can a computer image effect BIOS level settings? I thought this was the same probability of a male getting pregnant.

I was also under the impression that even if the hard drive was taken out of a computer that I would still see the HP screen, because this is still the BIOS in control. Then the BIOS would pass off control to the OS on the hard drive, which in this case would be Windows XP. So I'm just not seeing how it was able to make this change... I just don't get it...

---

### Post by gn2 on 2009-06-08
There can be a BIOS boot order and a Boot Device Selection Menu both of which are separate functions.

The boot order will determine the order in which the BIOS "looks" for a bootable operating system if left to it's own devices.
If the HDD is before Network in the list and there is an OS on the HDD, then it will boot from HDD.

It's the same reason Live CDs don't always boot, because the CD drive can be listed after the HDD by the manufacturer to stop non-system CDs (e.g. game or audio) from preventing the PC from booting.

If the HDD has it's MBR wiped, it will be passed over and the BIOS will boot from the next in the list.
 
The Boot Device Selection Menu when brought up by the specific key (F12?) presents a list of the detected bootable devices for the user to manually select from.
Usually (but not always) this list will be in the same order as the BIOS boot device order.

**Edit**: Bootable devices are not always enabled in the BIOS even though they are detected and appear in the list.
It could be possible that the F12 call for network booting failed because the network was not enabled as a boot device.

---

### Post by Roasted on 2009-06-08
Right. I understand what you're saying. These computers in particular do not have the ability to set network boot as an option in the boot order.

F9 - Boot Order
F10 - Setup
F12 - Network

If I touch nothing, it by default looks to the pre-set BIOS boot order and takes off with whatever media it finds first. If I hit F9, I can manually select CD, HDD, removable device, etc. However, in both the pre-set BIOS boot order, along with the F9 boot menu, network booting is not an option. I assume this is due to the fact that it has a dedicated (F12) key specifically for network booting purposes.

The BIOS checks out fine and everything is enabled accordingly. On top of that, these BIOS's are locked with a password so nobody else can make changes except the tech department.

I just don't see how this was possible... And it's not like it's a major problem, cause everything works. It's just a "aw what the...?" thing that I want to figure out.

---

### Post by gn2 on 2009-06-08
If you go in through F10 and look at the advanced boot options, is there a way to enable or disable the network as a boot device?

---

### Post by Roasted on 2009-06-08
The network booting option within the BIOS is set to "enable." But it never shows up under F9. I am assuming this is because the BIOS has a pre-set hot key specifically for network booting.

I have another HP dc7100 here on my desk. It wasn't one from this same lab but it's an identical model. I disabled network booting in the BIOS and the F12 option disappeared. When I re-enabled it, it re-appeared at the HP splash screen. 

So it seems there's no way to control the network boot option being part of the boot menu. It's simply a hot key that you must hit to successfully network boot it.

Even still, how does an image effect a BIOS level setting? I just can't grasp this.

---

### Post by gn2 on 2009-06-08
If the MBR of the HDD is wiped as part of the imaging, the BIOS will pass it over even if there's an OS installed.

I've also heard of a hidden utility being placed on the hard drive by some manufacturers which can prevent another OS being installed onto the hard drive.

Have you checked the BIOS version numbers to see if the three that played up have an earlier version?

I must say it does sound quite baffling :?

---

### Post by Roasted on 2009-06-08
I did not check BIOS versions, but I am nearly positive they are all identical since they all were bought at the exact same time and no manual flashing of the BIOS was done to my knowledge.

When we get computers in, I wipe them clean. I completely format the hard drive of all partitions. I have YET to find a utility or hidden partition by Dell, HP, or any of those other head honcho's where it's actually useful. It's always a pain in the !!! and I always delete the hard drives without even caring to power them up first. Then I create a single NTFS partition and install Windows and then go on my merry way with setting up the first image manually, then cloning to the rest afterwards.

---

