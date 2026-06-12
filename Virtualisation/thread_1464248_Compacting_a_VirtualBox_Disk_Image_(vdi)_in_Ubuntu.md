---
title: "Compacting a VirtualBox Disk Image (vdi) in Ubuntu"
date: 2010-04-28
forum: Virtualisation
---

### Post by mdl4 on 2010-04-28
I noticed that a lot of the how-to's on this were outdated and contained incorrect details. Just thought I would pass this along. 

This is text only. Get the complete version (with screenshots) on my blog at [http://mdl4.com.]("http://mdl4.com")

Compacting a VDI
1. Start the virtual machine with the VDI you wish to compact. Delete all unnecessary files. At this point, I recommend running the Windows Disk Cleanup wizard. It can free up half a gigabyte or more in some cases.

Once you're finished cleaning up and deleting old files, right click the disk, click Properties &gt; Tools &gt; and the "Defragment Now" button. Click "Defragment."

Note: Be sure to defragment your disk several times (at least twice)

Once you're finished defragmenting, go to [Microsoft's Sysinternals Live Site]("http://live.sysinternals.com") and download the Secure Delete executable onto your virtual machine. Run it by opening a command prompt (Start > Run, then type cmd, and hit Run) and browsing to the download directory. Then, run it with the -z and -c options set.
C:\>sdelete.exe -z -c c:

-c is the most important, because it zeroes the free space on your VDI, allowing it to be compacted. It may take a few minutes.

When sdelete finishes and returns you to the command prompt, shutdown the virtual machine. When the machine has finished shutting down, open your terminal and run VBoxManage with the following flags:

$ VBoxManage modifyhd /_full_path_to/disk.vdi compact

Obviously, in place of _full_path_to, put the full path to the .vdi file you wish to compact. It should take a few minutes. When VBoxManage finishes, check the size of your file. It should be smaller. In my case, it was almost 6 GB (~ 50%) smaller. I needed to make my images smaller so I could back them up, in preparation for a big upgrade :)


VBoxManage is a very powerful tool, and it can be used to perform a number of management related tasks, including resizing and cloning disk images. The [VirtualBox User Manual]("http://download.virtualbox.org/virtualbox/3.1.6/UserManual.pdf") (pdf) can be found on the VirtualBox website.

---

### Post by mariolopezjr on 2010-04-28
Thank you for the great tutorial!

Do you mind if I post the tutorial on my forums and of course crediting you?

---

### Post by Dayofswords on 2010-04-28
i use 7zip on my vmware image to get to 21% of its size 
but great guide

---

