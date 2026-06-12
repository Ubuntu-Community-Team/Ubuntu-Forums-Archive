---
title: "Too many changes in six weeks"
date: 2006-06-01
forum: Testimonials &amp; Experiences
---

### Post by cristianrosa on 2006-06-01
I've been using ubuntu for a year now, and it rocks. I use it as my desktop, on servers and even in a cluster enviroment for physical simulations.
But the last week when i saw the changes of Dapper RC, i felt frustrated, the delay of six weeks, that was intented for the final polish of ubuntu, translations, artwork, bugfixes,  was used for adding a new installation method with a graphical installer?. I think it do not match the objectives of a long term support release, it throws away all the polish work done before. 
I said ok, lets tryit.
First of all the new desktop cd installer failed to run because it couldn't start X, i got a black screen, then i rebooted in safe graphic mode and i could run install. This wasn't a problem before because i didn't have to run a WHOLE system just to make an instalation, but maybe is just my case.
Dapper rocks, i only feels cheated with the delay for polishing used for adding an installer.
Congratulations and i hope this not to be done again.

---

### Post by towsonu2003 on 2006-06-02
[QUOTE=cristianrosa]This wasn't a problem before because i didn't have to run a WHOLE system just to make an instalation[/QUOTE]
I think you got confused by the recent name changes. the one that doesn't need the whole system is called something like dapper-alternative. the dapper-desktop (or named similar) is the liveCD with an installer (that is what you used I guess). I guess they want people to use the liveCD installer though... why? don't know. :-D

---

### Post by mostwanted on 2006-06-02
Because it's faster. The Live CD install took 15 minutes me (time to ser up user account, passwords, time zone, included) and I could browse the Internet on the same computer while installing. It doesn't have all the features of the old installer, but it certainly improves in the speed area.

---

### Post by cristianrosa on 2006-06-02
I think the new installer is the right direction to take, it's faster and graphical, but it was introduced in the six weeks for polishing the system. It's a huge change and it's not tested like the rest of the release. I think the delay weeks where for adding this installer, not for making the system more stable. If you pay attention you can see that the whole system is very clean and eye candy, but the installer is far away from being at the same point, i even discovered a bug, not critical, but it shows the inmaturity of the application. If you make a partition and then you right click it for "moving or resize" and change the size by writing the numbers in the spin box insted of clicking the arrows that adds or substracts a unit to the value it holds you don't get enabled the apply button, but if you click one of the arrows it enables it.
How can this be a LTS release with an installer tested for only a week, and with a GUI bug on it?
It seems far more stable the flight CD 7, with the old Live CD and Installation CD.

---

### Post by Terracotta on 2006-06-02
I second that, the gui installer is nice and easy, but why doesn't it ask or detects screen resolution? For the first time with Kubuntu I had to manually edit xorg.conf to allow resolution higher than 1023x768 (I know xserver-config or something alike exists but that's just pressing enter all the time without knowing what it actually asks, when I just want the screen resolution changed :S ).

---

### Post by Sevoma on 2006-06-04
X didn't start problably because you had the wrong refresh rates in the xorg.conf. So... that means that even if you did get it installed you would have no X until you put in the right refresh rates most likely.

---

### Post by jdong on 2006-06-04
There are definitely merits to the new graphical approach. Before the install, you get the feel of the system. And since the LiveCD is virtually identical to a brand-new Ubuntu install, having two CD's for the purpose seems like a waste.


As you've identified, there are also downsides to the system:

(1) More points of failure: Specifically, there is a chance that X cannot configure itself correctly, and that makes the install fail. However, I would not rate that as an installer problem per se. The LiveCD uses the same GUI detection routines as the final system, so if the LiveCD installer couldn't configure the system, it'd mean that the traditional installer would install a copy of Ubuntu that didn't start X, also. It's better to know these things beforehand than after investing time and space to installing Ubuntu!

As far as your issue, incorrect detection is usually blamed on poor hardware -- specifically, your monitor reported that it's capable of display modes that it's really not. Ubuntu thinks it initialized the monitor correctly, but since there is no way for monitors to report its status back to Ubuntu, we can only assume that the user is seeing the output. Fortunately there is "safe" mode for this situation. If you'd be kind enough to do so, **file a bug against xserver-xorg** on Launchpad so we can investigate exactly why it didn't detect your screen properly and hopefully correct the problems for the next Ubuntu release/update.



