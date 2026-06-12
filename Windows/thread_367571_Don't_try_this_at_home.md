---
title: "Don't try this at home"
date: 2007-02-22
forum: Windows
---

### Post by Yossarian on 2007-02-22
I would like to relate an amusing misadventure I had with Windows XP Pro.

I have two hard disks in my computer, both 40 gigs, both with 1 huge ntfs partition each.  I set it up so one was mounted to C:\, and one was mapped to C:\Documents and Settings\Patrick\Desktop.  This works well as I always download files to my desktop, so both disks are at about equal usage.

I was showing a buddy how I did it (you do it through the management console or something in the Control Panel) and saw that you can assign a parition multiple mount points.  

I wanted to know if Windows would let you map something that didn't make sense, so I made a folder on my desktop called Stupid, and mapped the parition that was already mapped to the Desktop to that folder.  So I have now a folder that contains itself.

Windows happily let me do this.  Not wanting to tempt fate I quickly undid it and closed the control panel.  However, the mapping stayed (although it said it didn't) so when I tried to delete the Stupid folder (holding shift to not move it to the recylce bin) it tried to delete everything.  Luckily something was read only, or in use, or something, so it failed right away with an error message and didn't get lost in madness.

Anyone tried anything similar?  If someone has a windows installation they don't care about, it would be cool to try mapping a folder to itself, or mapping two folders to each other.

I've never tried doing this with linux or BSD, are these systems smart enough to not let you do this?

---

### Post by erlyrisa on 2007-02-22
That's interesting - you learn something new everyday. (it's not the same as a network type mount is it?)
I am temping changing mysetup - I currently have a 'booting hardrive' which contains multiple OSes, but things like the Program Files directory have been moved to me d: -(WHICH REMINDS ME win98 won't be able to do what your talking about - damn it.)
-This mounting thing could be really cool for external USB drives - wonder if it works for that.

---

### Post by FuturePilot on 2007-02-22
That's interesting. Once I wiped out the System32 directory......:lolflag:

---

### Post by diepruis on 2007-02-22
> **FuturePilot said:**
> That's interesting. Once I wiped out the System32 directory......:lolflag:

At least you've never deleted vmlinuz (i.e. the kernel) because you thought it was a temp file.

---

### Post by 3rdalbum on 2007-02-23
You can actually do something similar with Linux.

Make a symbolic link to your desktop (middle-drag the "Desktop" icon from your home directory to the desktop). Just for fun, rename it to "Desktop". Now, double-click on the symbolic link. A file manager window opens, showing you all the things on the desktop. Double-click the symbolic link in the file manager. The same thing appears. If you check the location that is being displayed, it is: ~/Desktop/Desktop/Desktop.

---

### Post by Yossarian on 2007-02-23
Just to add this in case it comes up, what I did was fixable.   Here's what I did:

1) Opened the control panel program to manage the disks.  Removed the mount points to C:\ etc, so that the second drive is now only mapped to F:\ or whatever

2) Moved all the files, minus the evil folder, from the partition to a network share (only because I didn't have enough local disk space)

3) Deleted the evil folder by holding shift+delete to bypass recycle bin

4) Moved files back.

Not elegant, but did the trick.  Also I would like to point out that all the files I put at risk were stuff I didn't really care about, and I had backups of my important stuff if my pc had exploded, etc.

---

