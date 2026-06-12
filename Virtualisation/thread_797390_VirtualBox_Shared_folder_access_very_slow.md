---
title: "VirtualBox Shared folder access very slow"
date: 2008-05-17
forum: Virtualisation
---

### Post by Pete317 on 2008-05-17
I recently got a new hard drive for my desktop and, for various reasons, decided to install Ubuntu Studio 7.10 and to run XP from within VirtualBox. Everything works great except for one thing - I have a second hard drive containing several gigs of stuff which I want to access from both Ubuntu and XP. I set up file sharing and, within XP, created new network places pointing to my shared folders and it does work, except it's sooo sloooow that it's virtually unusable. It takes up to several minutes to access the files in a single folder.

My questions are:

1) Is there any way of speeding up the shared access?
2) Can I set up my second drive so XP can access it directly without going through a share?
3) I don't seem to be able to copy files between Ubuntu folders and XP. From an Ubuntu folder I click on Copy but when I move across to the Windows folder the Paste option is greyed out. I have set up my clipboard to be bi-directional and seamless operation appears to work well, so am I doing something wrong?

---

### Post by cb951303 on 2008-05-17
I don't know how vb handles shared folders but I prefer using samba :popcorn: it works like a charm

---

### Post by Pete317 on 2008-05-17
Thanks. After a bit of a struggle I got the shares set up in Samba.
I'ts working a lot better now.

Still can't figure out why the clipboard doesn't work, though...

---

### Post by rune0077 on 2008-05-17
Have you installed the XP guest edition in VirtualBox? This makes it much easier to use shared folders (you don't actually have to set up a share, you just need to set the folders XP can access from the settings), and it should allow you to copy/paste freely from host to virtual system. Also, it'll let you move the mouse freely, treating the virtual system likes it's just a normal running application.

---

### Post by cb951303 on 2008-05-17
[http://code.google.com/p/virtual-box-windows-guest-additions-installer/](http://code.google.com/p/virtual-box-windows-guest-additions-installer/)

---

### Post by Pete317 on 2008-05-17
Yes, I have installed the guest addons, and the mouse pointer sync and seamless windows work well - except for the copy/paste

---

### Post by rune0077 on 2008-05-17
> **Pete317 said:**
> Yes, I have installed the guest addons, and the mouse pointer sync and seamless windows work well - except for the copy/paste

Not really sure what the issue is then. Is it just the actually copy/paste? Can you drag and drop text etc?

---

### Post by Pete317 on 2008-05-18
I can copy/paste text between files in XP and Linux, both ways, but I cannot drag/drop or copy/paste files in any direction.

---

### Post by rune0077 on 2008-05-18
> **Pete317 said:**
> I can copy/paste text between files in XP and Linux, both ways, but I cannot drag/drop or copy/paste files in any direction.

Oh okay, I'm not sure you should be able to do that. I have never tried it myself. Can't you just copy the file into your shared folder, that way is should be available on both ends.

---

### Post by Pete317 on 2008-05-18
Now that I've gotten my Samba shares up and running, I probably don't need it - my interest is now more out of curiosity than anything else.

Thanks anyway

---

### Post by Kiri on 2008-05-19
Does it matter what format the disk is when using samba shares?
Currently I have been using an NTFS formatted disk through the vbox shares and have also noticed it to be very slow (and cpu instensive).
I would like to see if I can get samba shares working better..

---

### Post by cb951303 on 2008-05-19
> **Pete317 said:**
> Now that I've gotten my Samba shares up and running, I probably don't need it - my interest is now more out of curiosity than anything else.

Thanks anyway

dragging/dropping or copy/paste files between host and guest isn't supported... that's why we have shared folders feature ;)

---

