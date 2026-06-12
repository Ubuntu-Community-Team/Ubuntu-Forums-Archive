---
title: "[SOLVED] Gparted Live CD hitting a snag in vmware server..."
date: 2008-02-02
forum: Virtualisation
---

### Post by diablo75 on 2008-02-02
I downloaded the gparted iso and created a new VM called sandbox, then removed the default CD-Rom device and told it to mount the gparted livecd iso file instead.  While booting it within vmware server, and I get this stuff that just stays there and essentially brings the boot process to a halt (almost).  The only thing that seems to be changing is the sd number.  E.g, sd 0:0:0:1, sd 0:0:0:2, etc.

See screenshot attached.

---

### Post by fjgaude on 2008-02-02
Did you install VMware on the right drive, a SCSI for real?

---

### Post by diablo75 on 2008-02-02
The screenshot your looking at is from the actual Virtual Machine only, and VMware works perfectly fine; I have windows running in one machine right now.

I created a new machine and called it sandbox.  I then altered the hardware configuration of it so that instead of mounting the actual CD-ROM drive, it mounts the gparted live CD iso as a CD-ROM, and boots from there.  Things start off ok, but a minute into the startup, that screenshot I posted above is all you ever see.

---

### Post by fjgaude on 2008-02-02
From here, I don't have a clue as what could be wrong.

---

### Post by diablo75 on 2008-02-02
I burnt the ISO off, and I still get the exact same problem.  A couple things that stand out:

It looks like it's trying to access scsi devices that don't exist, and just loops over and over trying to mount them, that's what it looks like anyway.

There's also this thing that says "Clocksource tsc unstable"  (See new screenshot).

---

### Post by Shazaam on 2008-02-02
I have VMware Player and it does the same thing (doesn't recognise an iso). The only workaround that I have found is to burn the .iso as a "cd image" to a blank cd/r. I also set up my virtual drives as IDE.

Try this to make a blank vm......

[http://www.easyvmx.com/](http://www.easyvmx.com/)

---

### Post by diablo75 on 2008-02-02
I did that already.  Burned a fresh disc, and attempted to boot off of it instead of the iso.  Exact same stuff is happening...

---

### Post by Shazaam on 2008-02-02
Did you burn it as an "cd image" or a direct copy of the iso?

---

### Post by diablo75 on 2008-02-02
A CD image.  If I had just burnt a data CD, it wouldn't have gotten as far as it did (see screenshots).

---

### Post by PhrankDaChickenGeek on 2008-02-02
I've had the same problem - took me forever to figure it out.

Go to the folder location where you have your VMWare machines stored.
Open the folder with your vmware machine
Find the *.vmx file and open it
Find the line labeled "scsi0.present = "TRUE" and change it to
```
scsi0.present = "FALSE"
```
Save, Exit your editor
Restart VMware server, and try again

Let me know it that fixes it.

---

### Post by diablo75 on 2008-02-03
That did the trick!  Thank you very much!

---

