---
title: "no audio device in vmware"
date: 2008-01-19
forum: Virtualisation
---

### Post by tjksn on 2008-01-19
I have installed VMWare on my Gutsy setup and it works great at loading windows XP.  Most everything works with the following exceptions: 1) no sound, 2) Games will not load.  I checked the sound settings and found no audio device is listed.  Anyone have any ideas?

Tom

---

### Post by fjgaude on 2008-01-19
Do you install the VMware Tools while in Windows?

---

### Post by tjksn on 2008-01-19
Yes I installed VMWare tools while in windows.  I copied my hardware profile and named it VMWare, then installed the VMWare scsi drivers.  I next setup VMWare to use a physical drive (where I have an installed copy of XP) and when it initially setup I went to the VM tab and clicked on install VMWare tools.  All of this went smoothly and everything else I've tested works fine.

Tom

---

### Post by Thund3rstruck on 2008-01-20
I've been using VMWare Server on Linux since the BETA some time ago and on all the hardware I have used it on I have never had sound in any of my Windows VMs. 

I'd really like to know how to solve that one myself

---

### Post by fjgaude on 2008-01-20
I can't think of anything right now... I've had no issue with sound in VM WinXP. All my USB devices work, printers, scanner, UPS control. I usually turn sound off so there is no interference with it when I'm on the Ubuntu side.

Have you tried the forums on the vmware.com site?

---

### Post by ayates on 2008-01-20
I had to add a Sound Blaster card inside of XP with add/remove hardware.

---

### Post by ed.lazda on 2008-06-13
I have struggled for ages ](*,) to get sound working on a Win XP guest system running on Kubuntu -- from about Edgy till now.

Finally found out that Windows Audio services were turned off in the guest machine. Turned them on - sound works !! :biggrin:

Hope this might help some others out there who may have overlooked this!

---

### Post by himagain on 2008-06-14
> **ed.lazda said:**
> I have struggled for ages ](*,) to get sound working on a Win XP guest system running on Kubuntu -- from about Edgy till now.

Finally found out that Windows Audio services were turned off in the guest machine. Turned them on - sound works !! :biggrin:

Hope this might help some others out there who may have overlooked this!

Hi Ed,
Congratulations! 
I'm stuck with this in VirtualBox - may change over!  Where is the  switch for this in VMWare?

Cheers!

---

### Post by ed.lazda on 2008-06-16
Hi -- the switch is in Windows, not vmware. Go to Control Panel --> Administrative Tools --> Services, and scroll down to Windows Audio. If it's already running, then I haven't solved your problem :(.

If it's disabled, double click to open it, set startup type to automatic, and click on start.

---

### Post by Protazy on 2008-06-27
I did it in another way. Start vmware server but don't start windows. Go to VM menu then select SETTINGS when menu pop up click on +ADD and select add sound or similar. There will be two options: 1. auto-detect and something with dsp. I took that with dsp. It started work :)

---

### Post by dwhitney67 on 2008-08-29
> **Protazy said:**
> I did it in another way. Start vmware server but don't start windows. Go to VM menu then select SETTINGS when menu pop up click on +ADD and select add sound or similar. There will be two options: 1. auto-detect and something with dsp. I took that with dsp. It started work :)
Thanks, your suggestion worked!

---

### Post by maphilli14 on 2008-08-29
Seems to me that /dev/dsp does not play nice with Pulseaudio and will not share the audio drivers.  If I start my XP up 1st then it gets audio and nothing else.  If I start sound in FF, Amarok etc.. then boot XP, it gets no sound at all!

Mike

---

### Post by dwhitney67 on 2008-08-29
I do not know if it makes a difference or not (wrt to the audio), but I am using VMware Server 2.0 (beta release).

I chose the 2.0 version because I was having trouble getting VMware 1.5.0 to recognize my 80GB iPod classic; in fact, in some instances, iTunes hung when I plugged in the iPod, and in other instances I got the WinXP "Blue Screen of Death".

The UI for 2.0 is different from earlier versions, but looks nice.  The UI runs in Firefox (or whatever browser one happens to use).

---

