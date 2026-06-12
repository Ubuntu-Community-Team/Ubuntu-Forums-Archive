---
title: "how to vsftpd and chroot jail somebody"
date: 2008-06-22
forum: Server Platforms
---

### Post by cheruvim on 2008-06-22
So you have a bunch of users and you want them to have their own little ftp play area so they don't go poking around. You also don't want anyone else to get in

The best way to do this is to put the users in a chroot jail.. A chroot jail basically says, "make directory X the root of the server. Anything outside of X cannot be accessed." vsftpd provides a way for you to set the users home directory as the chroot jail. Each user thus who has a home dir, can use that dir as their ftp play area, wet their diapers, build sand castles and the whole sort of general mish-mash (WSGMM for short).
 
So you set up vsftpd like this:
anonymous_enabble=NO
local_enable=YES
chroot_local_user=YES

#Then you can add some optional tweaks like
chroot_list_file=/etc/vsftpd.chroot_userlist
chroot_list_enable=YES
# this means chroot all local users EXCEPT the ones in the chroot_list_file
# if chroot_local_users is NO then the list becomes a list of users who ARE chroot'ed upon login

Now you are wondering "I want joe to access my cool stuff in folder X, but I don't want to move X to his folder.. that would be a pain." So you try a symbolic link.. Well that doesn't work because a symbolic link says "Let joe jump to X" but chroot says "Joe can't go anywhere but here, buzz off!" It has been known that if you hard link a file it will work because a hard link basically says that logically file x is equal to file y even though they are in physically different places on the disk. You cannot, however, hard link directories. So the thing to do is to mount dir X into Joe's directory:

mount --bind /full/path/to/dir/X /joes/directory/<mountpoint>

where <mountpoint> is the name of a directory you have created that will serve as the place on the disk where the X dir is to live (not physically just logically). This is now set up where /joes/directory/X/piratew0rz is now accessable via the jail. 

Use this with caution, make sure your permissions are set right.

The caveat with this (and this is the experimental part) is what if you have to restart the server (does fstab support directory mounts like this?). I assumed not so I edited the start script for vsftpd to include two additional executables that basically execute the mount and umount commands for joe's dir which is getting into the "do it wrong and you foo bar the whole operation" territory.

Hope that helps.
C.

-- edit --

you can however soft link from a location within the directory you are rooted to any other place within that directory because after all you are still within the jail.

Example:
if I am chrooted to /home/cheruvim and I do ```
ln -s /htdocs serverDir
``` It SHOULD work. Remember / = /home/cheruvim as per chroot then a link called serverDir will link you to /htdocs which is really /home/cheruvim/htdocs. The point is that since you are still within the confines of the jail the ln command will work.

---

### Post by beandog on 2012-10-25
> The caveat with this (and this is the experimental part) is what if you have to restart the server (does fstab support directory mounts like this?).

Yes, you can add a bind mount to /etc/fstab:

```

echo /mnt/source /mnt/destination none bind >> /etc/fstab

```

Mount the drive:

```

mount /mnt/destination

```

Verify it's mounted:

```

mount
Returns: /mnt/source on /mnt/destination type none (rw,bind)

```

---

