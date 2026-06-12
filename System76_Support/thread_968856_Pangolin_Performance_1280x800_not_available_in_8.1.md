---
title: "Pangolin Performance: 1280x800 not available in 8.10 Intrepid"
date: 2008-11-03
forum: System76 Support
---

### Post by phyzome on 2008-11-03
When I upgraded to Intrepid, my screen resolution came up 1024x768, which is small, distorted, and ugly on my widescreen laptop, a panp4i.

System -> Preferences -> Screen Resolution presents a very confusing dialog. (Also, the Help button doesn't work.) If I uncheck "mirror" (what is that?) then I can select 1280x800. The screen resizes, but Gnome does not. See attachment.

xfix in recovery mode was of no use, and adding a Display subsection to xorg.conf with appropriate modes did nothing.

Obviously, I should have waited to upgrade. But how was I supposed to know?

---

### Post by phyzome on 2008-11-03
By the way, I did a full system backup with rsync just before upgrading. I should be able to restore my system to 8.04 by booting from LiveCD and rsyncing back, yes?

---

### Post by thomasaaron on 2008-11-03
It's available in Intrepid. Sounds like some sort of xorg issue during the upgrade process.

Try:
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo apt-get --purge remove xserver-xorg-video-intel
sudo apt-get install xserver-xorg-video-intel
sudo dpkg-reconfigure xserver-xorg #Choose all defaults
sudo reboot -h now

---

### Post by phyzome on 2008-11-03
I went ahead and rsync'd everything back into place. There were far too many bugs. (Suspend key didn't work, ACPI had some problems, screen resolution, cheese stopped working...) Also, the upgrade process itself had a number of problems, such as not recognizing the perfectly good Intrepid CD. It had to download everything instead of loading from CD.

Perhaps I will try again in a few weeks.

> **thomasaaron said:**
> It's available in Intrepid. Sounds like some sort of xorg issue during the upgrade process.

Try:
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo apt-get --purge remove xserver-xorg-video-intel
sudo apt-get install xserver-xorg-video-intel
sudo dpkg-reconfigure xserver-xorg #Choose all defaults
sudo reboot -h now

Thanks for the tip. Is this the sort of thing that will be resolved after a few weeks, or will I definitely need to do that when I upgrade?

Also, how will we know when 8.10 is officially supported?

---

### Post by thomasaaron on 2008-11-03
> Is this the sort of thing that will be resolved after a few weeks, or will I definitely need to do that when I upgrade?

Your problem is probably pretty random in nature considering the number of customers who have upgraded and the relatively few who have encountered problems. 

My suggestion is just an educated guess as to how you might fix it. It's not a regular thing you would do after every upgrade. I'm just betting that you have some sort of config file corruption somewhere. I kind of doubt it is a bug, per se - but I could be wrong.

```
Also, how will we know when 8.10 is officially supported?
```

It is officially supported when Canonical releases the final version (i.e. after the beta and alpha versions). So, that would've been Friday? or Saturday?

---

### Post by phyzome on 2008-11-03
> **thomasaaron said:**
> My suggestion is just an educated guess as to how you might fix it. It's not a regular thing you would do after every upgrade. I'm just betting that you have some sort of config file corruption somewhere. I kind of doubt it is a bug, per se - but I could be wrong.

I'd rather not go through the backup/restore process again, if possible. (There's too much room for error.) Is there a way I could put my current system into VirtualBox and test the upgrade process that way? Would that be sufficient to flush out any display issues?

---

### Post by thomasaaron on 2008-11-03
I'm sure it's probably doable... somehow... but it seems a little complex. You might be onto something, though.

You might create an Ubuntu VM in virtualbox (not your primary installation, but an... expendable... VM) and run the upgrade on that. That way, if it gets hosed, who cares.

But I don't think the VM would have a direct connection with the hardware. It would *really* be using the xserver/xorg of the main install. So, it might not work the way you would hope.

To be honest, this is why I prefer keeping a separate home partition and doing a fresh install. Ubuntu is a complex OS, and there are just so many little crannies that errors could conceivably slip through in the upgrade process -- whether it is something the devs missed or a data corruption because of stressed servers.

One might also create a separate partition for installing and testing new Ubuntu versions. Then, if you like it, you can transfer your files over to the new partition.

Hey, at least you were smart enough to do a good backup! That's something to be happy about, yes?:lolflag:

---

### Post by phyzome on 2008-11-03
> **thomasaaron said:**
> To be honest, this is why I prefer keeping a separate home partition and doing a fresh install. Ubuntu is a complex OS, and there are just so many little crannies that errors could conceivably slip through in the upgrade process -- whether it is something the devs missed or a data corruption because of stressed servers.

I've certainly considered it, but I have some concerns:
[LIST]
[*]What happens to MySQL databases and settings?
[*]Local apache2 website configurations?
[*]SSH settings like AllowUser?
[*]GDM login settings?
[/LIST]

It's not that I've reconfigured my system to any great extent, but I've got a lot of data and settings that would be lost by in a fresh install.

> **thomasaaron said:**
> One might also create a separate partition for installing and testing new Ubuntu versions. Then, if you like it, you can transfer your files over to the new partition.

