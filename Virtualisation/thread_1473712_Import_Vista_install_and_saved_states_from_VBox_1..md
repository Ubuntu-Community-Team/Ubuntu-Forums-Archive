---
title: "Import Vista install and saved states from VBox 1.5.6 (hardy) into Lucid"
date: 2010-05-05
forum: Virtualisation
---

### Post by arsenic23 on 2010-05-05
OK, I'm getting the feeling that the solution to my problem is simple and I'm just being dense, but I need to get my Vista install from my old Hardy setup working in Lucid.  I still have both installs running so I can boot back and forth into either to make changes.

I originally thought I could just copy the drive image over, but without the saved states it is just as it was right after installation of the OS.  So then I deleted my .Virtualbox folder and copied the old on into my Lucid install.  Nope, Virtualbox won't even startup when I do that. (I'd give the error but I'm booted into Hardy right now.)  Then I made a setup exactly like the original, using a copy of the HD image, and copied the save states over.  They never showed up in the manager, even after a reboot.

I can't reinstall the OS, it's not an option.  What is the best way to get this working?  I thought there might be a way to flatten the save states, applying them to the virtual disk image, but I just don't see it.  

( Also I'm using the Lucid repo VB on the Lucid install, in case that is relevant. )

---

### Post by arsenic23 on 2010-05-05
Oh for crying out loud!  Why is the merge snapshot option labeled 'Discard Snapshot'?  That's stupid.

Well I think I messed my disk image up messing around before I realized this.  Oh well, live and learn.

---

