---
title: "NFC for Meizu Pro 5"
date: 2016-11-29
forum: Ubuntu Phone and Tablet
---

### Post by al1u on 2016-11-29
Dear all,

Since a week I'm an Ubuntu Touch OTA 13 user on my MEIZU Pro 5.
First of all, many thanks for all the stuff made on Ubuntu by the community to make it works on this phone.

I'm currently looking for an application able to use the NFC chip of this phone, for reading and/or programming Tags.

Is there a way to get access to the NFC also by the way of a library for developping a custom app please ?

By advance, thanks for your help.

Best regards,

Alain

---

### Post by dumazdamaz on 2016-12-01
This is a dev question. You will nit get an answer here, but try asking on some dev email list

---

### Post by PaulW2U on 2016-12-01
> **al1u said:**
> I'm currently looking for an application able to use the NFC chip of this phone, for reading and/or programming Tags.

Is there a way to get access to the NFC also by the way of a library for developping a custom app please ?
Alain, for such specialised help you might want to take a look at the [“Ubuntu Phone”]("https://launchpad.net/~ubuntu-phone") team in Launchpad which is an open team with nearly 3,000 members. By using their mailing list you are far more likely to get an answer to your question than posting here. Hope that helps.

---

### Post by al1u on 2016-12-02
Hi dumazdamaz, hi PaulW2U,

ok,then I will do that, thanks for your reply !

Alain

---

### Post by dumazdamaz on 2016-12-04
But, nevertheless, the chances are high that it will not work and it is even very possible that getting it to work is such a low priority issue that it will never work. Or in other words, the entire phone might be obsoleted before the functionality is implemented.

---

### Post by al1u on 2016-12-05
Yes, I understand what you mean.
But for my project I need it to work. As I can see, on the standard device emulator image, there is a nfc module existing in the kernel but not in the meizu image, the modules are missing. In the kernel source it is present but it seems not to be compiled in the Meizu image.
I will try my chance by compiling the Meizu kernel with the nfc module and see how to use it...

Hope to get some results ...

---

### Post by lapor2 on 2016-12-08
Good luck and please let us know how it will work.

---

### Post by al1u on 2016-12-29
Hi, Since OTA14, I found that they are no NFC modules as the kernel is not working with modules,but I found that there is a compiled driver for it. I will try to do something with libnfc...
Still work in progress, I will let you know ... Thanks !

---

### Post by dumazdamaz on 2016-12-31
Right, it is using an android kernel 3.10 I believe

---

