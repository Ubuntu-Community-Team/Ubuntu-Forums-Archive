---
title: "Serval Pro 3 ...formerly with working bluetooth"
date: 2009-10-31
forum: System76 Support
---

### Post by Trevor Bramble on 2009-10-31
Ubuntu 9.04

Linux wayfarer 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:32 UTC 2009 x86_64 GNU/Linux

Once upon a time I had bluetooth.  I recently needed to use it again and found that it not only wasn't enabled, but it couldn't be enabled (Fn+F2).

What can I do to get this working again?

---

### Post by Vadi on 2009-10-31
Serval 3 has bluetooth?

---

### Post by thomasaaron on 2009-11-02
Hi, Trevor.

I'm having a little difficulty finding your config in our database under your name. (Don't put any private info here, though.)

Is your system the FL9* or the EL80?
Have you set up the bluetooth icon to appear when adapter is present?

---

### Post by Trevor Bramble on 2009-11-02
Hi, Tom.  The system was originally purchased for me by my employer.  How should I go about updating that information?

It's an FL90.

There is no recognized Bluetooth device.  I can force the icon to sit my tray, but there are no listed devices to work with.  Attempting to view and work with devices via CLI (as described [here](https://help.ubuntu.com/community/BluetoothSetup)) came up empty.

And the reaction I'm looking for when I do Fn+F2, seeing the WiFi/Bluetooth activity LED change from blue to that strange blue+orange again, does not occur.  The blue blinks merrily away with no change.

---

### Post by thomasaaron on 2009-11-03
Hi, Trevor.

I'm not sure that you can change that. It's in our database as a matter of permanent record.

Usually we just ask for the order number, or the name of the person who purchased the computer.

I've not played with that Serval model for a long time, and the one I have in the shop doesn't have bluetooth. My boss has one with bluetooth, and I'll test with that when he gets in.

I'm a little confused, though. The Fn-F2 shows the wirless icon on the one I have in the shop. Are you *sure* that turned on the bluetooth?

Anyway, I'll run some tests on it.

---

### Post by Trevor Bramble on 2009-11-03
No, I'm not.  It's a matter of "well nothing else worked".  And now that you've questioned it, I do only see that antenna icon rather than antenna/bluetooth icon over the physical toggle along the front.

I have also attempted just flicking that toggle on the front to its off position and re-enabling it with all my hopes and dreams behind those millimeters of movement.  Surprisingly, even that didn't work. =^)

Is there anything other than that switch to try to enable the onboard device?  The BIOS is ...on the stark side, so I don't think I've missed anything relevant while looking through there.  Anything I can try on the Linux side?  All of the utilities mentioned at the aforementioned URL seem to rely on a device being there to work with.

Cheers,
Trevor

---

### Post by serval1 on 2009-11-04
Speaking a little out-of-turn here, I have never seen a Serval-3, but on the Serval-5 to enable the Blue-tooth you need to press 
Fn+F12, not Fn+F2.

Is this a function of the machine or the System76 drivers?

---

### Post by thomasaaron on 2009-11-04
Hi, Serval1. This is an older Serval.

---

### Post by jdmelton on 2009-11-04
Trevor, Tom,

I have a Serval P3 (FL90) with Bluetooth
Ubuntu 8.04 LTS AMD64 with the latest System76 driver.
Bluetooth Applet 0.25

Unfortunately, I do not have any Bluetooth devices at the moment, but normally run with:
Mode - Other devices can connect
Services - Audio/Serial/Input enabled and Network disabled
General - Select class of device automatically and Only display when adapter is present

My F2 key has an icon for the wireless adapter but not the bluetooth one.

When I press Fn+F2, I do not get a reaction on the bluetooth or wireless icons on the panel but I do get this:

dmesg | tail
[  214.969826] atkbd.c: Unknown key pressed (translated set 2, code 0x84 on isa0060/serio0).
[  214.969836] atkbd.c: Use 'setkeycodes e004 <keycode>' to make it known.
[  214.971331] atkbd.c: Unknown key released (translated set 2, code 0x84 on isa0060/serio0).
[  214.971340] atkbd.c: Use 'setkeycodes e004 <keycode>' to make it known.

And lshw has this:

*-usb:0
    description: Bluetooth wireless interface
    product: Foxconn Bluetooth 2.0 plus EDR
    vendor: Broadcom Corp
    physical id: 1
    bus info: usb@2:1
    version: 1.00
    capabilities: bluetooth usb-2.00
    configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s

*-pci:6
     description: PCI bridge
     product: 82801H (ICH8 Family) PCI Express Port 6
     vendor: Intel Corporation
     physical id: 1c.5
     bus info: pci@0000:00:1c.5
     version: 03
     width: 32 bits
     clock: 33MHz
     capabilities: pci normal_decode bus_master cap_list
     configuration: driver=pcieport-driver
   *-network
     description: Wireless interface
     product: PRO/Wireless 3945ABG Network Connection
     vendor: Intel Corporation
     physical id: 0
     bus info: pci@0000:0c:00.0
     logical name: wmaster0
     version: 02
     serial: 00:1c:bf:6c:30:a1
     width: 32 bits
     clock: 33MHz
     capabilities: bus_master cap_list logical ethernet physical wireless
     configuration: broadcast=yes driver=iwl3945 ip=10.1.1.201 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

So, I am not sure if the bluetooth and wireless are tied together at the bios level.

If there is any other information that I can give, I would be glad to.

---

### Post by Trevor Bramble on 2009-11-04
Hi, jdmelton.

I fear this is the relevant piece of comparative information:

"Ubuntu 8.04 LTS"

Could you share the kernel revision you're using?

Thanks!

---

### Post by jdmelton on 2009-11-05
From uname -a
2.6.24-25-generic #1 SMP Tue Oct 20 06:49:12 UTC 2009 x86_64 GNU/Linux

I try to keep the latest updates installed.

---

### Post by Vadi on 2009-11-05
No bluetooth from lshw on my FL90 :|

---

### Post by jdmelton on 2009-11-05
Trevor,

I have not tried to connect to a Bluetooth device for over a year...

This morning I tried to connect to my Verizon Blackberry 8830. I did this in early 2008. At the time, I was running 32-bit Ubuntu that this Serval P3 was delivered with (Gutsy?). However, neither my laptop nor my Blackberry can find each other today.

hcitool scan does not find any device. I have enabled all services in the Bluetooth applet.

I have a 32-bit Gutsy live cd around here somewhere. If I can find it, I am going to see if that works.

I used these web pages today:
[http://perilsofdecadence.blogspot.com/2008/09/using-blackberry-8830-as-tethered-modem.html](http://perilsofdecadence.blogspot.com/2008/09/using-blackberry-8830-as-tethered-modem.html)
[https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)

---

### Post by thomasaaron on 2009-11-05
Trevor and Vadi.

Can you contact me via email (support...at...system76...dot...com) with your order numbers so I can look up your configuration?

---

### Post by Vadi on 2009-11-05
Um...

I'll see if I can still find the paper.

---

### Post by jdmelton on 2009-11-05
I had some interesting tests today. My Serpal P3 is an FL90, received in December 2007, and came with Bluetooth. It was originally shipped with Ubuntu 7.10 32 bit. I tried Bluetooth with my Blackberry 8830 in early 2008 and was able to find it, but that is all I did. I switched to Ubuntu 8.04 AMD64 LTS when it came out. I have the System76 driver installed and all the latest updates/upgrades.

My tests yesterday did not find the Blackberry. So, today I stopped in at Best Buy and picked up a USB RocketFish Micro Adapter.

Since I also have a Meerkat Ment1 from July 2009 with Ubuntu 9.04 32 bit, I decided to try the RocketFish on it first.
There was someting of a learning curve for me, but here are the commands:
hcitool dev (returned hci0 and the address)
hcitool scan (returned connection error)
sudo hciconfig hci0 reset
hcitool dev (returned hci0 and the address)
hcitool scan (found the Blackberry and address)

In the Bluetooth applet, I used set up a new device, selected PIN 1111, then the Blackberry. On the Blackberry, I got a prompt to enter the key number and then typed in 1111 and Enter. Success, then I disconnected. I shutdown the Meerkat, removed the RocketFish, then booted the Meerkat. After inserting the RocketFish this time, the hciconfig command to reset the device was not needed.

Serval Test 1:
The same sequence of commands did not work on the Serval with Ubuntu 8.04 AMD64 and its installed Bluetooth device.

hcitool dev (returned hci0 and the address)
hcitool scan (returned nothing)
sudo hciconfig hci0 reset
hcitool dev (returned hci0 and the address)
hcitool scan (returned nothing)

Next I inserted the RocketFish and repeated the commands.
hcitool dev (returned hci1 and the address)
hcitool -i hci1 scan (returned connection error)
sudo hciconfig hci1 reset
hcitool dev (returned hci1 and the address)
hcitool -i hci1 scan (found the Blackberry and address)

In the Bluetooth applet, a adapter new device was present under Preferences.
The applet is different in Ubuntu 8.04 and 9.04.
Nothing was present in Browse Device, and I did not get it to work.
However, the RocketFish did find the Blackberry, so I decided to continue.

Serval Test 2:
Removed the RocketFish and rebooted with a live cd of Ubuntu 8.04.3 i386.
hcitool dev (returned hci0 and the address)
hcitool scan (returned nothing)
sudo hciconfig hci0 reset
hcitool dev (returned hci0 and the address)
hcitool scan (returned nothing)

Next I inserted the RocketFish and repeated the commands.
hcitool dev (returned hci1 and the address)
hcitool -i hci1 scan (returned connection error)
sudo hciconfig hci1 reset
hcitool dev (returned hci1 and the address)
hcitool -i hci1 scan (found the Blackberry and address)

In the Bluetooth applet, a adapter new device was present under Preferences.
Nothing was present in Browse Device, and I did not get it to work.

Serval Test 3:
Removed the RocketFish and rebooted with a live cd of Ubuntu 9.04 i386.
Same results as tests 1 and 2 with hci0 and hci1.

Serval Test 4:
Removed the RocketFish and rebooted with a live cd of Ubuntu 9.04 AMD64.
Same results as tests 1, 2, and 3 with hci0 and hci1.

Serval Test 5:
I turned the wireless switch off, put the RocketFish in, and booted the installed Ubuntu 8.04 AMD64.

hcitool dev (returned hci1 and the address)
hcitool -i hci1 scan (returned connection error)
sudo hciconfig hci1 reset
hcitool dev (returned hci1 and the address)
hcitool -i hci1 scan (found the Blackberry and address)

In the Bluetooth applet, a adapter new device was present under Preferences.
Under Browse Device, the Blackberry was present.
This leads me to believe that there is a configuration issue for the applet which is another story...

Next, I turned the wireless switch on.
After reconnecting, I decided to test the installed Bluetooth device again.
No luck. This time it was hci1. I tried the reset also.

The difference between these two is that after booting, the RocketFish needs to be reset.
If not, when I run a scan with it, it gives a connection error.
After a reset, it finds the Blackberry and sometimes other phones of people passing by.
On the other hand, the installed Foxconn never gives a connection error and never finds anything.

So my belief is that it has ceased working (transmitting) for some reason.


Below this point is the results of running several commands on the Serval with its installed Ubuntu 8.04 AMD64. All of them are with the installed Foxconn device only.

lsusb:
Bus 002 Device 002: ID 0a5c:2101 Broadcom Corp.

hcitool dev:
Devices:
        hci0    00:1C:26:E7:A9:C7

lshw:
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.24-25-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Bluetooth wireless interface
                   product: Foxconn Bluetooth 2.0 plus EDR
                   vendor: Broadcom Corp
                   physical id: 1
                   bus info: usb@2:1
                   version: 1.00
                   capabilities: bluetooth usb-2.00
                   configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
              *-usb:1 UNCLAIMED
                   description: Generic USB device
                   product: Fingerprint Sensor
                   vendor: TouchStrip
                   physical id: 2
                   bus info: usb@2:2
                   version: 0.01
                   capabilities: usb-1.00
                   configuration: maxpower=100mA speed=12.0MB/s

hciconfig -a:
hci0:   Type: USB
        BD Address: 00:1C:26:E7:A9:C7 ACL MTU: 1017:8 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN 
        RX bytes:3214 acl:0 sco:0 events:62 errors:0
        TX bytes:742 acl:0 sco:0 commands:60 errors:0
        Features: 0xff 0xff 0x8f 0xfe 0x9b 0xf9 0x00 0x80
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH HOLD SNIFF PARK 
        Link mode: SLAVE ACCEPT 
        Name: 'aberto-0'
        Class: 0x08010c
        Service Classes: Capturing
        Device Class: Computer, Laptop
        HCI Ver: 2.0 (0x3) HCI Rev: 0x213b LMP Ver: 2.0 (0x3) LMP Subver: 0x41d3
        Manufacturer: Broadcom Corporation (15)

hidd --search:
Searching ...
        No devices in range or visible

---

### Post by Trevor Bramble on 2009-11-06
Sent you an email, Tom.

jdmelton, thanks for the thorough testing!  Hopefully that can help Tom get to the root of the problem.  I'm out of tricks and at his mercy. =^)

---

### Post by thomasaaron on 2009-11-06
Hi, Trevor.

Responded to your email. Everybody else, I've got a SerP3 with BT in the shop. Will test it next week.

---

### Post by Trevor Bramble on 2009-11-25
*bump*

Any news?

---

### Post by thomasaaron on 2009-11-27
No, not yet. I do have this issue on the whiteboard.

I'll have a look at it this coming week..

---

