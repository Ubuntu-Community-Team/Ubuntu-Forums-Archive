---
title: "Connecting Meizu MX4 using USB"
date: 2015-07-05
forum: Ubuntu Phone and Tablet
---

### Post by ttripkitt on 2015-07-05
Hi,

I'm the proud owner of a Meizu MX4 running Ubuntu. 

Generally, I'm loving it - it has surpassed my expectations, but I have several questions which I cannot see the answers to - ..

1.  When I connect the phone to my laptop (running Mint 17.1),i got nothing - zilch.  No recognition, although the phone shows as charging.  Any ideas?

2.  Given the Viber and Skype work on Ubuntu for laptop, what's the problem with them functioning on the phone?

3.  Are other screen keyboards in development, with Swype functionality?

Other than question 1, these are minor niggles and, compared to Android, I'm loving the Ubuntu phone experience - a real breath of fresh air in a stagnant smartphone market.

---

### Post by Harald_Walker on 2015-07-05
1. I managed to access it by enabling developer mode in the settings. I guess there might also be a way to reach it over the network. 
2. I guess the user interface. Same with image editing. A light version of Gimp with an interface for touch devices would be good for the platform.

---

### Post by NaneK on 2015-07-06
3. I don't think there is any other keyboard fully functionaly as default one.

btw. how is the battery? How long does it last?

---

### Post by fallenshadow on 2015-07-06
I was just gonna ask about this. Developer mode works fine for now. Guess we will have to wait for a more elegant solution to appear. :)

---

### Post by owenll on 2015-07-06
> **NaneK said:**
> 
btw. how is the battery? How long does it last?

Mine lasts quite well - 24 hrs light to average use on full charge

Edit: latest update to Ubuntu 15.04 (r3) has transformed battery life. Lasts several days now

---

### Post by Harald_Walker on 2015-07-06
Regarding battery life, there is a known bug [https://bugs.launchpad.net/canonical-devices-system-image/+bug/1470750](https://bugs.launchpad.net/canonical-devices-system-image/+bug/1470750) that drains the battery. 
After I restarted that process was no longer running and now the MX4 also doesn't get hot any longer. After I got my MX4 of course I directly updated the software and since then it had not been rebooted. (uptime was 3 days)

---

### Post by stanyo on 2015-07-07
I'm also using mx4 from yesterday.
1. Is there a way to change wheater farenhait to celsius?
2. I'm also missing viber and skype /I think there is viber port for arm, anyone?/

There were battery bug, showing 33% and suddenly, phone powered off. It was first charge anyway, so can't say will it happen again.
Also. there is no visual indicator working that shows is the phone actually is charging or not. Its very annoying.

---

### Post by Harald_Walker on 2015-07-07
Battery charge display might be related to:
[MX4] Battery statistics are incorrect
[https://bugs.launchpad.net/canonical-devices-system-image/+bug/1471913](https://bugs.launchpad.net/canonical-devices-system-image/+bug/1471913)

---

### Post by constantin.karl.mu on 2015-07-21
May I ask how exactly you managed to connect the phone to your laptop? I have activated developer mode, but it doesn't seem to be recognised when connected.

---

### Post by friTTe81 on 2015-07-21
I got one of them usb sticks that you can put the little memory card in.
So i usually put my phones card in that one and transfer music, for other stuff i use the internet

---

### Post by constantin.karl.mu on 2015-07-21
Unfortunately the MX4 has no memory card slots ... I read about adding the vendor id 0x2a45 to ~/.android/adb_usb.ini but it didn't do the job for my. I'm running 14.04 on my laptop and 15.04 on my MX4. Any more ideas anyone please? :)

---

### Post by constantin.karl.mu on 2015-07-22
Randomly started working now with adb. Don't know how to mount the device though.

---

### Post by howefield on 2015-07-22
> **constantin.karl.mu said:**
> Randomly started working now with adb. Don't know how to mount the device though.

Unlocking the phone should make it mountable.

---

### Post by constantin.karl.mu on 2015-07-22
It is unlocked but not recognized by ubuntu. lsusb shows ```
Bus 003 Device 013: ID 2a45:0c02
``` but I don't see what to do with that.

---

### Post by jtappin on 2015-07-22
I don't know if the Meizu MX4 is the same as the Aquaris 4.5 in this respect, but that appears as an MTP device not as an external drive.

Like your device, it appears as just an uninterpreted number pair in lsusb, and only a single line appears in dmesg.
```
[Jul17 14:32] usb 4-5: new high-speed USB device number 3 using ehci-pci

```

MTP devices are not mounted/unmounted, but can be opened with a file manager. I've generally found dolphin & thunar better than konqueror, and also had more consistent behaviour with my Manjaro machines than the Kubuntu ones.

---

### Post by constantin.karl.mu on 2015-07-22
Works now after updating :)

---

