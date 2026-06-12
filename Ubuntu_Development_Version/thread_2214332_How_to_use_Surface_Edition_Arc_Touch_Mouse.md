---
title: "How to use Surface Edition Arc Touch Mouse"
date: 2014-03-31
forum: Ubuntu Development Version
---

### Post by wolfy1339 on 2014-03-31
I recently bought a Surface Edition Arc Touch Mouse, and i couldn't get it to work under ubuntu 14.04.
Is there any specific way to get it working?

---

### Post by cariboo on 2014-03-31
Does anything show up in dmesg, when you start the system? I've used a similar Microsoft mouse that worked without any problems. To find if it is detected properly run the following command:

```
dmesg | grep Mouse
```

The output should look similar to this:

```
dmesg | grep Mouse
[   12.039603] logitech-djdevice 0003:046D:C52B.0006: input,hidraw3: USB HID v1.11 
Mouse [Logitech Unifying Device. Wireless PID:1028] on usb-0000:00:02.0-3:1
```

---

### Post by wolfy1339 on 2014-04-01
It seems today it connected and paired properly.
But i am unable to use it... I think my type cover might be the problem, i'm not sure.

---

### Post by javispedro2 on 2014-04-10
You will need Bluez 5. I think this is not coming until the next Ubuntu release.

---

### Post by aeyoun on 2014-07-24
You probably have [this problem]("http://marc.info/?l=linux-bluetooth&m=140405496213823&w=2"). There is a patch you can apply, however, you would likely just want to wait for an updated kernel that includes it.

---

### Post by javispedro2 on 2014-07-24
> **aeyoun said:**
> You probably have [this problem]("http://marc.info/?l=linux-bluetooth&m=140405496213823&w=2"). There is a patch you can apply, however, you would likely just want to wait for an updated kernel that includes it.

I am certain it's not that problem, because that problem is only caused with kernel 3.15 onwards and has very specific symptoms. 

On Ubuntu 14.04, the problem is that Bluez is at version 4 and a relatively recent version (>5.15) is required for Bluetooth 4 HID over GATT devices.

I don't know about the next Ubuntu but I doubt they'll update to Bluez5 considering Debian Sid only got Bluez5 very recently.

---

### Post by cariboo on 2014-07-24
Seeing as we are in the midst of test 14.10 Utopic Unicorn, this thread is no longer relevant here. Thread closed.

---

