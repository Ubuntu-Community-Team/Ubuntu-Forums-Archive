---
title: "[SOLVED] (virtualBox) Adding another virtual partition - can't get it to show in virt"
date: 2008-03-14
forum: Virtualisation
---

### Post by Arizon_Dread on 2008-03-14
Hey all you almighty virtualizers out there.

So, I've got a small problem. 

I have created a virtual XP machine through VirtualBox.
The problem is that I originally made the partition too small (only 8 GB) and I realized that .NET framework and visual studio takes up SPACE. so, I tried to change the maximum dynamic size, but couldn't figure out how (nvm the resizing shizzle, i found this: [http://ubuntuforums.org/showthread.php?t=634880](http://ubuntuforums.org/showthread.php?t=634880)
it's more hazzle than removing and redoing, so, just let me know how to get the new partition to show in the virtual OS.
) so I figured I'd add another partition of 6 GB for data (if I store the data on another partition, I can fit visual studio and all that jazz on the original partition)


this is a printscreen of the problem:

[http://i101.photobucket.com/albums/m67/_nudie/Screenshot-1.png](http://i101.photobucket.com/albums/m67/_nudie/Screenshot-1.png)

---

### Post by Hero of Time on 2008-03-14
I think the problem is that the hard disk gets the same drive letter as your virtual cd (not the one assigned by VBox). Check the computer management console (right mouse on My Computer then select Manage) and change the drive letter or assign one. See attachment.

---

### Post by Arizon_Dread on 2008-03-14
thanx, it was unallocated, so I just made a partition of it and it seems to work.

---

### Post by Hero of Time on 2008-03-14
Makes sense. After all, it's like placing a new hard drive in the computer and it never has a partition.

---

