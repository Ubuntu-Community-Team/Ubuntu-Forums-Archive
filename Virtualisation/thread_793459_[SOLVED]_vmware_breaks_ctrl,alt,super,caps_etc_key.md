---
title: "[SOLVED] vmware breaks ctrl,alt,super,caps etc keys"
date: 2008-05-13
forum: Virtualisation
---

### Post by nowhere@cox.net on 2008-05-13
i installed vmware server and when i try to rotate the cube off of the workspace on which the server console is running, vmware abruptly closes. after that, the control, alt, or super key will intermittently close other linux windows if press with focus. sometime like right now, my control, alt super and even shift and capslk keys don't do anything.

i tried remapping the vmware hot keys to ctrl-alt-shift instead with the same problem. i also tried remapping compiz rotate cube to super mouse 1 only but they all do the same thing. 

one interesting thing is that it seems that whenever vmware goes away, pidgin pops up... i have it running and a panel icon visible.

i have to log out and back in to regain functionality. i am running hardy 64 and have the latest vmware server installed.  

anyone know what's going on
thanks

---

### Post by jessika-kaos on 2008-05-13
I'm having possibly the same issue with vmware player. After a while of running the using tab with any ubuntu program causes that program to exit. Using the up arrow it a terminal window causes the window to exit, typing anything into tracker search causes it to exit, and various other quirks). Even after exiting vmware these don't resolve until I restart.

---

### Post by bobyy on 2008-05-14
Hy....
The same problem here...in virtualbox this problem seems to be solved somehow....in VBox sameles windows is working...in Vmware not....maybe somebody have a tip for us :)

---

### Post by nowhere@cox.net on 2008-05-14
This probably isn't a solution but I changed my hot-keys in vmware server to ctrl-alt-shift, changed my hot-key for compiz rotate cube to super-mouse1 and I have been careful NOT to press ctrl-alt-shift or ctrl-alt in vmware. I have not had the problem again. I am betting it only shows when you use one of those combinations where it is both the vmware release AND the rotate function. 

The same problem happened in vmware player too.

---

### Post by bobyy on 2008-05-14
Thx nowhere@..
It is true ...
Il will try to doit in your way ....maybe it is a solution :)

---

### Post by jessika-kaos on 2008-05-14
There's a bug posted [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/195982") which I think is the same thing. Some people have luck running setxkbmap, apparently.

---

### Post by bobyy on 2008-05-14
So ..it`s a bug....
Hell...i must switch to Vbox ...The only thing with Vbox is :
i must link interfaces ...and create Tap interface ...bla bla  a lot of work :))...
Ok dosent meter....
THX for help and tips

---

### Post by nowhere@cox.net on 2008-05-20
Just a quick update. Since I remapped the keys like I said in a previous post, I have not had the problem again. My perfectionist side doesn't like this as a solution but I remap the keys that way anyway so it doesn't affect the use...

---

### Post by jessika-kaos on 2008-05-20
There is also a tip posted in the above linked bug report: making sure that a default keyboard is ticked in Preferences > Keyboard. I haven't had any issues since doing that (granted I've only run vmware about 8 hours since then).

---

### Post by joserwan on 2009-03-17
> **jessika-kaos said:**
> There is also a tip posted in the above linked bug report: making sure that a default keyboard is ticked in Preferences > Keyboard. I haven't had any issues since doing that (granted I've only run vmware about 8 hours since then).

I had a default keyboard ticked, but it was the only one setted and I had the same problems as you.

I've setted another keyboard (non-ticked as default), and now it works.

---

### Post by froling on 2009-05-01
> 
 					Originally Posted by **jessika-kaos** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5006827#post5006827") 				
 				*There is also a tip posted in the above linked bug report: making sure that a default keyboard is ticked in Preferences > Keyboard. I haven't had any issues since doing that (granted I've only run vmware about 8 hours since then).*


This tip didn't solve this for me.. It may work better, but if I provoke <shift><alt>left/right it makes ctrl sticky in the host. 

On possible way to reproduce this is to focus VMWare move the mouse outside of the VMWare window and hit <ctrl><alt>right. If you are lucky the situation may be solved throgh <ctrl>g combination when you have the VMWare window focused and the mouse outside of the VMWare window (mayby only the key g is enough i.e. <ctrl> has gone sticky).

One other tip from the bug refrerence above is to execute ```
setxkbmap
``` in a console window to resolv the temporarly sticky <ctrl> situation.

---

### Post by toineurlings on 2009-12-28
I have the same problem but "setxkbmap" doesn't work for me, another problem is VMware a few seconds after starting just disappears. It does this most times but sometimes it just works. I first noticed I lost shift but after restarting ubuntu IT WORKS again but is still can't use ctrl.

I remember a sign when starting VMware which was talking about something with my keyboard, it wanted to lock something

In VMware I can use ctrl and I rebooted the PC several times. 

But I still haven't solved :confused:

edit: -I'm the only user on this pc with this problem but also the only one who use VMware
-when VMware disappears, all panels disappears and come back in a second but the icons on my desktop
-I just tried my arrow-keys, the horizontal also fail but the vertical work fine

---

### Post by toineurlings on 2009-12-28
SOLVED IT! It added a new keyboard with the same options and set it as default for the whole system, it worked.

So it has to do something with the option for the keyboard which is used ad installed. It didn't just worked with plugging in another keyboard at the same time. But.....
SHITTTTTTTTTTT start VWware and it showed up again, tried it again without VMware and it just works for a very short term (my arrow keys work again)

HUH... sometimes it works for 10 seconds and then it fails again

edit: It's getting stranger and stranger... I can zoom using ctrl+scroll

---

### Post by toineurlings on 2009-12-28
deleted VMware but it's not solved yet

---

### Post by toineurlings on 2009-12-29
here they talk about the problem but i -sorry, shift doesn't work- don't see a solution in this story
[http://www.vmware.com/support/ws55/doc/ws_devices_keymap_linux_longer.html](http://www.vmware.com/support/ws55/doc/ws_devices_keymap_linux_longer.html)

---

### Post by fermulator on 2010-04-18
> **froling said:**
> This tip didn't solve this for me.. It may work better, but if I provoke <shift><alt>left/right it makes ctrl sticky in the host. 

On possible way to reproduce this is to focus VMWare move the mouse outside of the VMWare window and hit <ctrl><alt>right. If you are lucky the situation may be solved throgh <ctrl>g combination when you have the VMWare window focused and the mouse outside of the VMWare window (mayby only the key g is enough i.e. <ctrl> has gone sticky).

One other tip from the bug refrerence above is to execute ```
setxkbmap
``` in a console window to resolv the temporarly sticky <ctrl> situation.

This worked for me!

---

