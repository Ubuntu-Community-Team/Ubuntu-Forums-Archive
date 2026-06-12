---
title: "Failed Raid Array"
date: 2010-02-22
forum: Server Platforms
---

### Post by scowcron on 2010-02-22
A friend of mine (running Debian Lenny) has recently had some issues with a drive dying in the raid array in his server. We've been digging around without much luck. Any help would be greatly appreciated.

Extended details are posted here: [http://lug.mtu.edu/pastebin/121]("http://lug.mtu.edu/pastebin/121")

---

### Post by kidders on 2010-02-23
Hi there,

According to the debug info you supplied, the array is fine, but there's something fairly low-level wrong with one of the component disks. For example the device could be dying, a cable could be dodgy, or there could be some sort of problem with the motherboard or PSU.

I'd suggest ...[LIST]
[*]Take a quick look at /raid to make sure your friend's stuff is still there (ie the filesystem is still OK) & unmount it.
[*]Remove any references to /ntfs in your /etc/fstab. It seems odd that it would mount if you don't know what it is, so I suspect there's something in your fstab that shouldn't be.
[*]Unplug the dodgy disk & reboot. Hopefully, the ATA bus errors will go away. Assuming they do, you could work on trying to figure out where the problem is by a process of elimination (eg swap around some power leads, data cables, hard disks, and so on).
[/LIST]

Remember to be careful with the array though -- you'll lose the whole thing if anything happens to another disk, or it falls out of sync for some reason -- don't use any of its disks to experiment on!

Also, just for future reference, it can be helpful to use **dd** to erase the first few megabytes of a device/partition, when you change its role. That way, you can destroy metainformation you're no longer interested in (eg NTFS filesystem headers), and prevent accidental screw-ups/confusion.

I hope that helps.

---

