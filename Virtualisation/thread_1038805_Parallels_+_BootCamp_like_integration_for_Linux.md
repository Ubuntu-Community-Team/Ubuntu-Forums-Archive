---
title: "Parallels + BootCamp like integration for Linux"
date: 2009-01-13
forum: Virtualisation
---

### Post by uberben on 2009-01-13
I love using Linux, but sadly there are times when I need to use Windows applications for school or other projects and Wine just doesn't cut it. Some programs require fairly intensive hardware integration (such as Adobe Creative Suite products) but others are ones that I would like to use along side my Linux apps.
What I would like to see is something along the lines of what Mac users have in a Parallels + BootCamp setup. Dual boot for full hardware support on the more greedy applications but allow the Windows install to be used as a VM as well. I know I could just install a VM and dual boot, but this uses double the disk space and means I can't easily share install directories and application data and whatnot between the full install and the VM.
I know that VitualBox has nice integration for mingling Windows windows amongst the Linux ones, but to my knowledge cannot boot a native windows install as a VM. I did some Googling and the best I could find was booting into a VirtualBox VM from the GDM login screen in order to have a minimum of Linux software running, but there would still be some and the VM would still be running on virtualized hardware. Does anyone have a better solution?

---

### Post by starcraftmaster on 2009-10-28
did any one find a simlar program

---

### Post by georgelenzer on 2009-10-29
I've wanted this myself.  The main issue is the difference in the hardware between booting on your real machine vs. booting in a VM.  At least on an Apple, you have a small set of real hardware which you could theoretically emulate in a VM so that the installed Windows drivers would think they're running on the same machine either way.  I suspect that's what Parallels does.

Doing this in the PC realm is harder because you have different hardware in the VM that likely does not match your actual hardware and that variance is huge across the PC platform.  Going in the reverse, I suppose someone could create a set of driver "masks" for Windows that would make it appear to Windows that it's running on the same hardware that the virtual environment has.  (sb16 sound, intel 10/100/1000 nic, cirrus logic video)  But then you have the problem of those masks essentially "downgrading" your hardware.

I don't think it's impossible to pull this off and there might be an even better way to do it, but nothing that's out there can do it yet for the Linux world.

One other possibility (and it's been a long time since I've used Windows) is "hardware profiles" in Windows.  I seem to remember in Win9x that they had hardware profiles that you could select for laptops that accepted certain hardware driver changes and shifted drivers around depending on if you were docked or not.  I don't know if they continued this in the Win2k/XP/Vista/7 lineage though.  If there is a way to load drivers for two sets of hardware in Windows, that *might* be a workable approach.  Hmmm... something new for me to think about.

---

### Post by georgelenzer on 2009-10-30
My limited searches indicate that this could cause some licensing and registration issues with Windows XP.  Some people claim that Vista changed the licensing a bit so it could work licensing wise, but that's likely based on the version of Vista.  It's also my understanding that you are not legally allowed to Virtualize Windows if you don't have the Enterprise or Ultimate versions.  Home and Professional don't allow virtualization (if you want to stay in compliance with the EULA).

Technically, it sounds like it's very feasible, but Windows will see this as two different installations even though it's on the same machine.  When it's presented with the virtual hardware, it will prompt you for re-registration in the VM.  And when you boot on the physical box, it will do the same.  I had this problem when I moved a Windows XP Pro VM from QEMU to Xen and back.

If, as some have suggested (and I can't verify), licensing for Ultimate and Enterprise allow for virtualization and multiple installations, that should work.  Although I doubt it, I'd love it if MS would provide for this to work on the PC side.  But, they have little incentive to do it since it would encourage people to spend time using Windows within Linux enough that they might begin to tip "the other way" and eventually ditch Windows for most things.

Either way, I'm going to give this a shot with Windows 7 from my MS Technet subscription.  (A little more expensive than buying Windows 7 outright, but you get access to all of their OSes for testing, so worth it if you're in my boat)

---

