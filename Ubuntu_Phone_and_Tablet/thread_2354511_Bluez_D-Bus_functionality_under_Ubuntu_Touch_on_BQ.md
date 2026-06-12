---
title: "Bluez D-Bus functionality under Ubuntu Touch on BQ Aquaris M10 Ubuntu edition"
date: 2017-03-03
forum: Ubuntu Phone and Tablet
---

### Post by podkiva on 2017-03-03
Hello,

I am developing a java application that uses D-Bus Bluez apis in order to communicate with my Bluetooth Low Energy device.

I was developing my application firstly under pure desktop Ubuntu 16.04, using Bluez 5.42, built from sources.

In my device I make use of advertising data in order to somehow distinguish my device from others BEFORE connecting or pairing. Particularly, I use it's name and the property "ManufacturerData" of the Device1 object exposed on D-Bus by bluez. This "ManufacturerData" property contains my own data.

However, when I translated my code into Ubuntu Touch installed on BQ Aquaris M10 Ubuntu Edition, I discovered that there is no such property "ManufacturerData" exposed by Device1 object. Also, under Ubuntu Touch the device name is not known before pairing/connection, so this means that I almost completely blind until I try to pair/connect to device.

I checked it with pre-installed on Ubuntu touch version 5.41 of Bluez, and then I updated it (also built from sources) to version 5.42, which is the same as on my desktop platform. The result was the same.

Does anyone has any ideas?

Thank in advance,
Ivan

---

### Post by jeremy31 on 2017-03-03
Moved to Ubuntu phone and tablet

---

### Post by podkiva on 2017-03-06
Looks like problem was in the -experimental option for bluez. The properties that I mentioned are experimental in bluez-5.41, so the bluetoothd service should be lauched with -experimental. But I actually did this in /lib/systemd/system/bluetooth.service config file, which worked for me on desktop ubuntu. Meanwhile, the Ubuntu touch uses upstart, so -experimental option should be written into /etc/init/bluetooth.conf in exec string:

[B]exec /usr/sbin/bluetoothd --experimental


[/B]in** /etc/init/bluetooth.conf**

Looks like now "ManufacturerData" is back again. But I am still not sure about 5.42 version, maybe somehow it was installed wrong way so that it wasn't launched at all by upstart.

---

