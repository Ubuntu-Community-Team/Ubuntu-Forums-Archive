---
title: "DG possible sudo breech"
date: 2009-10-16
forum: Ubuntu Christian Edition
---

### Post by shane2peru on 2009-10-16
Ok, I was on one of my kids account on the computer and just for kicks I opened the Dan's Guardian GUI.  After that it asked me for the childs password, and I gave it and it said she wasn't in the sudoer's file, however Dan's Guardian continued to open the GUI window.  I tried to edit the white list to see if it would allow me, and it didn't.  I didn't try other things since I was using her time and they have timekpr running too.  I just thought that was odd that it would even open the GUI when a non-admin user accessed it.  I thought I should let you know, and that should be fixed.  

Shane

---

### Post by Viva on 2009-10-16
I haven't used it, but maybe, it is like synaptic which can be opened without root privileges, but can be viewed.

---

### Post by david_kt on 2009-10-16
> **Viva said:**
> I haven't used it, but maybe, it is like synaptic which can be opened without root privileges, but can be viewed.

Yes you are right. Dansguardian gui menu could be viewed by non sudoer, but it would not able to edit anything. I will think of a way to prevent it to be viewed altogether.

DK

---

### Post by shane2peru on 2009-10-17
> **david_kt said:**
> Yes you are right. Dansguardian gui menu could be viewed by non sudoer, but it would not able to edit anything. I will think of a way to prevent it to be viewed altogether.

DK

Well, perhaps if it is only viewed and not able to edit anything, then I guess no harm is done.  I have never not been system administrator, so I don't know what opens and what doesn't.  It just kind of really took me for surprise when it opened up.  So long nothing can be changed, I guess it doesn't matter.  I think a simple sudo check would keep it from opening up.  Course I say that, I'm not sure how difficult that may be.  If it is major work, don't  worry about it.  I was just surprised.

Shane

---

