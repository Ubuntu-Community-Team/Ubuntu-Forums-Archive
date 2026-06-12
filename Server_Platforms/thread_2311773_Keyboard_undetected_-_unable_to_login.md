---
title: "Keyboard undetected - unable to login"
date: 2016-01-29
forum: Server Platforms
---

### Post by frepie on 2016-01-29
Hi
I have an old optiplex 760 that I want to use as a server, for the fun of it...
It is a dual boot machine (win7-ubuntu server 14.04)

One of the problems I have is that I can't log in. The keyboard seems to be undetected. The keyboard works in the bios and in Grub, but nothing happens on the login prompt.

---

### Post by MAFoElffen on 2016-01-30
Thiis is a fresh install right? And the keyboard was fine during the install? After about 25 years of doing this, I know a little about some of the idiosyncrasies of OS'es (DOS, OS2, Windopws, Unix, Linux) and hardware.

So the Opteron 760 came in 4 different case configurations. From the spec's I can see that it had PS-2 keyboard and PS-2 mouse ports... but they look like they were not default connections on the motherboard. Rather they were from a port plate taking up one of the PCI card slot plates (default installed in the last card slot.) wires plugged into the mother board. But it also has 8 USB 2.0 ports...

When it boots in BIOS message verbose mode or when you are in the system setup (BIOS), what is the version of the BIOS? The current version is A16, that was release on 03 Sep 2013, last updated 21 Mar 2014, with a status of recommended. If you go to the Dell support site and enter in your Support Tag # > go to driver downlloads > under BIOS, that it should point you to the right file to apply.

So what kind of Keybaord are you using? (USB or PS2?) And since it is a dual boot, I assume that it is working okay with Windows...

The first thing to try after that, is when it gets to the Grub menu, when you arrow to the Ubuntu menu selection, press <E> > <Arrow Down > to the Line that starts with "linux" and go to the end of that line.

Delete the text "quiet splash" and replace with "--verbose debug drm.debug=0xe plymouth:debug text" > Press <Cntrl><X> and it will boot with verbose messaging. It may be faster than you can read, but try to pay attention to the message for displayed errors. It will boot into a text-only console. (Instead of the vga graphical virtual tty display mode.)

See if you have keyboard or nor...

---

### Post by frepie on 2016-01-31
Thank you for your answer. My problem corrected itself when doing a re-install: I hadn't made the proper option installation selections. Now it is working fine.

---

