---
title: "require password to mount drives"
date: 2011-02-02
forum: Security
---

### Post by paul3200 on 2011-02-02
i have a triple boot of windows XP,7 and ubuntu 10.10 netbook remix

is it possible to require a password to mount the windows drives

there is no log on password on the ubuntu but i dont want people to access the other drives unless they have my password

---

### Post by WinstonChurchill on 2011-02-02
> **paul3200 said:**
> i have a triple boot of windows XP,7 and ubuntu 10.10 netbook remix

is it possible to require a password to mount the windows drives

there is no log on password on the ubuntu but i dont want people to access the other drives unless they have my password
You might try this: [http://ubuntuforums.org/showpost.php?p=5522236&postcount=6](http://ubuntuforums.org/showpost.php?p=5522236&postcount=6)

---

### Post by Morbius1 on 2011-02-02
Another possibility:

Edit the policykit file as root:
```
gksu gedit /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla

```Find the following section at the top:
 >    [Mounting, checking, etc. of internal drives]
    Identity=unix-group:admin
    Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*
    ResultActive=yesComment out the last line and add a new one so that section looks like this:
>     [Mounting, checking, etc. of internal drives]
    Identity=unix-group:admin
    Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*
    **[COLOR=Blue]#[/COLOR]**ResultActive=yes
    **[COLOR=Blue]ResultActive=auth_admin_keep[/COLOR]**There's no need to reboot so you'll know instantly if it works.

---

### Post by paul3200 on 2011-02-03
cheers Morbius1 did this first and it worked straight away

---

