---
title: "Is there a way to write a Fedora ISO to a USB stick from within Ubuntu?"
date: 2009-04-29
forum: The Cafe
---

### Post by garythegoth on 2009-04-29
I cant seem to find anything that dosent require having Windows or fedora installed to work.

---

### Post by jordanae on 2009-04-29
Actually Ubuntu makes it pretty easy. First go to System> Administration> USB Startup Disk Creator

All you need is a flash drive (USB stick) and an ISO of Fedora

good luck!

---

### Post by gn2 on 2009-04-29
If the above mentioned tool doesn't work with a Fedora .iso, try [unetbootin]("http://unetbootin.sourceforge.net/").

---

### Post by calrogman on 2009-04-29
> **jordanae said:**
> Actually Ubuntu makes it pretty easy. First go to System> Administration> USB Startup Disk Creator

All you need is a flash drive (USB stick) and an ISO of Fedora

good luck!

Except that this method only works with *buntu .isos.

Your best bet is to use UNetbootin which is available in the Universe repos.

EDIT: Hivemind.

---

### Post by garythegoth on 2009-04-29
> **jordanae said:**
> Actually Ubuntu makes it pretty easy. First go to System> Administration> USB Startup Disk Creator

All you need is a flash drive (USB stick) and an ISO of Fedora

good luck!

Sorry, I should have made it clearer.

I already tried that but it says its not a valid desktop iso. It appears to only work with Ubuntu systems.

---

### Post by garythegoth on 2009-04-29
> **gn2 said:**
> If the above mentioned tool doesn't work with a Fedora .iso, try [unetbootin]("http://unetbootin.sourceforge.net/").

Nice one (y).

---

### Post by jordanae on 2009-04-29
> **garythegoth said:**
> Sorry, I should have made it clearer.

I already tried that but it says its not a valid desktop iso. It appears to only work with Ubuntu systems.

Oh, sorry about that. I've always assumed that it'll use any ISO. Hence its name :/

---

### Post by garythegoth on 2009-04-29
> **garythegoth said:**
> Nice one (y).

Actually that didnt work, it just gives me error messages.

Is there any way to make it install the Fedora 11 KDE Beta x64_86?

---

### Post by calrogman on 2009-04-29
> **garythegoth said:**
> Nice one (y).

I don't get any credit?  :(

---

### Post by garythegoth on 2009-04-29
> **calrogman said:**
> I don't get any credit?  :(


Solve the post above your last one and you get a cookie :)

---

### Post by calrogman on 2009-04-29
Are you sure you had it all set up correctly?  You need to;
A) Click the correct radio button
B) Specify the .iso file
C) Specify the drive.

Literally *ANYTHING¹* could go wrong.

PROTIP:  Don't use sda*.


¹With the possible exception of your drive filling with llamas.

---

### Post by garythegoth on 2009-04-29
> **calrogman said:**
> Are you sure you had it all set up correctly?  You need to;
A) Click the correct radio button
B) Specify the .iso file
C) Specify the drive.

Literally *ANYTHING¹* could go wrong.

PROTIP:  Don't use sda*.


¹With the possible exception of your drive filling with llamas.

Radio button?
It still dosent work, but thanks anyway.

Also, why cant the USB Startup Disk Creator format a USB stick? Thats a pretty pathetic error.

---

### Post by dragos240 on 2009-04-29
That tool is used for putting ubuntu on a stick. You can try putting fedora on there using it though.

---

### Post by gn2 on 2009-04-29
[Here's a video how-to]("http://www.linuxjournal.com/video/creating-bootable-usb-install-drives-unetbootin") which mentions installing a required package to make it work.

---

