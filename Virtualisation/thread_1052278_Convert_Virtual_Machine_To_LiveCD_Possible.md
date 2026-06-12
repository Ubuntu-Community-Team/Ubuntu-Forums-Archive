---
title: "Convert Virtual Machine To LiveCD Possible?"
date: 2009-01-27
forum: Virtualisation
---

### Post by nfox on 2009-01-27
Hello,

I have Virtualbox and a WinXP install. I've dabbled with various LiveCD converters in Windows freeware-land but with only my Dell Reinstall CD, I can not get BartPE or WinPE to make a bootable LiveCD. I did get past the point of it telling me which drivers were missing and now it just simply dies. 

Since the traditional way of stripping installs into a CD's-worth hasn't worked for me, I was hoping there were alternative means. I'm mainly looking to be able to turn my Windows install into one that could fit on a CD.

Any help is appreciated.

---

### Post by HotShotDJ on 2009-01-27
I believe that the virtual disk used to run Windows in a VM needs read/write access, which would preclude using a CD to store the VD. (It is also possible that I'm completely wrong about that... if so, feel free to correct me with all due haste if you discover a way to do it. :) )

---

### Post by Dedoimedo on 2009-01-28
If you can't use BartPE or similar to make bootable Windows CD, because you don't have a full install CD, you might be have a problem.

BUT ...

Boot from Linux live CD and copy the i386 directory somewhere. Then, boot back into Windows, run Bart and when it asks you for the source, point to this i386 directory.

Furthermore, see here:
[http://www.dedoimedo.com/computers/ubcd4win.html](http://www.dedoimedo.com/computers/ubcd4win.html)

And then, remastering Linux - you can indeed create a bootable, redistributable iso from your install, including custom packages added, including virtual machine.

[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

Hope this helps.

Dedoimedo

---

### Post by nfox on 2009-01-28
Thanks for the replies. 

I'm almost positive it would need read/write but it would be nice if there was a workaround. 

I know about making custom Linux installs and backing up a current one:
```
sudo tar -cvpzf /destination/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/dev --exclude=/media --exclude=/destination/backup.tgz /
```

But Windows is the tricky one. I've tried all of the Dell fixes I could find and I'm probably the reason they don't work. Another question for another forum. I was hoping someone had another way of doing it.

Like making an ISO of a Windows partition and then vditool to convert it to a VDI which a program could run off of a disc. Maybe in the future..

---

### Post by thomasr on 2009-01-30
This is what I did:
Install Ubuntu. Whack out all the programs you won't need. Install VMWare Player. Use remastersys to make a live cd, which now has vmware player on it. Put the vmware virtual machine on a usb hard drive. 

Probably would work for virtual box.

---

### Post by nfox on 2009-02-01
thomasr, thanks for the idea. That sounds like what I should have thought... remastersys an install is perfect.

For others, this is what I'd do:

install minimal Ubuntu (as suggested)
and the startup script to include would be:
"VBoxManage startvm NAMEOFVM" upon login.


You know what I'll be doing. Maybe I can find a nice blend of performance to features.

---

### Post by zerin on 2010-09-16
@nfox
 
Hey! if you got around to building it. would you mind sharing it? i tried to make one, but i am failing so much.

---

### Post by nfox on 2010-09-16
zerin, take a look at remastersys. It's excellent and does what I was after:

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")

It's easier than chroot environment and customizing existing live CDs

---

