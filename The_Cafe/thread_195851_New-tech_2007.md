---
title: "New-tech 2007"
date: 2006-06-13
forum: The Cafe
---

### Post by cheuschober on 2006-06-13
So with all the trade shows and buzz about Vista and its logo structure I came across a little blurb about one of 2007's new technologies (already in limited OEM release), the hybrid harddrive. Now, for the uninitiated, hybrid drives have a large cache of flash ram that reduce the need to spin up the harddrive by keeping commonly used files in the flash including, if enough exists, the necessary boot files for the OS.

Microsoft was behind the 'developer's table the whole time with this and supposedly any laptop that wishes to qualify for Vista-Premium branding will have to have a hybrid drive. Samsung has stated that the drive was designed specifically to work with Vista. So my question to the community is whether or not we know if any linux distros are anticipating working on this or have gotten ahold of some of the pre-release drives? What are the rumblings down the pipeline? Do we have a potential winmodem scandal (this one far more damaging?)

I've a personal stake in the matter because mid-year 2007 I'll need to replace my current laptop and would like to take advantage of the newest tech, but there's more to it than that. The winmodem scandal was not a pretty sight and because I used to travel often, the lack of a consistent and simple solution for a long period kept me away from linux distributions. A winmodem isn't nearly as mission critical as, say, a hard drive. Are there those in the community thinking about the possibility of having to do some major reverse engineering or have contacts been made with a manufacturer for driver specs? 

It's a dirty nasty game MS likes to play and I wouldn't be surprised if these essential elements were 'locked' to the microsoft monopoly.

Thoughts? Answers?

~Chad

---

### Post by rcarring on 2006-06-13
I would have thought OEMs would figure out that selling laptops with 5400 rpm 40GB drives and 256MB ram is hardly going to win them any friends in the laptop gamer community.

This hybrid drive sounds like a great idea for improving game play, especially games that have to be "installed" onto the hard disk first and require 2-3GB of files.

As regards Linux, I would expect all the major distributions would be aware of new technology (if not, they should be =D). 

However, presently, some (maybe not all) distributions have trouble with SATA hard disks, so I imagine that the hybrid drive may present some problems without some major re-tooling in the kernel area.

What do other people think?

---

### Post by cheuschober on 2006-06-13
I agree it would be a boon for gamers but I'm much more interested in what it could do for suspend states, boot, and most especially battery life but to intelligently use a mega cache like that you have to have either some really smart drivers or a very complex software layer (which really are, sort of, one in the same). But just think -- wouldn't it be nice to have all of your binaries on a flash cache for spin-less execution (since writes are limited but reads are virtually unlimited with flash) and then home + etc on the magnetic disk.

Here, since we're talking about it, let's step up the tech a bit more and talk how, not unlike smp the peformance boost that would be theoretical as the binary to perform an action can be loaded and read while the disc spins and searches to the actual data the action is being performed on. I'm not certain how fast the theoretical I/O of an average hdd controller is (And similarly is on the mb) but I'm going to assume that drive seek time / drive speed is the bottleneck.

---

