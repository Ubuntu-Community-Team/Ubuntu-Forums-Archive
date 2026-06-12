---
title: "No backlight after suspend"
date: 2013-03-02
forum: Ubuntu Development Version
---

### Post by ping-wu on 2013-03-02
Installed 13.04 into one of the partitions of an Acer Aspire 15.6" notebook.  Problem: No backlight after waking up from suspend.  I can "see" (just barely) the sign-in dialog window, but it was very dark.  This was probably only due to a reflection from the ambient light, the backlight was not turned on.

I have 11.04, 11.10, 12.04LTS, and 12.10 installed on other partitions of the same notebook.  13.04 is the only version that gives the this no-backlight problem.

---

### Post by beidl on 2013-03-03
> **ping-wu said:**
> Installed 13.04 into one of the partitions of an Acer Aspire 15.6" notebook.  Problem: No backlight after waking up from suspend.  I can "see" (just barely) the sign-in dialog window, but it was very dark.  This was probably only due to a reflection from the ambient light, the backlight was not turned on.

I have 11.04, 11.10, 12.04LTS, and 12.10 installed on other partitions of the same notebook.  13.04 is the only version that gives the this no-backlight problem.
I've gotten the same problem. What I did to work around this problem:
> sudo gedit /etc/pm/sleep.d/00-displayfix

Copypasta the next few lines and save.

```
#!/bin/sh
case "$1" in
        thaw|resume)
        echo 500 > /sys/class/backlight/intel_backlight/brightness
        ;;
        *)
        ;;
esac
exit $?

```

Finally, make it executable:
> sudo chmod a+x /etc/pm/sleep.d/00-displayfix

The script might be a little different depending on your hardware. If it does not work, just find out the path to your backlights interface.

---

### Post by ping-wu on 2013-03-03
> **beidl said:**
> I've gotten the same problem. What I did to work around this problem:


Copypasta the next few lines and save.

```
#!/bin/sh
case "$1" in
        thaw|resume)
        echo 500 > /sys/class/backlight/intel_backlight/brightness
        ;;
        *)
        ;;
esac
exit $?

```

Finally, make it executable:


The script might be a little different depending on your hardware. If it does not work, just find out the path to your backlights interface.

Thanks, your workaround works!

---

