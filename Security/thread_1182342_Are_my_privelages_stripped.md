---
title: "Are my privelages stripped?"
date: 2009-06-08
forum: Security
---

### Post by governmentproj13 on 2009-06-08
First of all, I had wanted to change the mount point of a partition.  I had set up my original installation with a partition for root, sd1, and a partition for my personal files, sd2, which i accidentally set the mount point for /usr instead of /home.

I backed up both /home and /usr to my Windows XP partition, sd3, using the command "sudo cp -a" since I heard a lot of people attempting to do the same thing were getting issues with permissions not staying the same and having issues upon rebooting after the process was done.  Regardless of doing this, I still encountered permission issues with /home, so I looked up that the default is 755 for home and 644 for the .dmrc file.  I changed both home and the .dmrc using the commands "sudo chmod -R 755 /home" and "sudo chmod 644 /home/.dmrc" respectively, and changed the ownership of home using "sudo chown -R christen /home".

Now, everything seems to be back to normal, both /home and /usr work and have the right files in them, but I am still lacking some functionality, like my wireless (onboard Atheros card).  The drivers are proprietary and were working before, but I can't even access the wireless drivers under Gnome because it gives me an "authorization" issue.  In fact, a lot of things were having these authorization issues, including when I tried to open Users and Groups.  Also, sd3 and any external storage device won't mount anymore, automatically or manually, I'm guessing for the same reasons.

It almost feels like the user "christen" may have its administration privileges stripped, which I don't remember doing.  And I could be wrong.  I'm not sure how to check or change this, and before I go into researching that, I wish I could find out why and how they were changed in the first place, and fix that problem first, because I feel like it has something to do with this whole mount point change thing, and I don't want to miss any more problems lurking under the surface because of it. Also, I'm hoping maybe that'll fix the other things like wireless and mounting.

Anyway, if anyone can point me in the direction I need to be pursuing, I would greatly appreciate it. Right now, the only way I can use the internet or access other partitions is to use Windows XP or a live CD!

---

### Post by cdenley on 2009-06-09
If you changed the permissions for everything in /usr and /home, then I would suspect that is your problem. NTFS doesn't support unix permissions, so if you wanted to backup to that filesystem, you should have used a tar archive. You might be able to fix every file that requires special permissions, but if I were you, I would re-install ubuntu.

---

### Post by lensman3 on 2009-06-09
Make sure the $HOME directory for the logins have moved to your new mount point.  $HOME directory is the fifth field in /etc/passwd.  I think a login will just hang if there is now home directory or dumps you to  / (root.  Don't forget to change the permissions on the dot directories and the dot files.  The recursive flag on chmod is dangerous (inconvenient) because it can go up the directory tree.  SELINIX can be a pain too because it can try to restore your changes.

---

### Post by governmentproj13 on 2009-06-18
Aw man, I didn't even think of that!  Well, is there any way I can fix my permissions? I don't really care if it takes a while or if it's a hassle; I put a lot of work into that partition (don't ask why I didn't make a full backup image...).

EDIT: In fact, ANY solutions that could get my admin privileges back would be AWESOME.  I can't find ANYTHING to help me with.

---

