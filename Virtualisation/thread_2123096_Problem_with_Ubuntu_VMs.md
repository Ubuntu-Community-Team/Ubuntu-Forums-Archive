---
title: "Problem with Ubuntu VMs"
date: 2013-03-07
forum: Virtualisation
---

### Post by long2511mdd on 2013-03-07
I installed Oracle Virtual Box, I did install Extension Package either.  But I still cannot use "Share Folders" or connect to my Flash Drive.

I run Windows 7 Professional 64 bits on Ubuntu 12.04 VMs.

What I received after I tried to acess "Share Folders" is that 

" Failed to access the USB subsystem.

 VirtualBox is not currently allowed to access USB devices. You can  change this by adding your user to the 'vboxusers' group. Please see the  user manual for a more detailed explanation.

"

What should I do?

---

### Post by Cheesemill on 2013-03-07
Have you done what it said and added your user to the vboxusers group?
The command you need is...
```
sudo gpasswd -a username vboxusers
```
Replacing username with your actual username.

---

### Post by long2511mdd on 2013-03-07
I did add my username to the vboxusers group, but there is no differences

---

### Post by long2511mdd on 2013-03-07
It worked, thank you, after I shutdown guest OS and use the command, it has been done.

---

### Post by Cheesemill on 2013-03-07
Sorry, I forgot to mention that.

You need to log out and back in again for the new group membership to take effect.

---

### Post by long2511mdd on 2013-03-11
Solved

:)

---

