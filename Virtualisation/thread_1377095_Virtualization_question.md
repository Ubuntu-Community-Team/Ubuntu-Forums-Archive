---
title: "Virtualization question"
date: 2010-01-09
forum: Virtualisation
---

### Post by deamon_knight on 2010-01-09
So I guess this would be the right place to post!

I'm having a very difficult time making sense of all the VM options here so I'm wondering if someone could answer my question. I have a 3GHz P4 running Karmic 9.10 32bit. Using this as the host OS, I want to be able to run Windows XP/Vista/7 , and/or a Linux Distro, and/or PowerPC based Linux Distro, and/or the PowerPC version of MAC OSX, as a guest OS. 

I'm stuck on QEMU for running a PowerPC based VM on an x86 system. It looks like it should be possible, but There seem to be files I need that I can't understand how to get.

Is there a better way to get this to work, or is it simply not possible? Should I try VirtualBox instead?

---

### Post by jocampo on 2010-01-10
Not sure about Power PC but you should be able to run almost all Windows Os and most important Linux distros using VBox. You should try it. Vbox is very stable and easy to use/learn. Be sure you download 3.0 at least so you can run Karmic Koala.

Supported VBOx guests:
[http://www.virtualbox.org/wiki/Guest_OSes]("http://www.virtualbox.org/wiki/Guest_OSes")

---

### Post by deamon_knight on 2010-01-10
Well, getting a Virtual PowerPC for playing around in the Mac OS or PPC Based Distros environment is one of the key objectives. Anyone know how this can be done?

---

### Post by AlexandreP on 2010-01-11
Since the VM emulated an IBM PC-Compatible processor *(and I think it even uses the characteristics of the processor of the host PC)*, you won't be able to run a PowerPC distribution inside a VM *(maybe you would succeed on a PPC computer, though)*.

---

### Post by lukeiamyourfather on 2010-01-11
There's virtualization tools out there for PowerPC, but they don't support hardware virtualization so it'll be ***dog slow***. If you're interested in OS X why not use a more recent version that's x86 or amd64? Correct me if I'm wrong but there's not even PowerPC support in the last few version of OS X. A PowerPC Linux distribution isn't going to offer anything that an x86 or amd64 distribution doesn't offer as well so it seems like a fruitless effort. Cheers!

---

### Post by deamon_knight on 2010-01-12
The reason I'd want to emulate a PPC environment is that I still have to support PPC based units from time to time. Since Ubuntu is no longer officially supporting PPC I'm having a hard time finding a decent LiveCD as a base for testing.

---

