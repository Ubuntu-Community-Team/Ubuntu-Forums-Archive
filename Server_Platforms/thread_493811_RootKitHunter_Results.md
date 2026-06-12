---
title: "RootKitHunter Results"
date: 2007-07-06
forum: Server Platforms
---

### Post by waveslider on 2007-07-06
Hey everyone,

I just ran RootKitHunter, and it found everything to be OK except for this warning:

"WARNING, found:  /etc/.java (directory)  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory)"

What does that mean? Is that anything to worry about?

---

### Post by dreadlord_chris on 2007-07-06
> **waveslider said:**
> Hey everyone,

I just ran RootKitHunter, and it found everything to be OK except for this warning:

"WARNING, found:  /etc/.java (directory)  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory)"

What does that mean? Is that anything to worry about?

You are fine - rkhunter was just informing you of **hidden** directories it found in your root filesystem. Any name that starts with a *dot* (.) is considered hidden.

---

