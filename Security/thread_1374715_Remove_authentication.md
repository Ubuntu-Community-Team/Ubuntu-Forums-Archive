---
title: "Remove authentication"
date: 2010-01-07
forum: Security
---

### Post by niyasc on 2010-01-07
How can I remove authentication completely from my pc??
How can I edit the files present in the partician filesystem???:popcorn::(:)

---

### Post by kiranmurari on 2010-01-07
[B][COLOR=Red]Removing authentication completely is not a recommended practice.[/COLOR]

[/B]If you want to login to the machine without providing username password, you can choose "Log in automatically" during installation phase. For creating a paswordless login after installation, please refer to the following link:
[http://ubuntuforums.org/showthread.php?t=513820](http://ubuntuforums.org/showthread.php?t=513820)

You can add the username to the "/etc/sudoers" file for installing stuff whenever you need to without being prompted to enter the password. You add the following to the /etc/sudoers file:
```
$ sudo visudo
# username may pull updates from the repos when he wishes
username ALL=NOPASSWD: /usr/bin/apt-get update

# username may install things whenever he wishes
username ALL=NOPASSWD: /usr/bin/apt-get install *
```Is this what you have been looking for?

Regards,
Kiran

---

### Post by umar_zulfiqar on 2010-11-01
not work for me any help>>>>>>?
i want to disable athuntication for software center and network or proxy settings

---

### Post by cariboo on 2010-11-01
You may find the [RootSudo]("https://help.ubuntu.com/community/RootSudo") page helpful.

---

### Post by sisco311 on 2010-11-01
Create a new pkla file:
```
gksu gedit /var/lib/polkit-1/localauthority/50-local.d/custom.rules.pkla
```

With the following content:
```

[Software Center]
Identity=unix-group:admin
Action=org.debian.apt.*
ResultActive=yes

[Network Manager]
Identity=unix-group:admin
Action=org.freedesktop.NetworkManager.*
ResultActive=yes

[Proxy]
Identity=unix-group:admin
Action=com.ubuntu.systemservice.getproxy;com.ubuntu.systemservice.setproxy
ResultActive=yes

```

For more details see: [http://hal.freedesktop.org/docs/polkit/](http://hal.freedesktop.org/docs/polkit/) and 
```
man pklocalauthority
```

---

### Post by umar_zulfiqar on 2010-11-06
thax for reply no more aythentication for software center but network and proxy wants privileges are required to change gconf system values any help for that>>>>?

---

### Post by sisco311 on 2010-11-08
> **umar_zulfiqar said:**
> thax for reply no more aythentication for software center but network and proxy wants privileges are required to change gconf system values any help for that>>>>?

You're welcome!

How do you change the network and proxy settings?

---

### Post by umar_zulfiqar on 2010-11-09
> **sisco311 said:**
> You're welcome!

How do you change the network and proxy settings?

network connection and network proxy in the system>>>preferences

---

### Post by umar_zulfiqar on 2011-02-27
> **umar_zulfiqar said:**
> network connection and network proxy in the system>>>preferencesok i got it on my own

---

