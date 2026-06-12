---
title: "Serious bug in VirtualBox 3.0 - file permisions messed up in shared folders!"
date: 2009-07-02
forum: Virtualisation
---

### Post by yesint on 2009-07-02
Dear All,
I've upgraded VirtualBox to 3.0 and immediately went into serious trouble. I have Ubuntu 9.04 host and WinXP guest. If I open a file in MS Word, which is located in the shared folder (physically located on Ubuntu host) and then save it. After save the permisions for this file become -r-------- regardless of initial permissions!
As a result the next save fails with the message "the file is read-only". It is said that this bug was already fixed in 3.0beta, but it does not!!!

---

### Post by bkraptor on 2009-07-02
You can temporarily fix it by chmod u+rw filename in a terminal on the host.

---

### Post by Perryg on 2009-07-02
I just tested this and  it retains the permissions for me.  I do not have Word on the Windows XP guest but did use wordpad.  Can you send me the bug ticket that you are referring to so I can check it out for you?

---

### Post by yesint on 2009-07-04
> **Perryg said:**
> I just tested this and  it retains the permissions for me.  I do not have Word on the Windows XP guest but did use wordpad.  Can you send me the bug ticket that you are referring to so I can check it out for you?

The closest one is probably #3785 and a bunch of related bugs. I also posted this problem to VirtualBox forum and some other troubles seem to exists as well [http://forums.virtualbox.org/viewtopic.php?f=2&t=19465](http://forums.virtualbox.org/viewtopic.php?f=2&t=19465)

---

### Post by yesint on 2009-07-04
> **bkraptor said:**
> You can temporarily fix it by chmod u+rw filename in a terminal on the host.

Try doing this each time when you want to save changes in your text and you'll understand the "usefulness" of this workaround :)

---

### Post by Perryg on 2009-07-04
What are you using for your mount statement?
I found that the best way was to put the mount in the rc.local file see below.

mount -t vboxsf -o rw,gid=1000,uid=1000 Shared /mnt/Shared

Where Shared is the share name you used in VBox and the complete path to the mount.  uid & gid are your numbers.  
Check them by running id in terminal, but they should be 1000 if this is the original install login you used.

---

### Post by yesint on 2009-07-05
> **Perryg said:**
> What are you using for your mount statement?
I found that the best way was to put the mount in the rc.local file see below.

mount -t vboxsf -o rw,gid=1000,uid=1000 Shared /mnt/Shared

Where Shared is the share name you used in VBox and the complete path to the mount.  uid & gid are your numbers.  
Check them by running id in terminal, but they should be 1000 if this is the original install login you used.

I created shares using VrtualBox GUI and then enabled them in the guest with "net use x: \\vboxsvr\share-name"
I can't see how this can make any difference with permissions...

---

### Post by Perryg on 2009-07-05
Ooops, Sorry I had it backwards.  Your guest is Windows.  I have a notebook that I use for Ubuntu and run XP on it and the home system is Vista with Ubuntu on it.  That way I can test both directions.  I have tested this though on my system and do not have this problem, so what we need to do is see what the difference is.  One thing that sticks out is the share name with the - in it.  While this should not matter to Windows it does mess with Linux.  Could you try to change the name and remount and see if this changes anything.  Also no caps, or special characters in the share name.  Also what is the mount point (folder) that you are sharing?  Is it a folder in your home folder?  Does the VBox user have full rights to this folder?

---

### Post by yesint on 2009-07-06
> **Perryg said:**
> I have tested this though on my system and do not have this problem, so what we need to do is see what the difference is.

