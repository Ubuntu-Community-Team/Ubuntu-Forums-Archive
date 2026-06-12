---
title: "Bluetooth Dongle doesnt work on ubuntu 13.10"
date: 2013-08-29
forum: Ubuntu Development Version
---

### Post by jorge-alcantarafilho-q on 2013-08-29
My bluetooth dongle used to work on ubuntu, before i update it to 13.10. Now bluetooth menu shows no adapter. Here are some shortened outputs:
 ~$ sudo lsusb
Bus 002 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 003: ID 0461:4d2b Primax Electronics, Ltd Wireless Laser Mini Mouse (HID)

~$ hciconfig
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 00:1B:10:00:0F:46  ACL MTU: 1017:8  SCO MTU: 64:0
    DOWN 
    RX bytes:457 acl:0 sco:0 events:16 errors:0
    TX bytes:68 acl:0 sco:0 commands:16 errors:0

~$ sudo lsusb -v | grep Blue
[sudo] password for jorge: 
Bus 002 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
  bDeviceProtocol         1 Bluetooth
  idProduct          0x0001 Bluetooth Dongle (HCI mode)
  iManufacturer           1 Bluetooth v2.0
  iProduct                2 Bluetooth V2.0 Dongle
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth

:~$ hcitool dev
Devices:

Also, when i click the blueman button on gnome panel, no options appear.
Thank you all.
I am somewhat new around here.

---

### Post by jorge-alcantarafilho-q on 2013-08-31
I am really lost out here. Already tried installling and uninstalling all bluetooth packages, blueman, bluez and everything, without any luck. And it was working perfectly on 13.04. I guess I should have had waited for the actual release.
Any help would be more than welcome.

---

### Post by mörgæs on 2013-08-31
When installing the development version *you* are supposed to be the one providing help (by finding and reporting bugs). 

Moving the post to the U+1 forum where related issues are being discussed.

---

### Post by fooman on 2013-08-31
to open bluetooth manager (blueman),  click the ubuntu icon at the top of the unity launcher and type "blueman" (no quotes).  you should see "bluetooth manager" appear in the dash....click on it to open.

i also get no options when i right/left-click on the blueman icon in the panel,  but it opens fine using the method above.

i have a very cheap bluetooth dongle here which works fine in ubuntu 13.10 (64bit)

---

### Post by fooman on 2013-08-31
found this: 

[https://wiki.ubuntu.com/HardwareSupportComponentsBluetoothUsbAdapters](https://wiki.ubuntu.com/HardwareSupportComponentsBluetoothUsbAdapters)

scroll down to "bluetake"...looks like thats your device.  it says that it "Works out-of-the-box in Ubuntu v10.04 ~ 11.04 [COLOR=#ff0000]*Stopped working reliably in 11.10*[/COLOR]"

and gives this suggestion: 

> Might need same fix as Belkin : add "blacklist  hci_usb" to /etc/modprobe.d/blacklist.conf, and add "hci_usb reset=1" to  /etc/modules 



---

### Post by jorge-alcantarafilho-q on 2013-09-01
Thanks for the replies. If i did post this to the wrong section, i apologize.
My dongle is surely that bluetake one. But still, i got no luck after doing what is sugested there.
The device didn't appear in the bluetooth manager. 
also
~$ sudo hciconfig hci0 up
Can't init device hci0: Operation not supported (95)


I submited some logs to lauchpad. I hope they fix this on the stable release of saucy salamander.

---

### Post by mörgæs on 2013-09-02
> **jorge-alcantarafilho-q said:**
> 
I submited some logs to lauchpad. 

Good, please link to the report so other people with a similar problem can follow the progress.

---

### Post by jorge-alcantarafilho-q on 2013-09-06
Here you go!
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1221995](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1221995)

---

### Post by atlus2 on 2013-10-22
> **jorge-alcantarafilho-q said:**
> My bluetooth dongle used to work on ubuntu, before i update it to 13.10. Now bluetooth menu shows no adapter. Here are some shortened outputs:
 ~$ sudo lsusb
Bus 002 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 003: ID 0461:4d2b Primax Electronics, Ltd Wireless Laser Mini Mouse (HID)

~$ hciconfig
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 00:1B:10:00:0F:46  ACL MTU: 1017:8  SCO MTU: 64:0
    DOWN 
    RX bytes:457 acl:0 sco:0 events:16 errors:0
    TX bytes:68 acl:0 sco:0 commands:16 errors:0

~$ sudo lsusb -v | grep Blue
[sudo] password for jorge: 
Bus 002 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
  bDeviceProtocol         1 Bluetooth
  idProduct          0x0001 Bluetooth Dongle (HCI mode)
  iManufacturer           1 Bluetooth v2.0
  iProduct                2 Bluetooth V2.0 Dongle
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth

:~$ hcitool dev
Devices:

Also, when i click the blueman button on gnome panel, no options appear.
Thank you all.
I am somewhat new around here.

I updated to 13.05 last night and now I want to reinstall my previous verson. Buetooth on/off selector is not working, just stays on and I want it off.
Also my login options wont load my desktop only if i login to Xubuntu Session.

---

### Post by zika on 2013-10-22
1. You've waken up old thread... This is U+1 forum and You are in danger of not getting as much answers as You could if You posted Your question in proper forum...
2. What version is 13.05, half of 13.10...? ;)

---

### Post by howefield on 2013-10-22
Thread closed.

Please post in the general forums, rather than this forum which is for the development release.

---

