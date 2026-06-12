---
title: "EOS boot issues, new install. video driver? GUI fail to load"
date: 2015-03-20
forum: Ubuntu/Debian BASED
---

### Post by Wade_Patton on 2015-03-20
***I'm here because: ***

I can't log back in to ElementaryOS.org because i forgot my password and my manager doesn't have it and the recovery email won't come through.


***Background: ***

I've been bouncing around the web for 2 hours this morning and finally registered for this site.  

I'm fairly fresh to Linux operating systems, but have been dicking around with computers since DOS was king and we used bulletin boards for inter-connectivity, however i am no "command line" guru.  I have gotten a bit familiar with "sudo", whatever that means.;)


***Problem:*** 

I am now trying to get a functional installation going on a ***Compaq AMD Nvidia*** setup for a friend. I have been running a trouble-free (dual boot) installation of EOS-luna on my machine (off-lease refurb) for a month or two now.

After full-Linux-only installation, it will boot to GUI on the thumbdrive practically every time.  It will only boot to GUI from HDD on the*** first*** cold-boot of the day.  **Thereafter will always boot to login prompt.  **

He said a virus had corrupted the OEM Win8 system, so I did a **full install** of EOS from the same "stick" that I installed mine from.  I did the 382 upgrades when it booted properly, the other day, but it will not regularly boot to GUI, unless i boot with thumbie. [I] I have installed two or three times.  
[/I]
I don't know diddle about Linux commands (am learning rather quickly-i can do that), i just copy what folks post online and it generally works.  I've been trying to update the nvidia drivers but can't figure out how to "convert" the command i saw somewhere to use the 346.47 edition of nvidia drivers -or even if that is the proper driver set or if indeed* that* has anything to do with the problem.

I have just now rebooted with the TD and found that the graphics are: ***GeForce 6150 LE (rev A2)***.

I don't have any more time to sink into it today, hope someone can get me pointed right.  I've been over dozens of posts from lots of searching this morning and am weary of copying command line stuff.

Be glad to report the "details" per request, such that i give you the right stuff and not all the "spurious" information.  I cannot cut/paste/copy/print.  I can only eyeball and re-type using this machine.  Well I could take pics ... but maybe that won't be necessary.

Thanks for any guidance.  Hope this one is easy.  Cheers!

---

### Post by Wade_Patton on 2015-03-20
More info:

Attempt to reboot from HDD results in login prompt.  Pressing CTRL+ALT+f7 gives a list of "OK's" until:

[B]* Starting LightDM Display Manager  [fail]
                                                           [ OK ]
[  32.003101] [drm:drm_crtc_helper_set_cofig] *ERROR* failed to set mod on [CRTC:6]
[/B]
 
?

TIA

---

### Post by Wade_Patton on 2015-03-20
Simply doesn't make sense to me how the system can load from TD and not from HDD, if video drivers was issue.

Also, there is no data to save/protect.  I have no problem wiping out the HDD, but don't know how to do that in Linux.  I thought the full-install would take care of that.  If that could eliminate issues or if there's a way to re-flash the bios, I'm game.

I don't want to have to resort to XPpro, but that's my next option and it will work for the dedicated application this PC is going to be subjected to-when i get it to GUI properly

---

### Post by Wade_Patton on 2015-03-20
After letting the box cool off for three hours, it started up properly.

What to do now?  I have absolutely no faith that it will re-start.  But now that I'm "in" on the HDD installation, how to sort this out?  

Thanks!

I also see that this EOS is built on Ubuntu 12.04.  Does this mean that I may find solutions in the Ubuntu 12.04 section?

---

### Post by Wade_Patton on 2015-03-20
Well then I've been searching in the Ubuntu proper sections.  I don't know what to search for really.  Seems that installing the right video drivers and re-installing are the best options anyone ever has.

I don't know how to install the right video drivers.  That's why I listed the graphics adaptor above. I understand the Nvidia and AMD can be problematic.  

I do know how to ***re-install. *** I suppose I'll re-install it one or three more times tonight.   I don't know what could change after doing multiple re-installs.  But then I'm no code master, a code-nothing eh.


Buehler?  Anyone?



I suppose while it is running on the proper HDD installation, I'll try to download drivers via the web.  

now loading Java so Nvidia can scan my system...this stuff never ends does it.:rolleyes:

---

### Post by Wade_Patton on 2015-03-20
Well, as a forum-head I thought this was the place to ask.  Apparently not.

I got it fixed.  see y'all laters.

---

