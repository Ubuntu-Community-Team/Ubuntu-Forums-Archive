---
title: "Why has my default bootsplash changed to a persistent ugly purple progress screen?"
date: 2010-12-20
forum: Ubuntu Studio
---

### Post by cshard on 2010-12-20
Although this problem is "solved", it's still unknown why my system was unable to recognise my gfx settings and allow plymouth to work correctly. For the time being, I have to stick to the default disc installation of Ubuntu Studio 10.10 AMD64 ver. and not update anything major via synaptics.

If someone can take note of this oddity and explore it further...?



----------------------------
As the title says, this is the problem I'm facing. I'm nearly at the end of my patience with Ubuntu Studio, and I think I've reached the limit of my knowledge on how to solve this thing.

My question is simple. Why is my default boot splash screen constantly defaulting to an ugly purple one, and why am I not able to recover from this problem even after a full reinstall?

I am using a brand new MSI laptop :
Model : FX603
CPU : Intel Core i5-450M
GPU : Nvidia GeForce GT425M / 1 GB DDR3
RAM : 2 x 2GB DDR3
Dual Boot : Windows 7 Home / Ubuntu Studio 10.10

Sequence of events and troubleshooting steps at each stage:
[LIST=9]
[*]Ubuntu Studio did a complete update of all packages, including a new Linux Kernel
[*]I installed the official Nvidia GPU drivers using the inbuilt application. After it restarted, Studio would only boot to shell mode.
[*]Using various forum threads, I attempted to purge the nvidia drivers from the system, I tried to manually edit the xorg config file to use the default gpu settings (Changed "nvidia" to "nv"), and finally managed to restore default setting by entering recovery mode
[*]While booting back into GDM, I see that the nvidia drivers are still listed as "active". I deactivate them.
[*]After recovery, I noticed that grub was showing more than one Linux Kernel. I entered recovery mode again to attempt to clean the list of redundant entries
[*]While booting, the purple screen starts showing up
[*]I enter recovery mode again and attempt a DPKG repair. This happens a few times. However, the only effect is to restore the boot splash and logo briefly, then it will revert to the purple splash again
[*]I attempt to reinstall the system one more time. During or after grub is being installed, the power cuts. I repeat the reinstallation again and the power does not cut again. Installation is a success.
[*]Purple boot splash shows up again. I attempt DPKG repairs again, with only temporary effects
[/LIST]

Why is this problem persisting, even after I did a full reinstall? Could one of the events listed have permanently altered the hardware of my laptop, and that is preventing a recovery? This is especially strange because a DPKG repair will temporarily restore everything, but 2-3 reboots later and I'm back to square one. Also, my system will shutdown normally with the logo fully visible. It's only affecting my startup.

Which of the following is most likely to have causing all this pain?

[LIST]
[*]The nvidia driver installation and attempts to purge them
[*]Restoring failsafeX graphics mode
[*]Trying to clean GRUB using recovery mode
[/LIST]

I'm now running a clean install of Ubuntu Studio 10.10 and I'm still getting that purple screen when booting up. Is there any way to permanently restore it back to the Studio default blue logo again? I do not want to repeat yet another full reinstall.

---

### Post by cascade9 on 2010-12-20
> **cshard said:**
> Which of the following is most likely to have causing all this pain?

[LIST]
[*]The nvidia driver installation and attempts to purge them
[/LIST]


IMO, this. The FX603 uses switchable graphics (optimus) and nvidia doesnt support it with linux.

---

### Post by cshard on 2010-12-20
That's also my suspicion as well, but I can't figure out why I'm still getting that purple boot screen despite a complete reinstall. I've long purged the system, well, nuked it per say with a fresh install, and any changes it did should have disappeared. Unless it affected the hardware itself?

That said, can I manually change the boot screen myself to the default Studio 10.10 one?

--------------

