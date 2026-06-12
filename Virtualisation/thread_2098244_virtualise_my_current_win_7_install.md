---
title: "virtualise my current win 7 install"
date: 2012-12-26
forum: Virtualisation
---

### Post by marks_linux on 2012-12-26
I currently dual boot ( theoretically - I can't remember last time I booted into windows).

Question is is there a way of virtualising my current win 7 install so I can run in virtual box (or similar) if needed?

---

### Post by Paddy Landau on 2012-12-26
It's possible. But it's not for the faint-hearted. And, of course, your hardware needs to be strong enough to do this (especially your RAM).

The problem is that because of the drivers involved, once you virtualise your Windows, it is unlikely to boot normally. It is also possible to muck it up and trash your existing installation, so be sure to have full backups before you start.

I am no expert in this area, but search for solutions in this forum and in [Ask Ubuntu]("http://askubuntu.com/").

[http://ubuntuforums.org/showthread.php?t=984437](http://ubuntuforums.org/showthread.php?t=984437)
[http://ubuntuforums.org/showpost.php?p=6122463&postcount=6](http://ubuntuforums.org/showpost.php?p=6122463&postcount=6)

---

### Post by Vegan on 2012-12-26
I use Hyper-V and run Linux as a guest OS. I can run both the desktop and the server version of Ubuntu but management has to be done manually.

---

### Post by haqking on 2012-12-26
You can use disk2vhd or depending on how good you are with such things you can take a clone of it and then clone it into a prepared virtual machine.

However some aspects of that such as activation can provide stumbling blocks for some users.

There is also this method [http://www.sysprobs.com/physical-virtual-virtualbox-virtualbox-p2v](http://www.sysprobs.com/physical-virtual-virtualbox-virtualbox-p2v)

Peace

---

