---
title: "Restricting access to NTFS partition or even folder"
date: 2008-11-20
forum: Security
---

### Post by jdackle on 2008-11-20
Hi,

This may be so basic I don't actually know whether it belongs in "Security Discussions" but here we go...

I currently have both Hardy (can't install Intrepid so no point in mentioning that to me if it provides better support for this...) and Vista on my notebook.

Vista's "regular" Users (i.e. w/o Admin, Public and the hidden users (but somehow "Default" got in there too, will see about that later)) are on a separate partition.
Some in-personal-home folders and files in Ubuntu should point (symlink) to some folders and files in that partition.
So my hd (only one) is basically setup like this:
**sda1** - NTFS, Vista system/programs - Regular users' folders in C:\Users symlinked ("mklink /D") to corresponding folders in sda5 (E: )
**sda5** - NTFS, Vista regular users / Ubuntu symlinks destinations
**sda7** - ext3, Ubuntu Hardy Heron system and "unsharable" user data - Specific folders and files in /home/user1, /home/user2, etc (Documents, Music, Firefox profiles' specific files and folders, ...) pointing to corresponding specidic folders/files in sda5

*Note 1: I do not want to use an ext3 fs for shared partition because I rather not trust Windows to reduce access to folders/files Ubuntu uses too (and I ear the ext3-fs driver for Windows can rather easily be _re_configured to grant access to other folders in Linux, including the root "/"...)*

So, what I want to know is:
**1.** How can I mount sda1 (C: ) so that only root can access it (I believe I can use visudo to prevent other users than the first one access to sudoing into it...?)?
**2.** (harder I guess) How can I mount sda5 (E: ) so that only one Ubuntu user, besides root in the same manner as in #1, can access it?
**3.** Better stil than #2 (and possibly even harder :( but really what I wanted), can I mount specific folders in sda5 to be accessible to specific users only in Ubuntu (e.g. sda5/User1 only accessible to Ubuntu's user1, sda5/User2 only to Ubuntu's user2, etc)? (mount tweaking preferred but safe and secure workaround to the same effect apreciated too. ;) )

In brief: **How to implement #1 AND (#2 OR (possibly XOR) #3), being #3 preferred over #2?**

*Note 2: I might use folder encryption _on top_ of the above, but haven't researched about this yet and again, I would prefer it _on top_ of the above, _not exclusively_.*

TIA :)

---

### Post by cdenley on 2008-11-20
I think what you would want to do is create entries for the filesystems in /etc/fstab. Then it will be mounted with whatever options you want (uid, umask, etc). NTFS permissions are ignored in Linux. Unix permissions are created at mount time for the entire drive. You can't have special permissions for certain files/directories. Any Windows user will be able to access files created in Linux.
```

man mount.ntfs-3g

```

---

### Post by jdackle on 2008-11-20
Thanks for the reply.

I will see that man-page and post any doubts I may have regarding it here.


Regarding:> **cdenley said:**
> Any Windows user will be able to access files created in Linux.
I believe you meant to say "Any Windows user will be able to access files created**, in his/her own Windows user-folder,** in Linux."

---

### Post by cdenley on 2008-11-20
> **jdackle said:**
> Thanks for the reply.

I will see that man-page and post any doubts I may have regarding it here.


Regarding:
I believe you meant to say "Any Windows user will be able to access files created**, in his/her own Windows user-folder,** in Linux."

No, I mean the NTFS permissions will be full for everyone for files created on your NTFS filesystems from Linux, as far as I know. This means when the drive is mounted in Windows, everyone will have access to those files. I don't know this from experience, but skimmed through the manpage a little before my post.
> 
Windows users have full access to the files created by ntfs-3g.

Were you expecting NTFS permissions to be translated into Unix permissions and Windows users to be translated to Unix users?

---

### Post by jdackle on 2008-11-20
> **cdenley said:**
> No, I mean the NTFS permissions will be full for everyone for files created on your NTFS filesystems from Linux, as far as I know. This means when the drive is mounted in Windows, everyone will have access to those files. I don't know this from experience, but skimmed through the manpage a little before my post.
Oh, I see your point now!
Well, in Widows (at least Vista), User1 will not be able to access User2's "home" folder withtout providing the Admin's password first. Thus, even though there might be folders/files in User1's home-folder that do not have the corresponding NTFS persmissions set, User2 will never be able to see them as he/she cannot enter User1's folder anyways. ;)
Of course, this is trusting Windows' security... :lol: And that's why I'll probably encrypt the folders later.

> **cdenley said:**
> Were you expecting NTFS permissions to be translated into Unix permissions and Windows users to be translated to Unix users?
No, not really. It would be great though! :mrgreen: I do understand that, in the presented scenario, that would have to be all in NTFS-3G's side (or at least through it) as I am granting NO access to Windows regarding Linux. And I do know NTFS-3G does NOT support it.

---

### Post by jdackle on 2008-12-14
Haven't had the time to look ah this sooner (I've just been accessing the paritions through GNOME in order to mount it on every session start...).

So, to start off, here's a question related to mount.ntfs-3g (not directly about it but directly related, yes). Its manual page says:> If ntfs-3g is set setuid-root then non-root users will be also able to mount volumes and via /etc/fstab if the 'user' or 'users' mount (8) option is specified.
So my first question is whether mount.ntfs-3g is setuid-root in my system or not.
```
ls -l /sbin/mount.ntfs-3g
lrwxrwxrwx 1 root root 12 2008-11-29 02:55 /sbin/mount.ntfs-3g -> /bin/ntfs-3g
```
```
ls -l /bin/ntfs-3g
-rwxr-xr-x 1 root root 36972 2008-05-30 17:49 /bin/ntfs-3g
```
I would say mount.ntfs-3g is NOT setuid-root, otherwise it would be something like lrw**s**rwxrwx, right?

