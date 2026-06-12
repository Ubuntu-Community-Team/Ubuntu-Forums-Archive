---
title: "Properly Holding Ubuntu Kernel in Production"
date: 2019-09-01
forum: Server Platforms
---

### Post by selcoric756 on 2019-09-01
Hello,

I have an application that's pretty sensitive deployed to approx 100 servers in prod. I need to hold down the current kernel in prod without breaking anything. When I run

```
dpkg --list | grep linux-image
```I see:
```
ii  linux-image-4.15.0-55-generic                  
ii  linux-image-4.15.0-58-generic 
ii  linux-image-generic 

```
To hold down the kernel, but when i run```
dpkg --list
```I see:```

linux-image-generic
linux-base
linux-headers
linux-headers-generic
```

my question is, what do i need to hold to make sure the kernel stays the same when auto updates start?

---

### Post by TheFu on 2019-09-02
There is no guaranty that holding any specific package won't break things.

You can use **apt-mark**.  From the manpage:
```
PREVENT CHANGES FOR A PACKAGE
       hold
           hold is used to mark a package as held back, which will prevent the
           package from being automatically installed, upgraded or removed.

       unhold
           unhold is used to cancel a previously set hold on a package to
           allow all actions again.

       showhold
           showhold is used to print a list of packages on hold in the same
           way as for the other show commands.
```

apt-mark is handy for backups and restores too, but that is unrelated.

---

