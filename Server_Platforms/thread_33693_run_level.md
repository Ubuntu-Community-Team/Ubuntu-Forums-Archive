---
title: "run level"
date: 2005-05-11
forum: Server Platforms
---

### Post by baza41 on 2005-05-11
Hi,

how do I change the default run level so my Hoary server boots to console rather than Gnome?

Thanx

Baza

---

### Post by Buntu on 2005-05-11
To boot into runlevel 3 once, wait for the grub menu, and select the kernel you want to boot, then press edit and put a 3 behind the kernel image.

For a more permanent solution, edit your grub menu.lst file:

/boot/grub/menu.lst

Copy the default entry, and modify it by putting a 3 behind the kernel version. This way, you can choose between runlevel 3 and 5 when you boot your computer:

title           Ubuntu, kernel 2.6.10-5-386 - Runlevel 3
root            (hd0,4)
kernel          /vmlinuz-2.6.10-5-386 **3** root=/dev/hda6 ro quiet splash
initrd          /initrd.img-2.6.10-5-386
savedefault
boot

---

### Post by Alexander Kirillov on 2005-05-11
[QUOTE=baza41]Hi,

how do I change the default run level so my Hoary server boots to console rather than Gnome?

Thanx

Baza[/QUOTE]
 In ubuntu - unlike RedHat - initlevels 2-5 are identical by default. So if you want to start in console mode, you will need to edit an init level. Search these forums - it had been discussed before.

---

### Post by LordHunter317 on 2005-05-11
Debian runlevels don't work like RH runlevels.

Unless Ubuntu has changed something, every runlevel will boot into a GUI, as 2-5 are identical.

If you want a runlevel that doesn't start X, you'll have to make it yourself.  Look at update-rc.d or edit the symlinks manually.

However, you can just hit Ctrl-Alt-F1 to go to the console.

---

### Post by JonahRowley on 2005-05-11
To change the default runlevel, edit **/etc/inittab**.  Change this line from
```
id:2:initdefault:
```
to
```
id:3:initdefault:
```

Or, since you're running Ubuntu on a server, just don't install Gnome, or X.  There is a *server* install option, which installs only the base system.

---

### Post by baza41 on 2005-05-11
I like to have a gui, because I like to use phpmyadmin :)

Baza

---

### Post by JonahRowley on 2005-05-12
You don't need a GUI to access phpmyadmin, it's server-side..  You can access that from a different machine.  There's not much sense in physically going to your server, starting up a 100 meg desktop environment, launching a 40 meg browser, doing whatever, shutting it all down and going back to your workstation.

Changing it to runlevel 3 won't actually prevent the GUI from loading though.  In Ubuntu, apparently runlevels 2-5 are exactly the same.  So change to runlevel 3 and remove things like alsa and gdm from rc3.d's startup.  To assist you in this, there is the **update-rc.d** script, **man update-rc.d** for more info on that.

---

