---
title: "Secure Linux OS from USB Flash Drives"
date: 2013-02-26
forum: Security
---

### Post by Cyrebo on 2013-02-26
Hi,

I'm looking for something which I'm not sure exists, that is, a way of optimizing my system (Kubuntu 12.10) to only allow a specific usb to be connected to it and no other. 

I want only my personal usb to be recognized and other usb sticks throw an error message or are just rejected.

Is this possible or am i in way over my head with this?

Thanks in advance for any help.

---

### Post by chadk5utc on 2013-02-28
Not sure what you wish to do is possible, however it is possible to limit access to system resources/devices/drives using user/group management and removing those permissions from other users/groups.

---

### Post by Cyrebo on 2013-03-01
I see what you mean but that implementation won't give me the security i desire because my account details could be compromised. I know there's a way of programming it so that when a USB is connected you automatically sync it to a folder so perhaps there may a way of performing another action to reject the usb?

---

### Post by Cyrebo on 2013-03-01
Hi, I want to optimize my system (Kubuntu 12.10) to reject/block all unknown usb devices except my own. Does anyone have any ideas of how to implement a system like this please? I've seen automatic device syncing but i was wondering if there was a way of changing the sync action to reject or block where the device is not my personal usb drive. 

Thanks in advance for any replies/advice on this.

---

### Post by chadk5utc on 2013-03-01
This is a duplicate thread it is advised, suggested, asked that you post one question per thread and be patient as you will get answers but some may take time....

---

### Post by matt_symes on 2013-03-01
Treads merged.

I don't think what you want is possible without some firmware on the stick itself to identify itself.

After all, how could a usb stick be identified as trusted or not without that ? Any identifing data on the stick could just be copied off onto another identical stick.

You can have system less secure of course where ubuntu reads something of filesystem but that is hardly secure.

---

