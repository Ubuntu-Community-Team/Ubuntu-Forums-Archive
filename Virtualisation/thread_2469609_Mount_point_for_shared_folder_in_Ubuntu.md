---
title: "Mount point for shared folder in Ubuntu"
date: 2021-12-03
forum: Virtualisation
---

### Post by peterqb on 2021-12-03
I have tried to set up a shared folder using Virtual Box. It asks for the mount point. Wat should I enter for that? Once in Ubuntu how do I mount the shred folder for permanent use? The manual is not very clear on this.

Many thanks in advance.

pqb

---

### Post by ajgreeny on 2021-12-03
Ignore the request for a mountpoint, leaving the box blank and it will still work fine in my experience. I never set a mountpoint but left it to mount automatically.

However, what is your host OS and what guest?
I always has Xubuntu as my host and a variety of Linux distros and Windows OSs as guests; it may be different using Windows as host.

If using a Linux guest make sure that the guest user is a member of the ***vboxsf*** group or sharing will fail.

---

### Post by lammert-nijhof on 2021-12-04
Agree I use Virtualbox since 2010 and I never specified a mount point, Virtualbox will create its own mount point by adding "SF_" in front of the folder name. so the mount point will be /media/SF_<folder name>

---

### Post by peterqb on 2021-12-06
Thank you for the replies.

I have set up a directory/folder in Virtual Box with host system macOS. How do I find the directory/folder in Ubuntu?

Thanks

pqb

---

### Post by ajgreeny on 2021-12-06
Have you added your Ubuntu guest OS user to the vboxsf group?

If you have not done so you will not have a shared folder from your MacOS available; if you are a vboxsf group member the shared folder should be at /media/SF_folder as mentioned by lammert-nijhof above.

All this is assuming that everything in MacOS as host acts similarly to Ubuntu as host; I know nothing about Mac systems and for all I know they may be very different in behaviour.

---

