---
title: "Change Local Console to 50 lines"
date: 2009-12-13
forum: Server Platforms
---

### Post by Vegan on 2009-12-13
I was wondering, long ago on DOS you could use the VGA in 80x50 mode with a BIOS call.

I was wondering if its possible to have the local console permanently set to 80x50 so I can see more of the screen/output at once.

---

### Post by BkkBonanza on 2009-12-13
Not sure if there's an easier way but the way I do this is to modify either the menu or toolbar icon to run a command like,

gnome-terminal --geometry 128x40+140+60

The geometry option tells what size to open the window as, and start position.

---

### Post by craigp84 on 2009-12-13
If you're talking about the actual console rather than a terminal program under X, uncomment the "vga=791" in your /boot/grub/menu.lst

-c

---

### Post by Vegan on 2009-12-13
no such file menu.lst in my /boot/grub directory

should i create one?

I am using 9.10 for what is worth

---

### Post by craigp84 on 2009-12-13
I've never updated to any of the 9.x releases so i dont know if there's maybe been some changes to the way grub is setup.

I've just checked (albeit on an old 6.06 box) and it's the "# defoptions = vga=791" line you're after. that comment char at the beginning of the line has to stay there, then do a "sudo update-grub" and it'll take the instruction on this commented out line and append it to the applicable stanzas below.

Now all you need to do is translate these instructions into a more modern ubuntu release :) sorry i cant help further, i just dont have a box with a newer version available to me right now.

You're not using lilo instead of grub are you? Just a thought that came to mind there.

---

### Post by Vegan on 2009-12-13
grub is still there, stashed away in /dev/sda5 formatted with ext2

There are a ton of files in /boot/grub to chose from with 9.10

As for version 6, you are way behind the curve.

lilo comes to mind from eons ago with FreeBSD 3 on my old Compaq Deskpro 386 that cost me an arm and a leg.

BTW I tried using Google ad nauseum and found nothing useful as usual.

resizecons -lines 50 > no good, characters are cut off

---

### Post by lswb on 2009-12-13
While running from the console try cd /usr/share/consolefont

Use the setfont command to try some of the font files you find there, for instance
setfont Uni1Fixed16 (not necessary to use the psf.gz extension with the setfont command) should give a 128x48 console.

---

### Post by BkkBonanza on 2009-12-14
You may find this page useful,
[http://linuxandfriends.com/2008/09/17/vga-modes-used-linux/](http://linuxandfriends.com/2008/09/17/vga-modes-used-linux/)

You can add the vga= boot parameter during boot by pressing esc during grub first stage and then editing the boot command and adding a vga mode. This allows you to test if it will even work before editing grub at all. Not all video modes work as I recall having to do this for my server long ago and some modes just won't take. It required finding a mode my system supported. Also as mentioned above article you may want to check that the framebuffer driver is present as I don't know if that is for Ubuntu.

---

### Post by andrew.46 on 2009-12-14
Hi Vegan,

> **Vegan said:**
> lilo comes to mind from eons ago with FreeBSD 3 on my old Compaq Deskpro 386 that cost me an arm and a leg.

lilo is still the default bootloader for Slackware...

Andrew

---

### Post by Vegan on 2009-12-14
I remember an old e-book call Ralph Brown's Interrupt List that seems to have disappeared. I remember is because there was a call that you could use in an Assembler call to change the EGA/VGA to 80x43 or 80x50.

The old list was very comprehensive.

---

### Post by mdm230 on 2009-12-15
vga switch is deprecated in grub2 which is the default with 9.10 server. Still looking for a work around myself to get better than 640x480 on the console(before rebuttal, there is no x server installed), so I feel your pain. What is worse is there is little or no documentation or the posts are so poorly worded that I can't get any worthwile google results either.

If/when I find a workable method, I'll try to post it.

m

---

### Post by Vegan on 2009-12-15
Par for the course, lets try and keep this alive as world+dog could take advantage of it.

---

### Post by lswb on 2009-12-15
Have you tried the setfont command described in post #7? I am able to set my console to various fonts yielding 25 to 96 lines and 80 to 170 characters per line. This is on a laptop with native 1024x768 resolution, ymmv.

---

### Post by Vegan on 2009-12-15
I gave up on it and installed the desktop so I can more easily edit the various config files as the work I was doing was hard as hell to figure out manly due to limited help available.

I was working on using user accounts with a default /home/*/user where a default www folder can hold the client web site on an intranet. I wanted to learn how to do this so I could better use Linux properly.

The changes I wanted were tricky as the examples on various sites were incorrect so I had to fix them.

Now the next headache, a new backup strategy.

If I find the old interrupt list, I could make a simple C program to enable it as its OS independent.

---

