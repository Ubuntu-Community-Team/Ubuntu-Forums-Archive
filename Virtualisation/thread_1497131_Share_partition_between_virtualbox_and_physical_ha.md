---
title: "Share partition between virtualbox and physical harddrive"
date: 2010-05-30
forum: Virtualisation
---

### Post by s990we on 2010-05-30
Is this possible?
I have windows 7 and ubuntu lucid on my harddrive, I have virtualbox on both OS, now is it possible to mount my ubuntu partition as a guest os in virtualbox (with windows 7 as host)?

I was able to mount an ext4 usb-hdd in a virtual ubuntu (with windows 7 as host) by "sending"? the usb connection to virtualbox, but i dont find any way to do this with an internal drive.

---

### Post by TheFu on 2010-05-30
> **s990we said:**
> Is this possible?
I have windows 7 and ubuntu lucid on my harddrive, I have virtualbox on both OS, now is it possible to mount my ubuntu partition as a guest os in virtualbox (with windows 7 as host)?

I was able to mount an ext4 usb-hdd in a virtual ubuntu (with windows 7 as host) by "sending"? the usb connection to virtualbox, but i dont find any way to do this with an internal drive.

If I understand what you want, I don't think it is possible. I think you'd like to dual boot into which ever OS you like and then mount the other OS file system for read-write access. That will work if you boot Linux, but I don't believe there are any "safe" EXT4 drivers available for MS-Windows. I could be wrong.

I'd suggest that you pick a host OS, then either reload or convert the other into a virtual machine to run as a client OS from inside a .VDI or .VMDK file.  You can minimize the client OS install to just a few GB (OS and programs) and leave most of the data on a partition controlled by the host OS. File security will be less, since you'll need to open the permissions for the client to use it and NTFS doesn't support the same permissions as any *nix file system. You'll use the built-in VirtualBox "Folder Sharing" for access by guest OSes and then mount the shared folder from inside the client using the normal method of the client (map a drive or mount using the vboxsf driver).

Or you could use samba and have both VM and physical machines running simultaneously.

---

### Post by s990we on 2010-05-31
Thats correct, but I dont want to mount the ext4 partition in windows (I know I cant do that) but rather somehow mount it directly in virtualbox. 

After I posted I installed ubuntu to a usb stick in virtualbox (w7 as host) and I can boot from it from a real computer, but virtualbox dont seems to be able to boot from a usb. 
But if I boot an alredy installed ubuntu then I can mount the usb in there. I just cant boot in virtualbox from it. 

And since this works on a usb memory it should be possible with a normal harddrive?

---

