---
title: "detecting optical drives - a few questions"
date: 2011-04-14
forum: Wine
---

### Post by mystmaiden on 2011-04-14
When I autodetect drives with wine config it gives me the following -

```
A:  /media/floppy0
c: ../drive_c
D: /media/Poser 5
E: /media/sda3
H: /home/mystmaiden
Z: /

```

I'm a bit confused about the d drive, its showing Poser 5, which is a program I have installed under wine as having its own drive. Is this normal?

My other question is, can I just use F and G for the optical drives? Also under Places/Computer in Ubuntu it lists just CD Drive and CD/DVD Drive so if I use the command line will Wine know which is which?

thanks 

mystmaiden

---

### Post by cogadh on 2011-04-14
If the disk for that app is in your CD drive when you auto-detected drives, then Wine will create the Windows drive with the label from that disk. 

You honestly don't need to autodetect drives in Wine anymore, unless you are trying to run a game that is having problems with its copy protection. 

As for how Wine knows what drive to use, it really doesn't need to, just you need to know that. When a disk is inserted in a drive, Ubuntu will automount it, creating a mount point in /media with the same name as the disk's label. As long as you know that label (it's pretty easy to figure out), then you tell Wine what it is when you run it in the terminal. For example, if that "Poser 5" is a disk, then you would run an executable off it like this:
```
wine /media/Poser\ 5/setup.exe
```

---

### Post by mystmaiden on 2011-04-16
Thanks for the explanation, very much appreciated. I had run the poser disc on the last time I opened wine and so it was still showing. When I opened wine again, it had gone.

---

