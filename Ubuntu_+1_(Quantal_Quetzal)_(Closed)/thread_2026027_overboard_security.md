---
title: "overboard security"
date: 2012-07-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ronacc on 2012-07-14
while I understand the importance of security I also know that making it too obtrusive and intrusive only makes people determined to circumvent it . A case in point is startup disk creator , I hardly think it is necessary in a sane OS to require no less than 3 invocations of the sudoers password for the act of creating a startup usb stick . On starting SDC it creates a bogus device (sr1) that must be ejected before you can select the .iso to burn , ejecting the imaginary device requires the sudo password . then if you decide to erase the usb stick before you burn the .iso to it that again requires your password and finally when SDC  goes to install the boot loader it again requires the password . This is so absurd that I had difficulty writing this without resorting to forbidden language .

---

### Post by mc4man on 2012-07-14
This is one of those things that from one perspective, ours, that's excessive in doing one thing, make a startup usb.
From elsewhere there's likes some valid reasons to require auth on the 2 different actions. 
So they're not going to remove those auths & I guess there's no inclination to treat the startup disk creator as a whole, either 1 or no auth

If there is or a new bug on that maybe something would happen, maybe not

On a user note you can just add a .pkla to /var/lib/polkit-1/localauthority/50-local.d  for that to allow without auth


Edit: if so

```
sudo nano /var/lib/polkit-1/localauthority/50-local.d/usb-creator.pkla
```

one way

```
[usbcreator format]
Identity=unix-group:sudo
Action=com.ubuntu.usbcreator.format
ResultActive=yes

[Install bootloader]
Identity=unix-group:sudo
Action=com.ubuntu.usbcreator.bootloader
ResultActive=yes
```

---

### Post by ronacc on 2012-07-14
thanks , I'll do that , but just as I said above excessive security invites circumvention .

---

