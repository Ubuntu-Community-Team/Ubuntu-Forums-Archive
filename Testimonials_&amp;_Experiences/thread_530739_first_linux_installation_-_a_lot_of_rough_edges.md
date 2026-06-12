---
title: "first linux installation - a lot of rough edges"
date: 2007-08-20
forum: Testimonials &amp; Experiences
---

### Post by AlpineCarver on 2007-08-20
first some background: i have a lot of experience with unix, but have been away from unix-like OSes for a number of yrs. this is my first linux experience. i normally build my own PCs and install windows on them.

attached at the end of this post is a list of the problems i had, just getting ubuntu 7.04 (feisty fawn) running on a new AMD X2 build using a Biostar TF7050-M2 motherboard. i'm still in the process of selecting, installing, and learning about applications, so i'll mostly refrain from commenting on them, except for the following 2 brief comments:
[LIST=1]
[*]while still runnning under windows, our family had already switched our routine "personal productivity" work to open-source apps: OpenOffice, Firefox, and Thunderbird. these run nicely under ubuntu...

[*]EXCEPT that OpenOffice has a font problem under linux (not under windows) that was a major problem for me. if anyone cares to see the sordid details, [CLICK HERE](http://qa.openoffice.org/issues/show_bug.cgi?id=79586). (and if the issue matters to you, add your "vote" for getting this bug fixed...)
[/LIST]
at the end of the day, i have a usable system, and i think i'm going to like ubuntu, but this was a **lot** more work than any windows install i've ever done. many of the issues listed below took hours of googling to figure out. if i had it to do over again, i would just buy a new pc from lenovo or (shudder) dell with linux pre-installed. perhaps if you happen to pick the right components, you wouldn't have the problems i had, but who would want to take a chance on possibly wasting several days wrestling with an installation, except for "hobbyists" who do this kind of thing for fun?

here are the specific issues i encountered and eventually solved:
[LIST]
[*]installer won't make a partition > 200GB. doesn't tell you that the size is the problem; just fails. had to use a gparted livecd.
[*]installer can't talk to my keyboard (ibm/lenovo usb ultranav), but installed system can. had to use a different keyboard during installation.
[*]installer **can** talk to my SATA DVD drive, but installed system **can't**. the BIOS "SATA Operation Mode" default value of "IDE" worked during install; had to switch it to "AHCI" for the installed system.
[*]X server failed to start. had to boot into "safe graphics mode."
[*]system complained about "buffer overflow on device fd0". in BIOS, had to set "drive A" to "none."
[*]installer stalled at 83% - “Installing language packs” / “Downloading package lists”. chose “skip”.
[*]system / restricted drivers – enable “NVIDIA accelerated gfx” results in a black screen. rolled back to a partition image i'd made earlier and tried to install a graphics driver from nvidia.
[*]many problems installing nvidia graphics driver. could have been avoided if i'd found the right "howto" guide, but i thought i'd just use the instructions that came from nvidia. silly me...
[*]system refused to display at the full resolution of my 1600x1200 screen. eventually fixed by adding the following line in /etc/X11/xorg.conf:
	Option "ModeValidation" "DFP-0: NoMaxPClkCheck”
and prepending to the “metamodes” string in the “Screen” section – “1600x1200 +0+0;”
[*]gnome "hardware sensors" applet would not display CPU temps for my dual-core AMD processor. had to download the latest version and build from source.
[/LIST]

---

### Post by K.Mandla on 2007-08-21
A good list, and many worth mention. I think it's important to note that some of the points you made fall outside Ubuntu's control. The font issue is, as you demonstrate, an issue with OOo, and not Ubuntu. 

And in all fairness, how much of your video problems are really the fault of Ubuntu? Once you've installed proprietary drivers, you've wandered outside Ubuntu's control. ...

And the BIOS-fixable floppy check is something I get too, from time to time. I know it irritates some people, but more irritating would be no floppy check and a system that has a fd0 that can't access it.

Otherwise, a good list. Did you file or confirm any bug reports on Launchpad? That would be the next step.

---

### Post by AlpineCarver on 2007-08-21
> **K.Mandla said:**
> I think it's important to note that some of the points you made fall outside Ubuntu's control. The font issue is, as you demonstrate, an issue with OOo, and not Ubuntu.

true, but this problem would have completely prevented me from using any flavor of linux, since all my documents use these fonts, so i think the bug should be of concern to those who care about ubuntu. (it doesn't seem to be of much concern to any of the OOo developers...)

> And in all fairness, how much of your video problems are really the fault of Ubuntu? Once you've installed proprietary drivers, you've wandered outside Ubuntu's control. ...

the first thing i did was go to system / restricted drivers. it gave me the option to enable &#8220;NVIDIA accelerated gfx&#8221;, which i clicked. it then proceeded to load some version of the nvidia graphics driver, but not one that works with my hardware. i think at least that much is a ubuntu problem. at the very least, it should refuse to load a driver, rather than load one that hoses your system. anyway, i assume the next release of ubuntu will include an nvidia driver of version 100.14.11 or later, which would solve this problem.

> Otherwise, a good list. Did you file or confirm any bug reports on Launchpad? That would be the next step.

some of these are already filed; i added comments to several.

---

### Post by em007a on 2007-08-21
Glad you stuck with it and have a usable system. One thing is for sure, if you need to re-install for any reason you'll have a much easier time now that you know what to look out for.

---

### Post by 3rdalbum on 2007-08-22
The keyword of your post was "new". This sounds like the sort of problems you'd encounter with attempting to run a brand-new system with a distribution whose components are a couple of months old.

The good news is that the next version of Ubuntu, or possibly the one after it, will be where everything works absolutely perfectly. But at least you now have refreshed your Unix experience!

---

### Post by wolfen69 on 2007-08-22
welcome! and dont give up. it gets easier everyday.

---

### Post by Iesvs on 2007-09-28
I had an old install of Feisty Fawn and I recently did a whole hardware upgrade complete with a new **Biostar TF7050-M2**.
Everything worked just fine, and I'm glad I avoided the harddrive problems that seem to have plagued others who have used this motherboard - one of the perks of having a harddrive with a previously installed OS, I suppose.
The only problem I've run into though is that I can't get sound over the HDMI down.
I haven't been able to really mess around with it, but that's tonight's plan.
What I wanted to know was whether anyone else had problems with audio in the TF7050.

Also, there are a TON of unknown devices, but that might be a stayover from my previous hardware config.

If I can't get audio to work, I might just reformat and install the Gusty beta.

---

### Post by armandh on 2007-09-28
usb keyboard problem on my sons xp install too
not just a linux problem

---

### Post by AlpineCarver on 2007-09-29
> **Iesvs said:**
> 
What I wanted to know was whether anyone else had problems with audio in the TF7050.


i'm using the normal audio connections thru the motherboard's I/O panel, and it's working fine, both speakers out and mic in. i haven't tried audio over hdmi.

i think i recall seeing some discussion of problems with audio over hdmi in the past, but i don't recall what conclusions anyone came to.

---

