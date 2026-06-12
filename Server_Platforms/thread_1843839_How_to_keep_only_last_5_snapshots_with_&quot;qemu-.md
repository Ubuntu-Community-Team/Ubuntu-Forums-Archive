---
title: "How to keep only last 5 snapshots with &quot;qemu-img snapshot&quot;?"
date: 2011-09-14
forum: Server Platforms
---

### Post by toshko3 on 2011-09-14
Does anyone know a way?
Or the only way is to create snapshots with date as name and delete the last with a script? Because this would be tricky.
I want to know if there is a simpler way.
Thanks! :popcorn:

---

### Post by rubylaser on 2011-09-14
Deleting all but the five most recent wouldn't be too hard.  If you're writing all your snapshots out to a consistent directory, you'd just need to do something like any of [these]("http://stackoverflow.com/questions/25785/delete-all-but-the-most-recent-x-files-in-bash").

---

### Post by kevinthecomputerguy on 2011-09-14
If its using vzdump, you can add a file named vzdump.conf to the /etc directory, with this entry.

#/etc/vzdump.conf
maxfiles:5

---

### Post by rubylaser on 2011-09-14
vzdump is dead simple and that's what I use on Proxmox for my backups, but if he's fimiliar with qemu-img, a simple bash script should do it.

---

### Post by toshko3 on 2011-09-20
Thanks for the replies, but the problem is that I do the snapshots inside the .img file itself. So as I understood the only way to manage them is with qemu-img. The problem is that this command is too simple to do anything like this and therefore I have to make a script with some grep and other fancy bullsh**s to do the job. Unfortunately the snapshots are not files outside the image.:(

---

### Post by rubylaser on 2011-09-20
I'm not sure what you mean. I'm not going to be able to help you much, as I'm using vzdump on Proxmox to handle all my snapshot needs.  It creates an individual vm img file for each snapshot.

---

### Post by toshko3 on 2011-09-21
Thanks, but this is not what I want. I use qemu and kvm on clean Ubuntu server 10.04.3. I have read about problems/bugs when doing a live snapshot (when the machine is running), so I use the most stable way:

virsh shutdown virtualmachinename
qemu-img snapshot -c snapshotname /media/images/vda1.img
virsh start virtualmachinename

There is no problem of shutting down the machine between 19.00 and 6.00AM, so I prefer this as the most secure way of doing a snapshot. This command does the snapshot in the main (and only one) image file. I use qcow2 as image format and maybe this is the reason (because it can). Maybe if I use raw images it will create another external file for every snapshot, I don't know.
If anyone with experience could help... please!
Thanks!

---

### Post by rubylaser on 2011-09-21
> **toshko3 said:**
> Thanks, but this is not what I want. I use qemu and kvm on clean Ubuntu server 10.04.3. I have read about problems/bugs when doing a live snapshot (when the machine is running), so I use the most stable way:

virsh shutdown virtualmachinename
qemu-img snapshot -c snapshotname /media/images/vda1.img
virsh start virtualmachinename

There is no problem of shutting down the machine between 19.00 and 6.00AM, so I prefer this as the most secure way of doing a snapshot. This command does the snapshot in the main (and only one) image file. I use qcow2 as image format and maybe this is the reason (because it can). Maybe if I use raw images it will create another external file for every snapshot, I don't know.
If anyone with experience could help... please!
Thanks!

I'm not sure where, you read about hanging, if you're running your vm in LVM, the snapshot happens without interrupting the virtual machine at all using LVM's snapshot feature.  This is the most stable way to do a snapshot and why Proxmox uses that as it's snapshot method.

What you're doing isn't really a snapshot, it's an offline backup and wouldn't be acceptable in a production environment.  Sounds like you're trying to do something atypical and that's why you're not getting any responses.  I wish you luck, but I really would investigate [vzdump]("http://pve.proxmox.com/wiki/Backup_-_Restore_-_Live_Migration") and online snaphots further, they work great.

---

### Post by toshko3 on 2011-10-18
Well, thanks for vzdump, but I don't want to use neither LVM nor consistent backups. I need snapshots without LVM.

---

### Post by toshko3 on 2011-10-18
Also I don't (as many others, I believe) want to use any fancy solutions like proxmox. I want a clean "Ubuntu server" environment.

---

### Post by toshko3 on 2011-10-18
This is an example of why I don't want to do the snapshot online:
[http://www.spinics.net/lists/kvm/msg59377.html](http://www.spinics.net/lists/kvm/msg59377.html)

---

### Post by toshko3 on 2011-11-24
Anyone?:(

---

### Post by toshko3 on 2011-12-13
Am I the only one who is going to do this??? :?

---

