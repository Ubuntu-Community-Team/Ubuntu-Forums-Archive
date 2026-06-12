---
title: "daily-live xubuntu mouse frozen"
date: 2017-09-24
forum: Ubuntu Development Version
---

### Post by VMC on 2017-09-24
Todays xubuntu daily-live "***artful-desktop-amd64.iso 2017-09-24 02:26 1.2G***" wireless mouse is frozen. It has worked every week up until today's ISO. Tried both USB flash and normal loop-back install work react the same way.

---

### Post by mc4man on 2017-09-24
Tried on a live session & yeah, my usb (wireless) mouse did nothing. Was detected on boot (kernel.log) & disconnecting/reconnecting it showed up in syslog. Maybe some power management issue?

Also noticed that when trying to search in any of the logs mousepad opened a search dialog but wouldn't accept any keyboard input..

---

### Post by Cavsfan on 2017-09-24
Same thing here. I installed Ubuntu from yesterday's daily and it worked after 5 days of trying. Today I wanted to install Xubuntu and it did not allow the mouse to move or the keyboard to do anything.

So, I booted back into Ubuntu and installed Xfce and am in the process of converting it to Xubuntu or as near as it gets.

---

### Post by flocculant on 2017-09-24
Thanks - I've been blindsided by issues I've got with virtual machines - thought mouse was tied up with that.

---

### Post by flocculant on 2017-09-24
Could possibly be xserver-xorg-input-synaptics which we've quite recently added to the iso to fix [lpbug]1686081[/lpbug]

That landed on the 20th which would 'probably' have been the 21st iso.

---

### Post by mc4man on 2017-09-24
I'd bet dollars to doughnuts that if you guys using Xubuntu put back xserver-xorg-input-libinput & rebooted your usb mice would start working again
(even though xserver-xorg-input-synaptics will always override it.
Not suggesting as a permanent solution, just to see...

---

### Post by flocculant on 2017-09-25
we added -input-all

live now has input after I rebuilt the iso

Thanks for posting peeps.

---

### Post by VMC on 2017-09-25
Thanks for your input. Today's xubuntu ISO fixed my frozen keyboard/mouse input.

---

### Post by flocculant on 2017-09-25
> **VMC said:**
> Thanks for your input. Today's xubuntu ISO fixed my frozen keyboard/mouse input.

Thanks for yours ... if I'd not seen this thread I would have assumed the issue to be tied up with my ongoing vm issues :)

---

### Post by Cavsfan on 2017-09-25
Thanks for letting me know today's ISO works with the keyboard/mouse. 

Ubuntu with Xfce is pretty close but, not the real Xubuntu.

I'll download today's ISO. Just wanted to check here first.

Thanks again!

---

### Post by flocculant on 2017-09-25
Well - as I've probably said before - the best place to check Xubuntu stuff is #xubuntu-devel :) No guarantee's that I'm not missing from here for days ...

You can get there simply if you don't generally IRC by using the relevant tab on [https://dev.xubuntu.org/](https://dev.xubuntu.org/)

---

### Post by Cavsfan on 2017-09-25
I got it installed and everything went well. Getting it all like I like it at this time.

But, I must say that the menus in the top left on Ubuntu with Xfce added behave exactly like Arch Linux, (e.g Settings appear outside the menu box to the right in a long visible list) while the Xubuntu menus are inside the menu box and are limited to the size of the menu box.
You have to scroll the menu down to see what is below. Although I know you can resize the menu for everything but, it's not the same.

But, I have the backgrounds set to change after 10 minutes. That's pretty nice. I've never tried that or seen it before

Just thought I'd throw that in there.

---

