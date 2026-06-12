---
title: "[SOLVED] Optiplex 330 fails to reboot"
date: 2008-08-30
forum: Server Platforms
---

### Post by ScatterBrain on 2008-08-30
I've installed 8.04.1 (Hardy) on a brand new Dell Optiplex 330.  Installation went fine, until the reboot was issued.  The machine failed to ever reboot.  I ended up powering the machine off and then back on to continue.

Everytime I tell the machine to reboot with:

```
reboot -n
```it basically goes through all the motions and then then leaves me with a message:

```
Rebooting the system.
```and then just stops.

I'm hoping that someone can help me with this - while I don't expect the machine to be rebooted often, it will be located in a remote location and I will need to reboot it at some point.

Other than the reboot issue, the machine is working fine.

Thanks in advance...

---

### Post by cariboo on 2008-08-30
Check /var/log/messages to see if anything sticks out and maybe try:

```
sudo shutdown -r now
```

to see if it will reboot.

Jim

---

### Post by ScatterBrain on 2008-08-30
> **cariboo907 said:**
> Check /var/log/messages to see if anything sticks out and maybe try:

```
sudo shutdown -r now
```to see if it will reboot.

Jim

The logs look clean - simple shutdown and then a clean start up (manually by me).

I tried the shutdown -r and received the got to the same situation:

```
[...]
* Will now restart
[15665.642096] Restarting system.
```Then a hang.

---

### Post by ScatterBrain on 2008-08-30
Fixed it!  A bit more Googling [turned up this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213754"), which gave me the cure.  I had to add this to the **# kopt** line in** /boot/grub/menu.1st**:

```
reboot=b
```After that, I dropped to a command line and issued:

```
update-grub
```followed by a graceful shutdown and then boom, reboots are back in business.:guitar:


Looks like it has something to do with kernel 2.6.24.

Thanks for all your help!!!

---

