---
title: "Shared Folder in Virtualbox -can it be shown as a real hard drive, NOT network drive?"
date: 2014-04-30
forum: Virtualisation
---

### Post by Toupee on 2014-04-30
Hi guys!  Back on the Linux train with Kubuntu 14.04 this time.  So far so great, I'm virtualizing Win 8.1 to get my Adobe CS apps and it's working great.  Now I'm just dealing with getting all my files easily accessible.

For work, I use Box.com sync, which works a lot like Dropbox.  Unfortunately, I'm running into some issues with the Windows applet. When I set the folder I want it to sync with (it already exists on my 2TB hard drive), it complains that it only supports NTFS and HFS file systems.  Of course this must be because it sees my shared folder as a network drive.

[IMG]http://i.imgur.com/yCIFer7.png[/IMG]

I could have it sync to a new folder inside the vbox image, but I don't want that.  I want to be able to access it inside kubuntu, as well, and I'll probably need to boot into regular windows from time to time.

I think the simplest way would be to have the shared folder appear as a regular hard drive in Windows, NOT a network drive.  Is this possible?

Thanks in advance!

---

### Post by TheFu on 2014-05-03
I don't know the answer, but since nobody else as responded, I'll throw out a few ideas. The vboxsf driver leaves much to be desired. I've had issues with editors refusing to work because the file locking is sub-par. Don't get me started about the file permissions issues.

Either create another vHDD for the VM  - that's another VDI file.
Or
Create a block device on the hostOS for iSCSI storage and share that. Inside Windows, connect to the iSCSI server, then treat the remote storage as a local vHDD.
Or 
Perhaps an NFS share wouldn't be caught by Adobe? If your Windows has NFS capability, try that. Enterprise and Ultimate do.
Or
Move the files inside the VM (as above), but create a network share (CIFS or NFS) from the VM out onto the network. This should be fine for view-only needs or editing of standard image files.

Neither of these methods is ideal since both require a "format" and data to me moved/copied into the new storage locations.
[This]("https://help.ubuntu.com/community/VirtualBox/SharedFolders") might help too. I didn't read it.

BTW, the best source of information on virtualbox is the virtualbox forums and their documentation. Have you tried there?

Regardless, I hope this provides options to try.  Not using proprietary software would be much easier, I suspect.

---

### Post by Toupee on 2014-05-05
Thanks TheFu, I really appreciate the reply and the ideas.

I just had another idea.  Perhaps I can make a symlink from the virtual hard disk to the real folder.  It would require twice as much space, but my total cloud storage is under 50GB, so I could probably spare it.

I did just move my virtualbox image to my SSD to see how performance improves.  I could create another virtual disk on the ol' 2TB HDD to try this symlink thing, though.

Thanks so much!  And I'll try the virtualbox forums too.

---

### Post by CharlesA on 2014-05-06
The way shared folders is designed, it will not show up as a local drive.

---

