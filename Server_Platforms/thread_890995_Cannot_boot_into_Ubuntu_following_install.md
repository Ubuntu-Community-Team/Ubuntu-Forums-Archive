---
title: "Cannot boot into Ubuntu following install"
date: 2008-08-15
forum: Server Platforms
---

### Post by Enigmatic on 2008-08-15
I installed Ubuntu server (amd64) on a box that was previously running Openfiler 64bit. 

It installed fine, but on the reboot with the CD removed, all I get is the word GRUB, and nothing else on the screen, no OS options to choose from. Any ideas? I've never run into anything like this before.

---

### Post by wilbbe01 on 2008-08-15
I think I had this happen once before.  I don't remember what I did, but knowing how bored I probably was, I probably just reinstalled and it worked.  I am not sure though.  You could boot off of a livecd I suppose and look and your grun configuration and see if it looks right.

---

### Post by Enigmatic on 2008-08-15
I tried a reinstall with the same results. Mind you the settings were all the same so maybe that has something to do with it. Install media is fine though, m5dsummed it and checked after burning also.

---

### Post by promodus on 2008-08-15
First off, get rid of the boot splash.

Where you see:

```
GRUB Loading stage 1.5.

GRUB loading, please wait...
Press 'ESC' to enter the menu...3
```

Press Esc

Then on the first entry, press "e" to edit the line
Go down to the second line that starts with kernel, press "e" again.

Remove "quiet splash" then press enter

After that press the letter "b" to boot.
You will now see stderr & stdout kernel messages.

---

### Post by Enigmatic on 2008-08-16
I'm not sure if you're reading my post correctly or if I'm misunderstanding you. I am only seeing the word "grub" instead of the actual menu.

---

### Post by windependence on 2008-08-16
You may have to reinstall grub and make sure it's on the correct device. Also, make sure you are set to boot from the right disk in your bios.

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

-Tim

---

### Post by Enigmatic on 2008-08-16
Yes, it certainly sounds like that could work. For the time being I installed Debian which works perfectly, so I probably won't fool around with it again.

---

### Post by promodus on 2008-08-16
> **Enigmatic said:**
> I'm not sure if you're reading my post correctly or if I'm misunderstanding you. I am only seeing the word "grub" instead of the actual menu.

From the post that you mention Debian works, sounds like that hard drive is fine.

Sorry, I should of asked this first:
Just seeing GRUB did that go away? or did the word GRUB stay there?

---

### Post by Enigmatic on 2008-08-18
I just saw the word "GRUB" followed by a blinking cursor in the upper left corner. Nothing else on screen, and nothing else loaded.

---

### Post by promodus on 2008-08-19
My guess is, on the install something happened when the partition was created? (UUID Changed?)

GRUB could not find the configuration on the hard drive, that's why (I'm assuming) all you got was GRUB, nothing more. GRUB is not intelligent enough to search the drives, it has to know the direction to the initial configuration. Once it has that, it will give you the list of boot options.

[http://www.gnu.org/software/grub/manual/html_node/Stage1-errors.html#Stage1-errors](http://www.gnu.org/software/grub/manual/html_node/Stage1-errors.html#Stage1-errors)

"Read Error
    A disk read error happened while trying to read the stage2 or stage1.5. "

A quick search on google, "GRUB blinking cursor" I find a few hits.

Similar post before:
[http://ubuntuforums.org/showthread.php?t=283311](http://ubuntuforums.org/showthread.php?t=283311)

---

### Post by windependence on 2008-08-19
I had this same exact problem on a SuSE 11 install and the solution was to write grub to the MBR. Turns out the install only wrote it to /boot.

-Tim

---

