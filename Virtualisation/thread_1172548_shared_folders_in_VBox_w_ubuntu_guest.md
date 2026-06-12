---
title: "shared folders in VBox w/ ubuntu guest"
date: 2009-05-28
forum: Virtualisation
---

### Post by georgec32 on 2009-05-28
I see threads on sharing folders from ubunto host to windoze guest in Sun VBox but I need to go the other way.  

I have a guest Ubuntu 8.10 OS running under a Windows XP SP3 host.  I'm using a Compaq 6910p laptop and I have Sun VBox 2.2.2 installed on a 250Gb FAT32 USB external drive, and also have the ubuntu virtual machine on the USB HD.  I installed the VBoxGuestAdditions.iso.  I can add the USB HD shared folder (called U:SunVbx/Shared) using the 'Devices' button in the virtual machine.  I put it under 'machine folders' as permanent and I have all permissions.  I can't see any of the files I put into that folder from XP.  The folders are already created, both in windows (U:SunVbx/Shared) and in guest Ubuntu (/home/george/Shared)

I tried opening a terminal window and typing:  

sudo mount -t vboxsf U:SunVbx/Shared /home/george/

but I get an error that says:  

/sbin/mount.vboxsf: mounting failed with the error: Protocol error

Any ideas for what I might be doing wrong?  


georgec32

---

### Post by benerivo on 2009-05-28
In the Virtualbox settings, where you set up the shared folder, it is given a name which is all i think you need in the first part of the command (eg  i have my host's /media/Storage/Music shared and the share name is just Music). Then just create the mount point in the guest as you have done, and this command works for me...```
sudo mount.vboxsf Music /home/ben/Music
```

---

### Post by georgec32 on 2009-05-28
> **benerivo said:**
> In the Virtualbox settings, where you set up the shared folder, it is given a name which is all i think you need in the first part of the command (eg  i have my host's /media/Storage/Music shared and the share name is just Music). Then just create the mount point in the guest as you have done, and this command works for me...```
sudo mount.vboxsf Music /home/ben/Music
```

Thank you!  It worked just fine, following your suggested command. 

One more question .. do I have to do this every time I start the virtual machine?  I just restarted ubuntu VM and had to type this command in again.  I could do a shell or something, but is there any way to make this permanent?  I selected permanent when I defined the shared file, but it doesn't seem as permanent as I would have hoped :)

nice hat BTW ..

---

### Post by benerivo on 2009-05-28
> **georgec32 said:**
> ...do I have to do this every time I start the virtual machine?  I just restarted ubuntu VM and had to type this command in again.  I could do a shell or something, but is there any way to make this permanent?  I selected permanent when I defined the shared file, but it doesn't seem as permanent as I would have hoped :)
nice hat BTW ..You can add a line to /etc/fstab in the guest to mount it automatically. It would be something like...```
Music /home/ben/Music vboxsf defaults 0 0
```This is definitely possible, but my line above may have an error.

---

### Post by georgec32 on 2009-05-28
> **benerivo said:**
> You can add a line to /etc/fstab in the guest to mount it automatically. It would be something like...```
Music /home/ben/Music vboxsf defaults 0 0
```This is definitely possible, but my line above may have an error.

very cool .. it worked :D  Thanks!

---

