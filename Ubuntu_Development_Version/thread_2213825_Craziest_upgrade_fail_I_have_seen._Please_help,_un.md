---
title: "Craziest upgrade fail I have seen. Please help, unfixable system!"
date: 2014-03-28
forum: Ubuntu Development Version
---

### Post by FrancoNero on 2014-03-28
Hi folks.
Been using Ubuntu for years, consider myself kind of an advanced user, and I assure you I have spent the better half of the day trying things and googling around.

Here's what happened:
Upgraded my 64bit 13.10 to 14.04 this afternoon (upgrade, not a fresh install) on a Lenovo X1 Carbon which had previously worked flawlessly out of the box.

The first restart upon finished installation/upgrade rendered my machine unusable:
- I see no bios/lenovo screen upon powering on the machine
- screen stays blank (HD activity, screen is lit)

What I can do:
- plug a HDMI cord into the machine and use the laptop from my TV. Laptop screen stays blank

What I can't do (and here is where it gets weird):
- I cannot boot a live USB installation. Either because it just doesn't work, or it works but I don't see anything (because of the blank screen). At any rate, even if it works (which I cannot tell), in that option the 2nd screen isn't on.

HOW can I reset/reinstall my complete OS if I cant do a from-USB-installation? Is there a way (scripts, terminal commands etc) to reset all the boot parameters, grub, graphics drivers etc...?

How would I roll back to 13.10? So I am basically running a current daily 14.04

