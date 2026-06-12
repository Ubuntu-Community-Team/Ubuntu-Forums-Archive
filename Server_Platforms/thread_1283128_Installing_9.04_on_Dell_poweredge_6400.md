---
title: "Installing 9.04 on Dell poweredge 6400"
date: 2009-10-05
forum: Server Platforms
---

### Post by wonderfullyrich on 2009-10-05
I'm having a problem installing 9.04 server on a Dell Poweredge 6400 server with a PERC2 controller.
I've previously been able to install 6.06 on this machine, but when I try 9.04 I'm getting the following repeating error after I finish the installation and reboot.

aacraid: Host adapter abort request(x,x,x,x)

As I understand this it's a firmware issue with the Adaptec PERC controller, but I can't find firmware upgrade for a PERC2.  Am I S.O.L. or is this installation feasible?

Thanks,
Rich

---

### Post by trundlenut on 2009-10-05
I managed to update the firmware on my PE 2800 by downloading the firmware from the Dell website and creating bootable floppies which I then used to successfully update the firmware.

If you go to the dell support website and select your server (either by model or service tag) you can then download the firmware - choose the floppy option.  you will need a windows machine with a floppy drive to do it easily and then you just need to boot from the floppy(s) you create.

I just had a quick look on the dell website and found the update for the PE 6400 OK.

I also managed to update the firmware on the tape drive using the instructions and download for Red Hat linux from the Dell website.

---

