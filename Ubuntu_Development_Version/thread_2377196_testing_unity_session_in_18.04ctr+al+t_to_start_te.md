---
title: "testing unity session in 18.04/ctr+al+t to start terminal doesn't work"
date: 2017-11-10
forum: Ubuntu Development Version
---

### Post by monkeybrain20122 on 2017-11-10
It works only if install xserver-xorg-synaptic but even then have to press the keys really hard (in gnome session no extra force required)

Edited: same issue in Artful.

---

### Post by ventrical on 2017-11-10
Working good here and I have proposed = on.

---

### Post by monkeybrain20122 on 2017-11-10
> **ventrical said:**
> Working good here and I have proposed = on.

It "works" but have to wait really long and press really hard for the terminal to show up. Not so in Ubuntu 16.04 or 18.04 gnome session. This is from yesterday's daily iso (not an upgrade from 17.10) and I also enabled proposed.

P.S As indicated this happens also in unity session of 17.10 and I have tested it (17.10) on two different machines so it is not my hardware.

Edited: just to be sure, I removed the package xserver-xorg-input-synaptics and rebooted. It turns out that it does "work" but in the same sluggish fashion (press really hard and wait really long) so whether xxis is installed makes no difference here. But I can't test unity-session without it installed since otherwise tab for click doesn't work and clicking constantly drives me insane and also with libinput I can't enable edge scrolling and two finger scrolling together even with a script that again drives me up the wall,---xxis works on gnome-xorg as both edge and two finger scrolling work once script is run but not surprisingly not on Wayland)

---

### Post by ventrical on 2017-11-10
> **monkeybrain20122 said:**
> It "works" but have to wait really long and press really hard for the terminal to show up. Not so in Ubuntu 16.04 or 18.04 gnome session. This is from yesterday's daily iso (not an upgrade from 17.10) and I also enabled proposed.

P.S As indicated this happens also in unity session of 17.10 and I have tested it (17.10) on two different machines so it is not my hardware.

Edited: just to be sure, I removed the package xserver-xorg-input-synaptics and rebooted. It turns out that it does "work" but in the same sluggish fashion (press really hard and wait really long) so whether xxis is installed makes no difference here. But I can't test unity-session without it installed since otherwise tab for click doesn't work and clicking constantly drives me insane and also with libinput I can't enable edge scrolling and two finger scrolling together even with a script that again drives me up the wall,---xxis works on gnome-xorg as both edge and two finger scrolling work once script is run but not surprisingly not on Wayland)

I had this problem early on in the 17.10 cycle. I forget where I filed the bug. What had happened is that I changed from gdm3 to lightdm and tried to get back to gdm3. Nothing could fix them except a fresh install.  So  I had install with 17.10 and I had no problem with terminal  ctrl+alt+t as long as I leave gdm3 alone. 

I had installed full 18.04 .ISO and it worked beautiful (ctrl+alt+t) in wayland. Installed lightdm and can't get wayland now. I think there is a problem that gdm3 will not re-install correctly. I don't know if you had this problem.

regards.

---

### Post by monkeybrain20122 on 2017-11-10
I have not installed lightdm. Did you install xserver-xorg-input-synaptics?

---

### Post by ventrical on 2017-11-11
> **monkeybrain20122 said:**
> I have not installed lightdm. Did you install xserver-xorg-input-synaptics?

Nope.

---

### Post by monkeybrain20122 on 2017-11-12
I find something interesting. If press ctr+alt+t together then terminal doesn't start or need to press very hard perhaps several times. But if press t with a very very tiny, almost imperceptible delay after ctr+alt (still holding down ctr+alt) then it starts right the way without extra effort. 

Strange

---

### Post by ventrical on 2017-11-12
I created an .ISO  here: [http://people.ubuntu.com/~twocamels/?_ga=2.149497846.1161564998.1510407443-1546152944.1510407443](http://people.ubuntu.com/~twocamels/?_ga=2.149497846.1161564998.1510407443-1546152944.1510407443)

it is stock <ubuntu-unity-amd64.iso>

I have  permission to  build and distribute from Canonical Legal.

> 
I find something interesting. If press ctr+alt+t together then terminal  doesn't start or need to press very hard perhaps several times. But if  press t with a very very tiny, almost imperceptible delay after ctr+alt  (still holding down ctr+alt) then it starts right the way without extra  effort. 

Strange 		


That could happen on most any system <scan codes> if IRQ requests are competing for the same interrupt but I don't really know why it would happen on unity. I coul dbe a resource problem or problem with systemd. I do know that I had it happen on several installs during 17.10

---

### Post by Chanath on 2017-11-13
> **ventrical said:**
> I created an .ISO  here: [http://people.ubuntu.com/~twocamels/?_ga=2.149497846.1161564998.1510407443-1546152944.1510407443](http://people.ubuntu.com/~twocamels/?_ga=2.149497846.1161564998.1510407443-1546152944.1510407443)

it is stock <ubuntu-unity-amd64.iso>

I have  permission to  build and distribute from Canonical Legal.

Would you start a new thread on this?
It is legally sanctioned and it is 18.04.

---

### Post by monkeybrain20122 on 2017-11-13
> **ventrical said:**
> I created an .ISO  here: [http://people.ubuntu.com/~twocamels/?_ga=2.149497846.1161564998.1510407443-1546152944.1510407443](http://people.ubuntu.com/~twocamels/?_ga=2.149497846.1161564998.1510407443-1546152944.1510407443)

it is stock <ubuntu-unity-amd64.iso>

I have  permission to  build and distribute from Canonical Legal.0

Nice. Is a unity flavour for 18.04 on the table?


> That could happen on most any system <scan codes> if IRQ requests are competing for the same interrupt but I don't really know why it would happen on unity. I coul dbe a resource problem or problem with systemd. I do know that I had it happen on several installs during 17.10

Tried your iso, still the same. Again a small delay of +t while holding ctr+alt works.

---

### Post by ventrical on 2017-11-13
> **monkeybrain20122 said:**
> Nice. Is a unity flavour for 18.04 on the table?


Things have been moving lightning fast on this. I'm stunned.

Regards..

---

### Post by ventrical on 2017-11-13
> **Chanath said:**
> Would you start a new thread on this?
It is legally sanctioned and it is 18.04.

All the i's have been dotted and the t's crossed. Just have to wait for confirm. it is legally sanctioned remix atm.

---

### Post by Chanath on 2017-11-13
> **ventrical said:**
> All the i's have been dotted and the t's crossed. Just have to wait for confirm. it is legally sanctioned remix atm.

So,let's have a separate thread.:)

---

