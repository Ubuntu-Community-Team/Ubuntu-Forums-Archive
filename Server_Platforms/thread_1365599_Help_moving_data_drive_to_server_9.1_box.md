---
title: "Help moving data drive to server 9.1 box"
date: 2009-12-27
forum: Server Platforms
---

### Post by kodb on 2009-12-27
**I origninally posted this in the beginner forum but added here as it may be more advanced topic even if I'm a total ubuntu/linux newbie! ** 			 			 		   		 		 		Hello all and thank you in advance as this is my first post here.
I am in the process of converting both our home and office networks to ubuntu 9.1 server/desktop environments and throwing away as much ms stuff as possible. I've gotten a preliminary homeserver set up on an old HP P4 box with a 50G drive. I have gotten samba and nfs set up and working. My question is how do I take a 750G sata drive that has been sitting in a usb toaster to store our videos and move that drive into the inside of the server box (not via usb but via the sata connectors) so that I can share the video over the network? Is this possible? I searched and could not find an answer
Thanks again for helping this newb (Ubuntu)
KODB

---

### Post by Cheesemill on 2009-12-27
***Step 1:***

First you need to set up fstab so that it automatically mounts the new drive every time you boot your system:
[How to fstab (Ubuntu Forums post)]("http://ubuntuforums.org/showthread.php?t=283131")
[How to fstab (Ubuntu Wiki)]("https://help.ubuntu.com/community/Fstab")



***Step 2:***

Set up Samba to enable file sharing:
[How to setup Samba (Ubuntu Forums post)]("http://swiss.ubuntuforums.org/showthread.php?t=202605")

---

### Post by kodb on 2009-12-27
Thanks for the links Cheesemill; that helps with the mounting the drive.
I already have samba set but actually am more interested in doing the "sharing" via nfs and between the ubuntu/xubuntu boxes that are running in the house now.
Currently i have a /srv/homeserver setup that the ubuntu clients access via their /var/homeserver folder under the filesystem.  I'm trying to be able to do the same thing with the video harddrive without necessarily (or even desirous) to do so with windows boxes.
I hope I am conveying this correctly.
Thanks,
KODB

edited:  I found what looks like the nfs way to do later in the link you posted above; wil try that and see if I can get working here.  Thanks

---

