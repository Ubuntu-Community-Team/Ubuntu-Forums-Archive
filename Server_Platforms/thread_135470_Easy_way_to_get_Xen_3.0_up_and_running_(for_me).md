---
title: "Easy way to get Xen 3.0 up and running (for me)"
date: 2006-02-23
forum: Server Platforms
---

### Post by j-a-p on 2006-02-23
I have been playing around with Xen lately and being a bit of a noob I struggled. Anyway I was persistent and now have Xen up and running and it was relatively easy.

I used the Xen 3.0.1 source package.

After extracting the tarball I ran:

```
make xen
``` 
then

```
make tools
``` 
I edited the Makefile in the top level directory of the xen-3.0-1 directory.  I changed the following line:

from
```
KERNELS ?= linux-2.6-xen0 linux-2.6-xenU
``` 
to
```
KERNELS ?= linux-2.6-xen
``` 
The I issued then command:

```
make world
``` 
Apparently using the xen0 and xenU kernels are not really appropriate for your regular distro, but the xen kernel compiles configured with all you need. I have sound working, which was a problem for me.

I entered the linux-2.6.12.6-xen directory then ran

```
make modules
``` ```
make modules_install
``` 
After this I created an initial ram disk:

```
mkinitramfs -o /boot/initrd.img-2.6.12.6-xen
``` 
Then I changed the grub menu.lst file to add an entry appropriate to xen and the xen-linux kernel and initrd:

```
title    Xen 3.0 / XenLinux 2.6
kernel    /xen-3.0.1.gz  
module    /vmlinuz-2.6.12.6-xen root=/dev/hda6 ro console=tty0 
module    /initrd.img-2.6.12.6-xen
``` 
Then I rebooted and it worked.  There were some errors with dependencies, so I ran:

```
depmod 2.6.12.6-xen
``` 
which seemed to sort this out.

The other problem I had was not being able to mount partitions on my 2nd hard disk (/dev/hdbn)

I discovered that if I removed EVMS it was resolved.

```
apt-get remove evms
``` 
I know this is not a very good guide and it is from memory, but I thought I would just get the basics out to those who have suffered (like myself) getting xen running. I now have a desktop which functions as a regular Breezy machine but with the added luxury of being able to run virtual machines too.

I have noticed no difference in performance as of yet and I wouldn't even know I was running a xen machine. I intend to get into this a lot more and since I am learning python presently I thought I may embark upon a GUI to manage the xen guests as I can't find a GUI anywhere for xen.

If anyone is interested in this I am prepared to give a more detailed explanation of what I did. Also you have any suggestions please let me know.

---

### Post by j-a-p on 2006-02-23
Just a quick note, I'm no kernel expert and am only experimenting with compilation, so my methods may not be strictly correct.  Most of what I learnt was from running make help!

---

