---
title: "Unable to set file permissions !"
date: 2010-10-03
forum: Security
---

### Post by Rebelli0us on 2010-10-03
In Nautilus I select a directory on local NTFS volume. I'm logged in as root, right-click > Properties > Permissions and I set "Others" to "none". But it doesn't work.

My objective: I want my friends & visitors to use and enjoy Ubuntu but without access to my NTFS volumes.

---

### Post by sisco311 on 2010-10-03
FAT/NTFS file systems don't support Unix/Linux file permissions. You have to set the permissions at mount time with the uid, gid, umask/dmask/fmask mount options.

See: [thread=283131]How to fstab[/thread]

---

### Post by Rebelli0us on 2010-10-03
Thank you, that sounds much too technical. Is there a way to create a new user and restrict his/her access to their Home directory?

---

### Post by bodhi.zazen on 2010-10-03
> **Rebelli0us said:**
> Thank you, that sounds much too technical. Is there a way to create a new user and restrict his/her access to their Home directory?

No, users must have access to large areas outside of their home directory.

Confining a user is an order of magnitude more difficult then learning how to mount a partition and Linux permissions.

I suggest you see :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

If you still wish to try to confine a user to his or her /home , start reading

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

[[all variants] Introduction to AppArmor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1008906") 

[Jailbash]("http://ubuntuforums.org/showpost.php?p=9799756&postcount=5") 

Then identify all the binaries and libraries such a confined user might need, and start moving them to the chroot in their home. Then decide how you  are going to keep such a chroot up to date.

Or start writing a jailbash apparmor profile.

And well, that give you an idea of the scope of the question you are asking.

---

### Post by sisco311 on 2010-10-04
> **Rebelli0us said:**
> Thank you, that sounds much too technical.

It's not hard at all, but if you are unsure on how to edit/create the fstab entry, then open a terminal (Applications -> Accessories -> Terminal) and post the output of:
```
sudo blkid -c /dev/null
```
```
mount
```
and
```
cat /etc/fstab
```

---

### Post by Rebelli0us on 2010-10-23
Thank you. The mount command shows a user named "friend"...

```
gvfs-fuse-daemon on /home/friend/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=friend)

```

It seems the "NTFS configuration tool" settings are universal and not per user (as in Windows).

How do I edit fstab to disallow "friend" to mount NTFS partitions?

---

### Post by Morbius1 on 2010-10-23
>  How do I edit fstab to disallow "friend" to mount NTFS partitions?     By doing exactly what sisco311 suggested. Assuming ntfs-config actually added a line in fstab then please post the output of fstab:
```
cat /etc/fstab
```It's likely all you need to do is add a umask=077 and a uid=1000 to the line but let's see what you've got to start with.

---

### Post by Rebelli0us on 2010-10-23
ok, here's fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdb5 :
UUID=c3f2dd10-a613-4661-bd4b-c468f00ae204	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda1 :
UUID=B8C87616C875D2DC	/media/1_1	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sdb1 :
UUID=14F81815F817F3A8	/media/2_1	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sdb6 :
UUID=6bc74f78-e2ab-448b-ae5e-3d71f521412e	none	swap	sw	0	0


```

What does it mean?

---

### Post by Morbius1 on 2010-10-23
Let's take the first one as an example:
>  UUID=B8C87616C875D2DC /media/1_1 ntfs-3g defaults,locale=en_US.utf8    0    0This will mount the partition with owner = root and permissions set to allow read write access to everyone. To limit that to just you you could modify that line like this:

```
UUID=B8C87616C875D2DC /media/1_1 ntfs-3g defaults,uid=1000,umask=077,locale=en_US.utf8    0    0
```uid=1000 will make you the owner
umask=077 will turn off all access to everyone but you.

When you're done editing fstab,  save it and then:
```
sudo umount /media/1_1
```Then:
```
sudo mount -a
```Then check the ownership and permissions:
```
ls -dl /media/1_1
```

---

### Post by Rebelli0us on 2010-10-23
Thanks, I'm reading your post and checking if I know how to make changes without trashing the OS.

Also, in "mountmanager" there is on option "Who can mount the partition". Would that work as well?

---

### Post by Morbius1 on 2010-10-23
I do not use ntfs-config, mountmanager, pysdm, or any other GUI. Too big a risk of messing something up.

Running "sudo mount -a" will produce an error message if you've done something wrong or made a typo.

---

### Post by Rebelli0us on 2010-10-23
Thank you. Do I just open fstab in gedit and edit one line? Is it just one comma-delimited string?

In nautilus "properties" for the partition, root is currently the owner. By specifying UID do I exclude root and/or other administrator-type users?

---

### Post by Morbius1 on 2010-10-23
You have to open fstab as root:
```
gksu gedit /etc/fstab
```
A normal user cannot edit fstab

Root will still have access because it's ... well ... root.

---

### Post by Rebelli0us on 2010-10-23
Thank you. I edited fstab as per your post, then I logged in as user "friend" and cannot see the NTFS partitions at all! I tried using ntfs-config but without password I guess "friend "is limited to ext3?

Can I edit fstab to add other admin-type users (e.g. 1002,1003 etc.) to the list of those allowed to mount NTFS?

So this works. Thanks for understanding the importance of the original question.

---

### Post by Morbius1 on 2010-10-23
>  Can I edit fstab to add other admin-type users (e.g. 1002,1003 etc.) to the list of those allowed to mount NTFS?The partition is already mounted. It's just that "friend" has no access. You don't want other users , even "admin" users to mount and unmount the partition. You can alter the fstab line to allow other users access but it becomes a little involved.

*[COLOR=Blue]For example[/COLOR]* you could set the line in fstab to look like this:
> UUID=B8C87616C875D2DC /media/1_1 ntfs-3g defaults,uid=1000,[COLOR=Blue]gid=users,umask=007[/COLOR],locale=en_US.utf8    0    0Then you would have to add all the other users you want to have access to the "users" group. Let's say I'm another user who you want to grant r/w access:

```
 sudo gpasswd -a morbius users
```

---

