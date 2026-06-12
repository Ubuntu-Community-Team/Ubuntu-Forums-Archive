---
title: "Touchpad doesn't work in Ubuntu and derivatives"
date: 2017-05-22
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-05-22
In my laptop, Medion e6239T, the touchpad doesn't work with Ubuntu. I haven't tried with any other distros, except Ubuntu based ones. It doesn't work in any Ubuntu flavour. Googled, and found that it doesn't work in many types of laptops. In a way, this problem doesn't trouble me much as the laptop has a touch screen, but its a problem to those, who use the touchpad rather than the mouse. Do you guys have this problem, and is there a solution for this?

---

### Post by Chanath on 2017-06-23
$ synclient
> 
Couldn't find synaptics properties. No synaptics driver loaded?
cat /proc/bus/input/devices doesn't show the touchpad. 
I know from the Windows installation that touchpad is seen as PS/2 mouse

Here is the dmesg [https://paste.ubuntu.com/24930714/](https://paste.ubuntu.com/24930714/)

can anyone help?

---

### Post by ventrical on 2017-06-23
I have an old Toshiba Satalite L300. The touchpad works somewhat but it will not scroll the icons in gnome-shell. It does that on HP laptops too.

Regards..

---

### Post by Chanath on 2017-06-23
> **ventrical said:**
> I have an old Toshiba Satalite L300. The touchpad works somewhat but it will not scroll the icons in gnome-shell. It does that on HP laptops too.

Regards..

This is a somewhat new laptop, bought new last year, but had been lying in a warehouse for sometime. I had checked with the manufacturers too. Even though they don't support Linux, they asked me to check whether xserver-xorg-input-libinput is installed. Its installed. The touchpad is from Synaptics. Then tried 
$ synclient

> The program 'synclient' is currently not installed. You can install it by typing:sudo apt install xserver-xorg-input-synaptics

Installed xserver-xorg-input-synaptics
Then tried $ synclient
and got > Couldn't find synaptics properties. No synaptics driver loaded?
Back to phase one. 

In a way, with touchscreen and the mouse working, not having the touchpad working is not much of a problem, but only a reminder that in some laptops, the full Linux experience cannot be achieved. Something I don't like to feel. Anyway, I have an older laptop, about 6 years, a Lenovo, and in that all Linux distros I put in there works. 

What I'd like to know is, how to get the synaptics driver to start.

---

### Post by dino99 on 2017-06-23
Have you tried some custom config ?  [https://wiki.archlinux.org/index.php/Touchpad_Synaptics](https://wiki.archlinux.org/index.php/Touchpad_Synaptics)
You might also test with the latest release (artful) & kernel (4.12) as usual with recent hardware.
and also try debugging: [https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection)

an old request: [https://askubuntu.com/questions/262287/synaptic-touchpad-on-laptop-not-working](https://askubuntu.com/questions/262287/synaptic-touchpad-on-laptop-not-working)

---

### Post by Chanath on 2017-06-23
Yes, I went trough the Arch wiki. The manufacturer sent me that page.
> unable to find device SynPS/2 Synaptics TouchPad

Yes, went through the [https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection) page too. And the Ask Ubuntu pages too. Nothing helped.

I am using 17.10 64bit (Ubuntu, Xubuntu, Openbox etc), but with kernel 4.10.0-22-generic, the default. Maybe, I'll try to install kernel 4.12 later in the evening. Can't do it now, as its working time. Maybe this is some nutty laptop.

---

### Post by Chanath on 2017-07-05
Installed kernel 4.12 yesterday. Couldn't do it earlier. But the touchpad is not working.:(

---

### Post by rrnbtter on 2017-07-05
Greetings,
I'm getting this

cat /proc/bus/input/devices
I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=9
B: EV=b
B: KEY=6420 30000 0 0 0 0
B: ABS=260800011000003

and this
rrnbtter@rrnbtter-110-15ISK:~$ synclient
The program 'synclient' is currently not installed. You can install it by typing:
sudo apt install xserver-xorg-input-synaptics

This is on a late model Lenovo Ideapad and everything is perfect Touch Pad, FN Keys, and all. There is some validity to the idea of using Linux OS on qualified equipment. There are some vendors that have a better Linux track record than others. The only issue I have with this system is that I have to manually install RTL Wifi drivers when I change kernels. My wife has a slightly updated version of the same laptop and she has no problems whatever.

---

### Post by Chanath on 2017-07-06
Hi,

$ [COLOR=#000000]cat /proc/bus/input/devices
I don't get
[/COLOR][COLOR=#000000]N: Name="SynPS/2 Synaptics TouchPad"
[/COLOR][COLOR=#000000]at all. Its s though the touchpad is not there. 

[/COLOR]$ synclient
Couldn't find synaptics properties. No synaptics driver loaded?

Both xserver-xorg-input-synaptics and xserver-xorg-input-libinput were installed. Uninstalled input-synaptics, reinstalled input-libinput, but nothing happened.


I have Lenovo laptops, and the touchpad works out of the box. It doesn't work with this Medion laptop, even though Medion is owned by Lenovo. I have to live with it, I believe.

---

### Post by ventrical on 2017-07-12
> **ventrical said:**
> I have an old Toshiba Satalite L300. The touchpad works somewhat but it will not scroll the icons in gnome-shell. It does that on HP laptops too.

Regards..

OK. I got it working (scroll) on my L300. There is this sort of demarcation line to the right on the touch pad and  half of your finger has to be on the smooth frame and the other half on the touchpad and it will scroll. I don't know yet if the sensitivity is adjustable.

---

