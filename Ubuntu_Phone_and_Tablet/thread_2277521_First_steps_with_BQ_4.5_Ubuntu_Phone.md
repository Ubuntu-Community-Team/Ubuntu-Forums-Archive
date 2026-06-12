---
title: "First steps with BQ 4.5 Ubuntu Phone"
date: 2015-05-09
forum: Ubuntu Phone and Tablet
---

### Post by heinzi77 on 2015-05-09
Hi all

I received my Ubuntu phone BQ 4.5 recently.
One of the first things people use to do with a new cell phone is importing the contacts.
Could not find a function for this. Is there any or do they really expect people to do this manually?

So to analyze the situation I tried to connect my phone with the Ubuntu PC over an usb cable.
I expected that the Ubuntu phone would be connected to the Ubuntu PC without any further interaction which seems not to be the case.
The log on the PC does not show any errors:

```
May  9 19:16:17 svsambia kernel: [ 3792.822740] usb 1-2.2: new high-speed USB device number 10 using ehci-pci
May  9 19:16:17 svsambia kernel: [ 3792.928195] usb 1-2.2: New USB device found, idVendor=2a47, idProduct=2008
May  9 19:16:17 svsambia kernel: [ 3792.928201] usb 1-2.2: New USB device strings: Mfr=2, Product=3, SerialNumber=4
May  9 19:16:17 svsambia kernel: [ 3792.928205] usb 1-2.2: Product: Aquaris_E4.5
May  9 19:16:17 svsambia kernel: [ 3792.928209] usb 1-2.2: Manufacturer: BQ
May  9 19:16:17 svsambia kernel: [ 3792.928212] usb 1-2.2: SerialNumber:
May  9 19:16:17 svsambia mtp-probe: checking bus 1, device 10: "/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.2"
May  9 19:16:17 svsambia mtp-probe: bus: 1, device: 10 was not an MTP device

```
(Deleted the serial number value)

So I installed a terminal on the phone . But analyzing a phone without a keyboard turns me nuts. :(
So I tried to ssh the phone from the PC. The ssh-server seems to be installed on the phone. But connection gets refused.

So how do you connect the phone to do analysis?

Regards
Heinzi

---

### Post by lgd on 2015-05-09
I know it doesn't help you directly but for all this problems we have solutions in the German forum and wiki construction site but some on askubuntu in English, too. Maybe some here, too. For a first step, to get a shell, you need to install on the PC and then start:
> 
sudo apt-get install android-tools-adb
adb shell
resize

But before that you have to activate *"System settings -> Info about this device -> Developer mode"*.

---

