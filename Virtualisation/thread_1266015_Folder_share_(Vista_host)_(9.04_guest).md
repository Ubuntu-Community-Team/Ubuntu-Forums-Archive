---
title: "Folder share (Vista host) (9.04 guest)"
date: 2009-09-14
forum: Virtualisation
---

### Post by olymacfoogal on 2009-09-14
Hi all,

Ok I've been looking hard for an answer to this, I am extremely newbish. I have set up a shared folder, I selected it by clicking devices, folder sharing and selecting a file in the host that i want to share. I then checked the virtual box manual for how to mount this into ubuntu and failed to understand how to do it!

I tried this: mount -t vboxsf [-o OPTIONS] sharename mountpoint

but it gave me a manual on what mount means...

I checked the forums but everyone seems to have ubuntu as the host and windows as the guest. 

Please help!

---

### Post by Perryg on 2009-09-15
When sharing a folder you must make sure that it does not contain spaces or illegal characters.  Then in a terminal you need to create a mount point and then run the mount statement.  See example below.

```
sudo -i <password>
mkdir /mnt/<sharename>
mount -t vboxsf <sharename> /mnt/<sharename>
```

Replace <sharename> with the actual name you gave the share.
Also adding this to the /etc/rc.local file will mount it every time you boot the guest.
```
mount -t vboxsf <sharename> /mnt/<sharename>
```
Again replace the <sharename> with the actual name you gave the share.

---

### Post by olymacfoogal on 2009-09-16
Thank you thank you thank you!!!

---

### Post by olymacfoogal on 2009-10-07
This works really well but to try and make it easier to access it I mounted it in: 

/home/<myname>/<sharename>

This means I could drag and drop on the ubuntu side without using the cmd line.

However I do not have permission to write to the folder. Because 'root' created the folder I tried to give 'me' permission to write to it by:

chmod o+w /home/<myname>/<sharename>

This seemed to work but once I mounted it it became roots again and I could not write to it... any ideas?

At the minute I have to sudo copy to and from the folder, which is easy I suppose but would it be nicer to drag and drop :)

---

