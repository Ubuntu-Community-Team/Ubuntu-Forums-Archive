---
title: "Nautilus problem in ubuntu 11.04"
date: 2011-05-15
forum: Ubuntu Studio
---

### Post by kadlam on 2011-05-15
I recently upgraded and now having problems with nautilus. 
1) I don't know for sure if it's related but all of the icons on my desktop (files located in desktop) have little lock symbols in the upper right-hand corner of the icon. 
2) I cannot open files from the desktop (because they are evidently locked)
3) I cannot open any of the folders listed when I go to "Places" (between Applications and System top of the screen)

Running nautilus from the terminal, I CAN go to different folders and open files in the usual manner. 

Any ideas why I'm having the troubles from desktop?

Thanks,
Ken

---

### Post by SecretCode on 2011-05-15
The lock symbol means you don't have permissions to those files. 

In terminal, run
```
ls -l ~/Desktop
```
and see if there are any files owned by root or another account.

---

### Post by kadlam on 2011-05-15
I used nautilus from terminal (which works fine) and looked at the permissions and found that there was no access allowed for Desktop. So I changed it but I still cannot access any of the files on the desktop.
 
This may be a bigger problem than file permissions. When I try to open anything from 'PLACES' nothing happens. When I shut down the machine I get a message, "FILE MANAGER NOT RESPONDING."  
 
So...still looking for a solution.

---

### Post by Pablo_F on 2011-05-16
Just trying to guess, but maybe the file system went to read only mode because of some hard disk IO error?

Try running fsck from a Live CD. (fsck /dev/whateverpartition)

Cheers, Pablo

---

