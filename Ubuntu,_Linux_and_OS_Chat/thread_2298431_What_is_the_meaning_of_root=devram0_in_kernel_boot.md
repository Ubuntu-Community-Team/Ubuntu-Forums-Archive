---
title: "What is the meaning of root=/dev/ram0 in kernel boot parameters?"
date: 2015-10-10
forum: Ubuntu, Linux and OS Chat
---

### Post by kagashe on 2015-10-10
What is the meaning of root=/dev/ram0 in kernel boot parameters?
What if it is omitted or replaced by root=/dev/sdxx
I am sorry that I am asking this kind of question after using linux for more than 10 years.
But I need to ask.

Kamalakar

---

### Post by SeijiSensei on 2015-10-11
I don't see that in the entries in /boot/grub/grub.cfg on my system.  They all use UUIDs like this:
```
linux   /boot/vmlinuz-3.16.0-45-generic root=UUID=d5b782fb-49d1-438c-b1e4-e521b571ef69 ro recovery nomodeset
```

How did you install Ubuntu?

I could see Ubuntu using a ramdisk like /dev/ram0 if you're booting off a DVD and using "Try Ubuntu."  In that case it would make sense to copy the basic files off the disc into RAM for better performance.  That's just a guess, though.

---

### Post by v3.xx on 2015-10-11
root=device-name
              Specifies the device to be used as the normal root filesystem.

---

### Post by SeijiSensei on 2015-10-11
I thought the question was more about why use /dev/ram0 for the root filesystem rather than a disk drive.

---

