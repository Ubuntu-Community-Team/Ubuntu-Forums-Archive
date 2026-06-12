---
title: "Manually mapping brightness function keys (Lemur Ultra)"
date: 2012-09-05
forum: System76 Support
---

### Post by joe4ska on 2012-09-05
Hi everyone,
So I'm a big fan of distrohopping and one of the things that bothers me with my amazing Lemur Ultra is that when trying other non Canonical supported distributions the System76 drivers will not allow you to install them. Distros like LinuxMint, PeppermintOS, WattOS etc.

Xubuntu, Ubuntu Studio, Lubuntu, Kubuntu, no problem everything works flawlessly out of the box.

But as a hopper I must hack away and try Fedora, Arch, Fuduntu, Gentoo or whatever.

So does anyone know where I can find out how to manually configure my Fn keys so that when I hit Fn + F9 and Fn + F10 I'll be able to lower and raise the brightness by say oh 10%?

I'm guessing that buried in the System76 drivers is a .conf file somewere but I'm not sure how to find it on my System in Ubuntu so I can pick it apart and try to adapt it to other distributions.

As you don't mind not having brightness control via Fn keys or the card reader working straight away nearly any distribution will work 100%. Only exception has been wifi under FSF distributions like Trisquel or Parabola.

My sincerest thanks to anyone that can point me in the right direction.

---

### Post by joe4ska on 2012-09-05
Okay i tried to hunt down some information after post based on similar questions

for reference I ran the following commands
> 
$ ls /sys/class/backlight/

acpi_video0  intel_backlight


> $ ls /sys/class/backlight/*/
/sys/class/backlight/acpi_video0/:
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type

/sys/class/backlight/intel_backlight/:
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type


---

