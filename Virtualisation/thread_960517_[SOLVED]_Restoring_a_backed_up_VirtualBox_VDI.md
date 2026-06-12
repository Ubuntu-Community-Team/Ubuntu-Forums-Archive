---
title: "[SOLVED] Restoring a backed up VirtualBox VDI"
date: 2008-10-27
forum: Virtualisation
---

### Post by M4rotku on 2008-10-27
Hello all,

I decided to use my working XP virtual machine to try my hand at recovering lost data.  First I copied the VDI file onto another partition for safe keeping.  Not being sure how this works :confused:, I booted a system rescue cd in the VM.  Then, in command line, I mounted the partition and did the infamous "rm -rf *". :)  I managed to use photorec to recover the files, but they were not named.  Accepting this as a partial success, I tried to restore my Virtual Machine to the way it was.

I thought that I was very clever in copying the VDI file to another partition, now all I had to do was replace the current VDI with the one that I backed up and all would return to normal.  However, after I switched out the VDI's, I still received the same error message when trying to boot from the hard drive.

> NTLDR is missing
Press Ctrl+Alt+Del to restart

How would I go about fixing this.  I tried to reassociate the VM with the VDI, but I don't know if that worked.  I don't know if I failed to reassociate properly, or if i simply need to repair something to allow it to boot.  Can anyone help me fix this?  I really need this VM to work.

Much thanks,
M4rotku

---

### Post by M4rotku on 2008-10-30
bump

---

### Post by Mistrblank on 2008-10-31
I want to say it's just a bad boot image and you need to restore the MBR on the VDI file.  

Search for Ultimate Boot CD or UBCD.  Download the disk image and mount it to the CD slot in VirtualBox.  There are some MBR utilities on that Disk I've used to restore physical machines that should work here.

---

### Post by M4rotku on 2008-10-31
Can you recommend a specific utility on that disk or is it intuitive enough that I will manage?

---

### Post by FrostyFlames on 2008-11-01
If you still have the XP install CD, you can get into a recovery console when it starts loading the CD.

Here is a fine example:
[http://www.lockergnome.com/blade/2006/12/12/ntldr-is-missing-how-to-repair/](http://www.lockergnome.com/blade/2006/12/12/ntldr-is-missing-how-to-repair/)

---

### Post by M4rotku on 2008-11-02
It's not a matter of restoring the MBR.  I booted with the windows xp install cd and maneuvered to the C:\ directory and when I listed the files, there was only one file in existance:  bootex.log

Can anyone else help me reassociate the backed-up VDI with the machine?

---

### Post by M4rotku on 2008-11-05
bump

---

### Post by M4rotku on 2008-11-08
bump

---

### Post by Ameneon on 2008-11-09
Hm, that's really not good (and I'm not saying that to scare you, I'm a novice at Vbox myself - only recently managed to get a fully working sharing of folders between the host and the guest....), one would think that the .vdi file would be for all intents and purposes a "virtual disk image" and thus would represent the whole drive. If that's not the case it suddenly makes using vbox for any kind of testing a gamble if you also use vbox for anything production-related. Not to mention that if vdi's are not self-contained then what other files on the host system are involved and what possible security risk might there be in a worst-case scenario?

Tried looking in the .VirtualBox directory but while each machine has settings in the "Machines" subdirectory (thus not contained in the VDI), these appears to be related to how Virtualbox interfaces with the machine, not the functionality or content of the machine itself, which from as much as I can see is all in the .VDI file.

Question: Have you tried rather than replacing the current installation in Vbox trying to remove the installation altogether and then create a new installation from scratch and then point it to your old .vdi file?

Ie rather than replacing the installation in virtualbox itself, remove the installation and create a new one pointing to your (hopefully) known good backup vdi file now safely copied back to where it should be.

---

### Post by M4rotku on 2008-11-10
That sounds like a good idea.  I'll try it and then get back to you.

---

### Post by M4rotku on 2008-11-10
Nevermind, it was a matter of a stray snapshot, I didn't need to back up the drive, the snapshot had the backed up image.  Thus, when I tried to back up with copy/paste, I was still using the same snapshot and that's why it didn't work.

---

