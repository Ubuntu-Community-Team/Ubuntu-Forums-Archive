---
title: "kvm permission denied"
date: 2008-04-07
forum: Virtualisation
---

### Post by -random on 2008-04-07
dudea@64BiTuBuNtU:~$ sudo adduser alrich kvm
[sudo] password for dudea:
Adding user `dudea' to group `kvm' ...
Done.
dudea@64BiTuBuNtU:~$ kvm -no-acpi -m 512 -cdrom /media/sdb1/dc/images/ubuntu32.iso -boot d roar.img
open /dev/kvm: Permission denied
Could not initialize KVM, will disable KVM support

[http://ubuntuforums.org/archive/index.php/t-350691.html](http://ubuntuforums.org/archive/index.php/t-350691.html)

iv'e read that sudo kvm -no-acpi -m .....etc works, but i don't want to run the virtual machine with user privelages.

any help! fankz:-({|=

---

### Post by -random on 2008-04-07
So... iv'e got both vista and hardy running in virtualbox,

but don't think i should mark this thread as solved since it isn't a sollution. Don't mind 4 the sollution now... so can a lucky moderator plz delete this thread?

thkx!

---

### Post by Loïc2 on 2008-09-23
Tou can just add yourself to the kvm group to get the permissions.

```
sudo adduser Your_Login kvm
```

Don't forget you need to reconnect before it work - logout/login or, simply :

```
su Your_Login
```

---

