---
title: "Separate Home Parition Worth it?"
date: 2011-10-11
forum: The Cafe
---

### Post by mamamia88 on 2011-10-11
I've tried it before with a fresh install and had problems with proper icons and backgrounds loading.   Do you think it's worth it as long as I have all my music on 2 different mp3 players and backup my documents on external drive before installing?

---

### Post by kaldor on 2011-10-11
If you intend on doing a lot of fresh installs or distro hopping, then yes. If not, then I see no reason to bother.

---

### Post by mamamia88 on 2011-10-11
Would a separate data partition be a better idea?  That way I can have 1 central location for windows and linux data?  I still boot into windows for when I have to use excel and would be nice to only have 1 copy of my files on the computer

---

### Post by lincoln32 on 2011-10-11
usually I do use /home so I can reinstall or swap OS's but I usually end up 
doing fresh install anyway. just remove any file with .XXXXX in /home and then you will only save your files not all the OS stuff but then I usually decide to clean it all and copy what I want to the my server so it is a waste for me to use /home but I do it anyway:p

---

### Post by Elfy on 2011-10-11
This was recently mulled over - [http://ubuntuforums.org/showthread.php?t=1854501](http://ubuntuforums.org/showthread.php?t=1854501)

---

### Post by Morbius1 on 2011-10-11
> **mamamia88 said:**
> Would a separate data partition be a better idea?  That way I can have 1 central location for windows and linux data?  I still boot into windows for when I have to use excel and would be nice to only have 1 copy of my files on the computer
A separate data partition sounds like a good idea to me. You can even "bind" portions of the partition to your home folder. For example:

Let's say you create a data partition formatted in NTFS ( and I would do this in Windows btw ) and mount it automatically to /WinD in fstab:
```
UUID=DA9056C19056A3B3 /WinD ntfs defaults,nls=utf8,dmask=000,fmask=111,uid=1000,windows_names 0 0
```Then create a set of subfolders in /WinD like: Documents, Pictures, Downloads, etc...

Then bind /WinD/Pictures to /home/username/Pictures:
```
sudo mount --bind /WinD/Pictures /home/username/Pictures
```You can set up your own upstart job to have all these "binds" start on boot automatically ( POST #41 ): [http://ubuntuforums.org/showthread.php?p=10899012#post10899012](http://ubuntuforums.org/showthread.php?p=10899012#post10899012)

You can also do this with symlinks but I personally hate symlinks ;)

---

### Post by mamamia88 on 2011-10-11
> **Morbius1 said:**
> A separate data partition sounds like a good idea to me. You can even "bind" portions of the partition to your home folder. For example:

Let's say you create a data partition formatted in NTFS ( and I would do this in Windows btw ) and mount it automatically to /WinD in fstab:
```
UUID=DA9056C19056A3B3 /WinD ntfs defaults,nls=utf8,dmask=000,fmask=111,uid=1000,windows_names 0 0
```Then create a set of subfolders in /WinD like: Documents, Pictures, Downloads, etc...

Then bind /WinD/Pictures to /home/username/Pictures:
```
sudo mount --bind /WinD/Pictures /home/username/Pictures
```You can set up your own upstart job to have all these "binds" start on boot automatically ( POST #41 ): [http://ubuntuforums.org/showthread.php?p=10899012#post10899012](http://ubuntuforums.org/showthread.php?p=10899012#post10899012)

You can also do this with symlinks but I personally hate symlinks ;)

 That sounds like a great idea.  What I am thinking of though is like 20gb win 7 20gb ubuntu and everything else as a shared ntfs partition.    I would store everything of importance on that partition.  Any reason that wouldn't work out well?

---

### Post by Morbius1 on 2011-10-11
I don't know about the relative size of each of those partitions but one note of caution:
>    I would store everything of importance on that partition.If that means documents, pictures, etc then that's fine since you're mounting the partition with you as owner and any file you add to them will also be owned by you.

But NTFS partitions don't preserve Linux file permissions so if you do a backup of certain files like fstab, smb.conf, etc.. without creating an archive like a tar file then the original permissions on those will be lost. 

You might consider adding an additional Linux Data partition for those type of things.

---

