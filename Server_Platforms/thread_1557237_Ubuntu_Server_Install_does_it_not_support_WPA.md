---
title: "Ubuntu Server Install: does it not support WPA?"
date: 2010-08-20
forum: Server Platforms
---

### Post by AndyWD on 2010-08-20
This is my first post so I hope i put it in the right area!

Essentially I am trying to install Ubuntu server 10.04 and connect to a wireless network.

I have inserted the WiFi adapter (it is a Linksys WUSB54GC) which I know to work in Ubuntu Desktop 10.04 out of the box so I thought it would work similarly in Ubuntu server. 

It detects the WUSB54GC during install and also my network. It then asks for a WEP key. 

These days I thought running WEP on a wireless network was not the done thing as it is the easiest to crack so I am confused as to why this is the only option offered during install.

 I am using WPA2 with a pre-shared key. I am able to connect straight away with the WUSB54GC in ubuntu desktop which shows it supports the set up I have.

Still I tried entering s:"my network key" as it suggests to do so for pass phrases but it is unable to connect.

I have also tried adding the WUSB54GC after install and i didn't get anywhere with that either.

Would much appreciate any enlightenment on the issue. I have tried searching around but haven't been able to find much, or maybe i haven't searched hard enough.

Many Thanks

AndyWD

---

### Post by CharlesA on 2010-08-20
Is it listed in ifconfig?

---

### Post by AndyWD on 2010-08-20
> **CharlesA said:**
> Is it listed in ifconfig?

I am currently mid install! but i disconnected it quickly to try on my other server. ran ifconfig command but i don't think it showed.

It said something about Local loopback and listed my network address as 127.0.0.1

---

### Post by CharlesA on 2010-08-20
You should see eth0, lo and wlan0 or something like that.

eth0 = wired
lo = loopback
wlan0 = wireless

See if it's listed after a clean install.

---

### Post by AndyWD on 2010-08-20
> **CharlesA said:**
> You should see eth0, lo and wlan0 or something like that.

eth0 = wired
lo = loopback
wlan0 = wireless

See if it's listed after a clean install.

Ok will do!

---

### Post by AndyWD on 2010-08-20
> **CharlesA said:**
> You should see eth0, lo and wlan0 or something like that.

eth0 = wired
lo = loopback
wlan0 = wireless

See if it's listed after a clean install.

it unfortunately does not show.

It lists eth0 and lo interfaces, no wlan0

i installed it in Virtualbox and once again it asked me if i wanted to use the wireless as default. i selected Ethernet for installation

---

### Post by AndyWD on 2010-08-20
and i did check it was connected in virtual box after installation !

---

### Post by AndyWD on 2010-08-20
[FONT=monospace]Just ran this command and it did list wan0

[/FONT]lshw -C network

except it was under *Disabled so i ran 

sudo ifconfig wlan0 up which i believe enabled it.

Then ran 

iwlist wlan0 scan 

which showed me no results.

---

### Post by CharlesA on 2010-08-20
Sounds like it's not being detected. What kind of wireless card is it?

---

### Post by JBAlaska on 2010-08-20
Start the terminal and do:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```

Add the line:
```
blacklist rt2800usb
```

Save and reboot.

---

