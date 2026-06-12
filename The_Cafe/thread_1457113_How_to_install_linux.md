---
title: "How to install linux?"
date: 2010-04-18
forum: The Cafe
---

### Post by m4tic on 2010-04-18
I read in the early days how linus had the linux kernel running. I wonder if its possible to run install only the kernel on a virtual machine. Can this be achieved? If so how do i start

---

### Post by ajgreeny on 2010-04-18
Just the kernel alone with absolutely nothing else is pretty pointless.

You can, however, install just a commandline OS using the alternative install CD, from the usual download pages, or the minimal CD from [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD).

---

### Post by m4tic on 2010-04-18
thanks for your response. I wanted to build my own os. I found linuxfromscratch.com , the tutorials there are step by step and i recomend any user to it. i'm half way done building my own operating system but i think i'm going to start over and do it on my harddrive since running from a virtual machine slows the process and it currently doesn't work well with my 2 cores, but i may run into hardware problems. But will see

---

### Post by Khakilang on 2010-04-18
Once you're finish share us your result.

---

### Post by m4tic on 2010-04-18
i have a grub problem, it gives this error
```
root:/tmp# /sbin/
reboot
WARNING: could not
determine runlevel -
doing soft reboot
(it's better to use
shutdown instead of
reboot from the
command line)
shutdown: timeout
opening/writing control
channel /dev/initctl
init: timeout opening/writing control channel /
dev/initctl
root:/tmp# ...
bash: ...: command not found
root:/tmp# grub> root (hd0,1)
bash: syntax error near unexpected token `('
root:/tmp# grub> kernel /boot/grub/core.img
bash: grub: command not found
root:/tmp# grub> boot
bash: grub: command not found
root:/tmp#
``` 

this is section 8.4.3

---

### Post by ssam on 2010-04-18
[http://www.manlug.org/content/blogsection/5/71/](http://www.manlug.org/content/blogsection/5/71/)
have qemu images of some very old linux versions

---

