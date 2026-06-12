---
title: "Ubuntu Server stuck at GRUB"
date: 2008-08-26
forum: Server Platforms
---

### Post by StrangeWill on 2008-08-26
Right after POST, I get the message:
GRUB

And a blinking cursor, that is ALL. Just switched from Fedora9, figured I'd get better hardware support in Ubuntu.


Running with two SATA drives, when I go into install it constantly prompts me as my old primary as being HDB, but that doesn't matter right? After making that my primary drive it shouldn't matter, yes?

Edit:
And I can't type anything, so this isn't the GRUB loader actually running.


Edit2:
After a bit of searching, seems GRUB isn't installing correctly, I'll try pulling the secondary drive so that it's not getting confused for some weird reason.

It BETTER have not destroyed the data on my other drive.

---

### Post by falcon61102 on 2008-08-26
You may need to reinstall the GRUB because if you deleted your Fedora install you may have taken a portion of the GRUB with it.  Boot up from a LiveCD and open a terminal.  Then run the following:
```
sudo grub
find /boot/grub/stage1
root (hdX,Y)
setup (hdX)
```

Replace the X,Y with the output of the find command.  For the setup command, just use the first number which is the HD number of your install.

---

