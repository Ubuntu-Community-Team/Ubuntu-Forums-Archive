---
title: "Error in Sun Ent 450 - Installation"
date: 2007-12-24
forum: Sun Sparc Users
---

### Post by Lacroix on 2007-12-24
Currently this is what I have:

**Sun Enterprise 450 Server** (4x ultrasparc-II 400 mhz, open boot 3.16 2048 MB memory)

I've tried installing with Ubuntu 7.10 64-bit but got these error after Stop + A , boot cdrom :

Bad magic number in disk label
Can't open disk label package
Can't open boot device.


**[COLOR="Red"]Any solution/s? Need help. Urgent[/COLOR]**

---

### Post by Par E Liljergren on 2008-01-03
Hi,

You need to get hold of a Sun Solaris installation cd (first cd) and boot from it with the command:

boot cdrom -s (now you will be booted into single user mode)
At the prompt that appears after a while type in:
# format

Now you will see some information about your disk or an error message stating that they are wrong labled. When you are asked to select a disk do select the first one (0) and then type the command

> Label

Just accept to label the disk by pressing "y" to the question if the system should re-label it. After that is done you type the command:
>Disk 

and select the next disk and repeat the steps made with the first disk. You just keep going on until all disk has been re-labeled. 

Hopefully, it will work now to install Ubuntu. I have succeded on my SUN Enterprise 450 Server. I have another one to fix too so it will run Ubuntu. 

Hope this can help you.

Kind regards
Perry

---

