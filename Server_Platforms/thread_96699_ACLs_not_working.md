---
title: "ACLs not working"
date: 2005-11-29
forum: Server Platforms
---

### Post by mweichert on 2005-11-29
Hi guys,

I am using Ubuntu Breezy, with kernel-2.6.12. I have the following
packages installed:
-acl
-libacl1
-attr
-eicel

I'm trying to create a directory to contain source code used by the
developers. I've done the following, while logged on as root

mkdir /src
chown :developers /src
chmod 770 /src
setfacl -m g:developers /src

Now, if I'm logged in as a developer (belonging to the 'developers'
group), and try this:
cd /src

I get a permission denied error. What am I doing wrong?

Any help appreciated, thanks.

Regards,
Mike

---

### Post by LordHunter317 on 2005-11-29
You need to mount the filesystem with the 'acl' option.  Check the mount(8) manpage, edit /etc/fstab as necessary and then umount/mount the filesystem.

---

### Post by mweichert on 2005-11-29
[QUOTE=LordHunter317]You need to mount the filesystem with the 'acl' option.  Check the mount(8) manpage, edit /etc/fstab as necessary and then umount/mount the filesystem.[/QUOTE]

I already have the filesystem mounted with the 'acl' option. I'm have the following in /etc/fstab:

/dev/sda2       /               reiserfs noatime,acl,user_xattr,usrquota,grpquota 1       2

I hope I can get this working. Thanks for the reply!

---

