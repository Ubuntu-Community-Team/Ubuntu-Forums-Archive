---
title: "greeter says ubuntu session selected but actually ubuntu-wayland"
date: 2017-07-18
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-07-18
This is what happens on first login of a fresh install.
The only way to get an ubuntu session is to log out, switch selected to wayland on ubuntu, switch back to ubuntu.

However if you shutdown or reboot from a wayland session, next time at greeter it will again say ubuntu but really it's ubuntu-wayland.

bug here, maybe wrong source, maybe already filed elsewhere
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1705157](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1705157)

---

### Post by corradoventu on 2017-07-19
I have the same problem on 2 installations from:
Ubuntu 17.10 "Artful Aardvark" - Alpha amd64 (20170717)
Ubuntu 17.10 "Artful Aardvark" - Alpha amd64 (20170710)

---

### Post by rrnbtter on 2017-07-19
Greetings,
since Ubuntu 17.10 resolves to Gnome Desktop on Wayland it seems to me that Ubuntu means Wayland. 

Option 1: Ubuntu , gets
x11
wayland

and 
Option 2: Ubuntu on wayland, gets
wayland
wayland

Either way it is wayland. 
You won't be able to install a x11 .deb under option 2.

---

### Post by mc4man on 2017-07-19
> **rrnbtter said:**
> Greetings,
since Ubuntu 17.10 resolves to Gnome Desktop on Wayland it seems to me that Ubuntu means Wayland. 

Option 1: Ubuntu , gets
x11
wayland

and 
Option 2: Ubuntu on wayland, gets
wayland
wayland

Either way it is wayland. 
You won't be able to install a x11 .deb under option 2.

No, ubuntu(default) should be, (and is) X11, ubuntu on wayland is wayland. 

The issue is it always resets to ubuntu irregardless of last session used.

---

### Post by mc4man on 2017-09-14
Should be fixed in upcoming gdm3 package, both in regards to log outs & 1st. login after install 
(- later won't be testable until new image containing shows up, either tomorrow or early next week..

---

### Post by Chanath on 2017-09-14
> **mc4man said:**
> This is what happens on first login of a fresh install.
The only way to get an ubuntu session is to log out, switch selected to wayland on ubuntu, switch back to ubuntu.

However if you shutdown or reboot from a wayland session, next time at greeter it will again say ubuntu but really it's ubuntu-wayland.

Could you explain this?
I have Ubuntu and Ubuntu  on Xorg. If I reboot/shutdown after using Ubuntu, it'd boot again to Ubuntu, and vice versa. 
> $ echo $DESKTOP_SESSION
ubuntu


What do you mean by ubuntu-wayland here? Isn't default Ubuntu is on Wayland?

---

### Post by mc4man on 2017-09-14
> **Chanath said:**
> 


What do you mean by ubuntu-wayland here? Isn't default Ubuntu is on Wayland?
When this thread was started & when this bug first appeared the choices where different

---