Help is much much apprciated. I am totally frustrated, I have no backup laptop to take to work with :(

---

### Post by pqwoerituytrueiwoq on 2014-03-28
if you can't get to the bios either your monitor came unplugged or your motherboard took a crap
you could plug the hdd into another system and see if it will boot and/or reinstall 13.10 to that drive
if you cant see the bios i would guess either the screen or the motherboard is dead
can you use the system with a hdmi cable?

---

### Post by tgalati4 on 2014-03-28
I have a personal rule:  Never trash a working system.  If you want to try new and shiny, try a Live USB boot or install on a new or 2nd partition.

Look at your grub configuration file to see what kernel boot switches were used on the previous installation.  Perhaps a simple *nomodeset* is needed.

---

### Post by ventrical on 2014-03-29
> **FrancoNero said:**
> Hi folks.
Been using Ubuntu for years, consider myself kind of an advanced user, and I assure you I have spent the better half of the day trying things and googling around.

Here's what happened:
Upgraded my 64bit 13.10 to 14.04 this afternoon (upgrade, not a fresh install) on a Lenovo X1 Carbon which had previously worked flawlessly out of the box.

The first restart upon finished installation/upgrade rendered my machine unusable:
- I see no bios/lenovo screen upon powering on the machine
- screen stays blank (HD activity, screen is lit)

What I can do:
- plug a HDMI cord into the machine and use the laptop from my TV. Laptop screen stays blank

What I can't do (and here is where it gets weird):
- I cannot boot a live USB installation. Either because it just doesn't work, or it works but I don't see anything (because of the blank screen). At any rate, even if it works (which I cannot tell), in that option the 2nd screen isn't on.

HOW can I reset/reinstall my complete OS if I cant do a from-USB-installation? Is there a way (scripts, terminal commands etc) to reset all the boot parameters, grub, graphics drivers etc...?

How would I roll back to 13.10? So I am basically running a current daily 14.04

Help is much much apprciated. I am totally frustrated, I have no backup laptop to take to work with :(



You could try the Plop boot loader from your CD rom or any other bootable CD and see what happens. Plop will give you Boot from USB option. That may work.

---

### Post by wgarcia on 2014-03-29
The fact that you can't see even the initial screen of the machine being started suggests that there may be something wrong before your Ubuntu installation has even the chance of starting. Can you hear any activity in the hard disk, or anything else suggesting that the machine is trying to boot?

---

### Post by FrancoNero on 2014-03-29
> **pqwoerituytrueiwoq said:**
> if you can't get to the bios either your monitor came unplugged or your motherboard took a crap
you could plug the hdd into another system and see if it will boot and/or reinstall 13.10 to that drive
if you cant see the bios i would guess either the screen or the motherboard is dead
can you use the system with a hdmi cable?

The system works fine, but I only see it on the external screen connected via hdmi.

I cannot take the hard drive out, it's an x1 carbon

---

### Post by FrancoNero on 2014-03-29
> **tgalati4 said:**
> I have a personal rule:  Never trash a working system.  If you want to try new and shiny, try a Live USB boot or install on a new or 2nd partition.

well I have a backup of everything, but all this doesn't help me now ;)

> 
Look at your grub configuration file to see what kernel boot switches were used on the previous installation.  Perhaps a simple *nomodeset* is needed.

how do I do that?

---

### Post by FrancoNero on 2014-03-29
> **ventrical said:**
> You could try the Plop boot loader from your CD rom or any other bootable CD and see what happens. Plop will give you Boot from USB option. That may work.

I don't have a CD room

---

### Post by FrancoNero on 2014-03-29
> **wgarcia said:**
> The fact that you can't see even the initial screen of the machine being started suggests that there may be something wrong before your Ubuntu installation has even the chance of starting. Can you hear any activity in the hard disk, or anything else suggesting that the machine is trying to boot?

As I said in the initial post, the system works fine, I just need to plug in the external screen via HDMI to actually see it. There is of course HD acitivty, however this being and SSD powered machine there is obviously no sound ;)

---

### Post by wgarcia on 2014-03-29
Then the hardware failure maybe in the screen, right? It's always black since this system starts? Again, the Ubuntu installation doesn't seem to be responsible of that if the screen never gets to show anything once it gets powered.

---

### Post by pqwoerituytrueiwoq on 2014-03-29
since the main display never gets a bios splash screen i am sure this wont work but have you checked your monitor settings to see if 2 screens show up in your configuration options?

---

### Post by steeldriver on 2014-03-29
... or run xrandr to see if it detects the internal screen. It also might be worth doing a harder reset (power the machine down and remove+reinsert the battery).

---

### Post by grahammechanical on 2014-03-29
I do not have a laptop so I am more than likely talking rubbish, but ... this being a laptop is there some physical switch or control over the laptop screen? A key combination that switches off the laptop screen and directs signal output to an external monitor? Or adjusts screen brightness? What happens when the user closes the laptop lid? Does the screen stay lit? Or is there a micro switch that physically switches off power to the screen. It would be part of the hinge mechanism of the lid. I may not know much about laptops but I do have some experience with micro switches. They do get stuck.

Oh, another thing. When the system was 13.10 did System Settings>Brightness and Lock work as it should or did you need to install some additional software, perhaps through a PPA to get an effective control of brightness? The Upgrade would not have upgraded any PPA software and in fact might have zeroed any software brightness settings.

Regards.

---

### Post by buzzingrobot on 2014-03-29
> **FrancoNero said:**
> 

how do I do that?

Hold a shift key down during the boot process.  This should bring up the Grub menu.  You'll see an option to edit it.  That's where you can add the "nomodeset" parameter to the kernel boot string. 

I'm unclear, but if the BIOS screen is visible via the HDMI, resetting the BIOS to its default state might be worth a try.

Since you can see HDMI output, it appears the video hardware is working.  I suppose -- but don't see how -- something might have disabled the VGA output.  Or, you've found a juicy 14.04 bug.

If it's a an actual video card in the machine, is it accessible?  I once spent a very long day dealing with a similar issue on a tower machine, only to find out that the video card had become unseated just enough to cut the connection.

---

### Post by Bibek on 2014-03-29
go to the bios settings and check if under boot display device , thinkpad lcd is selected or not. sometimes in rare cases, the external display can be set as default. if that doesnt help, looks like your lcd failed.

---

### Post by FrancoNero on 2014-03-30
> **wgarcia said:**
> Then the hardware failure maybe in the screen, right? It's always black since this system starts? Again, the Ubuntu installation doesn't seem to be responsible of that if the screen never gets to show anything once it gets powered.

probably in either graphics adapter or screen or both...  it seems like the upgrade triggered it. even though it might not be primarily responsible. i let the laptop sit for a day, and i just booted and it worked, aside from someflickering..... extremely weird situation

---

### Post by FrancoNero on 2014-03-30
> **pqwoerituytrueiwoq said:**
> since the main display never gets a bios splash screen i am sure this wont work but have you checked your monitor settings to see if 2 screens show up in your configuration options?

yes both show up, just the primary is blank (but has light).

I am now up and running again. indicates that there is something wrong with the hardware, probably loose contacts due to overheating etc?

---

### Post by FrancoNero on 2014-03-30
> **steeldriver said:**
> ... or run xrandr to see if it detects the internal screen. It also might be worth doing a harder reset (power the machine down and remove+reinsert the battery).

there is no way to remove the battery on an x1 carbon

---

### Post by FrancoNero on 2014-03-30
> **grahammechanical said:**
> I do not have a laptop so I am more than likely talking rubbish, but ... this being a laptop is there some physical switch or control over the laptop screen? A key combination that switches off the laptop screen and directs signal output to an external monitor? Or adjusts screen brightness? What happens when the user closes the laptop lid? Does the screen stay lit? Or is there a micro switch that physically switches off power to the screen. It would be part of the hinge mechanism of the lid. I may not know much about laptops but I do have some experience with micro switches. They do get stuck.

Oh, another thing. When the system was 13.10 did System Settings>Brightness and Lock work as it should or did you need to install some additional software, perhaps through a PPA to get an effective control of brightness? The Upgrade would not have upgraded any PPA software and in fact might have zeroed any software brightness settings.

Regards.

hi. interesting thoughts. however, everything worked as expected before, no modification necessary. the screen seems to work, it just didnt get any signal... i also suspect a physical damage where the signal from the graphics adapter doesnt get transmitted... maybe a damage from overheating or something

---

### Post by cariboo on 2014-03-30
I almost merged this with a thread that had a similar title , but seeing as this problem is nothing similar to that thread, I changed the title back to it's original, because the new title didn't explain what the problem was.

---

### Post by FrancoNero on 2014-03-30
thanks.

Update: After having the laptop lying around for half a day, it booted today. I am using it. The bios splash screen shows, and I can boot into unity ubuntu without problems. The boot process does look a bit weird though (at one point a black screen with a purple frame, and then lots of HAL udev etc errors...).... I will have an eye on how it develops. There was no change in the OS....

---

### Post by bapoumba on 2014-03-30
> **FrancoNero said:**
> there is no way to remove the battery on an x1 carbon

Just to address this point, there should be a small button you can press with a paper clip at the bottom to run a hard reset.

---

### Post by FrancoNero on 2014-03-30
the machine is working now... no idea why

still this bug:  [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1289809](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1289809)

---

