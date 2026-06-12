---
title: "How to flash Android tab using Ubuntu ?"
date: 2017-02-10
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxyogi on 2017-02-10
Hi, I have downloaded the official firmware from [here]("https://www.asus.com/Phone/ASUS_Fonepad_7_FE170CG/HelpDesk_Download/"). How do I flash my Asus Fonepad 7 from Lubuntu ?

---

### Post by linuxyogi on 2017-02-10
```
sudo apt-get install android-tools-adb android-tools-fastboot
```

Now when I do 

```
fastboot flash recovery custom-recovery.img< waiting for device >
```

Its stuck at < waiting for device >

I have booted the phone by pressing the vol+ and power key.

---

### Post by linuxyogi on 2017-02-11
Bump

---

