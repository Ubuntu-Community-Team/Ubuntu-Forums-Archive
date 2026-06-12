---
title: "Temporary Files"
date: 2010-04-15
forum: Security
---

### Post by TomAbada on 2010-04-15
hi all
im using Ubuntu on live USB
and i want to know if im writing on openoffice or recording on sound recorder
(without saving) and unplug the USB from my computer

can any remains of ANY information are being recorded on tmp files ???

thanks in advance

---

### Post by LeeDaugherty on 2010-04-15
Question:  Are you running Live, or have you set the USB up to save your changes (persistance?)...and if you aren't concerned with tmp files on the USB, the answer is probably not.  Here's why.  During normal Live CD/USB boots, the hard drive of the system is not mounted, therefore it (by normal means) cannot be written to.  If the drive has been mounted during the Live CD session, it is still very unlikley as Live session are store mostly in RAM (except in the persistance case mentioned earlier).  Now, if you wanted to go one-step futher, this IMO was facinating when it was discovered, but is overly paranoid.  Cold-boot attacks were proven a reality last year publically.  There is a utility (can't remember the name off the top of my head), that if I came to the PC right after you and booted, I could RAM dump and actually be able to retrieve a good amount of whatever you had in memory.  Yea, I found it shocking too, the old, turn the computer off and RAM goes away was proven wrong.  Now, let's look at some facts.  I think I have less than a minute to get to the PC, and when I boot, I'm going to write over a fair portion of memory destroying information.  And when I dump it, it's going to be Linux files, librarys, random stuff, and unless I know what I'm looking for, it won't be easy.  But it's afun story, so I thought I'd point it out.

---

