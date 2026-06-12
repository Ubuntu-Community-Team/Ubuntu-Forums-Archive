---
title: "Verify cryptsetup cipher"
date: 2008-08-28
forum: Security
---

### Post by jbrown96 on 2008-08-28
I created an encrypted partition, but I want to make sure that the cipher and some other options are actually being applied. I used ```
sudo cryptsetup --verify-key --verbose --cipher "serpent-xts-essiv" /dev/sda1 name
```
How can I be sure that it is using serpent with xts and essive? 

Thanks

---

### Post by MountainX on 2009-03-03
what did you learn about this? I have the same question.

Where can I find more about how to use XTS when I install Jaunty, which I'm planning to do now? Thanks

---

### Post by flyingbrass on 2009-03-08
Try:

sudo cryptsetup luksDump /dev/sda1

---

### Post by MountainX on 2009-03-08
Thank you. Very helpful. In my case I had to specify the device in terms of /dev/mapper/NameOfCryptVolume.

---

