---
title: "Disable scroll lock"
date: 2007-05-23
forum: Server Platforms
---

### Post by Chancellor on 2007-05-23
I found out today that pressing scroll lock on the local console of my 7.04 server will cause the display to freeze until its pressed again... is there a way to disable this?  I use a KVM and this behavior causes all kinds of problems.

Do I need to recompile the kernel or is there a kernel option I can pass to disable scroll lock usage?

---

### Post by dxdemetriou on 2007-05-23
I have this problem too, but some times is useful if I want to freeze the screen to see some error :)
I am using the button most times I am not sure, except the shutdown/restart from gnome, when I press 2 times the scroll lock immetiatelly after I press the button it don't freeze
I hope somebody to know something, or even configurable kvms, or something

---

### Post by craigp84 on 2007-05-24
I don't think you're grasping the idea of "scroll lock".

Nonetheless, editing /etc/console-tools/remap to include the following line will make Linux see it as a ctrl key.

```
s/keycode 70 = Scroll_Lock/keycode 70 = Control/;
```

See the comments in /etc/console-tools/remap for more details, also see the output of dumpkeys, and read up on "man sed" if you're struggling to make it work (most likely due to whitespace).

Hope this helps,

-c

---

