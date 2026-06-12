---
title: "Proper variable for Apparmor here?"
date: 2012-12-16
forum: Security
---

### Post by Hungry Man on 2012-12-16
/lib/x86_64-linux-gnu/libdbus-1.so.* mr,


I want this to work on 32bit and 64bit systems. Is there a variable here that will allow for this?

I don't want to use *, I'd like something similar to {32,64} (unless that's the one for this?).

---

### Post by samiux on 2012-12-16
> **Hungry Man said:**
> /lib/x86_64-linux-gnu/libdbus-1.so.* mr,


I want this to work on 32bit and 64bit systems. Is there a variable here that will allow for this?

I don't want to use *, I'd like something similar to {32,64} (unless that's the one for this?).

The code may be looking like this :

```
/lib/{i386,x86_64,}-linux-gnu/libdbus-1.so.* mr,
```

Samiux

---

### Post by Hungry Man on 2012-12-16
I've never been on 32bit Linux. Is the folder i386-linux-gnu? 

If so that should work, I just want to confirm.

---

### Post by samiux on 2012-12-16
> **Hungry Man said:**
> I've never been on 32bit Linux. Is the folder i386-linux-gnu? 

If so that should work, I just want to confirm.

You can confirm it by using virtual machine.

Samiux

---

### Post by Hungry Man on 2012-12-16
Downloading 4GB just to test for this would be a bit of a pain. I'll give googling a go later.

---

### Post by vasa1 on 2012-12-16
> **Hungry Man said:**
> I've never been on 32bit Linux. Is the folder i386-linux-gnu? 

If so that should work, I just want to confirm.
Will this help? It's from Lubuntu 12.10

---

### Post by Hungry Man on 2012-12-16
Yep, thanks.

---

