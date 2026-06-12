---
title: "No permission?!"
date: 2011-05-19
forum: Security
---

### Post by DMRider_10 on 2011-05-19
Just installed Lubuntu on my lappy having had Ubuntu 10.04 in the past and liked it. I dont seem to be able to get permission to move files though?

I open LXTerminal and have tried the commands:

Sudo nautilus
gksudo nautilus
gksu nautilus

But still I cant drag drivers into the driver folder? (/usr/lib/xorg/modules/drivers)

Can anyone help?

Thanks

---

### Post by SteveDee on 2011-05-20
Lubuntu uses the file manager "pcmanfm".

So to copy a file to /usr/lib/xorg/modules/drivers simply navigate to this folder, then select the "Tools" menu and select "Open Current Folder As Root", then enter your [admin] password.

A second window will then open and you should be able to copy any file to this folder (I've just tried it, and it works OK).

If you still have Nautilus on your laptop, I guess you must have either installed Lubuntu packages over Ubuntu, or installed Nautilus separately.

---