P.s.: I do not want it to be setuid-root... I'm just checking with you guys... ;)

---

### Post by mssever on 2008-12-15
> **jdackle said:**
> ```
ls -l /bin/ntfs-3g
-rwxr-xr-x 1 root root 36972 2008-05-30 17:49 /bin/ntfs-3g
```I would say mount.ntfs-3g is NOT setuid-root, otherwise it would be something like lrw**s**rwxrwx, right?
That's correct.

---

### Post by jdackle on 2009-01-02
I got this working (not for particular folders, but for a whole partition). Only, there's something really weird about this setup... It is working alright but it's the way it works that is weird.

So, this is the line I added up to my /etc/fstab:> /dev/sda5	/media/Users	ntfs-3g uid=1000,gid=1000,umask=0007,relatime,streams_interface=windows,nodev,noexec,rw,errors=remount-ro,ownerAs you can see, I used the umask option to set the permissions for every file and folder in the partition (including its root directory). By looking at it, I'd say **the user and the group who own the mountpoint/partition have absolutely NO right to it**, no reading, writing nor executing/opening. However **all other users have all rights (read, write, execute)!**

But this is what I get on "ls -nd /media/Users":> drwxrwx--- 1 1000 1000 4096 2008-12-27 01:35 /media/Users/**It's the exact opposite!** So now you know why I set the umask that way... I'd initially set it up as 0770 - the result then was d------rwx !
So, basically, what is happening is the umask option is being read like this: the special bits (0---) are always unset (I haven't tried changing this but the following bytes makes me think it would be so). The User, Group and Others bytes are **INVERTED**! 7 turns to 0 and 0 turns to 7; 5(r-x) will turn to 2(-w-), I've tried it.

So it's working alright but I have to setup the umask inversely. Is there some hidden logic to this I'm missing? Or is this some sort of bug?

---

### Post by mssever on 2009-01-03
> **jdackle said:**
> So it's working alright but I have to setup the umask inversely. Is there some hidden logic to this I'm missing? Or is this some sort of bug?
You've discovered the correct behavior. The term "mask" is used for something that modifies something else. In this case, consider how the permissions get set on a newly-created file in a filesystem that understands Unix permissions: Normally, files are created with permissions of 0666 and directories with 0777. But, those permissions usually aren't desired. Enter the umask.* The bits of the umask are subtracted from the default permissions to produce the actual permissions that get set on a new file or directory. So, if you use the Ubuntu default umask of 0022, then a default file will have permissions of 0666 - 0022 = 0644.

When it comes to your NTFS example, since Windows filesystems don't support Unix-style permissions, the driver has to fake it. So it applies the umask you supplied in your fstab to the default permissions. Actually, that's not fully true. If my memory is correct, the umask applies across-the-board to both files and directories, which start with 0777 permissions before the mask is applied. But you can use fmask and dmask instead to control file and directory permissions separately. For example, to remove the x-bit from files, you can set the fmask to 0133 (or using your example, 0117) and the dmask to 0022 (or 0007) since directories are pretty useless without the x-bit.



* Type "help umask" for a brief description.

---

### Post by jdackle on 2009-01-03
Thanks a lot, mssever! Every answer I get from you is a well-worth "Thank you"! :D

Now to confirm your "guess":> **mssever said:**
> When it comes to your NTFS example, since Windows filesystems don't support Unix-style permissions, the driver has to fake it. So it applies the umask you supplied in your fstab to the default permissions. Actually, that's not fully true. If my memory is correct, the umask applies across-the-board to both files and directories, which start with 0777 permissions before the mask is applied.I can confirm both files and directories seem to start with 0777 permissions before the umask is applied. The _unmounted_ /media/Users permissions are: _drwxr-xr-x, hence, 0755_. Were these the original permissions the umask would act upon, the result would be _0750 or_, in case the result of the umask subtraction is _the absolute value, 0752_. But we've seen _the actual result is 0770_, so naturally the umask was subtracted _from 0777_. ;)

> **mssever said:**
> But you can use fmask and dmask instead to control file and directory permissions separately. For example, to remove the x-bit from files, you can set the fmask to 0133 (or using your example, 0117) and the dmask to 0022 (or 0007) since directories are pretty useless without the x-bit.That was a sweet bonus! :D I was actually considering searching about this or posting a new thread! :lol: It's quite obvious, actually, but I don't think I'd have thought of it myself...

Cheers! Have a Great 2009, mssever! \\:D/

---

### Post by mssever on 2009-01-03
> **jdackle said:**
> Now to confirm your "guess":I can confirm both files and directories seem to start with 0777 permissions before the umask is applied. The _unmounted_ /media/Users permissions are: _drwxr-xr-x, hence, 0755_. Were these the original permissions the umask would act upon, the result would be _0750 or_, in case the result of the umask subtraction is _the absolute value, 0752_. But we've seen _the actual result is 0770_, so naturally the umask was subtracted _from 0777_.
I couldn't tell from your post whether you understand this or not, so I thought I'd post it just in case: The permissions of the directory that serves as your mount point have absolutely no effect when you mount something on that directory. The permissions of the mounted filesystem supersede those of the mount point. In fact, the mount point technically doesn't even need to be empty. If you mount a filesystem on a non-empty directory, the directory's contents will become unavailable and the directory's permissions will be determined by the mounted filesystem. Once you unmount the filesystem, the directory's permissions and contents revert to what they were prior to mounting.

> Cheers! Have a Great 2009, mssever!You too!

---

