---
title: "Bluetooth connection on E4.5 issue"
date: 2016-05-17
forum: Ubuntu Phone and Tablet
---

### Post by g4sgx on 2016-05-17
Hi,

I have tried to pair my Parrot CK3100 with my E4.5

The first time it came up with the passcode entry on the phone, but instead of 1234 I entered 0000.

It will now not pair or even give me the option of entering a new code.

How can I delete any reference on the phone so I can get the passcode entry option again? I cannot seem to get it to forget the CK3100.

From my dealings with bluetooth it is necessary to delete all references of the device and start again.

Iain

---

### Post by Talkless on 2016-05-18
I have same Parrot in my car, and I cannot even enter code with E5. Paring simply fails. I guess I will try to debug it as described in [https://wiki.ubuntu.com/DebuggingBluetooth](https://wiki.ubuntu.com/DebuggingBluetooth) and reporting a bug.

---

### Post by coffeecat on 2016-05-18
> **g4sgx said:**
> 
How can I delete any reference on the phone so I can get the passcode entry option again? I cannot seem to get it to forget the CK3100.


Have you tried System Settings -> Bluetooth, tapping on where your device is listed under "Connect when automatically detected", and then tap on "Forget this device"?

---

### Post by Talkless on 2016-05-21
I have just paired with CK3100! Though there is no sound - parrot shows crossed note symbol. My call received did not hear me, and I did not hear receiver.

To pair, I had to got to Parrot Advanced Settings -> Pair.. or something > Auto-pair with sync on. Address book is synced, I can initiate call, but there is no sound in either directions. 

If I select Ubuntu Phone as sound output (in Ubuntu call app while in call) - sound, mice works and I can talk, but there is no mic/sound routing through Parrot.

---

### Post by Talkless on 2016-05-21
I've created bug report: [https://bugs.launchpad.net/ubuntu-rtm/+source/bluez/+bug/1584362](https://bugs.launchpad.net/ubuntu-rtm/+source/bluez/+bug/1584362)

---

