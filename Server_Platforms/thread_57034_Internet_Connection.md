---
title: "Internet Connection"
date: 2005-08-15
forum: Server Platforms
---

### Post by koggo on 2005-08-15
I installed my ubuntu system as a server the other day,
and when i've installed it & booted into ubuntu the internet worked fine but when i resetted it the internet stopped working?!?!
I tried reinstalling it and it did the same?!?!

---

### Post by nad on 2005-08-15
What did you reset and what is your connection method?

---

### Post by koggo on 2005-08-15
I reset the computer and I have an ADSL connection via a router, and have NET & DHPC (or something i cant remember)

All of my whendoze pcs work fine.

---

### Post by nad on 2005-08-15
Give the server a static ip address, restart networking: /etc/init.d/networking restart  check  ifconfig and see if you can ping slashdot,org .

If not, can you ping your local machines?

---

### Post by koggo on 2005-08-15
No Luck

---

### Post by nad on 2005-08-15
What is the output of:

lspci

ifconfig

route

Can you ping 127.0.0.1 ?

---

### Post by koggo on 2005-08-16
lcpci:

0000:00:01.0 Host Bridge: Intel Corp. 440BX/ZX/DX - 82442BX/ZX/DX Host Bridge (rev 02)
0000:00:01.0 PCI Bridge: Intel Corp. 440BX/ZX/DX - 82442BX/ZX/DX AGP Bridge (rev 02)
0000:00:07.0 ISA Bridge: Intel Corp. 823714B/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IPE Interface: Intel Corp. 823714B/EB/MB PIIX4 IDE (rev 01)
0000:00:07:2 USB Controller: Intel Corp. 823714B/EB/MB PIIX4 USB (rev 01)
0000:00:07:3 Bridge: Intel Corp. 823714B/EB/MB PIIX4 ACPI (rev 02)
0000:00:11.0 Ethernet Controller: 3com Corperation 3c90TB 100BaseTX [Cyclone]
0000:00:13.0 PCI Bridge: Digital Equipment Corperation DEC chip 21152 (rev 03)
0000:01:00.0 VGA Compatible Controller: Matrox Graphics, Inc. MGA G200 AGP (rev 03)
0000:02:00.0 SCSI Controller: Adaptec AHA 294OU2/U2W/7890/7891

ifconfig:

eth0:
Link encap:Ethernet Hwaddr 00:CO:4F:8E:B4:D4
inet addr: 10.1.1.9 Bcast:10.155.155.155 Mask: 255.0.0.0
inet6addr: fe80::2co:4fff:fe8e:bfd4/f4 Scope:Link
UP BROADCASTING RUNNING MULTICAST MTU:1500 Metric:1
RX Packets:0 errors:1 dropped:0 overruns:0 frame:1
TX Packets:11449 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisions:3 txqueuelen:1000
RX bytes:0(0.0 b) TX Bytes:1678902 (1.0 MiB)
Interrupt: 19 Base Address: 0xdc00

lo:
Link encap: Local Loopback
inetaddr:127.0.0.1 Mask: 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING UTU:16436 Metric:1
RX Packets:1147579 errors:0 dropped:0 overruns:0 frame:0
TX Packets:114579 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX Bytes:88626418(84.5 MiB) TX Bytes:88626418(84.5 MiB)

route:

Kernal IP Routing Table
Destination   Gateway   Genmask   Flags  Metric   Ref   Use   Interface
10.0.0.0        *               255.0.0.0  U         0          0      0       eth0
default          10.1.1.1    0.0.0.0      UG       0          0      0       eth0


And yes, I can ping 127.0.0.1.
Man that took aaaaaages to write down & type up again... hope it was worth it.

---

### Post by heimo on 2005-08-16
[QUOTE=koggo]
Link encap:Ethernet Hwaddr 00:CO:4F:8E:B4:D4
inet addr: 10.1.1.9 Bcast:10.155.155.155 Mask: 255.0.0.0
[/QUOTE]

Your broadcast address should most probably be 10.255.255.255. Don't know if it'll have any effect on your network problems.

---

### Post by koggo on 2005-08-16
[QUOTE=heimo]Your broadcast address should most probably be 10.255.255.255. Don't know if it'll have any effect on your network problems.[/QUOTE]

