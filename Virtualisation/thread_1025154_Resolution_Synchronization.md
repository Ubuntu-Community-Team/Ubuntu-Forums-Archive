---
title: "Resolution Synchronization"
date: 2008-12-29
forum: Virtualisation
---

### Post by icyest on 2008-12-29
I have a 1440x900 display on my host Laptop, and I'd like my Virtual Box's monitor (running Windows XP Professional) to synchronize with that exact same resolution. It only goes up to 1280x1024. I'm basically trying to turn one whole face of the cube in to windows XP. What can I do to make my Windows XP have 1440x900 resolution?

---

### Post by bodhi.zazen on 2008-12-29
Install the Guest Additions (on the windows guest) and run virtualbox in full screen mode.

---

### Post by icyest on 2008-12-30
how would I go about doing that? I don't get it. It says download an iso from the internet?

---

### Post by darkness5723 on 2008-12-30
What you want to do is locate the VBoxGuestAdditions.iso file. I believe it's located in /usr/share/VirtualBox (I don't have vbox installed atm to check). Then you want to mount it to the virtual drive inside your VM. Do this by going to CD/DVD on the settings page of the VM you want to install to. Mount it to the virtual drive, then boot up your VM. Go inside the .iso in your VM (it will appear as the physical drive in Windows), then run the windows .exe appropriate for your windows installation.

Sorry if this is a bit unclear, as I said I don't have VBox installed atm to give you EXACT instructions, but these should explain how to do it.

---

### Post by solwic on 2008-12-30
> **icyest said:**
> how would I go about doing that? I don't get it. It says download an iso from the internet?

No.  When running your VM, it's at the bottom of the second menu (the menu across the top of the VM window..."Devices", I believe...I don't have anything installed in VBox to show me)...it says "Install Guest Additions" or something similar.  Click that, and it should automount the cd in your Windows install.  It may even autorun.  

Good luck!

---

### Post by underdog512 on 2008-12-30
I believe you have to be running the non opensource edition.

---

### Post by icyest on 2009-01-01
I'd like my virtual machine to be able to read my host computer's cd's. Wouldn't having it read the guest addition .iso inhibit this capability?

---

### Post by bodhi.zazen on 2009-01-01
> **icyest said:**
> I'd like my virtual machine to be able to read my host computer's cd's. Wouldn't having it read the guest addition .iso inhibit this capability?

Yes it will, but you only need to mount the iso to install the additions, you can then o back to using your CD.

---

### Post by doughorne on 2009-01-03
I just love it when I search for a resolution and find it.  Love the support and info on this thread.  I am now rockin' XP at full 1920x1200 resolution in VB. :D

---

### Post by icyest on 2009-01-04
> **doughorne said:**
> I just love it when I search for a resolution and find it.  Love the support and info on this thread.  I am now rockin' XP at full 1920x1200 resolution in VB. :D

It helps to know that this thread is assisting other people than myself. I'm compiling a list of most probable technical encounters/difficulties that an ex-windows into linux user might encounter. Wouldnt you agree that this is the best linux community?

---