The main downside of the GUI installer, to me, is the RAM requirement. It takes a lot more RAM (usually 64MB on top of the minimum to run Ubuntu off the HD) to run the live installer. This is more of a problem for XUbuntu, which is more or less designed for old hardware. A system with 128MB of RAM, for example, has no issues running Xubuntu, but the LiveCD will feel extremely sluggish due to the lack of RAM.

---

### Post by jdong on 2006-06-04
[QUOTE=Terracotta]I second that, the gui installer is nice and easy, but why doesn't it ask or detects screen resolution? For the first time with Kubuntu I had to manually edit xorg.conf to allow resolution higher than 1023x768 (I know xserver-config or something alike exists but that's just pressing enter all the time without knowing what it actually asks, when I just want the screen resolution changed :S ).[/QUOTE]

It detects resolutions. It will always to try to put flat panels at native resolution (highest) and select a sensible resolution for CRT's based on reported display size. Ubuntu likes the idea of no questions asked.

Naturally, this requires the hardware to cooperate and it never ceases to amaze me how awfully mutated hardware can be. It's a good idea to build in a backup "expert mode" as a workaround, but the problem is that a workaround often gets accepted as a "solution" if it's put into a product.

---

### Post by cristianrosa on 2006-06-05
I see that the topic of the thread was misunderstood.
I'm not against the new installer, i think it's a great step in the right direction, it's a must for a system that tries to compete against other desktop OSs, the point is, that up to the beta release there wasn't any graphical installer, it was introduced in the RC, so here we can conclude a few things:
[LIST]
[*]The installer had only one week of real testing, component which i consider critical, as it is the first part of all the user experience with the OSs, if it fails, Ubuntu fails.
[*]It is a contradicion with the objectives of Dapper, if it is supposed to be a LTS release compared to Fedora or Suse, you just can't add features as huge as a graphical installer, no matter how cool it is, in the delay weeks that were initially intented for stabilizing the system. This kind of features must be planned before and it should receive the testing it deserves.
As i said in the previous post, it's obvious that the install aplication is far beyond the quality of the rest of the system.
[/LIST]
I think this change was a very inmature decision by the developers, or they have other objectives that are not being told.

---

### Post by jdong on 2006-06-05
Actually, the desktop installer first appeared on the LiveCD around April when 6.06 was supposed to release. Prior to that, it was also being developed by Ubuntu and it was based on the Guadalinex live installler (which was a tried-and-tested product).

You are correct in noting that the Live installer was quite "rushed" in development -- it quite literally took up to the very last day to iron out every last bug that we could find. I found the Live installer unusable until the RC came out.


If you look through the "dapper-changes" archive, you'll see that there was practically a Ubiquity/Espresso upload every other day, showing the fury of its development.


In the end, I think they got the bugs ironed out quite well.

---

### Post by cristianrosa on 2006-06-05
You are right, i didn't follow the dapper changes archive. But you are confirming what i see as a bad thing, it's development was very fast and fourious. That is no good for an stable release, in that last period changes must be soft and clean. What if the release date wasn't posponed?, the installer would be totally different.
Anyway, the release is great and stable! but not as stable it could had been if the new installer would had been developed for the next release.

---

### Post by jdong on 2006-06-05
I understand your concern, and you do raise a valid point. From the software engineering standpoint, the live installer was a reckless exception to an otherwise orderly, stable development cycle.

Fortunately, it didn't end up catastrophically unpolished (resists ripping on SUSE 10.1 ;) ), but nonetheless if they'd started earlier that'd have been better. However, I think the factors for continuing with the live installer were:

(1) There's always the text-mode installer (Alternate CD) that is tried, true, and Debian-stable.

(2) One of the greatest points of criticism for Ubuntu has been its text-based ("archaic") installation system. If we released Dapper with a text installer only, every reviewer would be attacking that :)

