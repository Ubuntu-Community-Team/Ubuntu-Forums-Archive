---
title: "wow problems--cd won't eject, can't copy from disc to folder"
date: 2009-08-19
forum: Wine
---

### Post by jalehtor on 2009-08-19
Well, I have ubuntu 8.1 and the latest version of Wine installed. I have the Wow discs, and I'm having problems.

1. I can't eject the disc...when I try, I get "You are not privileged to unmount the volume 'WoWDisc1," and "only root can unmount."

2. I'm trying to follow the instructions at the ubuntu community. I have a wow folder on my desktop and the disc 1 icon. When I open the disc and right click on the info to copy, nothing happens. When I drag the icons to the folder nothing happens. When I click on the icons at either place, it says installer unable to start, no installer data found. 

WHAT am I doing wrong (other than everything)?

---

### Post by pedro_orange on 2009-08-20
Have you tried ejecting the disk as su? :P

How are you trying to eject?

```
sudo wine eject d:
```

Or something like that?

To copy a disk's contents to a folder on the hard disk, select all the icons on the disk (ctrl+a) Select the destination folder, and hit Ctrl+v

Have you read [https://help.ubuntu.com/community/WorldofWarcraft#Installing%20WoW](https://help.ubuntu.com/community/WorldofWarcraft#Installing%20WoW)

---

