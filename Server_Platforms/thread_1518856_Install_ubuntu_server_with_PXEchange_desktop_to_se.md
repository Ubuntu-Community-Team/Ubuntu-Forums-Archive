---
title: "Install ubuntu server with PXE/change desktop to server"
date: 2010-06-27
forum: Server Platforms
---

### Post by Cyber1000 on 2010-06-27
Hi everybody, new to ubuntu, new to this forum!
I came to linux a couple of years ago, starting off with fedora, also learned it at university, so no newbie neither with GUI nor commandline. I always deployed fedora with pxe. (with a tiny tftp-"server" on my dd-wrt-rouer)
 
So now to the point :-): 
For now I want to set up an ubuntu-server. (version 10.04 as fileserver)
I have seen the pxe-install and downloaded it and it worked without any problem out of the box like fedora does. But I didn't read that the pxe-install seems only to exist for the desktop edition. doooh ...
 
My questions:
**Is there a way to install server edition with PXE?**
On [https://help.ubuntu.com/10.04/serverguide/C/preparing-to-install.html](https://help.ubuntu.com/10.04/serverguide/C/preparing-to-install.html) it appears to me that the main difference to the desktop-edition is the kernel. So I have also run the command:
```
sudo apt-get install linux-headers-server linux-image-server linux-server
```
It seems to work fine, now loads the server kernel and my nfs-datatransfer is measurable faster. 
Can I go with this installation? There is no gui installed, but openssh, nfs, samba, ftp, unison (dual way file sync) and the server-kernel.** Can I say for now that I have a server-installation** or are there any other significant differences between server and desktop version (besides the kernel)?
 
Thanks for your help.

---

### Post by vikjon0 on 2010-10-25
I think the only diff between the client and server is the kernel. The server kernel is optimized for server hw and I guess if it is working it does not matter.

---

### Post by Cyber1000 on 2011-02-07
I know it is an old thread (actually it's "my" old thread :-) ). Just stumpled about it for now. Just wanted to say that this works without any problems. At least I haven't seen one this far. Just be sure to remove the "desktop kernel" after you have confirmed your server-kernel works (use grub to boot from the server kernel). Fortunately I had a repairdisk by hand :-)

---

