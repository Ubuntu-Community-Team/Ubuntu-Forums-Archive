---
title: "[VMware 7 + Guest Ubuntu 9.10] extra mouse buttons don't work"
date: 2009-12-06
forum: Virtualisation
---

### Post by Flake Remix on 2009-12-06
Hello guys.

Previously in such cases I just altered xorg.conf and changed mouse protocol from "ps/2" to "imps/2". Since there is no xorg.conf by default, I may be wrong with mouse identifier, either "Configured Mouse" is wrong one or I'm missing something else. [FONT="Courier New"]xev[/FONT] reacts on all the buttons, even the wheel, but not those two side buttons. This is my mouse:
[[IMG]http://i45.tinypic.com/2nrones.jpg[/IMG]]("http://www.microsoft.com/hardware/mouseandkeyboard/ProductDetails.aspx?pid=086")

So I have created a new [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] and put this into it, nothing else:

```
Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "imps/2"
EndSection
```

Buttons worked fine with older Ubuntu 7.04, well, because I could always alter xorg.conf.

---

### Post by Flake Remix on 2009-12-13
bump?

---

### Post by Flake Remix on 2010-03-07
Ok, I purchased another mouse:

[[IMG]http://i47.tinypic.com/28tuulk.jpg[/IMG]](http://www.logitech.com/index.cfm/mice_pointers/mice/devices/5845&cl=us,en)

I still can't get back/forward buttons working :( Anyone out there using Ubuntu as a guest OS in VMware?

---

### Post by fjgaude on 2010-03-07
Hey, the last time I had to do anything to get my multi-buttom mouse to work correctly I had this in the xorg.conf file:

```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device"                "/dev/input/mice"
        Option      "Protocol"              "ExplorerPS/2"
        Option      "Emulate3Buttons"       "false"
        Option      "Buttons"               "7"
        Option      "ZAxisMapping"          "4 5"
        Option      "ButtonMapping"         "1 2 3 6 7 4 5"
EndSection
```

I've not had to do this for a long time, since maybe 8.04.

Good luck!

---

### Post by dcstar on 2010-03-08
> **Flake Remix said:**
> 
.........
I still can't get back/forward buttons working :( Anyone out there using Ubuntu as a guest OS in VMware?

I assume you have these packages installed:

xserver-xorg-input-vmmouse
xserver-xorg-video-vmware

as well as VMware tools running on the client?

---

### Post by fjgaude on 2010-03-09
I have Ubuntu 10.4 running in Player 3.0.1... the back and forward mouse buttons don't work. I'm going to leave it as is until the release in late April.

As host, 9.10 works fine with the mouse buttons. Haven't tried it with a VMware guest.

---

### Post by Flake Remix on 2010-04-21
> **fjgaude said:**
> Hey, the last time I had to do anything to get my multi-buttom mouse to work correctly I had this in the xorg.conf file:


That doesn't work, xev still doesn't print any events from extra buttons.

> **dcstar said:**
> I assume you have these packages installed:

xserver-xorg-input-vmmouse
xserver-xorg-video-vmware

as well as VMware tools running on the client?

Yes, all these are installed. I can drug'n'drop files and copy-paste between host and guest os.

---

### Post by Flake Remix on 2010-04-29
Damn, in 10.04 buttons don't work either :(

---

### Post by Flake Remix on 2010-04-29
bump

---

### Post by MortenCB on 2010-05-01
I also have this problem.  Would love to get my Logitech G5 mouse to work, including the thumb-button.  

Out of the box, it works with scrolling, but I would really love for the thumb-button to work as well...

---

### Post by Preformed Cone on 2010-06-23
Add: 

mouse.vusb.enable = "TRUE"

to your ubuntu .vmx file.

---

### Post by vandi423 on 2010-12-28
First time Ubuntu user. Was having the same problem under VMware with my MX Revolution.

Adding: 

mouse.vusb.enable = "TRUE"

to my ubuntu .vmx file did the trick. Thanks!

---

### Post by viljoviitanen on 2011-04-05
Please mark this thread solved, mouse.vusb.enable = "TRUE" did the trick for me too! Vmware workstation 7 on Windows 7 host, Ubuntu 10.10 guest.

---

### Post by hardnrg on 2011-05-15
Just wanted to say thanks to Preformed Cone, this also worked for me, using Win7 host, VMware Workstation 7, Ubuntu 11.04, and a Logitech M510 (wireless with 7 buttons: i.e. 2 sides and tilt-wheel in addition to standard left, right, middle and scrollwheel)

This fix gives me the back/forward default action in Firefox from the side buttons... it doesn't make the tilt-wheel work, but I really don't care about that... it's just the back/forward functionality that I want and need

nice :)\\:D/

---

### Post by vitalitytri on 2012-01-30
Fixed my problem as well, thanks very much!

---

