---
title: "ftp access with mouting/symlinks"
date: 2008-12-16
forum: Server Platforms
---

### Post by suffice on 2008-12-16
hello there....i have got a question about directory access pertaining to an ftp server....

ubuntu intrepid, desktop ed.
vsftpd - (proftd had some bugs that were documented)

i set up an ftp sever with a second user on my computer..

so my home dir is /home/patrick
the other is /home/aisha

for ftp sake i dont want /aisha to be able just just browse around the /

i can log into aisha from the ftp, where it connects to her 'home folder'

she can do all the uploads yada yada no prob.....

now my media is on an external drive @ /media/external

i want to be able to let her into some of the folders in the external but not all...

i tried --
mount /media/external/VID/TV /home/aisha/TV
 but it said 'not a block device'

ive also tried a symlink with ln -s /media/external/VID/TV but that wouldnt let me click into while logged in...

now both users are part of the 'patrick' group, and ive set uploads to turn into 'patrick' owned files....

just wondering how to share a few files through mounts and links into the aisha folder without letting her access the whole /..


any ideas?

---

### Post by cdenley on 2008-12-16
```

sudo mkdir /home/aisha/TV
sudo mount --bind /media/external/VID/TV /home/aisha/TV

```
You might want to put that mount in /etc/fstab, assuming your external drive is already in there and always mounted.
```

/media/external/VID/TV /home/aisha/TV none defaults,bind 0 0 

```

---

### Post by suffice on 2008-12-16
thanks man....i knew it would be something like that....

works like a charm

---

