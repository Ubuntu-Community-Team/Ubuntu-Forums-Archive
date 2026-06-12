---
title: "Ubuntu Server - Garbled Terminal Fonts"
date: 2012-04-29
forum: Server Platforms
---

### Post by jbrice on 2012-04-29
This is Ubuntu Server V12.04 32- bit (updated to latest) installed on one system, then moved to new hardware.

On normal startup, terminal output text appears on attached VDU screen in the pattern expected, but font is garbled to the extent that it's unreadable. Everything else seems to working OK.

Problem still remains if booted normally after adding "nomodeset" to the appropriate line in etc/default/grub and running update-grub. 

However - after above edit - text output is OK if Edit mode entered in Grub menu (by pressing "E") and then F10 used to resume boot -  even if no actual editing is done to the Grub code.

I have run out of ideas from web searches as to where to go from here, so suggestions would be appreciated!

---

### Post by CharlesA on 2012-04-29
Did the other machine have different video hardware? I ran into a similar thing when I swapped my drive to a different machine.

---

### Post by jbrice on 2012-04-29
> Did the other machine have different video hardware? I ran into a similar thing when I swapped my drive to a different machine.

Yes, I moved the hard drive to a new box. Solved the problem whereby the network conection moved from eth0 to eth1 because of new hardware, but this font thing has go me stumped.

---

### Post by CharlesA on 2012-04-29
Does the login prompt look ok if you switch TTYs?

Very strange indeed.

---

### Post by jbrice on 2012-04-29
> Does the login prompt look ok if you switch TTYs?

Switch TTYs? - I'm not familiar with that concept.

Have reinstalled Grub - no change. "nomodeset" may be a red herring - terminal fonts are normal if restarting after any "live" edit of the Grub menu, still garbled on restart after update-grub.

---

### Post by CharlesA on 2012-04-29
> **jbrice said:**
> Switch TTYs? - I'm not familiar with that concept.

Have reinstalled Grub - no change. "nomodeset" may be a red herring - terminal fonts are normal if restarting after any "live" edit of the Grub menu, still garbled on restart after update-grub.
Yeah, you'd have to do it from the console but hit:

ctrl + alt + f1 ---> ctrl + alt + f7

---

### Post by jbrice on 2012-04-29
> **CharlesA said:**
> Yeah, you'd have to do it from the console but hit:

ctrl + alt + f1 ---> ctrl + alt + f7

Ah thanks - doing that shows same patterns of text, but with garbled fonts on each TTY channel.

Further experimentation shows:
- hit E during Grub menu and then F10 (nothing edited) and terminal text is OK, however count-down to auto startup missing,
- then do sudo udate-grub and we are back to normal startup, but garbled terminal text on attached VDU.

---

### Post by CharlesA on 2012-04-29
I'm not sure what else to check cuz it only looks garbled when booting normally and works fine if you select an option from grub.

---

### Post by jbrice on 2012-04-29
I think a reinstall on the new hardware might be the appropriate way forward here, just in case something else has been corrupted.

Thanks for your thoughts on this.

---

### Post by CharlesA on 2012-04-29
That's probably a good idea.

I'd pop another drive in if you have one and see if it shows the same symptoms.

---

### Post by jbrice on 2012-04-30
Just done a clean install as suggested, and getting the same symptoms. At start of install there is an error message about "undefined video mode 314", but otherwise install was OK.

Searching the web for that error message leads me to believe that the problem is a smaller video memory than Ubuntu expects - thus getting over-written and hence garbled. 

On this box I cannot increase the video memory settings in the BIOS (a procedure recommended elsewhere to solve this problem), so I edited /etc/default/grub to force a low-memory VDU setting (see [http://pierre.baudu.in/other/grub.vga.modes.html](http://pierre.baudu.in/other/grub.vga.modes.html)) - I used vga=771 as I calculate it should fit into a 1MB video buffer - and then do update-grub. Edited line in /etc/default/grub now looks like:
GRUB_CMDLINE_LINUX_DEFAULT="vga=771"

Fingers crossed it seems to be working OK.

Thanks for your support.

---

### Post by CharlesA on 2012-04-30
Glad you were able to get it figured out.

---

