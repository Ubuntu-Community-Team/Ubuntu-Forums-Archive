---
title: "Reccomendations for DOS virtualization"
date: 2009-02-27
forum: Virtualisation
---

### Post by jwbrase on 2009-02-27
I'm trying to run some old DOS games that I found fun back in the day, and I'm having trouble finding a really good setup.

I'm looking for the following:

1. Game runs
2. Game runs smoothly
3. Can set equivalent CPU speed (alot of DOS games end up being too fast on a 3 GHz processor)
3. Sound works
4. Mouse works
5. Joystick works when needed, and does not interfere when not needed.
6. Freeware, or if not free, very low cost. Doesn't have to be open source.

I've tried DOSBox, Dosemu, and VirtualBox with FreeDOS.

DOSBox seems to come closest, but fails on points 2 and 5. The program I'm trying to run at the moment responds really slowly in menu's, responds in a timely manner in play, but the gameplay ends up being really jerky. Speeding up DOSBox's CPU just makes the game jerk around at a faster speed. I can speed it up to the point that the gameplay is too fast for my reflexes, and it still won't play smoothly.

Dosemu won't even run the game in question.

VirtualBox will run it, and it will run smoothly, but neither the mouse nor the sound will work. (Both are on USB. I've got the PUEL version since I'm just using it for personal use, so VirtualBox has USB support, but unfortuneately FreeDOS doesn't, and I haven't been able to figure out how to get VirtualBox to pass USB devices to FreeDOS as if they were older "normal" devices, which DOSBox seems to do automatically). Also, I haven't been able to figure out how to slow the virtualized CPU down on VirtualBox, so the game runs a bit too fast (fortunately only a bit).

Any suggestions?

---

### Post by MarblePanther on 2009-02-27
You can try FreeDOS:
[http://www.freedos.org/](http://www.freedos.org/)

---

### Post by jwbrase on 2009-02-27
> **MarblePanther said:**
> You can try FreeDOS:
[http://www.freedos.org/](http://www.freedos.org/)

Yes, that's what I'm using on VirtualBox, and I believe it's also what comes packaged with Dosemu. But the program I'm trying to run is just going to a black Window and hanging on startup in Dosemu, and has the problems that I listed before in VirtualBox.

I suppose I could try running it without virtualization, but that has alot of the same problems I'm having with VirtualBox: FreeDOS doesn't have USB capability, and I can't lug my processor down to 386/486 equivalent without something like DOSBox's CPU cycle control.

---

### Post by MarblePanther on 2009-02-27
> **jwbrase said:**
> Yes, that's what I'm using on VirtualBox, and I believe it's also what comes packaged with Dosemu. But the program I'm trying to run is just going to a black Window and hanging on startup in Dosemu, and has the problems that I listed before in VirtualBox.

I suppose I could try running it without virtualization, but that has alot of the same problems I'm having with VirtualBox: FreeDOS doesn't have USB capability, and I can't lug my processor down to 386/486 equivalent without something like DOSBox's CPU cycle control.

I haven't heard of any other viable options, other than what you have mentioned.  Sorry, I didn't notice you already mentioned FreeDOS.

---

### Post by yther on 2009-02-27
I would think you probably need good, old-fashioned device drivers for DOS.  DosBox (being designed for games) may handle some things automatically, but the others won't.  A USB mouse driver should be fairly easy to find (google "freedos usb mouse" for example), and as for your USB audio, try the manufacturer's web site, or the site of whoever makes the chips that are in it, and Google of course.

It may take a little fiddling with CONFIG.SYS, but it should probably be possible.

This is for running FreeDOS in VirtualBox, BTW.  That will likely be the most flexible environment for your customized setup.  I don't think VirtualBox will "pass USB devices to FreeDOS as if they were older &#8216;normal&#8217; devices."  If there were "guest additions" for DOS, that might handle it, but I don't believe there are.

---

### Post by jwbrase on 2009-02-27
> **yther said:**
> I would think you probably need good, old-fashioned device drivers for DOS.  DosBox (being designed for games) may handle some things automatically, but the others won't.  A USB mouse driver should be fairly easy to find (google "freedos usb mouse" for example), and as for your USB audio, try the manufacturer's web site, or the site of whoever makes the chips that are in it, and Google of course.

It may take a little fiddling with CONFIG.SYS, but it should probably be possible.

This is for running FreeDOS in VirtualBox, BTW.  That will likely be the most flexible environment for your customized setup.  I don't think VirtualBox will "pass USB devices to FreeDOS as if they were older &#8216;normal&#8217; devices."  If there were "guest additions" for DOS, that might handle it, but I don't believe there are.

And you don't know of anything other than Dosbox that allows adjustment of the processor speed of the virtual CPU?

---

