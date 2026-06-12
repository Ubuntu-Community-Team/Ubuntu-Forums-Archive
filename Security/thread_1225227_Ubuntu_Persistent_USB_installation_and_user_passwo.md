---
title: "Ubuntu Persistent USB installation and user password"
date: 2009-07-28
forum: Security
---

### Post by weissnich on 2009-07-28
Hi,

I have installed Ubuntu Persistent on my usb stick following the instructions from pendrivelinux, now I wanted to set a password for user ubuntu (passwd ubuntu) but I still can get sudo access without getting asked for a password, can anybody help?

---

### Post by cdenley on 2009-07-28
It is probably just re-using a timestamp. Either wait 15 minutes or run this command:
```

sudo -K

```

---

### Post by weissnich on 2009-07-28
If I login again the user ubuntu still has no password.

---

### Post by cdenley on 2009-07-28
> **weissnich said:**
> If I login again the user ubuntu still has no password.

Are you not required to provide a password when logging in, or when using sudo? The first time you use sudo, you are prompted for a password. By default, after using sudo successfully, you can then use sudo for the next 15 minutes without providing a password.

If you want to force a password to be required every time sudo is used:
```

sudo EDITOR=gedit visudo

```
Change this line, adding the red text.
```

Defaults	env_reset**[COLOR="Red"],timestamp_timeout=0[/COLOR]**

```
Save, close.

---

### Post by weissnich on 2009-07-28
I disabled automatic login and for user ubuntu I am not required to provide a password and for sudo also I don't need a password.
Has something to do with this special pendrive edition, passwd user seems to work, but somehow it is not recognized.

---

### Post by cdenley on 2009-07-28
> **weissnich said:**
> I disabled automatic login and for user ubuntu I am not required to provide a password and for sudo also I don't need a password.
Has something to do with this special pendrive edition, passwd user seems to work, but somehow it is not recognized.

For the hardy livecd (and perhaps your pen drive), sudo is configured to not require a password at all. If that is the case, you can change that by running this command
```

sudo EDITOR=gedit visudo

```
and REMOVING the red text
```

%admin ALL=(ALL) **[COLOR="Red"]NOPASSWD:[/COLOR]** ALL

```

Also, the terminals are also configured to login automatically (/etc/event.d/tty1-6). For gdm, it should just be autologin and timed login.

---

### Post by weissnich on 2009-07-28
Thanks, this helped, now a password is required, but after a reboot all this is lost and I have again to set a password for the user ubuntu.
Maybe someone knows how to store this in ubuntu 9.04 persistent (from pendrivelinux.com).

---

### Post by cdenley on 2009-07-28
> **weissnich said:**
> Thanks, this helped, now a password is required, but after a reboot all this is lost and I have again to set a password for the user ubuntu.
Maybe someone knows how to store this in ubuntu 9.04 persistent (from pendrivelinux.com).

Apparently your whole filesystem isn't persistent. Perhaps only your /home directory is. I haven't really used any pendrive optimized configurations.

---

