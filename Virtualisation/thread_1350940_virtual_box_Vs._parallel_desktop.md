---
title: "virtual box Vs. parallel desktop?"
date: 2009-12-09
forum: Virtualisation
---

### Post by blueskyatfero on 2009-12-09
So some the reports I have been read about how well windows 7 works with suns virtual box have been varied so I thought Id put it to this community?? sun virtual box for free, or parallel desktop $69.95(aproxmately). I need windows for school and work. Not really wanting to partition because my hd is a little finicky when it comes to that sort of thing. Virtualization or a external HD is the way I'm headed so on the virtualiztion route what are the draw backs of virtual box???? what do I get if i pay for parallel desktops that i wouldn't get in Virtual Box? why would it be better, or not better, to run a system virtually as aposed to just getting a external for running windows. 

Thanks for you time and opinions

---

### Post by Druke on 2009-12-10
VirtualBox works fine for me.


I can't see any real advantages to going with a pay vm suite.

out of curiosity, what applications do you need to run on windows for school?

---

### Post by BT1 on 2009-12-10
Always try the free option first I always say.
 
If you have a copy of windows 7 then just go with virtual box. I've been running 7 in VB without issues. I too need windows for school because my instructor insists upon it when he walks to our tables and sees our notes. I've argued with him a lot but since he's a friend of the family, he used his professor discount at the university bookstore to buy me a copy of windows 7 pro for 8 bucks. All it took was complaining to his wife :P
 
When I asked why he insisted on windows, he said cause he's too old to deal with "voodoo booty magic". Booty (as in butt) of course in reference to "Ubuntu" :|
 
Good luck!

---

### Post by blueskyatfero on 2009-12-10
mostly I need to run excell, and word, and there have been some compatality issues with open office org., but also I am a math and engineeing major and there programs, such as mat lab I need to run, mainly because I'm taking  a mat lab class. I Just bummed a copy of Vista premium, used my old key, and installed it in virtual box, but the sound isn't working.  a friend of mine who is a CIS major just told me you can't install vista on an external any way, at least not legally?? Any help on how to get the sound working would be nice.

---

### Post by Druke on 2009-12-10
did you install the guest addons? (host +d [by default that means right ctrl + d])

---

### Post by BT1 on 2009-12-10
> **blueskyatfero said:**
> mostly I need to run excell, and word, and there have been some compatality issues with open office org., but also I am a math and engineeing major and there programs, such as mat lab I need to run, mainly because I'm taking  a mat lab class. I Just bummed a copy of Vista premium, used my old key, and installed it in virtual box, but the sound isn't working.  a friend of mine who is a CIS major just told me you can't install vista on an external any way, at least not legally?? Any help on how to get the sound working would be nice.

Just a theory... couldn't you install the OS to an internal hard drive, then take that hard drive and put it into an external case... and then run a Grub update when in Ubuntu that could recognize the OS right? Then you could boot into the OS when you start up your computer.......right? I know that when I have thumb drives with different flavors of linux installed, when I do a grub boot loader update it recognizes the OSes on those thumb drives.

Just a thought...from a linux Nub :D

Does anyone know if this would work, like install the Windows OS onto a drive, then copy the whole partition to a large thumb drive?

*runs off to test it*

---

### Post by Druke on 2009-12-10
I'm sure it would work, actually I would imagine you could install windows onto a drive like that as long as you could convince the installer that it is a hardrive to begin with (aka have it be an install option).

otherwise perhaps skillful use of "dd if=/dev/drive/partion/of/windows of=where/you/want/the/image/" then writing the image and bootloader to a drive.

though this seems to simple to not have been done already... so I'm guessing that this process breaks down at some point.

---

### Post by blueskyatfero on 2009-12-10
> **Druke said:**
> did you install the guest addons? (host +d [by default that means right ctrl + d])
that did the trick thanks!

---

