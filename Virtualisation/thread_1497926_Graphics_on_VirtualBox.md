---
title: "Graphics on VirtualBox"
date: 2010-05-31
forum: Virtualisation
---

### Post by godsmack_dmx on 2010-05-31
[COLOR="Teal"]I have installed windows 7 32-bit on virtualbox on my Ubuntu 10.04 & I installed virtualbox guest additions but the graphics performance are very low.

You can't start a game & the themes work like you have no driver installed for your VGA card.

I'm asking if it possible to run games on virtualbox windows 7 or not? [/COLOR]

---

### Post by VastOne on 2010-05-31
> **godsmack_dmx said:**
> [COLOR="Teal"]I have installed windows 7 32-bit on virtualbox on my Ubuntu 10.04 & I installed virtualbox guest additions but the graphics performance are very low.

You can't start a game & the themes work like you have no driver installed for your VGA card.

I'm asking if it possible to run games on virtualbox windows 7 or not? [/COLOR]

How much video memory are you allotting under Settings Display? Did you set the Enable 3d and 2D on the same menu?

I have a 1 gig vid card and I have 128 mb alloted for Win 7.  I play online games (poker) and they play perfectly.  I do not know if any high end games will play.

---

### Post by MooPi on 2010-05-31
3D games probably not. I play Starcraft & BroadWars and that is about all the virtual graphics can muster. If your really interested in high end games a dual boot is the best bet.

---

### Post by godsmack_dmx on 2010-05-31
I gave it 128 MB & my VGA card are GT240 512 DDR5. And I enabled 3d and 2D

---

### Post by BobVila on 2010-06-01
> **godsmack_dmx said:**
> I gave it 128 MB & my VGA card are GT240 512 DDR5. And I enabled 3d and 2D

Did you install the vbox additions in safe mode? The graphics drivers tend to... not work... if they're installed while the machine isn't in safe mode.

Also, don't expect miracles even when they're installed correctly. Virtualized graphics performance has always been underwhelming.

---

### Post by godsmack_dmx on 2010-06-01
I install Vbox additions in the safe mode and it still the same nothing change no games want to run.

---

### Post by jcoles on 2010-06-11
What video adaptor does VirtualBox emulate? It's hard to configure your guest system without that basic information. 

I have both Windows and Ubuntu guest systems and the only video resolution options I have available are 640x480 or 800x600. Is only low-end VGA supported? 

The VirtualBox display settings offer only amount of memory and on/off for 3D acceleration. As if video was ever that simple!

Yes, I have the Guest Extensions installed. I can't see that it made any difference to anything. Is there some way to confirm that the extensions are working?

---

### Post by blur xc on 2010-06-11
w/o guest additions you cannot go into full screen or seamless modes...  Also the guest os will captuer the mouse pointer, and you need to right ctrl (unless you changed your Host key) to release the mouse control back to your host pc.

BM

---

### Post by jcoles on 2010-06-11
System > Administration > Hardware Drivers confirms that VirtualBox extensions are in place. 

Unfortunately, the only video configuration in Ubuntu 10.04 (my guest system) Gnome is System > Preferences > Monitors. It provides no way to select a different video driver, even if the guest extensions have added one. 

Are there any tweaks to X system configuration files that can make this work?

---

### Post by TheFu on 2010-06-11
This doesn't sound like the guest extensions have actually been installed inside the client OS (MS-Windows) to me. I believe you will want to double check the installation. Just mounting the guest----.iso is not installing them. There is a real install program for Windows guest OSes and you get to click next, next, next a few times.

The enhanced graphics inside client machines automatically scale based on the window. If you X-Windows graphics setup isn't good, I could see where a client OS would have issues too.  I run dual monitors with Ubuntu as the hostOS - one at 1920x1200 and the other at 1280x1024. The WinXP clientOS can display graphics anywhere from 640x480 all the way up to 1920x1200 just by changing the size of the window that the VM is running inside.

As to performance ... well, I don't game, but I do video editing inside the clientOS. No major issues with video performance. HD Hulu playback is perfect inside the VM, if that means anything.

---

### Post by phr33k-dc on 2010-06-12
How does one go about install guest additions in safe mode?

---

### Post by jcoles on 2010-12-04
My previous experience with the virtualbox guest additions is that they make no difference to video resolutions or anything else. But when I tried installing them on a Ubuntu 10.10 guest, I got a garbled display (see attached). The VM in this state is unusable. The only thing to do is reset it. 

Is this a known problem with Ubuntu 10.10 (32-bit)?

---

### Post by afrodeity on 2010-12-10
Hit the F8 button I think when windows starts for safe mode.

However, I installed the additions in safe mode, and can't start any games. 

Are there other drivers that we need to install?

---

