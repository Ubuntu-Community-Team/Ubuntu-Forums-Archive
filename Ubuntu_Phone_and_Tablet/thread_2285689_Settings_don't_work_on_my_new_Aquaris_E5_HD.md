---
title: "Settings don't work on my new Aquaris E5 HD"
date: 2015-07-07
forum: Ubuntu Phone and Tablet
---

### Post by shokin on 2015-07-07
Hello, everybody, 

I ordered a phone Aquaris E5 HD and I got it today.

No problem for calls and messages, for photos and copying mp3 from the laptop (with Ubuntu) to the phone.

I changed once some settings. I didn't update to version 3 (shoud I have done this ?).

Now, when I go to the System Settings (Paramètres Système, in French), it does'nt go like the first time. [See [this video]("https://mega.nz/#!6RxDARCJ!lr0yWO06p79cDCBQc0K1vZGYlucmfthqaWCf2LIT7Io") (11.7 Mo, uploaded on MegaConz).

How to solve it ?

[On this phone, is it possible to choose my own mp3 as alarms, message rings and call rings ? Now it seems that I can choose only in a list.]

---

### Post by _march_ on 2015-07-08
Can you remember what you did exactly? Did you reboot your device? Update to version3 means?

Concerning ringtones you'll have to use the terminal at the moment : [http://askubuntu.com/questions/372759/ringtones-in-ubuntu-touch](http://askubuntu.com/questions/372759/ringtones-in-ubuntu-touch) If this "bug" affects you visit [https://bugs.launchpad.net/ubuntu/+source/ubuntu-system-settings/+bug/1268097](https://bugs.launchpad.net/ubuntu/+source/ubuntu-system-settings/+bug/1268097) 

Can you  do me a favour? Can you post your USB-ID (*lsusb*) of your bq E5 so I can add this on [https://wiki.ubuntuusers.de/Ubuntu_Touch#Geraete](https://wiki.ubuntuusers.de/Ubuntu_Touch#Geraete) Would be very nice. :)

**Edit:** Have you setup an account of "Ubuntu One"?

---

### Post by shokin on 2015-07-11
Hello, 

Sorry for late. The problem is solved. I cancelled and I tried again. It worked. Then I update the version 3.

I  live in Switzerland. Very good service. The charger (that was with the  phone) was done for AC power plugs and sockets of Switzerland.

I installed the terminal. How to know the path to my song ? (I don't really know how to use a terminal. How to copy/cut/paste/move files, how to go to a folder, to a file.)

---

### Post by grahammechanical on 2015-07-12
The Ubuntu phone gets something called Over The Air (OTA) updates. By accepting the OTAs your phone will be up to date with the latest Ubuntu phone operating system. You may find that OTA 4 is waiting for your device

[https://lists.launchpad.net/ubuntu-phone/msg13291.html](https://lists.launchpad.net/ubuntu-phone/msg13291.html)

Regards.

---

### Post by _march_ on 2015-07-19
Hi :)

Sorry for the delay - holiday. 

```
sudo mount -o remount,rw / 
sudo cp /path/to/your/ringtone/ringtone.ogg /usr/share/sounds/ubuntu/ringtones/ # Klingelton
```

After this just choose the ringtone in your settings.

[ubuntuusers.de]("https://wiki.ubuntuusers.de/Baustelle/Ubuntu_Touch_Erweiterte_Konfiguration#Klingeltoene")

---