(3) A bit of a stretch, but the live installer prevents people from installing Ubuntu onto incompatible computers. Everything from the kernel/drivers to the layout of the system and the X detection routines are identical to what's used post-setup... if it didn't work during setup, it's likely not to work afterwards! It's a lot more frustrating to spend partitioning and setup effort only to end up with a non-functioning install [not to mention the risks of breaking existing OS'es] than to know that (unfortunately) Ubuntu will likely not work without manual tweaking before investing the time with the Alternate installer.

---

### Post by cristianrosa on 2006-06-06
Good points, i never thought about reviewers and hardware compatibility. I hope for the next release to have a more polished installer, with nicer graphics and icons, after all, aren't they all about?. Goodwork!

---

### Post by vseehua on 2006-06-07
[quote=jdong]
(2) One of the greatest points of criticism for Ubuntu has been its text-based ("archaic") installation system. If we released Dapper with a text installer only, every reviewer would be attacking that :)
[/quote]

archaic doesn't mean it's bad... with breezy i can setup my laptop to install it easily.. but with dapper i had to set up an external monitor just because xorg doesn't detect my laptop screen properly...

i say, why throw away something that is not broken?

---

### Post by jdong on 2006-06-08
I'm not saying that the text-mode installer is bad, nor are we throwing it away.

---

### Post by fortherose on 2006-06-08
I am new to this forum and not too sure how to use it, but here goes. I don't know if I'm speaking to a group or an individual, but here is my question. How and where do I input the following data, in order to improve the performance of my ATI Radeon x700 on my laptop. I don't know much about programming, but I can follow directions well. Thank you very much...James

Section "Device"
Identifier "card0"
Driver "fglrx"
Option "no_accel" "no"
Option "no_dri" "no"
Option "DynamicClocks" "on"
Option "mtrr" "on"
Option "DesktopSetup" "Single"
Option "ScreenOverlap" "0"
Option "Capabilities" "0x00000000"
Option "CapabilitiesEx" "0x00000000"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "CenterMode" "off"
Option "PseudoColorVisuals" "off"
Option "Stereo" "off"
Option "StereoSyncEnable" "1"
Option "FSAAEnable" "no"
Option "FSAAScale" "1"
Option "FSAADisableGamma" "no"
Option "FSAACustomizeMSPos" "no"
Option "FSAAMSPosX0" "0.000000"
Option "FSAAMSPosY0" "0.000000"
Option "FSAAMSPosX1" "0.000000"
Option "FSAAMSPosY1" "0.000000"
Option "FSAAMSPosX2" "0.000000"
Option "FSAAMSPosY2" "0.000000"
Option "FSAAMSPosX3" "0.000000"
Option "FSAAMSPosY3" "0.000000"
Option "FSAAMSPosX4" "0.000000"
Option "FSAAMSPosY4" "0.000000"
Option "FSAAMSPosX5" "0.000000"
Option "FSAAMSPosY5" "0.000000"
Option "UseFastTLS" "0"
Option "BlockSignalsOnLock" "on"
Option "UseInternalAGPGART" "no"
Option "ForceGenericCPU" "no"
Option "KernelModuleParm" "agplock=0"
Option "PowerState" "1"
BusID "PCI:1:0:0"
EndSection

---

### Post by cristianrosa on 2006-08-10
I wasn't so wrong after all...
Quoting the release notes of 6.06.1:

> * Many fixes to the desktop CD installer, including a crash when
installing in Chinese but with a non-Chinese-speaking country
(#47687), issuing a warning in the partitioner if /boot is on XFS
(#47848) or system partitions are not reformatted (#47046), a crash
if packages on the running live session are unconfigured (#47859), a
crash with certain kinds of disk attached (#48732), more defence
against gparted/qtparted crashing (#47194, #48856), improved handling
of going back and forward in the advanced partitioner, and many more,
along with translation updates. 

The installer was not ready for a LTS release. :P

---

### Post by jetblack on 2006-08-10
> **jdong said:**
> A system with 128MB of RAM, for example, has no issues running Xubuntu, but the LiveCD will feel extremely sluggish due to the lack of RAM.

Agreed, and this is exactly what happened to me. The other issue I had is that the installation documentation isn't clear about the fact that xubuntu-desktop-alternative is just xubuntu-desktop with a text-based installer. If it had said that explicitly, I wouldn't have bothered with the livecd.

Is there a reason why there are two different cds? Couldn't a single install disk grant the option of booting the livecd or the text-based installer? Or is the idea for the livecd install to involve as little user interaction as possible?


EDIT: Whoops - thread necromancy. Ah well - I still have the question.

---

