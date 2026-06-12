---
title: "Windows95 sharing folders in VirtualBox?"
date: 2009-05-30
forum: Virtualisation
---

### Post by col48 on 2009-05-30
Host: Ubuntu 8.04 Hardy
Guest: Windows95
Virtualiser: VirtualBox

W95 is not officially supported, but it works more or less in VirtualBox.  However GuestAdditions (including the facility to share folders between guest and host) is not available for W95 so in principle data sharing is limited to external or virtual media.

Searching the net for help led me to a blog by a guy called Murali which gave me a way of mounting the Windows 95 'hard disk' in the Ubuntu file system.  This means I can transmit more data from the guest to the host than can be fitted onto a [virtual] floppy.  Transmitting in the other direction was possible using a [virtual] CD.  I do not have a physical floppy drive nor does the W95 machine have the ability to write to a CD.

The key is to know that the Linux file which represents the virtual hard drive is simply a file system prefixed by a lump of VirtualBox data.

There is a [COLOR="Red"]WARNING[/COLOR] that this only works without sabotaging the guest if the Virtual drive was originally created as fixed size.  (If it is fixed size, the byte at offset 76 [hex 4c] will be 02 rather than 01)

The length of the lump of VirtualBox data will not change but apparently it may not be the same from one VM to another.  In my case it is 40960 (hex a000) of mainly zero bytes.  The start of the file system is recognised by seeing the text FAT16 in the interpretation.

I can mount the file system by
```
sudo mkdir /media/myw95

sudo mount -t vfat -o ro,noatime,noexec,loop,offset=40960 ~/.VirtualBox/HardDisks/W95VirtDisk.vdi /media/myw95


```
/media/myw95 is called the mount point and I think this can be anywhere in your file system.  Creating it need only be done once.

Note that the type in the mount command is vfat not fat16.

I observe the owner of the files on the guest's virtual disk as seen from the host is root, so there may be issues if I want to write from host to guest.  I have not tried this yet.

[COLOR="Red"]This information should be used with care, as there is obviously a risk that the guest could be clobbered, and I make no guarantees![/COLOR]  But anyone else with more knowledge is welcome to add to the thread.

I hope it is an encouragement to others to keep looking for solutions - someone may already have done something close enough to what you want and revealed all on a blog or a forum.

---

