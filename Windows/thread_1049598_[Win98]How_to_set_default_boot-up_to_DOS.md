---
title: "[Win98]How to set default boot-up to DOS?"
date: 2009-01-24
forum: Windows
---

### Post by fiddler616 on 2009-01-24
Hello,
I recently dug an old computer out of my basement. After much thought, I've decided to turn it into a '90s arcade box--put Commander Keen, Duke Nukem, etc. on it, and use it ONLY for that.
I'd rather use DOS, in the interest of speed and compatibility, but it's kind of a drag booting into Windows, and then rebooting into DOS. Is there a way to set the default environment to DOS? (Apart from installing FreeDOS)
Thank you.

---

### Post by Frak on 2009-01-24
Click Start -> Shutdown -> Shutdown the computer in MS-DOS mode.
Type cd\ to get to the C:\> prompt.
Now type ```
attrib msdos.sys -r -a -s -h
```
Next type ```
edit msdos.sys
```
Finally, locate the line ```
BOOTGUI=1
``` and change the line to ```
BOOTGUI=0
``` 

Save the file and reboot.

---

### Post by fiddler616 on 2009-01-25
> **Frak said:**
> Click Start -> Shutdown -> Shutdown the computer in MS-DOS mode.
Type cd\ to get to the C:\> prompt.
Now type ```
attrib msdos.sys -r -a -s -h
```
Next type ```
edit msdos.sys
```
Finally, locate the line ```
BOOTGUI=1
``` and change the line to ```
BOOTGUI=0
``` 

Save the file and reboot.

Excellent, it worked, thanks!
And congratulations on the 3500 posts--time to think of a custom bean title :)

---

### Post by Frak on 2009-01-25
> **fiddler616 said:**
> Excellent, it worked, thanks!
And congratulations on the 3500 posts--time to think of a custom bean title :)
Way ahead of you :)

:lolflag:

Internet, Serious Business

---

### Post by fiddler616 on 2009-01-25
> **Frak said:**
> Way ahead of you :)

:lolflag:

Internet, Serious Business
Nic
Yeah, I hadn't refreshed for several hours, just keeping the tab open for when it was time to boot up the computer in question...Nice pick though.

---

