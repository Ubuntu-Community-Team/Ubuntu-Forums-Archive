---
title: "Need to recreate home directories"
date: 2010-06-30
forum: Server Platforms
---

### Post by preparationh67 on 2010-06-30
Due to an unfortunate series of hardware and software failures, the drive that had home directories was lost and there is no backup. I currently need to recreate user home directories, empty ones obviously, but I'm really not sure how to go about doing that. Any help?

---

### Post by arrrghhh on 2010-06-30
Well, the mkdir command may help.  Then you'll have to chown/chmod the directories to the proper user account levels.  I'm not sure if there's anything required in the directories, but there may be... I'm not sure.  It really depends on what DE they use I suppose.

---

### Post by preparationh67 on 2010-06-30
I know I could probably make a bash script to do it that way, but I'm hoping there is a better way to do it than that.

---

### Post by arrrghhh on 2010-06-30
Without backups, not really.  Good luck.

---

### Post by robots.jpg on 2010-06-30
If you create the directory with the correct permissions and copy the files from /etc/skel to it, that should cover everything the adduser command would have done.

---

