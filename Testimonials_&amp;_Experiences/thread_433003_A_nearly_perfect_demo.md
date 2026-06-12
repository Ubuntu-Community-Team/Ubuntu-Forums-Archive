---
title: "A nearly perfect demo"
date: 2007-05-04
forum: Testimonials &amp; Experiences
---

### Post by PantaRhei on 2007-05-04
Last night a friend dropped in and he asked me if it was really true that my computer was running now on Ubuntu. (I append a message to the emails I sent: "Free people are using free software. Ubuntu. A free
software for free people"). I showed him how smooth OpenOffice imported some Microsoft-office-files, how Firefox and Thunderbird worked, I processed an image with the GIMP,  showed the synaptic package-manager and finally demonstrated how Wine was running Fritz8. He was very impressed. Well, he said, can I try something? He went into his car and brought his digital camera in. He connected the camera to my computer and the symbol of a mounted disc popped up! Great! Then a dialog automatically popped up and requested us if we wanted to import the pictures because a disc with pictures was found. Splendid! We didn't want to import pictures, but only wanted to browse the pictures on the disc. Now he was really convinced that Ubuntu was working fine.:) 
However ... It was not possible to unmount the disc. When I wanted to unmount the disc, I got a message that it was not possible to unmount and the dialog popped again to tell us that pictures were found. (I guess that a task is running that locks the usb-mounted disc? Sees that the disc is unmounted, mounts the disc again and pops up the said dialog?). When we powered down the camera, the disc was automatically unmounted, but a warning popped up: "unsafe removal ....". :confused: 
Anyhow, my friend was really impressed and he confessed me, that this demo has put aside his prejudices on free and open software.:popcorn: :popcorn:

---

### Post by 3rdalbum on 2007-05-05
Here's a handy command that lists all the programs using a particular location:

```
lsof /media/usbdisk
```

Replace */media/usbdisk* with the mount point of the camera.

My guess is that you've hit upon a previously unconfirmed Nautilus bug - where you open a file browser window at a location, and Nautilus doesn't release that location it after you close the window. If that is the case, then the command I gave you will list Nautilus. You can quit Nautilus by running the "xkill" program and clicking on the desktop (or better yet, put the "Force Quit" applet onto your Gnome panel).

---

### Post by PantaRhei on 2007-05-05
Thank you, 3rdalbum for the advice. However when I want to convince my folks down here, I'll have to avoid the commandline anyhow. :-s :-s None of them do have any basic computer-knowledge. On the other hand they are able to send and reply emails, do some internet-banking and are able to store some of their camera-pictures on the hard-disc (although finding them back is sometimes troublesome):confused:).

---

