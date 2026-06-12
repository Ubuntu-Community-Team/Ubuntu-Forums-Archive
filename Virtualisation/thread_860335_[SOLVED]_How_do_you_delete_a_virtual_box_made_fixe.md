---
title: "[SOLVED] How do you delete a virtual box made fixed hard drive image?"
date: 2008-07-15
forum: Virtualisation
---

### Post by paulley_trolley on 2008-07-15
Hi, I installed virtual box on my computer, but then, after the fixed hard drive image (10 gig) was made, i decided not to and deleted the virtual machine, and uninstalled virtual box.  I can't find the hard drive image in the file browser,and it takes up a lot of space.  It's in the default place, i just don't know where it is saved so i can delete it.  Does anyone know what to do?

---

### Post by cosine352 on 2008-07-15
should be in the .VirtualBox/VDI

code
> gnome-open \.VirtualBox/VDI

---

### Post by paulley_trolley on 2008-07-15
It was there, but after i deleted it, i opened a new file browser and clicked properties to check how much free space was left, and it says the same thing, making it appear that it's still there.

---

### Post by jimmy the saint on 2008-07-15
If you are more comfortable in a graphical file browser hit <ctr>+H in your file browser and your hidden files will be shown.  At this point find your .virtualbox folder and look inside.  You will find a VDI folder which contains your virtual drives.

---

### Post by paulley_trolley on 2008-07-15
I found the .virtualbox folder, but it was empty, and i deleted it, and it still says the same amount of free space left.

---

### Post by voteforpedro36 on 2008-07-15
Did you empty the trash after you deleted it? That might clear the space.

---

### Post by paulley_trolley on 2008-07-15
> **voteforpedro36 said:**
> Did you empty the trash after you deleted it? That might clear the space.

Oh, duh, that did it, thanks everyone.

---

### Post by bodhi.zazen on 2008-07-15
You can do all this from the virtualbox gui.

First detach the hard drive from your virtual machine, then delete it.

---

