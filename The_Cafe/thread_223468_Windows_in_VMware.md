---
title: "Windows in VMware?"
date: 2006-07-26
forum: The Cafe
---

### Post by hizaguchi on 2006-07-26
So I got this new laptop and it came with Windows Media Center.  I'd like to install come CAD software since I've got a Windows license, and I also might take advantage of the OS to play some games.  Problem is, I enjoy not getting viruses and spyware, and I don't really want to reboot into Windows every time I want to use it.

My solution is to install XP in something like VMware and then run it there in a window when I need it for something.  This way I don't have to worry about updates or internet related stuff at all because I can just keep it cut off from the outside world.

So anybody running Windows XP in a virtual machine?  How is the performance for doing heavy stuff like gaming or CAD?  I've got a gig of DDR2 and a Turion 64 X2... would I be able to run heavy apps well or should I just try to use Wine?

---

### Post by G Morgan on 2006-07-26
The performance is great if you allocate 512MB of RAM and install VMware Tools. The VMware Player doesn't have the option for this but Workstation does and I think Server does.

Without VMware Tools its unusable.

A tip would be to setup Samba on the host machine then you can share files between the host and the guest with ease.

---

### Post by Kindred on 2006-07-26
I believe vmware still requires you to use its own display driver, without any kind of 3D performance at all.  It's fine for 2D stuff though, I used to use it for photoshop and it worked pretty well.

---

### Post by Virogenesis on 2006-07-26
can you boot off of usb because a usb pen distro might be better as vmware does suck for games and what have you.

---

### Post by hizaguchi on 2006-07-26
Ah, I totally forgot about the 3D performance.  I may have to try Cedega then.

---

### Post by mips on 2006-07-26
Use VMWare server, it's free like the plaer but not opensource.

---

### Post by hizaguchi on 2006-07-27
Does it handle 3D acceleration?

---

### Post by mips on 2006-07-27
I honestly don't know. But i did a little googling and found this:

[http://www.vmware.com/community/thread.jspa;jsessionid=8AA5C9B8858BE3511F42BD0F0ABC7558?messageID=328065&#328065](http://www.vmware.com/community/thread.jspa;jsessionid=8AA5C9B8858BE3511F42BD0F0ABC7558?messageID=328065&#328065)
[http://www.ubuntuforums.org/archive/index.php/t-84344.html](http://www.ubuntuforums.org/archive/index.php/t-84344.html)

---

### Post by e00878 on 2006-07-27
Thanks! Work's graet. Now I can run AutoCAD 2006 fluently.;)

---

### Post by AndyCooll on 2006-07-27
> **hizaguchi said:**
> Does it handle 3D acceleration?

No. For gaming (and other graphics card intensive tasks) VMware is not the answer to your problems. For most other things VMware is fine though. I play FM on it, and since this is a number crunching game rather than graphics intensive it runs great.

:cool:

---

### Post by hasimir44 on 2006-07-27
Has anyone tried [qemu w/ the accelerator]("http://fabrice.bellard.free.fr/qemu/")? I was reading about it in a magazine a couple of days ago. The website boasts "near native speeds" and has apparently beaten VMWare in different benchmarking tests. 

The qemu accelerator is closed source, but free to download.

---

