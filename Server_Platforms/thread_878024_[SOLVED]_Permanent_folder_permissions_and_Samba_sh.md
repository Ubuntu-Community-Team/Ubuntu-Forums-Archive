---
title: "[SOLVED] Permanent folder permissions and Samba share help"
date: 2008-08-02
forum: Server Platforms
---

### Post by Zyzzyva100 on 2008-08-02
I am running 8.04 server (recently upgraded from 6.06 LTS) and am now having problems with my samba shares.  I am the owner of the folders that I have shared, and need my wife and our media extender to be able to access the files.

On my Mac I am able to connect via samba without problem, and on my desktop (was gentoo, now back to ubuntu) I can connect via NFS without problem.  My wife (windows, ubuntu sometimes) can connect and see the files as long as I chmod 777 the folder everytime something new is added, same with the media extender.

So I think the problem is a permissions issue, but I just can't figure out how to fix it.  Any time something new is downloaded into the folder, whether it be moved there via the network or downloaded from usenet via SABnzbd, I have to change the permissions on the file for anyone but me to be able to access it.  

How can I permanently set the shares to be accessible by anyone (my network is secure) on my network, without needing to change the permissions again each time a file is downloaded?  This wasn't a problem under 6.06, but something changed when I upgraded and now I can't figure it out (I have a feeling I didn't have this set up properly in the first place).

---

### Post by redraiderbum on 2008-08-02
You could try to recursively set the whole directory tree with chmod.  Like if the shared folder is called '/storage' you could do this:

sudo chmod 777 /storage -R

That should make it so anything new added to the directory tree inherits the permissions of the rest of the tree.  If that doesn't work you could try changing the owner of the folder to a newly created user just for sharing folders.  Also, I'm not sure this is good security practice, but for my storage share I put the folder at the lowest possible level.  That is I make a folder to share:

/storage

Rather than doing this:

/var/storage

This enables me to recursively set the whole tree as owned by my account rather than the root account.  It just makes the directory management easier and it prevents changing ownership or permissions on a file that may cause the system to break if it is not owned by the root.

---

### Post by Zyzzyva100 on 2008-08-02
The thing that's killing me is that I did set the permissions recursively, and I do so  at the lowest level in the directory tree.  For some reason the files added to the shares don't seem to inherit the permissions that the rest of the folder has - that't my real problem.

---

### Post by redraiderbum on 2008-08-02
There is a samba option to inherit directory permissions.  I use webmin to administer my shares; there is a radio button option to inherit permissions.  I'm not sure how to do it in the samba config file.  It could be that the files transferred are retaining the permissions of the computer from which they came.

---

### Post by Zyzzyva100 on 2008-08-02
I found the samba option to inherit permissions (inherit permissions = yes), but that doesn't seem to do it.

Other folders or files within the share look like this:
```
tom@porky:/mnt/storage2/share/incoming/tom/Ubuntu8.04$ ls -al
total 717012
drwxrwxrwx 2 tom users      4096 2008-08-01 00:39 .
drwxrwxrwx 9 tom users      4096 2008-08-02 14:04 ..
-rwxrwxrwx 1 tom users 733079552 2008-05-15 07:11 ubuntu-8.04-desktop-i386.iso
-rwxrwxrwx 1 tom users    394174 2008-08-01 00:28 ubuntu-8.04-desktop-i386.nzb
-rwxrwxrwx 1 tom users      3198 2008-08-01 00:28 ubuntu-8.04-desktop-i386.par
-rwxrwxrwx 1 tom users      3022 2008-08-01 00:28 ubuntu-8.04-desktop-i386.sfv
```

While the newly moved or downloaded files look like this:

```
drwx------ 2 tom tom      4096 2008-08-02 14:01 .
drwxrwxrwx 9 tom users    4096 2008-08-02 14:01 ..
-rw------- 1 tom tom   2191294 2008-08-02 14:01 Jones - BSD Sockets Programming 
```

---

### Post by redraiderbum on 2008-08-02
Oh that may have been helpful.  It looks like the samba inherited group is perhaps different than the file system group.  You probably have the share set to inherit the privileges of the user 'tom' and the group 'tom'.  But perhaps in the file system you have the folder as owned by the user 'tom' and the group 'users'.  

For your samba config try changing the group to 'users' or perhaps 'admin'.  The group 'tom' looks like it doesn't have write or execute privileges on that tree.

It depends on which one is the file system group vs the default samba group.  You want the samba group to have equivalent or higher privileges than the filesystem group.

---

### Post by Zyzzyva100 on 2008-08-02
Ok, I seem to have the problem fixed.  Adding the inheritable permissions option to the smb.conf file fixed any problems I had on files that I moved from one folder to another, and I actually found an option in SABnzbd that is apparently new to allow me to set the file permissions for any new files.  All this so we can listen to some live concert recordings, at least now it works.  Thanks for the help!

---

### Post by redraiderbum on 2008-08-02
No problem, glad to help.

---

