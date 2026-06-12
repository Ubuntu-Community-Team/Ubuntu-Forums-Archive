---
title: "can we install apple iwork on ubuntu?"
date: 2009-04-25
forum: Wine
---

### Post by StormRoBoT2 on 2009-04-25
can we install apple iwork on ubuntu?

is there any application like wine where we can install mac application on ubuntu?

---

### Post by asdfoo on 2009-04-25
> **StormRoBoT2 said:**
> can we install apple iwork on ubuntu?

is there any application like wine where we can install mac application on ubuntu?

No

---

### Post by Meow27 on 2009-04-25
your best alternative is either MS office or openoffice.

---

### Post by StormRoBoT2 on 2009-04-25
any tutorial on how to install office 07/03? i have an ISO image file.. how can i install it ?

---

### Post by LinuxGuy1234 on 2009-04-25
> **StormRoBoT2 said:**
> any tutorial on how to install office 07/03? i have an ISO image file.. how can i install it ?

```
sudo mount -o loop /path/to/iso /cdrom
```
Replace /path/to/iso to the path to your Office ISO.
Then run your Office installer under wine. The CD is at /cdrom.
Remember to unmount when the install's done:
```
sudo umount /cdrom
```

---

### Post by StormRoBoT2 on 2009-04-26
Thanks [B]LinuxGuy1234

[/B]anyway i have install **Gmount-ISO **application and i have manage to install office 07 successfully :) 
[]("http://ubuntuforums.org/member.php?u=374807")

---