Oops that was a typo  :?

---

### Post by heimo on 2005-08-16
[QUOTE=koggo]Oops that was a typo  :?[/QUOTE]

Oh! You really typed all that... *wow* I really hope we can help you fix it.

---

### Post by koggo on 2005-08-16
Yes, *and*  im a slow typer.
Its all because I have no internet or network to copy & paste it to!

---

### Post by heimo on 2005-08-16
Can you ping the gateway? 10.1.1.1
 ```
ping 10.1.1.1

``` 

If yes, is DNS working correctly? 
 ```
dig ubuntu.com
``` 

If not, try disabling ipv6
[http://ubuntuforums.org/showthread.php?t=53451]("http://ubuntuforums.org/showthread.php?t=53451")
(restart after this change)

EDIT: No need to give exact outputs on these.

---

### Post by koggo on 2005-08-17
[QUOTE=heimo]Can you ping the gateway? 10.1.1.1
 ```
ping 10.1.1.1

``` 

If yes, is DNS working correctly? 
 ```
dig ubuntu.com
``` 

If not, try disabling ipv6
[http://ubuntuforums.org/showthread.php?t=53451]("http://ubuntuforums.org/showthread.php?t=53451")
(restart after this change)

EDIT: No need to give exact outputs on these.[/QUOTE]
 Nope :(

---

### Post by heimo on 2005-08-17
Do you have a link led (usually small green led near ethernet connector) on your network interface card? Is it lit? Howabout on the router / switch / other end of the cable?

---

### Post by koggo on 2005-08-17
[QUOTE=heimo]Do you have a link led (usually small green led near ethernet connector) on your network interface card? Is it lit? Howabout on the router / switch / other end of the cable?[/QUOTE]
 Yes on the ethernet card it has a green and an orange light, and on the router it has a green light, but it's not flashing, meaning it's connected but no activity.

---

### Post by heimo on 2005-08-17
If you change back to using DHCP and run 
```
sudo dhclient eth0
``` 
what do you get?

Isn't the network card / router ACT led blinking even then? Does it get "bind to" an ip address? If yes, howabout the ping / dig after that? Can you provide us any more details, dig some logs to find any error messages during boot? dmesg?

---

### Post by relix42 on 2005-08-17
[QUOTE=koggo]
eth0:
Link encap:Ethernet Hwaddr 00:CO:4F:8E:B4:D4
inet addr: 10.1.1.9 Bcast:10.155.155.155 Mask: 255.0.0.0
inet6addr: fe80::2co:4fff:fe8e:bfd4/f4 Scope:Link
UP BROADCASTING RUNNING MULTICAST MTU:1500 Metric:1
RX Packets:0 errors:1 dropped:0 overruns:0 frame:1
TX Packets:11449 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisions:3 txqueuelen:1000
RX bytes:0(0.0 b) TX Bytes:1678902 (1.0 MiB)
Interrupt: 19 Base Address: 0xdc00

Kernal IP Routing Table
Destination   Gateway   Genmask   Flags  Metric   Ref   Use   Interface
10.0.0.0        *               255.0.0.0  U         0          0      0       eth0
default          10.1.1.1    0.0.0.0      UG       0          0      0       eth0
[/QUOTE]

Unless your network is enourmous, I would say that with the combination of your IP address and gateway, your netmask should be 255.255.255.0 not 255.0.0.0.  This shouldn't effert your routing to local machines, but, should be fixed to eliminate it as an issue.

Additionally, you can try pinging the broadcast address to see if any of the machines can see you (ping -b 10.1.1.0 if you correct your netmask, 10.0.0.0 if you don't.) - a brodcast ping should have all the machines on the local subnet reponding to you.

 If you still can't get anything, it would seem to be a layer 1 or 2 issue (cables, cards and switches.)  Switch reboot perhaps?

---

### Post by nad on 2005-08-17
This info is helpful. Please also post the output of lsmod .

Support for these older network cards is waning. I have seen bios and duplex setting related issues with these.

Please see [http://www.scyld.com/vortex.html](http://www.scyld.com/vortex.html) for full details.

---

### Post by koggo on 2005-08-18
Yay, it's working again!

I did this:

```
sudo dhclient eth0
```

and it worked! even though i didnt change back to DHCP.

---

