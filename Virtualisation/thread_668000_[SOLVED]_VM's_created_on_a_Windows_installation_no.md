---
title: "[SOLVED] VM's created on a Windows installation not running on Ubuntu"
date: 2008-01-14
forum: Virtualisation
---

### Post by Udaho on 2008-01-14
I am trying to get VM's created in a windows version of VMware server 1.04 to open in VMware server on my Ubuntu gutsy box. I installed the VM's on a portable hard drive so I could take them back and forth between the two computers.

When I brought home my portable hard drive to open them I was able to add them to my inventory by clicking "Open a virtual machine" and browsing to the .vmx files but when I try to power them on the VM's flash the black screen and then close, apparently unable to POST.

When I look at the log it shows this as the error it first and repeatedly encounters:

"FILEIO: Unknown filesystem 0x65735546 for directory /media/Backup/Win_Server_2003_Standard. Using non-linking locking."

The VM's are server 2003. This seems like it would be a common enough scenario but I have had little luck with googling it. Any thoughts would be much appreciated.

---

### Post by Udaho on 2008-01-14
Success! After a little more searching I seem to have found the solution.

You must add a line to the .vmx file. I just navigated to it and opened it with a text editor. I then added the line:

mainMem.useNamedFile = "FALSE"

After I saved and closed the file the VM booted up correctly.

---

