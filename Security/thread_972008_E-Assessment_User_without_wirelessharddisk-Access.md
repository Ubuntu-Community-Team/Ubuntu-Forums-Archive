---
title: "E-Assessment: User without wireless/harddisk-Access"
date: 2008-11-05
forum: Security
---

### Post by chaelli on 2008-11-05
Hi,

I'm not really sure where to put this.. so tell me if I'm wrong!

I'd like to create a USB-Stick from which every student can boot his computer and then work on an exam. I've already got the stick, users, openoffice and all working.. but now the question is how I can restrict the students user-account so that the have no networkaccess at all and so that they cannot access any internal storage (or other usb-stick if possible).

This is all to make sure, that the have no access to any data whatsoever! I also want to mention that there are also IT students.. so they will probably try to re-establish a network connection.

I'd be glad to get any ideas on how to to this!


thanks in advance!

regards
Michael

PS: I used the usb-startup-disk creating tool of Ubuntu 8.10

---

### Post by milosz.galazka on 2008-11-05
What do you think about recompiling kernel?
Without support for modules, anything related to networking.

Access to internal storage will be probably more complicated but I think that it can also be accomplished that way.

---

### Post by cariboo on 2008-11-05
Create an unprivileged user, and then set the user to auto login, so there is no chance of them logging in as another user, then create the distribution on a usb key. Once you have one created and working properly, create an iso of the distribution on the usb device, then clone the orirgional to other usb devices.

Jim

---

### Post by chaelli on 2008-11-06
Hi again

thanks for the inputs!

Recompiling the kernel would be a way to go.. but only for networking.. I cannot deactivate hard-drive access there because then I would not be able to copy the saved files after the test (except maybe I could read the casper-rw from within windows? but is it possible to deactivate hard-drive access and still have access to the stick itself and to the casper-rw filesystem on the stick?

@Jim: That's what I did so far.. but this will still mount the harddrives and try to establish any kind of network connection.

greets
Michael

---

