---
title: "uninstalling vmware player 3.0.1"
date: 2010-07-16
forum: Virtualisation
---

### Post by yasiralthubaiti on 2010-07-16
according to vmware player guide, to uninstall you have to enter the following command in the terminal:
```
vmware-installer -u vmware-player
```

but after i enter the command the following message appears:

[COLOR="DarkRed"]root access is required for the operations you have chosen.
[/COLOR]
how to solve this?

---

### Post by wahr on 2010-07-16
don't forget "sudo" before that command to run it as root : )

you will be prompted for your root password, after which it should execute with no trouble (unless it's broken)

---

### Post by yasiralthubaiti on 2010-07-17
> don't forget "sudo" before that command to run it as root : )

you will be prompted for your root password, after which it should execute with no trouble (unless it's broken)

thanks, ... finally, it worked !! ... i don't know how i forgot about the "sudo" :-k ...

---

