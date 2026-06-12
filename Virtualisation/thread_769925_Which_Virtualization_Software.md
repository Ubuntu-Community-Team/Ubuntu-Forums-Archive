---
title: "Which Virtualization Software?"
date: 2008-04-27
forum: Virtualisation
---

### Post by Wake Rider on 2008-04-27
I still have an old install cd of Windows 98 which I would like to run as a guest under Ubuntu, in order to play some old games which will not run on Vista or XP. From past experience I was unable to get sound in VMware Server, so I was wondering which Virtualization software would be the best. VirtualBox? What are the free options?

---

### Post by tamoneya on 2008-04-27
I like virtual box myself.  I find that it works a lot easier than vmware and i really like the windowless mode where it seamlessly integrates the windows from the other OS into linux.

---

### Post by Wake Rider on 2008-04-27
I have installed VirtualBox and am in the process of installing Windows 98. How do I ensure that the Windows 98 virtual installation has NO access to the network? I only want to use it for some old games and don't want the hassle of having to run Anti-virus software.

---

### Post by FredB on 2008-04-27
If your processor is an intel-vt / amd-v enabled one, you can try KVM. It is a simple and quick answer to virtualization, even if you will have to use it on command line.

[https://wiki.ubuntu.com/KvmVirtManagerEtc](https://wiki.ubuntu.com/KvmVirtManagerEtc)

---

### Post by Dev'olution on 2008-04-27
I personally like vmware

---

### Post by Wake Rider on 2008-04-27
I have Windows 98 running now, but the resolution is stuck at 640 x 480. how can I increase the resolution? I thought I may have to install graphics cards drivers, but I can't find a driver for Windows 98 for a Nvidia GeForce 8600GT graphics card.

---

### Post by FredB on 2008-04-27
Install additional software from your emulator. You can find it easily in virtual box. Can't remember which menu :(

It will give you video driver among other things.

---

### Post by Wake Rider on 2008-04-27
Windows 98 in VirtualBox is still in crappy 640 x 480 16 colors with no sound. What do I do to fix it? Couldn't find a sound driver or a video driver. Where do I find Windows 98 Legacy drivers?

---

### Post by FredB on 2008-04-27
> **Wake Rider said:**
> Windows 98 in VirtualBox is still in crappy 640 x 480 16 colors with no sound. What do I do to fix it? Couldn't find a sound driver or a video driver. Where do I find Windows 98 Legacy drivers?

Install virtualbox additions. It will help you for both sound and video. For sound, verify that the output is not "null".

---

### Post by fhmanas on 2008-04-27
> **Wake Rider said:**
> I have installed VirtualBox and am in the process of installing Windows 98. How do I ensure that the Windows 98 virtual installation has NO access to the network? I only want to use it for some old games and don't want the hassle of having to run Anti-virus software.
As everybody is suggesting install virtualbox additions for your sound, mouse, video problems, don't provide your virtual machine a network card if you do not wish it interact with the outside world.  if you do need to get stuff from your host, you can attach a network card and attach it as HostOnly, this will just access your host drive.  You can also specify folder to be shared in your VBoxMachine and map it in Win98

---

### Post by Wake Rider on 2008-04-28
VirtualBox addons are not supported in Windows 98. It is too old.

---

### Post by Wake Rider on 2008-04-28
I have read to install the beta of Display Doctor 7 however it will not install. Something about an input / output error. Help!

---

### Post by sstusick on 2008-04-28
Virtual Box is great, I use it and prefer it to VMware.

---

### Post by agent8131 on 2008-04-29
VirtualBox is easy to use and free and open source but it doesn't really support Windows 98 so it is not ideal for this situation:

[http://virtualbox.org/wiki/Guest_OSes](http://virtualbox.org/wiki/Guest_OSes)

I'd say try QEMU and Qemulator.  QEMU emulates a video card that I believe is supported in Windows 98.  If it works and you have a system that supports KVM you can replace QEMU with KVM to get a performance boost.

---

### Post by FredB on 2008-04-29
For KVM, I can say you're perfectly right. I am using it with a great pleasure. But be sure to use sb16 for soundhw for win98.

---

