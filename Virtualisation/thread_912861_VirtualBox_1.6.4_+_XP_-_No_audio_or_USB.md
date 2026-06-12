---
title: "VirtualBox 1.6.4 + XP - No audio or USB"
date: 2008-09-07
forum: Virtualisation
---

### Post by haelen on 2008-09-07
I was wondering whether if, as well as physically selecting the "Audio" and "USB2" options in VB, there's something else I need to do / tweak - as audio and USB are not working.

TIA,
Tim

(running Hardy)

---

### Post by Killtodie on 2008-09-07
for audio install the guest additions under devices.

as for usb, i think everyone has an isusue with that. have you enabled it under settings?

---

### Post by Victormd on 2008-09-07
for USB support using the PUEL version, look at this [link]("http://www.virtualbox.org/wiki/User_FAQ") or check the last few posts on this [link]("http://ubuntuforums.org/showthread.php?t=913305&page=2").

---

### Post by haelen on 2008-09-08
Hi,

I'm using the PUEL version.

I've also noticed that there is nothing present in
/proc/bus/usb/devices.

Is that correct?

---

### Post by haelen on 2008-09-08
> **Killtodie said:**
> for audio install the guest additions under devices.

as for usb, i think everyone has an isusue with that. have you enabled it under settings?

I can't find the "guest additions under devices"

Where is it?

Thanks

---

### Post by Victormd on 2008-09-08
Check my screenshot for the location of the guest additions. For USB, check this [link]("http://ubuntuforums.org/showthread.php?t=913305&page=2") where I when through it with **Killtodie** to get his working.

---

### Post by haelen on 2008-09-08
Thanks. I had a look at the screenshot and I don't have the 3 menus "Machines | Devices | Help" showing on my VB. Even when my XP is not set to show in full screen resolution I seem to "lose access" to Ubuntu. Can't seem to toggle between the two.

---

### Post by Victormd on 2008-09-08
Hummm... don't really know what to say in that situation. I'll have to take a look at home (use windows @ work) and see if there's any option that enables/disables the VB menus and maybe we can go from there.

---

### Post by haelen on 2008-09-08
Great. Thanks a lot. :)

---

### Post by Victormd on 2008-09-08
The only thing I can think of is if you have **Seamless Mode** enabled (Host key + L). Can you post a snapshot of your screen after you've loaded the virtual machine?

---

### Post by haelen on 2008-09-08
Hi,

I've now been able to add "Guest addition". Still no audio though.

I am now also able to use a USB device by selecting the USB icon at the bottom of the VB interface.

---

### Post by Victormd on 2008-09-08
> **haelen said:**
> I've now been able to add "Guest addition".
Were you in seamless mode?

For the audio, how do you have it setup under your VB settings? Null, OSS, Alsa, or Pulseaudio? Try setting it to Alsa.

---

### Post by haelen on 2008-09-09
> **Victormd said:**
> Were you in seamless mode?

For the audio, how do you have it setup under your VB settings? Null, OSS, Alsa, or Pulseaudio? Try setting it to Alsa.

Yes, being in seamless mode was the problem. I switched to "Pulseaudio" which (amazingly) seems to work!

Thanks for your help.

Tim

---

