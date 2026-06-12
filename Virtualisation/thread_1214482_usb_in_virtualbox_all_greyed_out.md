---
title: "usb in virtualbox? all greyed out"
date: 2009-07-16
forum: Virtualisation
---

### Post by Arminius on 2009-07-16
I'm using virtual box version 3.0.2 r49928 under mythbuntu version 9.04
and all the usb options are greyed out, I go to the main settings in sun virtual box and use the green "add filter from device" load it up and not only is everything still greyed out, but the usb devices I added are still non functional.

so I went to /system/users and groups
and added my username as well as the root to the vboxusers group
enabled every privalige for my username I could think of.
still usb is just greyed out.

---

### Post by Arminius on 2009-07-16
bump

---

### Post by andrea000 on 2009-07-16
are you using the ose version if you installed it from
synaptic it does not have usb and will be grayed out you
also have to install guest additions to have usb

---

### Post by Arminius on 2009-07-16
nope not ose, I went to the website and installed the real version, also installed guest additions still greyed out

---

### Post by Arminius on 2009-07-17
bump

---

### Post by tacantara on 2009-07-17
I had problems with VB 3.0.2 the other day when I installed it (it wouldn't even open properly, so I couldn't access the VMs I had set up).  I reinstalled 3.0 and it is working the way it's supposed to.  Have you tried reverting to 3.0?  Unless they've worked out the bugs in the updated package, I'd be skeptical about using it.
 
If you're sure that the Guest Additions are installed (the VB Guest Additions icon will show up in the system tray if you're running Windows in virtual mode), try running a Google search on the problem....unless, of course, there's somebody else out there who has encountered this before ;)

---

### Post by PureLoneWolf on 2009-07-17
Did you logout/back in after you added your user to vboxusers?

I was tearing my hair out until I restarted for something else :)

---

### Post by Arminius on 2009-07-17
rebooting seems to have solved it, thanks PureLoneWolf

---

