---
title: "grrr bluetooth"
date: 2007-06-30
forum: The Cafe
---

### Post by stmiller on 2007-06-30
I've tried getting gnome and kde bluetooth utilities to work, but neither see my phone, and vice versa. I've set the phone to 'find me' and everything. The usb bluetooth device shows up in dmesg, and driver loads okay. So it's there, just cannot connect to anything.

Anyone else ever have any bluetooth frustrations? This is in Feisty 64bit.

---

### Post by SoulinEther on 2007-06-30
KDE OBEX client works great with my Sony Ericsson z520.

Then again I'm using x86.

---

### Post by ComplexNumber on 2007-06-30
> **stmiller said:**
> I've tried getting gnome and kde bluetooth utilities to work, but neither see my phone, and vice versa. I've set the phone to 'find me' and everything. The usb bluetooth device shows up in dmesg, and driver loads okay. So it's there, just cannot connect to anything.

Anyone else ever have any bluetooth frustrations? This is in Feisty 64bit.
i had the same proble the other day. installed a usb bluetooth device, and went to pair my phone up with the pc. unfortunately, that's as far as i got. it wouldn't pair because it wouldn't accept the standard pin number for all phones (ie 0000). if the pc requires some different pin code, then there is nothing anywhere which tells me that.

so i'm sticking to usb cable. bluetooth is horrendously slow anyway.

---

### Post by prizrak on 2007-06-30
Same problem still no solution. Bluetooth is pretty bad in Ubuntu, KDE and Gnome utilities are only used for OBEX for the most part. Neither supports DUN, ALSA is SUPPOSED to support audio over BT but in my experience it's not possible. Also you have to use the CLI to scan for devices ```
 hcitool scan 
``` I believe the command is.

---

### Post by DoctorMO on 2007-06-30
Yeh tell me about it; I wish I had more time to fully tackle the linux <> phone problem

---

### Post by bennyj on 2007-07-01
I have had the same problems.Though I finaly got my LG vx8300 to pair with my Fiesty x86 Desktop I can not transfer files from my phone to my pc or visa versa.I can select "Discover Services" on my cell phone and see "obex Push" and "obex File Transfer". But for the life of me I can not get my phone to show up in the "choose Blue Tooth Device" Dialouge box that pops up using Bluetooth file sharing.

Everytime I select a file and try to send it to my phone it will pop up a message on my phone saying"Please check the bluetooth recieving device". I have managed only to send a buissness card contact from my phone to my pc. Frustrating to be so close yet no cigar.

---

