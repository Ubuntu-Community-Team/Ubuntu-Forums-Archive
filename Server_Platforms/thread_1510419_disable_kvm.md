---
title: "disable kvm"
date: 2010-06-15
forum: Server Platforms
---

### Post by pedraxito on 2010-06-15
hi, im using ubuntu server 10.04

im using virtualbox but i want to disable kvm because everytime i reboot my server i have to unload manually this module and start manually vboxdvr ... so how can i disable kvm module?

---

### Post by beowulf1416 on 2010-06-15
have you tried uninstalling?

---

### Post by linux-hack on 2010-06-15
try this : 

```
man update-rc.d
```

---

### Post by metalf8801 on 2010-06-22
I've just been using the command 
sudo rmmod kvm-intel 

I do have to do that every time I start Virtualbox but there is a way to make it permanent by black linking kvm 

here's where I found this originally and it should be noted that was from a Fedora forum which may or may not matter 
[http://forums.fedoraforum.org/showthread.php?t=225292](http://forums.fedoraforum.org/showthread.php?t=225292)

I hope this helps 
Dan

---

