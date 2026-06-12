---
title: "Why is it so hard to log on to Samba?"
date: 2011-10-10
forum: Server Platforms
---

### Post by kamaji792 on 2011-10-10
It's so easy to log onto a Samba server from a Win box.  Synchronise the Samba and Win passwords and a simple batch file logs you in.  Even if this is not the case you can enter a user name and password and then you have access.

The official way (short of LDAP) is to create a mount point in 'fstab' with a 'credentials' file option.

All well and good but:
[LIST=1]
[*]You need to be a 'sudo' user to mount the share.
[*]How do you make the credentials file handle different users?
[/LIST]

Am I missing a trick, or is LDAP the only answer?

If you can help it would be appreciated - k 

PS - Yes I know there is a hack where you can SUID mount.cifs so any user can mount (and so write a script to get a username and password from the user to mount the appropriate shares) a Samba share.  This however does not work on versions after 10.04 and I am looking to the future and not having to re-apply the hack on every Samba update.

---

### Post by Morbius1 on 2011-10-10
> The official way (short of LDAP) is to create a mount point in 'fstab' with a 'credentials' file option.

All well and good but:
[LIST=1]
[*]You need to be a 'sudo' user to mount the share.
[*]How do you make the credentials file handle different users?
[/LIST]
1. If it's in fstab you don't have to be sudo to mount the share as it's already mounted.

2. You set the fstab parameters to allow one, a subset of the local users, or all local users to access the mounted share.

Alternately, you can use the gvfs method ( Nautilus > Network ) to mount and access the share when needed. You can even use gvfs to automount the remote share ( without using fstab ) each time the remote user logs into his machine and that server becomes available.

---

### Post by kamaji792 on 2011-10-10
Thanks @Morbius1 for the heads up on the Nautilus way of mounting Samba drives.  I have used it in the past but never been entirely happy with the results.  However I will give it another go as I can now see some advantages in using this system.

Thanks for now - k

---

### Post by Morbius1 on 2011-10-10
If you're interested, here's a mini HowTo on one way to automount ( via gvfs ) using a utility known as Gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

The gvfs method does have one disadvantage though and that's it's mount point. It will automatically mount to:
> /home/username/.gvfs/share-name on server-nameIf an application can access a hidden directory then there's no issue but if it can't you can create a symlink to a "non-hidden" directory. Either way it will create a mount icon on the desktop so you can manipulate the file directly from Nautilus.

---

