---
title: "Sales Question - Wild Dog options"
date: 2011-06-21
forum: System76 Support
---

### Post by benenglish on 2011-06-21
I apologize in advance for the length of this post but I'm trying to fully comply with the requirements listed in the "How to request support or product information" sticky.  That sticky asks for three pieces of info in these queries.

[LIST=1]
[*]First, which model?  I've just about decided to order a Wild Dog based on specs.  However, I'm having a little trouble deciding what to tick off for options.

[*]Second, what will it be used for?  The system will be used as my main desktop.  In no particular order (really, this is just a quick brain dump) this is the sort of stuff I do with my computer:
[LIST]
[*]I consume lots of media, typically downloading hundreds of thousands of files and file parts from usenet monthly.  On Windows, this means I frequently find myself opening a folder, clicking "Select All" and dragging a group of files to a new location - only to find that I've selected 20,000 files and the machine is now essentially useless while it grinds away for several minutes.  My linux boxes typically perform only a little better, though I always have the option to think ahead and do such moves via the command line so that things will go much quicker.  Still, it would be really nice to have GUI file management that could take some stress without flaking out.

[*]All those media files are stored on a separate 4-disk JBOD box so an eSATA connector is a must while the size of the boot disk is pretty meaningless.

[*]While consuming all those video and audio files, I constantly find myself trying to play high-def files that have caused all my prior Linux boxes to stutter or stop.  I need very strong video playback although this won't be, specifically, a media center.  It just happens that it will be located next to my TV.  I intend to hook up a new, large HD flat screen (not yet purchased) to the machine in the near future.  I'll also be upgrading my monitor to a 30" soon.  Most likely candidate is a NEC MultiSync PA301w, displaying at 2560 x 1600 and connected via "2xDVI-D w/HDCP, 2xDisplayPort 1.1a" video inputs, meaning that I'll need a card with a dual-link DVI output to run it - but that's not a problem, right?

[*]I've recently retired so I'm about to start playing with Gimp, Kino, and whatever I can find in the way of games.  Biggest emphasis is on Gimp; I used to be a photographer and I'll be doing a good deal of photo work.  Making transparencies for contact printing means working with still image files of 100 megs or more.

[*]I currently have 4 Linux boxes running and I want to combine them all to simplify the clutter.  To that end, the new machine needs to be spec'd well enough to run one or two virtual machines of fairly low power.[/LIST]

[*]Third, the questions.  I'm trying to sort out the options.  Maxing the processor and RAM are no-brainers but I have two areas where I'm unsure.

[LIST]
[*]To begin with, the video card choices have me confused.  There's not much in the way of heavy-duty Linux games that require crazy 3d performance and most of what I've described above is 2d.  So where's the sweet spot?  Specifically, as you go through the progression from the order page (bulleted below) what is gained with each step?  The $250 jump to the GTX 580, for example, isn't a problem for me but does it actually buy me any noticeable, real-world performance gain?

[LIST]
[*]     512 MB nVidia GeForce GT210  
[*]     1 GB nVidia GeForce GT430 ( +$49.00 )
[*]     1 GB nVidia GeForce GTS 450 ( +$109.00 )
[*]     1 GB nVidia GeForce GTX 460 ( +$219.00 )
[*]     1 GB nVidia GeForce GTX 560 Ti ( +$299.00 )
[*]     1536 MB nVidia GeForce GTX 580 ( +$559.00 )
[/LIST]

[*]Also, I have no experience with SATA III drives.  I always use whole-disk encryption and prefer it in hardware, either via Stonewood drives or an inline encryptor.  Both those options, however, limit me to SATA II.  Alternatively, I can do the encryption in software by re-installing the OS via the alternate install disk and preserve SATA III speeds.  Given my file management propensities, is it worthwhile to go for one of the SATA III drive options?
[/LIST]

[/LIST]
TIA for any thoughts,

Ben

---

### Post by isantop on 2011-06-22
> **benenglish said:**
> I apologize in advance for the length of this post but I'm trying to fully comply with the requirements listed in the "How to request support or product information" sticky.  That sticky asks for three pieces of info in these queries.

[LIST=1]
[*]Third, the questions.  I'm trying to sort out the options.  Maxing the processor and RAM are no-brainers but I have two areas where I'm unsure.

[LIST]
[*]To begin with, the video card choices have me confused.  There's not much in the way of heavy-duty Linux games that require crazy 3d performance and most of what I've described above is 2d.  So where's the sweet spot?  Specifically, as you go through the progression from the order page (bulleted below) what is gained with each step?  The $250 jump to the GTX 580, for example, isn't a problem for me but does it actually buy me any noticeable, real-world performance gain?

[LIST]
[*]     512 MB nVidia GeForce GT210  
[*]     1 GB nVidia GeForce GT430 ( +$49.00 )
[*]     1 GB nVidia GeForce GTS 450 ( +$109.00 )
[*]     1 GB nVidia GeForce GTX 460 ( +$219.00 )
[*]     1 GB nVidia GeForce GTX 560 Ti ( +$299.00 )
[*]     1536 MB nVidia GeForce GTX 580 ( +$559.00 )
[/LIST]

[*]Also, I have no experience with SATA III drives.  I always use whole-disk encryption and prefer it in hardware, either via Stonewood drives or an inline encryptor.  Both those options, however, limit me to SATA II.  Alternatively, I can do the encryption in software by re-installing the OS via the alternate install disk and preserve SATA III speeds.  Given my file management propensities, is it worthwhile to go for one of the SATA III drive options?
[/LIST]

[/LIST]
TIA for any thoughts,

Ben

Given your HD video and monitor requirements, I think  you would be best going with the GTS450 or the GTX460. As for SATA, I would go with software encryption for the extra speed from SATA III.

---

### Post by Blasphemist on 2011-06-22
I recommend that you be careful about any system where you'd have switchable graphics, one embedded and another added. There seems to be some support for this in the windows drivers but it is quite iffy for linux.

---

### Post by macaholic on 2011-06-22
> **Blasphemist said:**
> I recommend that you be careful about any system where you'd have switchable graphics, one embedded and another added. There seems to be some support for this in the windows drivers but it is quite iffy for linux.
I would respectfully disagree. For systems that have both embedded graphics and discrete graphics, the embedded graphics tend to just be ignored (unless you really want to use them for some reason). As far as I know, the only windows support for this is on laptops with [Nvidia's Optimus]("http://en.wikipedia.org/wiki/Nvidia_Optimus"), and there is a very new project called bumblebee that attempts to implement something like that on linux.

---

### Post by Blasphemist on 2011-06-22
> **macaholic said:**
> I would respectfully disagree. For systems that have both embedded graphics and discrete graphics, the embedded graphics tend to just be ignored (unless you really want to use them for some reason). As far as I know, the only windows support for this is on laptops with [Nvidia's Optimus]("http://en.wikipedia.org/wiki/Nvidia_Optimus"), and there is a very new project called bumblebee that attempts to implement something like that on linux.

I hear you. I can't speak to how well the windows drivers handle this just that the closed source drivers for windows say they handle it. I've also looked into bumblebee and debumblebee and they are a help though they seem to pretty klugy and temporary. I'm hoping wayland will allow for proper and efficient use of this configuration.

---

### Post by isantop on 2011-06-23
While the Wild Dog has both embedded and discreet graphics, only the discreet card will be used; the embedded graphics are disabled, and they do not switch.

---

