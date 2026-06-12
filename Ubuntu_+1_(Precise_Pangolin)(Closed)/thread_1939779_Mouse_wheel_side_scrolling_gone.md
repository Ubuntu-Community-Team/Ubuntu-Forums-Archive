---
title: "Mouse wheel side scrolling gone?"
date: 2012-03-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by snkiz on 2012-03-12
I have a mouse with a 2 axis wheel. pushing on the side of the wheel used to side scroll (10.10) but now just does normal scrolling. I thought it was  just a minor glitch, but now we're it beta. Anyone else notice this?

---

### Post by jb5 on 2012-03-18
I'm seeing this too. 
Mouse Side scroll action affects vertical scroll in window.
Seen in FFx & LibreOffice

---

### Post by PaulInBHC on 2012-03-18
I have a Microsoft mouse with side scroll and magnify but MS does not have drivers for linux. I think the generic ubuntu drivers are limited but check in your system settings window.

---

### Post by snkiz on 2012-03-18
There is no driver, it used to be X handling mice and things. Now I think its udev?? I think 10.10 used the same deal it worked there. I have a wireless MS keyboard and mouse, they've always performed better under Ubuntu  then under Windows. Until now ofcourse.

---

### Post by mc4man on 2012-03-18
I just hooked in a side scrolling mouse (logitech)  to this laptop (Dell, nvidia),  it works fine.
That being said I think they've introduced all sorts of possible mouse/touchpad scrolling, highlighting, ect.  issues, much of which affects some hardware but not others

(- even though it was 'fixed' I still once & a while get a stuck left click (drag) on this touchpad
I can fix that thru a synclient startup comm., but I shouldn't have to.

Will be interesting to see how much is resolved by release

---

### Post by neu5eeCh on 2012-03-18
Not seeing the issue with my own mouse: Logitech Anywhere MX

---

### Post by shuttleworthwannabe on 2012-03-19
If it is wireless USB Mouse, have you tried removing and reinserting the USB thingy from the machine? This seemed to resolve my MS Wireless Mouse issues--but, I do not have the side scrolling as you guys so it may be a different issue.

---

### Post by jb5 on 2012-03-19
MS mouse here too.
Worked flawlessly in previous iterations of Ubuntu. 

Nothing to alter in  
system settings &#8594; mouse

Tried unplugging USB sensor, didn't appear to fix issue for me.

---

### Post by snkiz on 2012-03-19
That's enough for me, found a bug that seems to match.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/694087](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/694087)

Me 2'd it. It's a little old but still open. I heading out but I'm going to comment with my mouse specs latter.

---

### Post by jb5 on 2012-03-20
> **snkiz said:**
> 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/694087](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/694087)


Ahh, thanks. Added info & clicked affects me too.

---

