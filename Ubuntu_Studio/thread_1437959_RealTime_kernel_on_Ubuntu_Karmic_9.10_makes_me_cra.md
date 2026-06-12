---
title: "RealTime kernel on Ubuntu Karmic 9.10 makes me crazy!"
date: 2010-03-24
forum: Ubuntu Studio
---

### Post by Kenny89 on 2010-03-24
Hi everyone.

I have just installed Ubuntu Karmic (9.10) i386 on my notebook PackardBell TJ65. I'd like to use Linux as a great Music Station using packages of Ubuntu Studio with low-latency kernel, so I tried to install realtime kernel typing

```
sudo apt-get install linux-rt
```

... as I did when I had Ubuntu Hardy, but I have problems after rebooting because the new kernel doesn't appear on the grub menu... Rather I can't see the grub menu on startup so I can't choose my favourite kernel and then the generic kernel is loaded automatically.

What can I do to solve that?

I tried typing this command on terminal after installing linux-rt

```
sudo update-grub
```

but doesn't work.
Any idea?

Thanks in advance. :D
Roberto

---

### Post by Capoeira on 2010-03-24
Karmic uses Grub2 wich is different, read this:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

(for example: press "shift" on boot to enter grub-menu)

---

### Post by Kenny89 on 2010-03-24
Thanks a lot for your answer, now It works!!
I explain what I did to show the grub list at startup.

First I opened with sudo privileges the file **/etc/default/grub**:

```
sudo gedit /etc/default/grub
```

then I found the string

```
GRUB_HIDDEN_TIMEOUT=0
```

This string means that the grub menu must be hidden, even if other kernels are installed.
So I putted a "#" before that string (to make it a simple comment).

Then I typed on terminal
```
sudo update-grub
```

and restarted the system..... Et voilà, I couldn't believe what my eyes were seeing: the grub menu has been restored, so I can choose at startup the kernel I want to load.

*** This informations were quoted from official [Ubuntu Wiki]("https://wiki.ubuntu.com/Grub2") ***

Thanks for the fast answer, now I can dedicate my time to the magic world of Music.

I hope this post could be useful for other users even if my english isn't perfect. ;)

See you ubuntians! :D

---