A quick update. Shortly after posting this, I found another thread regarding the purple boot screen, with someone calling it a "Fedora Style" boot screen. The link to this thread is : [http://ubuntuforums.org/showthread.php?t=1647571&highlight=purple+boot](http://ubuntuforums.org/showthread.php?t=1647571&highlight=purple+boot) . I wonder if this is caused by a bad update instead?

--------------

Additional Edit:
I just realized one different thing that was done during the latest reinstall. I had the laptop hooked up to my network. If this is indeed a problem that is caused by an update to Ubuntu, would the installer attempt to find updated files online during an installation, overwriting the disc defaults?

---

### Post by garvinrick4 on 2010-12-20
#Go into Synaptics and type in plymouth:
Select various plymouth themes and install.
#Run the first command and it will give you a selection of which theme
you would like to use. 
#run second command after choosing theme:
```

sudo update-alternatives --config default.plymouth 
```
```
sudo update-initramfs -u
```

---

### Post by cshard on 2010-12-20
@garvinrick4: Ok, just tried doing that. I downloaded the default Ubuntu Theme, replaced the default Ubuntu Studio them with it, and it seemed to work... the shutdown sequence showed a proper default boot screen with the Ubuntu logo, even if it was still the ugly purple color.

Once it booted up, it went straight back to square one. I'm beginning to get a grasp of what that ugly screen is - I think it's probably the plymouth-theme-ubuntu-text that shows up if there is no support for a graphical theme on the system.

If all this still doesn't work, I'm going to do one more reinstall, this time without a network connection. Maybe that's what caused a fresh install to force me to see plymouth-theme-ubuntu-text persistently.

---

### Post by garvinrick4 on 2010-12-20
Something just is not right. If themes were selected.
Like say the solar theme and installed in system.
Then run code and select and run the second code to update it will work.
Check that you are installing plymouth graphic themes are like 5 of them.
##Has nothing to do with reinstalling whole system. Is a themes plymouth thing.

---

### Post by cshard on 2010-12-20
Yep, something is definitely wrong. I just hope it's just a "that's a simple mistake" kind of wrong, not the doomsday scenario "your gpu is totaled" type of wrong. I shouldn't think that anything Ubuntu would install will permanently render my system unable to display a plymouth theme, so all my suspicion is on nvidia.

Anyway, I did this earlier :

1) Used synaptic to download plymouth-theme-ubuntu-logo
2) Ran the two scripts you posted
3) Restarted. Ubuntu bootsplah is visible while shutting down
4) During boot up, it reverts back to the plymouth-theme-ubuntu-text again

What you are suggesting is to download more themes and try to set them as default then?

A quick question : what would happen if I removed the plymouth-theme-ubuntu-text package? I haven't done it yet, but if it's causing trouble, would that force it to use another theme, or crash?

---

### Post by garvinrick4 on 2010-12-20
There is Glow, Spinifity,Solar,text, fade, they are grapical boot animation in synaptics.
Type in plymouth and they are about the last 5 or so in order. solar is a nice blue if you
cannot stand purple.

---

### Post by cshard on 2010-12-20
Hmm, so far so good. I downloaded Solar and set it as default. This time I let the system start without input and plymouth displayed the correct theme. I switched back to the default Studio theme and it seems to be back to normal.

I think I'm going to observe it for a while before I declare this solved. It's backtracked on me too many times for me to assume that it's fixed for good.

Many thanks, garvinrick4, and the others who posted to help me.

---

### Post by cshard on 2010-12-20
Uh, looks like a spammer decided to pay a visit? How do I get rid of the post above mine?

garvinrick4, the changes didn't stick. Worse, now my splash image when shutting down has disappeared and replaced with text. The problems happened again after logging on, and installing GParted in Synaptics.

I'm going to try setting it to Solar again to see if it will stick instead.

Update: Nope didn't stick. I'll keep at it for a bit.

---

### Post by cascade9 on 2010-12-20
> **cshard said:**
> That's also my suspicion as well, but I can't figure out why I'm still getting that purple boot screen despite a complete reinstall. I've long purged the system, well, nuked it per say with a fresh install, and any changes it did should have disappeared. Unless it affected the hardware itself?


When you reinstalled, you didnt install the nvidia drivers, right? To be honest I'm not sure its the nvidia drivers causing this though. 

If you report the post above yours, maybe a nice admin/mod will delete it for you ;)

---

### Post by cshard on 2010-12-20
Nope, none of that. After my brief struggle in shell mode, I decided not to risk it any further by touching the nvidia drivers again. Also, this is a brand new install, and unless connecting it to a network during installation will also auto download gfx drivers, I don't think there's any nvidia in this install.

A clean install shouldn't leave any trace of previous installations or settings, unless my knowledge of Ubuntu is really that bad. ^^

I think I'll just do a clean install again later without connecting it to a network. I'm still hoping it's something to do with the network connection during the installation I did this morning, and not something worse.

---

### Post by cshard on 2010-12-20
One clean install, far, far away from a network connection later...

Well, it appears to be that the updates to the linux kernel and other stuff broke my system. My system is now back to pre-update, and as far away from the update system as possible (although I do need to install GParted later) and I've got back my bootsplash.

I'm going to list this as partially solved, but I'm still no closer to the reason this happened. Is Ubuntu Studio 10.10 that different from the updates lurking in synaptics? ^^

---

