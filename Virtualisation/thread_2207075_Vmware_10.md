---
title: "Vmware 10"
date: 2014-02-21
forum: Virtualisation
---

### Post by pendulous on 2014-02-21
While testing Ubuntu I figure that I may as well setup my vm's and validate my tib images are still intact and the like. Also, backup this ubuntu install. All my hosted vm files and backups reside on an NTFS drive, which are mounted, rw capabilities, and shared (added and verfied within samba). 

This is the routine: VM10 is installed and functioning. created the intended VM directory/disk for this particular W8 test setup on the ntfs shared drive, boot into ATI2014 via emergency iso. Now that ATI2014 is loaded and navigating to restore then 'browse for backup' , 'computers near me' no shares are listed.


Has anyone experience with VM10 (or other), AcronisTI, while running under Ubuntu? Or someone willing to test it out and help find a solution?

---

### Post by pendulous on 2014-02-22
Not much of a solution, but setup an ftp server. Gadmin_Proftpd GUI is really clunky and errors out and crashes when presented with the following error:

```
GADMIN-PROFTPD could not find the proftpd configuration
or you are using a basic configuration that doesnt have
all the features that this program requires.


Do you want to overwrite your current proftpd configuration
with a suitable standard configuration for gadmin-proftpd ?

            (If you don't know then press yes)
```


Selecting 'Yes,' the application closes, selecting 'no,' the application is still active, but I'm unable to create users, directories, and doesn't create a 'generate new certificates.' Though, I setup webmin and a user and seems to be working somewhat, but super slow transfer speeds.

---

