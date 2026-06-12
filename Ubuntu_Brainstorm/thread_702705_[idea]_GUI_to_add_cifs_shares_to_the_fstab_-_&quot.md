---
title: "[idea] GUI to add cifs shares to the fstab - &quot;Map Network Folder&quot;"
date: 2008-02-20
forum: Ubuntu Brainstorm
---

### Post by maybeway36 on 2008-02-20
Many people like to be able to mount their Windows shares on the filesystem, so they can access documents and listen to music on the other computer. GNOME's "Connect to Server" seems like it should do this, but it does not - all it really does is make a shortcut; the share isn't mounted on the filesystem.
If this feature were implemented, it would essentially be Ubuntu's equivalent to the Windows "map network drive". All Linux programs would be able to access the share, even if they have no networking capability.
I would like to see this in Ubuntu by 8.10 (intrepid) at the earliest, but I don't think that's going to happen :\\

EDIT: Having a fusesmb GUI would be a good idea too. Also see: [brainstorm idea #48/]("http://brainstorm.ubuntu.com/idea/48/")

---

### Post by amlucent23 on 2008-02-20
+1,  I completely agree. I always run into this issue but never remember to suggest it.

---

### Post by mrsteveman1 on 2008-02-25
I agree.

Because most SMB browsers in Linux work without actually mounting anything it becomes difficult to work with network files. 

The kio:// stuff in KDE is a partial solution but a poor one in this case.

One thing that might help a lot is fusesmb, it blurs the line a bit between browsing and mounting but it does make the shares available on the filesystem itself.

Perhaps Ubuntu simply needs to include fusesmb by default and make an option in the GUI to turn it on, call it "Enable network browsing" and then include an icon for it on the desktop. Network shares would then have a definite mount point, but would not need to literally be mounted by hand.

---

### Post by Ms_Angel_D on 2008-08-29
Sorry for digging up this old thread, but It was the first result when I googled CIFS Gui. Anyway I just wanted to say I think this is a fantasic Idea, it's quite a pain to have to edit fstab by hand. Adding a GUI interface to it only makes sense.

---

### Post by damoxc on 2008-08-31
Installing gvfs-fuse does this partially, mounts the shares you connect to in .gvfs/....

---

### Post by maybeway36 on 2008-09-05
I would really like to see a cifs/fstab editor that connects a share on startup to somewhere in /media. I came up with this idea when my brother wanted to access his music library that was shared on another computer, and I had to edit the fstab manually.
I can't code anything except shell scripts, so someone else would have to actually do it (and I don't think any of the distros have yet.)

---

### Post by SoundFriend on 2008-09-06
I strongly agree, mounting server shares in Windows as local drives is so easy.

I am having no fun in mounting my server shares with Hardy desktop.  I used to have a working Feisty system once, but lost it.  

The correct settings in fstab elude me at present. The fstab format seems to have changed a bit as Ubuntu versions have changed.

John

D'oh, found the problem. SMBFS was not installed on the desktop.  Pity that the error reporting was a bit sparse: CIFS error 22

---

