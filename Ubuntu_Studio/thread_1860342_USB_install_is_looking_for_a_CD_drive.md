---
title: "USB install is looking for a CD drive"
date: 2011-10-14
forum: Ubuntu Studio
---

### Post by coldcaption on 2011-10-14
Howdy!
I've had a rough time getting Linux on my ThinkPad X120e. Linux Mint is the only one that's actually gone far enough to install now, but it was plagued by random, unpredictable freezes, which I'm hoping can be attributed to Mint and not all Ubuntu versions on this hardware.
Anyway, since Studio uses Gnome and comes with apps I'll use, I want to give it a shot. It boots to the alternative installer just fine, but the installer seems tuned to loading files from an optical drive. My machine doesn't have one, and I only have a 1 GB USB stick to use as install media. Can anyone suggest a work around? Thank you!

---

### Post by sgx on 2011-10-14
> **coldcaption said:**
> Howdy!
I've had a rough time getting Linux on my ThinkPad X120e. Linux Mint is the only one that's actually gone far enough to install now, but it was plagued by random, unpredictable freezes, which I'm hoping can be attributed to Mint and not all Ubuntu versions on this hardware.
Anyway, since Studio uses Gnome and comes with apps I'll use, I want to give it a shot. It boots to the alternative installer just fine, but the installer seems tuned to loading files from an optical drive. My machine doesn't have one, and I only have a 1 GB USB stick to use as install media. Can anyone suggest a work around? Thank you!

Howdy, put this in google

unetbootin flash drive ubuntu

I would go in the bios, and shut off all non-essentials, acpi, powermanagement, networking, bluetooth, and from ubuntu, disable screenlocking, screensaver, cpu scaling, anything that might dare to twitch.

Use synaptic to get rid of office and other bloatware, 3D GUIs,
my /usr/bin folder is 347 meg, I'll bet mint is a hair larger.:popcorn:
(I use mint 11 on a laptop and offffficially hate all laptops) :)
Cheers

---

### Post by coldcaption on 2011-10-14
I wouldn't then need to leave all my BIOS bells and whistles turned off afterward though, right? I like them when I'm not installing software! I also do use unetbootin, and run the integrity checks on new 'burns' once they're booted. I've already tried installing Kubuntu since posting this, and if my bootloader woes are solved soon, I may install Studio over it. Thank you!

---

### Post by sgx on 2011-10-14
Hi, you can turn them on as desired, if something fails that worked
moments ago, you have a trail you can doubleback on to check.

put

mint4win 2011 "mint 11"

in google gets you links for a windows
installer to put mint 11 on a windows partition, with a boot menu to choose which OS to launch. Uninstalls are also simple. Mint will see
your windows partition as a folder called 'host', with drag/drop etc

Cheers

---

