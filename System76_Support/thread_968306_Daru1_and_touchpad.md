---
title: "Daru1 and touchpad"
date: 2008-11-02
forum: System76 Support
---

### Post by perce on 2008-11-02
I've just installed Intrepid, and Fn-F9 doesn't switch the touchpad off anymore. This is not a surprise: it happened after any upgrade, and it was fixed by adding a line to the touchpad entry of xorg.conf. But now xorg.conf is almost empty, and in particular there is no touchpad entry.

---

### Post by thomasaaron on 2008-11-03
Please file a bug report on this one at launchpad.net/system76.
Please include if the function key combination is producing a keycode.
Also, please confirm that you are using the standard US keyboard layout.

---

### Post by perce on 2008-11-03
The key combination does not produce any keycode. I'm using a standard US keyboard layout. Before filing the report om the launchpad, I'd like to see if it produces any ACPI event, but I don't remember how to do it.

---

### Post by thomasaaron on 2008-11-03
tail -f /var/log/acpid

---

### Post by perce on 2008-11-04
I'm sorry, /var/log/acpid does not exist on my computer

---

### Post by thomasaaron on 2008-11-04
Ah! I upgraded, and /var/log/acpid is still there, but is inactive!

Try running...
```
acpi_listen
```

---

### Post by perce on 2008-11-04
On acpi_listen Fn-F9 returns:

hotkey ATKD 0000006b 0000001f

and so on: it adds 1 every time I press it. I'm filing the bug report.

---

### Post by thomasaaron on 2008-11-04
I've seen some other reports of bad keymapping in Intrepid (although this is the first I've heard of it on our machines). I wouldn't be surprised if this one gets fixed from upstream pretty quickly.

At any rate, it should be pretty simple to fix. We'll have a look at it next week (once we get finished bailing out everyone with hosed upgrades :lolflag:)

---

