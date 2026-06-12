---
title: "A few thoughts and questions on desktop (non-game) graphics performance"
date: 2010-11-07
forum: The Cafe
---

### Post by czr114 on 2010-11-07
Hello all,


(introduction)

First let me prefix this by mentioning that I'm categorically not referring to any issues with games or video playback in this discussion.

Let me also say that I'm not trying to dredge up the old, tired Windows vs. Linux partisanship, nor do I want to see another promising discussion derailed by such.


(background)

Here's the relevant hardware specs of the system in question:

[LIST]
[*]12 cores @ 3.2GHz
[*]16GB DDR3-1600
[*]4x SSD in RAID-5
[*]2x GeForce GT 220
[*]4 Physical Displays
[/LIST]
The system dual boots Ubuntu 10.04 x64 (GNOME) and Windows 7 x64. It is worth noting that the Windows 7 was installed from rebuilt media from which I stripped every bit of eye candy, bloat, and other such foolishness.

As a matter of comparison, the Ubuntu installation has also had all relevant eye candy and effects disabled in GNOME.

The Ubuntu installation is using the recommended NVIDIA driver with no problems. All logs for X, GNOME, NVIDIA, and related show no sort of problem or hint at any degradation from optimal.


(the issue)

I have been dual booting Linux and Windows for years. In my world, each has served a useful and necessary function, although since this new workstation came on line, the extent of the necessity of Windows is limited to Visual Studio 2010. By contrast, the Ubuntu installation serves many indispensable roles, running everything from custom software (for data processing purposes), to acting as a platform for LAMP development and testing. Thus, it can be said that the Ubuntu installation is more inherently necessary.

I'd be fine moving it to a VirtualBox and dispensing with Windows entirely, however:

Having used both side by side on this new workstation, I can, without a doubt, state that the Windows installation is far more responsive and less resource intensive for running virtually every desktop workstation task.

Under Windows, application, window, and desktop manipulation, as far as graphics calls are concerned, has been rendered almost completely imperceptible to the user.

By contrast, I haven't yet noticed that on Ubuntu.

Having dual booted both by side by side for years, there have always been those sorts of delays on both, but the difference hasn't been that noticeable. With this new workstation, however, everything from window manipulation, to scrolling, to graphic manipulation is seemingly instant on the Windows side, but carries a noticeable (but slight) delay and performance hit on the Ubuntu side.

On the Windows side, only the heaviest of web pages in Firefox (heavily adblocked and stripped of scripts and flash) appear and behave sluggishly. By contrast, an intense page can present some workload to Ubuntu.

Individually, it isn't a big deal, but cumulatively, it makes a huge difference to the power user engaged in heavy, purposeful multitasking.

On the Windows side, the entire desktop environment is being handled in DX11 with excellent use of Direct2D/3D in the appropriate applications. On the Ubuntu side, it seems like OpenGL just can't keep up.

Anyway, this train of thought was brought up by the impending release of Firefox 4, which plans to take advantage of Direct2D in Windows, but continue remaining unaccelerated in Linux.

For a heavy (and loyal) Firefox user, this makes a huge difference. The Firefox performance alone makes Windows much more responsive than Ubuntu.

A similar issue occurs in OpenOffice, which surprisingly, is much faster on Windows than Ubuntu.

This might seem like a trivial complaint to many people, but it makes a noticeable impact when multitasking with 2880x1800 pixels of real estate, and a flurry of IDEs, browser windows, utilities, text editors, sticky notes, mail clients, terminals, and everything else open, and being actively interacted with, tabbed, minimized, moved, and manipulated.

The big divide really comes in when considering that, finally, the desktop computer is running faster than the user can visually process it. Up until recently, my visual cortex had always been outperforming whatever desktop system I was using, regardless of OS or hardware.

I had been hoping to get off the Windows and go Ubuntu only, but I can notice myself spending more time doing non-OS-specific things in Windows, despite full knowledge it isn't as secure, can't be locked down as well, lacks so many wonderful features, and is a general minefield of malware.

I also have an ideological objection to unfree, closed source software, even though I am forced to buy and use it for productive purposes.

With the impending availability of a Firefox 4 RC, I am eagerly looking forward to the hardware acceleration of web page rendering, but am disappointed that no such acceleration will be available on any Linux platform.

I'm not a graphics guy, but from my research, I am getting the impression that DX11/Direct{2,3}D simply has OpenGL/X beat.

Is this an accurate assessment, or is there perhaps some setting or issue which might be degrading my Ubuntu performance?

Additionally, is there anything exciting in the OSS world's upstream which might be addressing these issues in future releases?

I hope I've simply misread some of the key differences between the two, am missing a key setting on Ubuntu, and can ditch the Windows, but that doesn't seem to be the case in fact.



Whew! That was a lot. I do hope somebody can at least put the curiosity to rest as to what's really going on here.

---

### Post by cariboo on 2010-11-07
This isn't really a support question, moved to the Cafe.

---

### Post by NightwishFan on 2010-11-07
OpenGL itself is not as high level as something like DirectX (as far as I know) so comparing them is hard. I think you are better off comparing GTK+/QT/Cairo etc to Windows.

Responsivness, I might hear you there, and I have been fighting with the issue. It is nothing even close to a show stopper for me. A tiny bit more of consideration is how long applications take to start on Ubuntu sometimes. (Much faster on Debian/Windows, again saving half a second is not a big concern for me, I use Ubuntu for other reasons). Using ext3 over ext4 seemed to help for me.

