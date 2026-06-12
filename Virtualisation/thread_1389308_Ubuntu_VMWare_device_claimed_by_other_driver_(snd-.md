---
title: "Ubuntu VMWare: device claimed by other driver (snd-usb-audio)"
date: 2010-01-24
forum: Virtualisation
---

### Post by adsbaer12 on 2010-01-24
SITUATION:
- The operating system of your computer is Ubuntu 9.10 (64bit)
- You have a USB-microphone connected to your Ubuntu machine
- Within Ubuntu you have VMWare for Linux 64bit installed (including a legit license key!) and you use VMWare to run a virtual Windows XP Pro SP3 (including a legit license key!) system within Ubuntu

PROBLEM:
- The USB-microphone cannot be available at the same time to both your real operating system (=Ubuntu) and VMWare's virtual Windows XP (="second" operating system) and when you run VMWware and boot the virtual Windows XP the following VMWare-message appears:
> "The specified device appears to be claimed by another driver (snd-usb-audio) on the host operating system which means that the device may be in use. To continue, the device will first be disconnected from its current driver."- When VMWare tries to "un-claim" the device from the current driver my entire computer freezes and I have to reset + reboot Ubuntu![U]

We want to use the USB-microphone only within the virtual Windows XP machine (in my case for the purpose of dictating into Dragon Naturally Speaking).[/U]

SOLUTION: blacklist snd-usb-audio
We have to stop Ubuntu from claiming the USB-device! In that way VMWare (and thus VMWare's virtual Windows XP) won't have any issues with two operating systems trying to access the very same device.

- first: close VMWare in case it's still running
- second: edit blacklist.conf...
```
sudo gedit /etc/modprobe.d/blacklist.conf
```- third: ...and add the line "blacklist snd-usb-audio" to the end of the blacklist.conf-file:
```
# prevent snd-usb-audio from claiming usb-mic
blacklist snd-usb-audio
```- four: save changes and REBOOT!
(changes will take effect AFTER reboot, snd-usb-audio will not be loaded then)

When you start VMWare after the reboot you should not see VMWare's device-claimed-by-other-driver-waring-message any longer! Hopes this helps & greetings! :P

[SIZE=1]used software / system requirements:
Ubuntu 9.10 (64bit), 2.6.31-17-generic, all updates up to jan24th2010
VMware-Workstation-Full-7.0.0-203739.x86_64.bundle (with valid license!)
Windows XP Professional SP3 install cd (with valid license!)
USB-Microphone (e.g. Behringer B1 Microphone)[/SIZE]

---

### Post by lidra on 2010-05-28
Thank you soooo much for writing this up. It works on 10.04 as well with VMware server 2.0.2. You saved me some good money with this. Thank you for sharing. Can I use part of your documentation above to write up a documentation on how to use Skype USB adapters ? 

Regards, 

Lidra

---

### Post by adsbaer12 on 2010-06-21
Hi Lidra,

thanks for your post and I'm glad I could help. Feel free to use the post for whatever purpose you desire. After all: information is free ;) Just so you know: I myself did not came up with the original solution, I just Googled it together from several posts around the Internet. So proper credit goes to the "real" authors (whom unfortunately I can't remember).

Regards,

adsbaer12 :p

---

### Post by ghafurjan on 2012-03-19
I have the same problem with video-card.
This massage coming:

The specified device is claimed by another driver (uvcvideo) on the host operating system. The device might be in use. To continue, the device will first be disconnected from its current driver.

I use VMWare workstation 8 and i can not enable directx.
My gust OS is Windows 7 Home 32 bit on Ubuntu 11.10 64 bit.
Can help me somebody how to fix it.

---

### Post by coffeecat on 2012-03-20
Old thread closed.

@ghafurjan, you have started a thread here:

[http://ubuntuforums.org/showthread.php?t=1943676](http://ubuntuforums.org/showthread.php?t=1943676)

Please do not post the same question to different threads. This dilutes community effort.

---

