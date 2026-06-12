---
title: "Bluetooth not working in Ubuntu 21.10 and Greater"
date: 2023-01-10
forum: Virtualisation
---

### Post by mrdj2023 on 2023-01-10
[COLOR=#232629][FONT=-apple-system]I am running ubuntu in virtualbox on a windows 11 host. The bluetooth controller is passed into the Ubuntu guest. This works great in ubuntu 21.04 and prior. However, whenever I use Ubuntu 21.10 or higher the bluetooth does not work.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]
In 21.10 and higher the command: ```
hciconfig dev
``` shows the device but it shows the status as DOWN. Trying the command: ```
hciconfig hci0 up
``` results in the error: ```
Can't init device hci0: Input/Output error (5)
``` I have tried all Ubuntu versions up to the latest including 22.04 LTS and 22.10. Nothing after 21.04 works.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]
There is one odd thing that makes the bluetooth work. I start up a VM in virtualbox with ubuntu 21.04 and confirm that bluetooth is working. Then, while keeping that VM up I start another VM with ubuntu (anything greater than 21.04) and confirm that the bluetooth controller is not available (because it is currently passed into 21.04). In virtualbox I remove the bluetooth controller from 21.04 which passes it to the other VM with 22.04. Then suddenly bluetooth works fine in the VM with version > 21.04.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]
My wifi/bluetooth card is an internal intel AX201.
[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Can someone help me figure out what is going on?[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]
Thank You![/FONT][/COLOR]

---

### Post by ajgreeny on 2023-01-10
Moved to Virtualisation which is a much better fit as this thread is about a virtual install, not using actual hardware but virtual hardware.

Unfortunately I can not help with this problem as I do not use Bluetooth in real or virtual hardware as I do not trust its security.

---

