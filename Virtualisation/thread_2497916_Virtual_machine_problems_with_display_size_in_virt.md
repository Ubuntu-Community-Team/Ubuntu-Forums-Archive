---
title: "Virtual machine problems with display size in virtual box and another problem with gn"
date: 2024-05-22
forum: Virtualisation
---

### Post by maclellan2 on 2024-05-22
I'm using Ubuntu 24.4 Sometimes I want to test things in Windows. A fresh install of Windows in Gnome Boxes won't let me choose anything under 64GB for Ram. That's twice as much as I have. Oddly enough, my computer with 22.04 installed it great, but there isn't enough disk space for it.

So then I tried installing Windows on my computer using 24.04 with Gnome-boxes. It refuses to install.

I setup virtual box, and it installed well, except there isn't an option to choose the right screen resolution. I need it to be 1920x1080. The only two settings I can choose from that would be anywhere close is 1280x1024 or 1600x1200.

I'm hoping there is a way to fix this by adding other display options.

Thank you,
Steve

---

### Post by TheFu on 2024-05-24
You cannot have 2 hypervisors installed at the same time, unless you manually remove the hypervisor kernel module used.  

Virtualbox requires something called "Guest Additions" to be installed for display management (and a few other things).  Additionally, the license for the guest additions is NOT F/LOSS, so beware.  Every time you run it, Oracle will be notified.  With the guest additions installed, be certain the vbox VM display memory is set to the highest number allowed, usually 128MB.  I haven't used vbox in over a decade, but the default used to be 9MB, which is fine for a non-GUI guest.

BTW, 24.4 isn't the correct term.  24.04 is. The leading zero-four is how Canonical decided to say "April" = ".04"; October = ".10".  It makes computer sorting easier.

---

### Post by MAFoElffen on 2024-05-25
64GB for a Windows VM??? 

I haven't used VBox in years (by choice)... But when I did, it had never forced me to use a minimum amount of RAM for an OS. I could always override what was recommended, even if that was not enough.

Something is wrong with that picture. I can see 64GB of vDisk, because the OS needs at least that much room to install. But it will run happy with most minimal apps with 4GB RAM. I do that all the time with KVM.

---

