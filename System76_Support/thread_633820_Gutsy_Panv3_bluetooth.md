---
title: "Gutsy Panv3 bluetooth"
date: 2007-12-07
forum: System76 Support
---

### Post by newsun on 2007-12-07
How do I use bluetooth with my panv3 gutsy? I prefer kde instructions as I run kubuntu, gnome if fine though just so I can get it working, initially I would like to pair my moto ht820 headset.

---

### Post by thomasaaron on 2007-12-07
I don't know much about bluetooth (or how to set it up with your particular device). But this is probably the place to start...

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by newsun on 2007-12-07
Thing is when I follow those insttructions there is no bluetooth adapter showing up...this is something I paid for when I ordered this panv3 from you guys, so any ideas on how to establish that I have the card or w/e it was you guys were to install when I ordered?

---

### Post by |Porsche on 2007-12-07
I dont know what a panv3 is or who you order it from... 

I had the same problem. I fixed the problem by doing an ```
apt-get remove bluez-utils
```, and then doing an ```
apt-get install bluez-utils
```. 

Once you do that, do a```
 hcitool
```, and let me know if you can now see the dongle. 

Once your computer can see the dongle, set the devices to "searching" mode and do a```
 hidd --search
```, if they dont connect do one by one ```
hidd --connect  <bluetooth_device_mac_address>
```

To find the mac address of your bluetooth devices you can set them to "searching" mode by click a connect (sync, or whatever the case might be) button wait a few seconds and then do a ```
hcitool scan
```

Let me know  how it goes.

---

### Post by thomasaaron on 2007-12-07
To verify that you have bluetooth installed, run this command:
sudo dmidecode | grep -i bluetooth

---

### Post by newsun on 2007-12-07
tried reinstalling bluez and didn't seem to help, also tried

sudo dmidecode | grep -i bluetooth

this didn't produce any errors and just returned me to prompt

---

### Post by thomasaaron on 2007-12-10
Please email me your name and order number at: support(at)system76(dot)com.

Include a link in this email to this thread, if you would.

Best,
T

---

