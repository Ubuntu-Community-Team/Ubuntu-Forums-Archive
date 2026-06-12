---
title: "No plymouth and disable boot text"
date: 2012-08-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by thotz on 2012-08-29
Ok, I have disabled plymouth. 
Is there a way to disable the boot messages?
I just want to see a black screen.

Thank you! Thomas

---

### Post by Harry33 on 2012-08-29
> **thotz said:**
> Ok, I have disabled plymouth. 
Is there a way to disable the boot messages?
I just want to see a black screen.

Thank you! Thomas

Yes there is.
Change this line in the file /etc/default/grub
into this
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

How did you disable Plymouth?
I did it by removing plymouth-theme-* and plymouth-label packages.

---

### Post by ajgreeny on 2012-08-29
In the grub configuration file /etc/default/grub you need to change the line
```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
``` to read
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```
I have only just noticed this is for QQ and my answer assumes that QQ's grub works just like Precise, which it may not, of course.

---

### Post by thotz on 2012-08-29
I did:

GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"

But now the screen is not fully black, because of the text messages.

---

### Post by ajgreeny on 2012-08-29
Try adding back the word quiet at the end of your current line ```
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth quiet"
```

---

