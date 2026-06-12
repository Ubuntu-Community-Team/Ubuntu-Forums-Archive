---
title: "One problem folder"
date: 2008-06-02
forum: Security
---

### Post by hooligan36 on 2008-06-02
I have 3 folders set up on my server. Photos, videos and music. I am having trouble with teh photos folder. i copy my photos from my SD card on a laptop (gutsy) and try to paste the newly labled pictures to the folder on teh server. I keep getting error messages and not being able to move them to the server. I can move music and videos by that procedure with no problem. I have the picture folder set up so that it can be read by Gallery2. 

Anyone can help with this. I have even changed the permissions of the SD card folder for everyone to have all access, but still no luck. I had to wind up using a SD card reader on the server to copy the pics and even then, before I changed the file permissions it said I did not have permission to see the files. I changed the permissions of the folder and then it will just show pic icons, it won't dispaly thums in the folder.

---

### Post by hooligan36 on 2008-06-03
bump

---

### Post by The Cog on 2008-06-03
What protocol do you use to talk to the server? SMB, ssh, nfs?

Does it say why you can't copy the files? Permission denied, timeout, disk full, other?

Can you do "ls -ld <foldername>" for all 3 folders so we can see their permissions and see if there's any difference.

Can you copy photos to the video folders, and videos to the photos folder? If so, that indicates the problem is perhaps with the destination folders rather than the source folder or the file type or file names.

---

### Post by hooligan36 on 2008-06-04
chris@server:/media/disk$ ls -ld Pictures
drwxr-xr-x 216 chris chris 12288 2008-06-01 23:42 Pictures
chris@server:/media/disk$ ls -ld Videos
drwxr-xrwx 2 chris chris 4096 2008-06-01 23:23 Videos
chris@server:/media/disk$ ls -ld Music
drwxr-xrwx 8 chris chris 270336 2008-06-01 23:32 Music
chris@server:/media/disk$ 


looks like there is a difference. Can you explain what it means? And what command (chmod?) to use to change it?

---

### Post by Dr Small on 2008-06-04
Try:
```
chmod 757 Pictures
```
to match the others.

---

