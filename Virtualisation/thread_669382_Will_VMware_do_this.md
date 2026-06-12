---
title: "Will VMware do this?"
date: 2008-01-16
forum: Virtualisation
---

### Post by Greg Mueller on 2008-01-16
I am setting up an observatory. I had all this stuff worked out with XP but then I got interested in Linux..

The way it was supposed to work...

A main fast XP computer in "the warm room", hooked to 3 other XP computers in the observatory via PCAnywhere. This would allow me to control the three computers from the comfort of a nice warm room, yet they would be semi autonomous, running their own XP apps.

But every time I messed with the hardware on a computer I have to re-register XP.

All the software is very XP specific and try as I may I can only get two of the many apps I need to run under Wine

If I set up VMware on the warm room computer, could I control the other three from there?
Would the three Linux computers be able to run apps off of the warm room XP computer?
Would all the serial and USB ports be functional on the Linux "terminal" computers?

Help very much appreciated

---

### Post by veloce on 2008-01-16
Here's a proposed set up for you:

"cold machines" continue to run XP

"warm machine" runs ubuntu.

From the ubuntu machine you use gnome-rdp to open rdp sessions to the "cold machines".

Not sure if you have xp apps to run on the warm machine.  If so, then use vmware server to create a xp vm on the "warm machine".  I would still connect to this vm using gnome-rdp as it is a cleaner interface.

Does this resolve your issues?

---

### Post by Tanker Bob on 2008-01-16
> If I set up VMware on the warm room computer, could I control the other three from there?
Would all the serial and USB ports be functional on the Linux "terminal" computers?

VMWare can see whatever the host computer/OS can see, as long as you allow the host to share the info. This includes USB, serial, network, etc., so if you allow the VM access, it will use those from the host. If your host can see the other computers on a LAN, so can WMWare. In this case, the host merely shares the network access with the VM. So, PCAnywhere should be able to see and control the other machines on the net, but be sure that you open the appropriate ports on all the firewalls, including the Linux host.

> Would the three Linux computers be able to run apps off of the warm room XP computer?

I'm not sure about running Linux on the 3 cold computers and running apps in a VM on the warm one. At the least, you would have to run a VM on all three, but I'm not sure what PCAnywhere can do remotely with the warm Linux computer under that circumstance. You can download the VMWorkstation or VMServer manual from VMWare and see what they say. I did that before I bought VMWorkstation to ensure that it would do what I wanted. If the warm computer ran XP, I think this scheme would work OK.

I hope that helps.

---

### Post by peitschie on 2008-01-16
Actually its even easier than this!

VMWare allows a single session to be shared amongst multiple hosts... I have successfully set up a network at home where a single linux computer hosts a WinXP VM, and all the other linux computers can connect to the VM and interact with that one session.  Keep in mind though, this is a SINGLE user system in that its like having 3 people sitting at the same computer.  So you can only run one program at a time...  On the other hand, if you simply duplicate the image a few times, and start up multiple instances,  you might be able to give each linux computer their own image.

Are all three linux computers likely to be using the programs at the same time...?

The other option as already talked about might be to use something like SeamlessRDP: [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization).  (Another link which I prefer: [http://www.gobanquet.com/blog/index.php/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/](http://www.gobanquet.com/blog/index.php/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/)).  But again, keep in mind that if everyone wants to run the same program it is like running the same program 3 times on one computer!

---

### Post by Greg Mueller on 2008-01-16
> Are all three linux computers likely to be using the programs at the same time...?

Two of them would be running one of the programs at the same time

(This is the easiest question to answer, I'm still thinking about the answers to the other questions posed.)

---

### Post by peitschie on 2008-01-16
Ahh bugger... I got the setup the wrong way around in my head :???: sorry.

You mean to control 3 Windows XP PC's from one (windows/linux/...) PC?

---

### Post by Greg Mueller on 2008-01-18
I'd actually like the cold PCs to run Linux and be controlled by the XP pc, but I'm having some USB problems running the software with Wine. So I'm trying to figure that out before I really know who's running what.

It would be easiest (I think) to be able to run the app under XP but have the cold computers (Linux) carry the load on their processors. 2 of the cold computers would be running the same app at the same time doing different things with it

If I can just figure out this USB problem I can go on with the quest

---

### Post by ByteJuggler on 2008-01-18
If your cold computer software wants XP and uses USB, then either they run XP naively, or they run XP on a VMWare workstation VM (which supports USB passthru from host to VM), or they run XP on a VirtualBox VM (which I *think* also supports USB passthru.)  Sadly, VMWare Server does not support USB passthrough IIRC.  Edit: Point is, VMWare Workstation = $$$, VMWare Server = free, and I think VirtualBox with USB passthru is also free.  So if you want a free as in gratis solution then VirtualBox is it for USB passthru, if I remember correctly.

On your warm computer, you can then use remote desktop to connect to each of the XP PC's to control them.  No need for PC Anywhere at all.  Remote desktop will likely work better as well.  If you need to have XP specific software on the warm computer as well, then you can likewise install XP on a VM and host it there.

---

### Post by peitschie on 2008-01-18
Just to correct a minor point, VMWare server does actually perform USB passthrough without any extra money being thrown at it ;)

So Greg, your basic setup becomes:
Cold PC1 (Running linux) > Runs WinXP emulated > runs software
Cold PC2 (Running linux) > Runs WinXP emulated > runs software
Cold PC3 (Running linux) > Runs WinXP emulated > runs software

Warm PC (Running WinXP) > Controls 3 cold PC's

The advantage this offers is that changing the hardware on the cold PC's will no longer require reactivation once you get the Windows XP image activated.  When you initially install WinXP on a virtual machine (under Virtual Box for example), it will likely ask you to activate.  Once you do this, you can then just copy the WinXP image onto the other two machines, and won't need to install :)

---

### Post by Greg Mueller on 2008-01-19
That's very interesting.
I'll have to experiment with that. I'm still trying to chase down the "failure to recognize the USB camera" thing.

I need to find a "Usb connections for the total idiot" book   :)

---

### Post by ByteJuggler on 2008-01-19
> **peitschie said:**
> Just to correct a minor point, VMWare server does actually perform USB passthrough without any extra money being thrown at it ;)


Hmm, interesting, I stand corrected.  Will definitely have to play with that now...!!!  (Now I'm slightly puzzled -- did this change recently or have I dreamt that this was only a feature on Workstation at some point?)

---

### Post by Tanker Bob on 2008-01-19
VMWare had USB 1.x support in late version 5, and picked up USB2 support in version 6.

Wine is hit and miss, mostly miss. I've found relatively few things that work well under wine, and those are all very simple programs.

---

