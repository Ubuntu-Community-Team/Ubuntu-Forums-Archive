---
title: "Virtualbox Win7 guest, 14.04 host, Canon camera doesn't work"
date: 2014-09-25
forum: Virtualisation
---

### Post by sgofferj on 2014-09-25
Now I have a similar problem as [I have with my printer]("http://ubuntuforums.org/showthread.php?t=2239871") also with my EOS 6D. Win7 will nag that the "device has malfunctioned" and cannot be installed. If I disconnect and reconnect, I even get an alert from Virtual Box that it cannot create the proxy file and a VERR_READ_ERROR. Of course, the camera is recognized and works fine on the host as well as on my Win8 laptop...

What's with the USB mess in Virtual Box on Ubuntu...?

---

### Post by fidelis2 on 2014-09-25
Well, I experience basically the same here but just with an USB printer instead of your USB camera. Shouldn't make much of a difference, however.
I couldn't and can't get a Win7 guest to use the USB device in a correct way. However, a fall-back to a WinXP guest **does work** and this is the configuration I use now: i.e. Ubuntu 14 host, standard Virtualbox with WinXP guest where the latter is configured in Virtualbox to use USB1, not USB2 (because USB2 doesn't work even for a WinXP guest).
I've explained the details here in [this thread]("http://ubuntuforums.org/showthread.php?t=2241234&p=13110108#post13110108").

In the end I'm happy it works well, and it's no big difference (for me) to use a WinXP guest instead of a Win7 guest -- on the contrary WinXP is faster than Win7 (even in Virtualbox), needs less CPU power, less RAM and less disc space.

---

### Post by sgofferj on 2014-09-25
Trouble is that WinXP is End of Life - no more updates and if I would install it from my old CD now I couldn't even update to the latest state because Microsoft pulled the plug on the update servers.
The annoying thing is that other USB devices, even exotic ones like my Contour ShuttleXpress work just fine...

---

