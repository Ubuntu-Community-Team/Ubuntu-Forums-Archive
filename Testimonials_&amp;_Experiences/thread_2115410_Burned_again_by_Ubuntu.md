---
title: "Burned again by Ubuntu"
date: 2013-02-12
forum: Testimonials &amp; Experiences
---

### Post by kg4jxt on 2013-02-12
I tried Ubuntu a few versions back but could not get wifi to work and gave it up. I had a nice souvenir though; the Grub loader which of course I could not remove. But technology has moved on so I tried again - strike two Ubuntu. This time I made a dvd from the iso download and it ran fine (just slow loading of course), and tried installing. But the installer dumped me into an impenetrable thicket of advanced jargon when I did not want to replace Windows 7, but instead "do something else". I was confronted with (to me) bizarre partitioning and swaparea questions that were not mentioned in the handy simple how-to-install instructions. Now I have an inoperable Ubuntu install and a nice souvenir: the Grub loader. I would not dream of going through this annoyance a third time (until the next computer purchase when I am liable to wind up with another rotten Microsoft OS).

Is it THAT HARD to develop an installer that does not require familiarity with system architecture to operate? :confused:

---

### Post by matt_symes on 2013-02-12
Moved to **testimonials and experiences**.

---

### Post by offgridguy on 2013-02-12
I can sympathize with your plight, however there is lots of help available in these forums.To begin i would suggest reading the gparted tutorial, to get an understanding of how partitioning works, still relative unless your computer is very new with gpt partitioning.
Tutorial here.

[http://dedoimedo.com/computers/gparted.html](http://dedoimedo.com/computers/gparted.html)

Ignore the advice, i didn't realize this was being moved to T&E, and this isn't a help forum.

---

### Post by mastablasta on 2013-02-13
First sorry for your experience, but just as you learned about windows before you started using it, you should also learn a bit about linux before you give it a try.
 
> **kg4jxt said:**
> Is it THAT HARD to develop an installer that does not require familiarity with system architecture to operate? :confused:
 
Ubuntu installer takes about 5 clicks a user name and password and it install everything automaticly. how more simple do you want it? is there any other installer for a PC OS that is even simpler?
 
what you are talking about is advanced OS install. try installing Windows next to MacOS or Linux. see how far you get and how easy it will be to dualboot... for starters windows will overwrite MRB with it's own boot manager that can only recognise windows and maybe MSdos (not sure about that). unlike GRUB or LILO that can recognise many different OS. an even nicer souvernir wouldn't you say?
 
to make an easy dualboot - create empty disk space (no format) using windows disk manager. then during install select install to largest empty/unformatted  disk space. and all the rest will be done automaticly.
 
oh and grub is easilly replaced by windows boot manager using windows repair disk (search "windows fixmbr"). 
 
btw paritions you need are / and /swap. swap is like pagefile. and you don't need it if you don't plan on hibernating or suspending. / (or root) is same as C:\ if you have UEFI boot (instead of BIOS) then you also need /boot 
 
 
a suggestion -to learn more about linux install without doing any changes to your current OS i suggets a virtual box install. here is a nice tutorial: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
and that you read a bit more about Ubuntu and Linux in Ubuntu manual (see my signature).

---

### Post by 3rdalbum on 2013-02-13
The Ubuntu installer could be a little friendlier in the Something Else screen, but there's really only two things you need to know to use it.

Choose a partition to install to. You can resize Windows easily on this screen to create empty space, I'm sure you got that far.

Now create a new partition or select an existing one to install to and click Properties. Select ext4 as the filesystem and / as the mount point.

And you're done.

Oh, you could set up swap and a separate /home and jazz like that, but for what you want it is probably not necessary.

Normally the installer will just give you an option for "Install side-by-side with Windows" so you don't need the Something Else option. I'm curious as to why this didn't appear for you. It is a lot easier but there are some situations where the existing partitioning is done illogically, usually by the computer manufacturer, that prevents this from working.

This forum is here primarily for help, not for ranting. Next time, please draw on our experience instead! We are always happy to help because that is what we are here for.

---

### Post by rg4w on 2013-02-13
> **kg4jxt said:**
> Is it THAT HARD to develop an installer that does not require familiarity with system architecture to operate? :confused:
If you've ever tried to install Windows on a Mac or OS X on a PC, you'll find the answer is "Yes".

Ubuntu has a much more challenging task than either of the other two popular desktop OSes because it has to run on machines designed for an entirely different OS.

If you buy computers with Ubuntu pre-installed, such as those from System 76, ZaReason, LinuCity, or others, you'll find an experience on par with other pre-installed systems.

That said, when installing on a computer designed for a different OS, Ubuntu does a remarkable job of handling the millions of possible combinations of hardware out there, running on most of them quite well under the default settings.

From time to time you may find your system has a component that may need tweaking, and the good folks in this forum can help you solve just about anything you may encounter.

---

### Post by tgalati4 on 2013-02-13
It's the difference between driving a car and pulling out the engine, putting in a new engine, and then driving the car.

How come replacing the engine is not easier?

---

### Post by leclerc65 on 2013-02-16
> **kg4jxt said:**
> 

Is it THAT HARD to develop an installer that does not require familiarity with system architecture to operate? :confused:

For a non Windows, non Linux user (like me) it's like a car driver trying to fly an airplane (Windows) and navigate a boat (Ubuntu).
For you Windows is easy because you are already familiar with it or it comes pre-installed.
Believe me, there are others which are much harder to install than Ubuntu. I never made an attempt at Arch.:p

---

### Post by PIE09gbLmgG6 on 2013-02-16
I found the process rather easy...install uninstall...

This is the best forum I've ever used...hands down...

ego-

---

