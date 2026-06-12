---
title: "Can't run Ubuntu 12.04 LiveCD"
date: 2012-04-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by gmilo2 on 2012-04-03
I can't boot the live cd for 12.04 on a Dell Dimension 4600i.  It gets to the "Stopping System Level V compatibility" boot message and hangs there.  I can hit ctrl-c to get to hit enter to eject the CD.  Have tried setting acpi=no, nomodeset.  I've also removed the graphics card and let it try with the onboard video, but the end result is always the same: no go.   There is a boot message early on that says: pwconv: failed to change the mode of /etc/passwd to -0600.    I am running 11.10 fine from the hard disk and have been for some time (though I recently reinstalled).  I also cannot install 12.04 but am mainly interested in booting the CD for now.  I checked the download against the sha256sum.  Could the CD burn be bad even though it seems okay?  (Checked disk for defects and it is fine)  Does anyone have any ideas as to what might be going on?

[FONT=arial, helvetica]uname -a
Linux pcone 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux

lshw.txt attached.


[/FONT]

---

### Post by mörgæs on 2012-04-04
Hi, welcome to the fora.

Best is to begin with some simple tests: Do other computers boot from the CD? 
If this one supports booting from USB, have you tried it?

By the way, thanks for posting the lshw file. If only more people would do so...

---

### Post by gmilo2 on 2012-04-04
Yes, I have an HP Compaq nx9420 laptop and it did boot from the CD.  The USB route didn't work on the Dell (supports booting from USB though).  I didn't try booting the laptop from USB but it probably works there.

---

### Post by mörgæs on 2012-04-04
You need to carry on testing. If your computer supports USB, this is preferred to CD. Also try the alternate ISO and Unetbootin. 

There is more advice in the post in my signature.

---

### Post by gmilo2 on 2012-04-04
If anyone has run into this before please let me know.  I have yet to have the live USB boot either.

---

### Post by sffvba[e0rt on 2012-04-04
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*


404

---

### Post by gmilo2 on 2012-04-12
Installing from the alternate CD worked.  I really only wanted to run it from the CD to check it out, but I'll take it.  Tried and tried and tried all kinds of tweaks that were suggested (with the regular CD) and it made no difference.  Hopefully the regular CD will work when the official release comes out.

---

### Post by mabovo on 2012-04-14
> **gmilo2 said:**
> Installing from the alternate CD worked.  I really only wanted to run it from the CD to check it out, but I'll take it.  Tried and tried and tried all kinds of tweaks that were suggested (with the regular CD) and it made no difference.  Hopefully the regular CD will work when the official release comes out.

Same here, "ad nauseam" !

---

### Post by pme 72 on 2012-04-15
Beta1 would not boot past the Try Ubuntu menu for me on my Compaq Presario AMD64 3500+. I am offsite with no access to my notes but if I remember correctly holding down the SHIFT key during start up sent me to a more familiar options screen. From there after choosing the CHECK DISK option the PC booted into the LiveCD environment. Sounds like a different issue than yours though.

---

