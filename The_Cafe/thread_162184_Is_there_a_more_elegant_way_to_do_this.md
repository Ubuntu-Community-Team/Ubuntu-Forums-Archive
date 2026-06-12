---
title: "Is there a more elegant way to do this?"
date: 2006-04-18
forum: The Cafe
---

### Post by K.Mandla on 2006-04-18
One of the new gizmos I have for my trusty Inspiron 8000 is a removable bay that holds a spare hard drive. It's useful here and there, not too fancy, but a fun addition to an already fun computer.

The laptop is a "communal" machine, in the sense that there are two or three user accounts on it. At present, the fstab is set up to mount that spare hard drive to a folder in one user's home. It's not ideal for the other people who use the computer, since they have to redirect to that user's folder to access the spare drive.

Is there a cleaner way to do that? I've tried mounting it to the root directory, but it's almost as clumsy. I'd love to be able to have a folder in each user's home directory that allowed them access to that drive, but it seems that fstab mounts the drive long before the user signs on.

Any suggestions? I'm sure there's a better way to do this than the hack job I came up with. Thanks in advance. :)

---

### Post by christhemonkey on 2006-04-18
A symlink to the harddrive?
```
ln -s /wherever/harddrive/is/ /home/whoever/hardrive
```
The 2 directories may be the wrong way round....i do forget terribly on these long tuesday nights.

---

### Post by aysiu on 2006-04-18
Well, there's a sort-of solution. Unfortunately, as far as I can tell, it doesn't work fully the way nature intended. I'll explain.

The best way to do this is to create a mount point outside of everyone's /home directory (something like /shared) and then (I'm assuming it's an Ext3 drive) have an /etc/fstab entry like ```
/dev/hdb1 /shared ext3 defaults 0 0
```

Then do a ```
sudo chmod -R 775 /shared
``` and make symlinks to /shared in everyone's /home directory.

Here's the unfortunate part. The *chmod* command will change permissions on all the files that are *currently* in there. Even if you *chown* the folder recursively so that everyone in the same group owns that directory, **newly created files will have 755 permissions, *not* 775 permissions**.

That means that if you create a file in that shared directory, you will be able to read from and write to that file, but someone else will be albe to read from that file and *not* write to it, unless you specifically change the permissions of that file after you create it.

I don't know a solution to this. If anyone does, please come forward and educate me.

---

