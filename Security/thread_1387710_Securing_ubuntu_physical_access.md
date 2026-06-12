---
title: "Securing ubuntu physical access"
date: 2010-01-22
forum: Security
---

### Post by Draggygarg on 2010-01-22
Hello gurus, I am a new guy here.

Basically I am running a server powered by Ubuntu on the first floor of my house(I live in the ground floor), now the first floor is also a guest house(Ran by my father) and we have a lot of strangers coming by. Now I do not want anyone to fiddle by, so my question being, how can I stop anyone undesired from physically accessing it and fiddling it with.

Running Ubuntu 9.10 with Gnome

My ideas were to lock the GUI, have a GRUB bootloader p/w and have a BIOS p/w. Now I know how to lock the BIOS, but I cannot get GRUB to have a p/w for changing the boot parameters as I don't have the grub-md5-crypt command on my machine. Also how would I go about locking the GUI(So that anyone know wants to enter the computer will have to enter the user's password in order to unlock it, but the server and the services will keep running)? Any other ideas that are effective?

Thanks a lot! :)

---

### Post by Sarmacid on 2010-01-22
Not sure about the grub, I think grub-md5-crypt worked on grub 1.5 and must have changed in grub 2.

About the screen locking, unless you have compiz, the shortcut ctrl + alt + L will work, or you can customize your own in System -> Preferences -> Keyboard shortcuts.

---

### Post by cdenley on 2010-01-22
You don't need to be logged in for the server processes to run. In fact, on a server, you should not be logged in unless you are actually working on it. Simply don't log in (or log out), and nobody can use it without a password unless they boot another device or use recovery mode.

The only effective way of protecting from physical access is to use full disk encryption. Disabling CD/USB booting, locking BIOS, and locking GRUB would stop casual users and slow down expert users, though. Even with encryption, I'm not sure it would be considered "safe" from physical access if you leave it decrypted with keys in memory all day, though.

---

### Post by Draggygarg on 2010-01-22
Is grub md5 crypt like any other md5? Or is it some special hash.

@cdenly, really? You mean services like samba and apache would run? My concern is that curious passbyers may try to fiddle with the computer, especially kids and I want to prevent that. Even shutting down/restarting.

---

### Post by cdenley on 2010-01-22
> **Draggygarg said:**
> 
@cdenly, really? You mean services like samba and apache would run? My concern is that curious passbyers may try to fiddle with the computer, especially kids and I want to prevent that. Even shutting down/restarting.

Yes, samba and apache start at boot. You don't need to log in. You may be able to shutdown by pressing the power button or restart with ctrl+alt+del. If so, I'm pretty sure you can disable this, but what is the point? They can always pull the plug if they want to shutdown or reboot.

---

### Post by doas777 on 2010-01-22
never underestimate the power of a locked door, with a reinforced window (so you can see if anyone is in there that shouldn't be).

---

### Post by Draggygarg on 2010-01-22
Thy cannot pull the plug since the box is inside a locked almirah, how can I disable those?

---

### Post by cdenley on 2010-01-22
> **Draggygarg said:**
> Thy cannot pull the plug since the box is inside a locked almirah, how can I disable those?

Lock up your chassis and keyboard as well. Usually the power button can power off the motherboard by holding it down for 5 seconds, which cannot be disabled with software. You may be able to configure this in BIOS, but usually not.

You can comment out the last line in these 2 files to prevent a ctrl+alt+del restart or a power button press ACPI shutdown.

/etc/acpi/powerbtn.sh
/etc/event.d/control-alt-delete

---

### Post by Draggygarg on 2010-01-22
Thanks for the tips, I'll get on securing it :)

---

### Post by EJeanmaire on 2010-01-22
Buy one of those enormous carnival stuffed animals, gut it, and stuff your computer in there; perfectly safe in there

---

### Post by cariboo on 2010-01-22
If you are running a server, there is no need to have a keyboard and monitor connected to it. This will stop most people from trying anything. If you case is lockable, lock it. Before putting the server in service, make sure the bios is only set to boot from the hard drive. Also set the system up so that X doesn't start at boot. If you do need a gui interface, you can always run startx from the prompt.

---