I suspect that this bug is "bad" in the sense that it only pops up in specific conditions. However, it is already confirmed [http://www.virtualbox.org/ticket/4381](http://www.virtualbox.org/ticket/4381) and it seems to affect mostly MS Office programs.

> **Perryg said:**
> One thing that sticks out is the share name with the - in it.  While this should not matter to Windows it does mess with Linux.  Could you try to change the name and remount and see if this changes anything.  Also no caps, or special characters in the share name.  Also what is the mount point (folder) that you are sharing?  Is it a folder in your home folder?  Does the VBox user have full rights to this folder?

The name of the share is just "work". The path in the host is "/home/semen/work" - nothing confusing.

---

### Post by stickleback99 on 2009-07-06
Does the same for me too!
Thanks yesint for highlighting this bug, it was driving me nuts.
I don't have any NTFS partitions so I can't say wether or not it behaves ok with these (as the report from your link suggests).
However on my shared folders (which happens to be Ubuntu /home)  within an MS Word the first save of a new file is ok, any further attemts to save render the file read only.
If I open an exiting file in my shared folder with MS Word it makes it read only immediately.

---

### Post by tvtech on 2009-07-06
[COLOR="Red"]Work Around for this bug[/COLOR]

If you have an instance of Nautilus open on your host to the directory which your files are stored permissions do not get altered by your guest.  Kind of irritating.  But it works!

let me know if anyone else has success with this.  I got it to work in Gnome and KDE installs of Ubuntu 9.04 kernel 2.6.28-13  vbox 3.0.0

---

### Post by tvtech on 2009-07-06
This [COLOR="Blue"][bug report]("http://www.virtualbox.org/ticket/4381#comment:3")[/COLOR] has been filed at virtual box.  

This [COLOR="Blue"][thread]("http://ubuntuforums.org/showthread.php?t=1202151")[/COLOR] also contains information pertaining to this problem. 

This bug doesn't appear to affect any other products beyond MS, and some MS visual studio save/loads.  Notebook by MS and Autocad by Autodesk do not appear to have a problem with the permissions being re-assigned for owner/group.  When reading writing to a shared EXT3-4 file system via an Windows XP guest.  As noted above if Nautilus is actively open in the host file permissions do not get modified by guest os file operations.

Has anyone had any luck confirming this problem on a file system other than EXT3-4 or with a program suite other than Microsoft office?  It appears to affect ALL MS office 2007 products.  If you are having a problem with this please upload you Virtualbox .log file to the [COLOR="Blue"][bug report.]("http://www.virtualbox.org/ticket/4381#comment:3")[/COLOR]

---

### Post by yesint on 2009-07-06
> **stickleback99 said:**
> Does the same for me too!
Thanks yesint for highlighting this bug, it was driving me nuts.
I don't have any NTFS partitions so I can't say wether or not it behaves ok with these (as the report from your link suggests).
However on my shared folders (which happens to be Ubuntu /home)  within an MS Word the first save of a new file is ok, any further attemts to save render the file read only.
If I open an exiting file in my shared folder with MS Word it makes it read only immediately.

Thanks for confirming this! Despite the confirmed bug ticket I still suspected that I did something wrong during update to 3.0.0.
My suggestion right now is to revert back to 2.2.4 and to wait for the patch because this bug really stops all work with the shares. 
The workaround with open Nautilus is a kind of arcane magic :) I can't even imagine why this helps, but anyway if you forget to open Nautilus in *all* folders, which you plan to use, you'll screw up the permissions. Imho, its better to revert to 2.2.4 if you use shares a lot.

---

### Post by tvtech on 2009-07-07
> **yesint said:**
> Thanks for confirming this! 
The workaround with open Nautilus is a kind of arcane magic :) I can't even imagine why this helps, but anyway if you forget to open Nautilus in *all* folders, which you plan to use, you'll screw up the permissions. Imho, its better to revert to 2.2.4 if you use shares a lot.

[COLOR="Red"][SIZE="4"]We have affected change[/SIZE][/COLOR] Barak Obama would be so proud of us.  They "the kind coding gurus at virtualbox" have fixed it in the SVN already and it will make be in the update for 3.0.0 when it's stable and released.  I think your right on the revert for 99% of people.  I think it might actually be a bug in Nautilus preventing a group/owner from modifying a files permissions via a share when nautilus is actively previewing the file.  But it solved my issue until 3.0.0 is updated.

---

### Post by yesint on 2009-07-10
> **tvtech said:**
> I think it might actually be a bug in Nautilus preventing a group/owner from modifying a files permissions via a share when nautilus is actively previewing the file.  
This is possible. Using one bug to prevent another bug is really cool :)

---

### Post by Perryg on 2009-07-11
Try Version 3.0.2 released yesterday.  Change log says that it has been fixed again.

---