Try customizing a kernel with 1000hz full premptive and tell me if you get resuslts. If so, than forward that data to the folks at Canonical and give them some hard data.

> Anyway, this train of thought was brought up by the impending release of Firefox 4, which plans to take advantage of Direct2D in Windows, but continue remaining unaccelerated in Linux.

This is incorrect. Linux will be accelerated.


Anyway this to me is just another Linux vs. Windows thread. Blantanty stating something is superior without programming with it means little. Though I agree your issues are indeed valid and deserve consideration, though not in a manner of "Vs". The issue very well might just be something to do with your Nvidia drivers.

---

### Post by czr114 on 2010-11-07
> **NightwishFan said:**
> OpenGL itself is not as high level as something like DirectX (as far as I know) so comparing them is hard. I think you are better off comparing GTK+/QT/Cairo etc to Windows.

That's where my experience starts to get a bit thin.

I know that video hardware includes explicit support for the DX graphics family, right along side OpenGL.

A quick glance at Wikipedia seems to suggest they're both software APIs with direct hardware support - which is where the issue lies.

Modern graphics are too complex to be rendered in software and crunched by the CPU - that much I know. That is why it's so critical for performance to get something speaking directly to the card.

> **NightwishFan said:**
> 
Responsivness, I might hear you there, and I have been fighting with the issue. It is nothing even close to a show stopper for me. A tiny bit more of consideration is how long applications take to start on Ubuntu sometimes. (Much faster on Debian/Windows, again saving half a second is not a big concern for me, I use Ubuntu for other reasons). Using ext3 over ext4 seemed to help for me.

Are you running an SSD? The performance difference is astounding, to a similar degree as adding an appropriate amount of RAM to a system bottlenecked in swap. Even if you can't fit everything on it, the entry models should be more than enough to fit boot, swap, system, and most of the user profiles - spillover of huge files can be handled by mounting the old magnetic stuff in your userdir accordingly.

> **NightwishFan said:**
> 
Try customizing a kernel with 1000hz full premptive and tell me if you get resuslts. If so, than forward that data to the folks at Canonical and give them some hard data.


The 1000hz preemptive appears to be in the repos already. Should I swap that in, or are you talking about a custom build?


> **NightwishFan said:**
> 
This is incorrect. Linux will be accelerated.

I could have sworn I saw none/none in the chart on the official FF4 features page, but you're right: mozilla.org is listing XRender/OpenGL as standard.

How that'll stack up in contrast to DX is beyond my expertise to estimate, but that bit is certainly a welcome development. Any HW acceleration will be a huge boost for 4.

> **NightwishFan said:**
> 
Anyway this to me is just another Linux vs. Windows thread. Blantanty stating something is superior without programming with it means little.


That wasn't the point, and I never categorically stated it as proven or generally applicable. I'm dealing with one instance here, not the type, as run on one piece of hardware. It's not scientific, but a benchmark is needed. Given that M$ is working so closely with hardware manufacturers, there's no way to avoid pulling it into the discussion.

I don't see this as being the nauseating type of Linux vs. Windows that need not be discussed anymore - it's more a question of how my hardware is being objectively utilized by two technologies: one working with the HW manufacturer, and the other trying to open up that cozy relationship.

The fact that the one issue I registered to discuss is so tiny should show that I'm trying to emulate one apparent feature in one product in another product, based on actual usage. Were OSS authors not looking to take what exists in the broader world and make it better, we wouldn't have so much of the free software we often take for granted.

If I had just said, in a vacuum, that my Ubuntu feels "graphically slow" (but by a so tiny margin), then it'd be awfully difficult to solicit useful advice from people who might have a better understanding of the "why" behind the hardware acceleration in each.

Anyway, I brought both in because I thought it might be relevant. If someone else posted a similar thread, but related to significantly disparate raw hard drive benchmarks, I could helpfully suggest that there exists a configuration problem in the slower of the two, as that hardware's performance should not be different from one to the other.

That's what I was hoping to accomplish here, in the absence of any explanation of an objective "why" accounting for the disparity.
 
> **NightwishFan said:**
>  
Though I agree your issues are indeed valid and deserve consideration, though not in a manner of "Vs". The issue very well might just be something to do with your Nvidia drivers.
I'm running the current NVIDIA accelerated graphics driver straight from the official repos, and I can't find any specific evidence of malfunction. Would you suggest disabling it for another?

---

### Post by NightwishFan on 2010-11-07
Ubuntu 10.10 has known regressions with the Nvidia drivers. Not sure how that plays in as I no longer have a Nvidia machine.

The only version to host a decent non realtime preemptive kernel is 10.04. If you have 10.04, use the preempt kernel from there. If you do not, then you might have to build one or find a ppa.

I did not mean to seem insulting, as I said it is a valid issue, just one cloaked in a lot of potential misinformation. As far as screen drawing goes on my intel hardware Ubuntu works great. It would be nice if you could aid in finding the cause for this problem. I assure you it is not some native superiority of DirectX.

Forgive me, and I hope to be of help. I just at first took your issues a bit lightly as they seemed vague. Though I do know that when you notice a bit of slug on a machine you use daily you DO notice. :)

Edit: Perhaps try a few different distributions in a live cd (as most allow you to install packges during the session)

---