Huh. I could definitely mirror my partitions to another drive, and use that as a test bed for upgrading. Perhaps I'll try that.

> **thomasaaron said:**
> Hey, at least you were smart enough to do a good backup! That's something to be happy about, yes?

I learned my lesson the hard way.

Oh, and for those of you following along at home, here is the command I used for backup:

```
sudo rsync --dry-run -av --delete-during --exclude=sys --exclude=dev --exclude=proc --exclude=tmp --exclude=mnt --exclude=media / /media/FreeAgent/fibonatch/ | tee results.txt
```

Remove the `--dry-run` once you're satisfied it does what you want.

To restore, I booted from a Live CD, mounted the laptop's root partition (and then the home partition onto that), and reversed the rsync command.

For safety, you might want to remount the backup drive readonly during a restore.

---

### Post by thomasaaron on 2008-11-04
I upgraded my personal GazV5 last night, and it was pretty close to flawless. I think I found my favorite way to do it.

I downloaded the alternate CD iso to my desktop, mounted that image and upgraded from it.

The whole process took about 30 minutes (as you don't have to download all the packages in real time from a server or CD). Then ran updates, ran the System76 driver, fixed my lamp server (which was disabled by the upgrade), and called it a night.

---

### Post by marcor on 2008-11-05
I have a panp4i with intel graphics with a fresh install of Ibex. The screen resolutions I can choose from all have the wrong ratios (4:3 instead of 16:10). The problem is that the system detects another screen but none is plugged in. You can see that with xrandx. here is the output of xrandr on my computer: 

LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       59.9*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
HDMI-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 connected (normal left inverted right x axis y axis)
   1360x768       59.8  
   1152x864       60.0*
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  

you can see that HDMI-2 is detected as if there was a screen plugged in. This is clearly a bug. I temporarily fixed the problem by disabling this output with xrandr but I am looking for a permanent fix.

Marco

---

### Post by phyzome on 2008-11-05
> **marcor said:**
> I have a panp4i with intel graphics with a fresh install of Ibex. The screen resolutions I can choose from all have the wrong ratios (4:3 instead of 16:10). The problem is that the system detects another screen but none is plugged in. You can see that with xrandx.

Aha! That's what mine was doing, too. A good clue as to the problem.

---

### Post by thomasaaron on 2008-11-06
Yes, we get this in the shop too. But it *only* happens on the PanP4i. It does not happen on the DarU3, which has the same graphics chipset, so it is probably an issue with the xserver-xorg-video-intel driver.

I've not figured out how to get rid of the "ghost" monitor. However, if you click on it, and then set the resolution to "Off", you can then click on the LCD box and set its resolution to the correct one.

You might want to file a bug against the intel driver on it. The only other thing I can think of is that there may be some hardware/wiring detail that causes the driver to think there is another monitor attached.

Weird! I've never seen that one before.

---

### Post by marcor on 2008-11-07
All right, I tried your fix and it worked. I also reported a bug in launchpad both as a system76 bug and xserver-xorg-video-intel bug. You can see my bug report there.

Thank for the help.
Marco

---

### Post by thomasaaron on 2008-11-07
You can go to System > Prefs > Screen Resolution and uncheck "mirroring", turn the ghost monitor off, and set your resolution for the LCD to the proper setting.

This is a problem, most likely with the Intel driver. It doesn't occur on our other machines that have intel graphics. Hardware detection problem, I'd guess.

It's going to have to be fixed upstream. I saw your bug report and will contribute whatever I can to help the fix it upstream.

---

### Post by calibre97 on 2008-11-12
phyzome,
Definitely, definitely, DEFINITELY leave enough room to try out new dot upgrades in their own partitions. I upgraded my laptop HD to a 160GB (149 working) model for this exact reason. I have a 30GB partition for stuff, a partition for Mandriva, a separate home partition for Hardy, a root partition for Hardy, a partition for Ibex, and a large partition for VMs. Of course there's also a swap partition. I started with Hardy in a single partition but then moved /home out to it's own space. I'm now mainly living in Ibex, but I installed VMWare 2.0 only to find that it doesn't work with 2.6.27 kernels so when (and it's rarely) I need XP, I boot into Hardy and fire up VMWare Server 1.6. Or is it 1.06? Anyway, previous version. This setup allows me to try stuff in a VM, or in it's own partition. Once I'm completely comfortable in Ibex, I'll drop the Hardy partition and have it available for something else.

By the way, I've never done this, but is it really a simple matter of installing to the / partition and then remapping to the /home partition or copying /home to /home(of new install)? I'm thinking this only works for RE-installs of the same distro version, right?

And finally, I'll try your rsync command next time. I've never used any excludes, but then I also haven't had to do any restores yet so maybe I don't have a 'good' backup eh? By the way, you can save a few keystrokes and just use -avn for the dry run. n=dry run.

---

### Post by thomasaaron on 2008-11-13
This bug was discussed earlier in this post. If you go to System > Preferences > Screen Resolution and uncheck the "Mirror" checkbox.

It only occurs on the PanP4i when imaged from a live cd. It could be a hardware design detail that confuses the intel driver.

---

