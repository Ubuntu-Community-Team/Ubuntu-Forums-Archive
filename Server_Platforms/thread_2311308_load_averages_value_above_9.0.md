---
title: "load averages value above 9.0"
date: 2016-01-26
forum: Server Platforms
---

### Post by cavarks on 2016-01-26
Greetings all,

I was after advice on a server setup with a couple of raid 6 arrays, that only hold large amounts of data, no real processing requirements at all.

The issue I have is this:

cavarks@server:~$ uptime
 23:00:29 up 5 days,  4:22,  2 users,  load average: 9.09, 9.04, 9.05

now running htop also show load average at this level, but visually show each core usage level at below 1% (constantly)
It an AMD Athlon(tm) 64 X2 Dual Core Processor 3800+

cavarks@server:~$ uname -a
Linux server 3.13.0-76-generic #120-Ubuntu SMP Mon Jan 18 15:59:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Memory usage is at 18% and no swap usage.
iotop indicated little activity...

This machine was originally a server 10.04LTS install with gnome then -> 12.04LTS -> 14.04LTS

Any tips as to what might be going on?

M.

---

### Post by Doug S on 2016-01-26
When top does not identify CPU usage or I/O wait as the source of the load average, then it might be a task or tasks in uninterruptible sleep (nine tasks in your case). Identify them with this command:

```
ps -e -o state,pid,cmd | grep ^D
```

vmstat can also be used, but only to give the number of tasks in uninterruptible sleep. Example:

```
doug@doug-64:~$ vmstat
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
0  0    168  69980 124836 2525672    0    0   252    29    1    0  0  0 99  0
```

where tasks in uninterruptible sleep are under the "b" column under "procs".

---

### Post by nerdtron on 2016-01-26
```
I was after advice on a server setup with a couple of raid 6 arrays, 
```

Raid 6 can be quite I/O intensive since it doubles the parity bit. Also if you use it as a NFS or Samba share, those can be increase CPU usage. What processes have high read or writes?

---

### Post by cavarks on 2016-01-26
Thanks for the reply guys.  I did something silly and restarted it Yesterday. As the load issue does not show up for a few days, I will have to wait.   

So I will dig a little deeper into it when the load climbs again. I have to say these LTS builds are rather impressive. Especially the upgrade path. This box was installed with 10.04 about 5 years ago.  2 upgrades later with all the packages that I have installed over that time (and unity with 12.04) and it does not miss a beat. This is really the first issue I have had, and it wasn't noticeable until I looked at the numbers. Obviously.  =)    

> What processes have high read or writes?    
None.    

> number of tasks in uninterruptible sleep.   
Yes, due to my ignorance I did not think to check. Thanks for the heads up. 
I am sure I will come back and ask for advice if I find tasks in such a state and I can't resolve the cause. 

   Cheers.  
M.

---

### Post by Doug S on 2016-01-26
> **cavarks said:**
> I am sure I will come back and ask for advice if I find tasks in such a state and I can't resolve the cause.Please come back and let us know, regardless. We always like to know how things turn out.

---

### Post by cavarks on 2016-01-28
Looks like a USB issue. Might be a hardware issue with the usb hub between the PC, keyboard and mouse. I normally ssh into the box, finally got time to dig into the syslog and found most of the log was full of this stuff. Feel kinda stupid I didn't check that first...

```
Jan 28 03:31:39 www mtp-probe: checking bus 1, device 5: "/sys/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.4"
Jan 28 03:31:39 www mtp-probe: bus: 1, device: 5 was not an MTP device
Jan 28 03:31:39 www kernel: [101309.528547] usb 1-3.4: USB disconnect, device number 5
Jan 28 03:31:39 www kernel: [101309.728030] usb 1-3.4: new low-speed USB device number 6 using ehci-pci
Jan 28 03:31:39 www kernel: [101309.825174] usb 1-3.4: New USB device found, idVendor=045e, idProduct=0040
Jan 28 03:31:39 www kernel: [101309.825180] usb 1-3.4: New USB device strings: Mfr=1, Product=3, SerialNumber=0
Jan 28 03:31:39 www kernel: [101309.825184] usb 1-3.4: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
Jan 28 03:31:39 www kernel: [101309.825186] usb 1-3.4: Manufacturer: Microsoft
Jan 28 03:31:39 www kernel: [101309.831161] usbhid 1-3.4:1.0: can't add hid device: -32
Jan 28 03:31:39 www kernel: [101309.831423] usbhid: probe of 1-3.4:1.0 failed with error -32
Jan 28 03:31:39 www mtp-probe: checking bus 1, device 6: "/sys/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.4"
Jan 28 03:31:39 www mtp-probe: bus: 1, device: 6 was not an MTP device
Jan 28 03:31:39 www kernel: [101310.040541] usb 1-3.4: USB disconnect, device number 6
Jan 28 03:31:39 www kernel: [101310.240032] usb 1-3.4: new low-speed USB device number 7 using ehci-pci
Jan 28 03:31:40 www kernel: [101310.337166] usb 1-3.4: New USB device found, idVendor=045e, idProduct=0040
Jan 28 03:31:40 www kernel: [101310.337170] usb 1-3.4: New USB device strings: Mfr=1, Product=3, SerialNumber=0
Jan 28 03:31:40 www kernel: [101310.337173] usb 1-3.4: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
Jan 28 03:31:40 www kernel: [101310.337175] usb 1-3.4: Manufacturer: Microsoft
Jan 28 03:31:40 www kernel: [101310.343162] usbhid 1-3.4:1.0: can't add hid device: -32
Jan 28 03:31:40 www kernel: [101310.343414] usbhid: probe of 1-3.4:1.0 failed with error -32
Jan 28 03:31:40 www mtp-probe: checking bus 1, device 7: "/sys/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.4"
Jan 28 03:31:40 www mtp-probe: bus: 1, device: 7 was not an MTP device
Jan 28 03:31:40 www kernel: [101310.552541] usb 1-3.4: USB disconnect, device number 7
Jan 28 03:31:40 www kernel: [101310.752034] usb 1-3.4: new low-speed USB device number 8 using ehci-pci
Jan 28 03:31:40 www kernel: [101310.849043] usb 1-3.4: New USB device found, idVendor=045e, idProduct=0040
Jan 28 03:31:40 www kernel: [101310.849047] usb 1-3.4: New USB device strings: Mfr=1, Product=3, SerialNumber=0
Jan 28 03:31:40 www kernel: [101310.849050] usb 1-3.4: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
Jan 28 03:31:40 www kernel: [101310.849053] usb 1-3.4: Manufacturer: Microsoft
Jan 28 03:31:40 www kernel: [101310.855162] usbhid 1-3.4:1.0: can't add hid device: -32
Jan 28 03:31:40 www kernel: [101310.855415] usbhid: probe of 1-3.4:1.0 failed with error -32
Jan 28 03:31:40 www mtp-probe: checking bus 1, device 8: "/sys/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.4"
Jan 28 03:31:40 www mtp-probe: bus: 1, device: 8 was not an MTP device
Jan 28 03:31:40 www kernel: [101311.064543] usb 1-3.4: USB disconnect, device number 8
Jan 28 03:31:41 www kernel: [101311.264030] usb 1-3.4: new low-speed USB device number 9 using ehci-pci
Jan 28 03:31:41 www kernel: [101311.361035] usb 1-3.4: New USB device found, idVendor=045e, idProduct=0040
Jan 28 03:31:41 www kernel: [101311.361039] usb 1-3.4: New USB device strings: Mfr=1, Product=3, SerialNumber=0
Jan 28 03:31:41 www kernel: [101311.361042] usb 1-3.4: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
Jan 28 03:31:41 www kernel: [101311.361044] usb 1-3.4: Manufacturer: Microsoft
Jan 28 03:31:41 www kernel: [101311.366171] usbhid 1-3.4:1.0: can't add hid device: -32
Jan 28 03:31:41 www kernel: [101311.366427] usbhid: probe of 1-3.4:1.0 failed with error -32
Jan 28 03:31:41 www mtp-probe: checking bus 1, device 9: "/sys/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.4"
Jan 28 03:31:41 www mtp-probe: bus: 1, device: 9 was not an MTP device
```


```
28 17:35:56 www kernel: [151966.303219] usb 1-3.3: USB disconnect, device number 4
Jan 28 17:35:56 www acpid: input device has been disconnected, fd 6
Jan 28 17:35:56 www acpid: input device has been disconnected, fd 7
Jan 28 17:35:56 www kernel: [151966.556032] usb 1-3.3: new low-speed USB device number 23 using ehci-pci
Jan 28 17:35:56 www kernel: [151966.657470] usb 1-3.3: New USB device found, idVendor=04cf, idProduct=0022
Jan 28 17:35:56 www kernel: [151966.657476] usb 1-3.3: New USB device strings: Mfr=2, Product=2, SerialNumber=2
Jan 28 17:35:56 www kernel: [151966.657479] usb 1-3.3: Product: USB Keyboard
Jan 28 17:35:56 www kernel: [151966.657482] usb 1-3.3: Manufacturer: USB Keyboard
Jan 28 17:35:56 www kernel: [151966.657484] usb 1-3.3: SerialNumber: USB Keyboard
Jan 28 17:35:56 www kernel: [151966.665214] input: USB Keyboard USB Keyboard as /devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.3/1-3.3:1.0/input/input193
Jan 28 17:35:56 www kernel: [151966.665433] hid-generic 0003:04CF:0022.00BE: input,hidraw0: USB HID v1.10 Keyboard [USB Keyboard USB Keyboard] on usb-0000:00:02.1-3.3/input0
Jan 28 17:35:56 www kernel: [151966.665724] usb 1-3.3: ctrl urb status -75 received
Jan 28 17:35:59 www kernel: [151969.716720] input: USB Keyboard USB Keyboard as /devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.3/1-3.3:1.1/input/input194
Jan 28 17:38:40 www kernel: [152131.170253] hid-generic 0003:04CF:0022.00BE: can't reset device, 0000:00:02.1-3.3/input0, status -71
Jan 28 17:38:40 www kernel: [152131.209268] hid-generic 0003:04CF:0022.00BE: can't reset device, 0000:00:02.1-3.3/input0, status -71
Jan 28 17:38:40 www kernel: [152131.249245] hid-generic 0003:04CF:0022.00BE: can't reset device, 0000:00:02.1-3.3/input0, status -71
Jan 28 17:38:41 www kernel: [152131.289243] hid-generic 0003:04CF:0022.00BE: can't reset device, 0000:00:02.1-3.3/input0, status -71
Jan 28 17:38:41 www kernel: [152131.329241] hid-generic 0003:04CF:0022.00BE: can't reset device, 0000:00:02.1-3.3/input0, status -71
Jan 28 17:38:41 www kernel: [152131.369246] hid-generic 0003:04CF:0022.00BE: can't reset device, 0000:00:02.1-3.3/input0, status -71
Jan 28 17:38:41 www kernel: [152131.409242] hid-generic 0003:04CF:0022.00BE: can't reset device, 0000:00:02.1-3.3/input0, status -71
Jan 28 17:38:41 www kernel: [152131.449243] hid-generic 0003:04CF:0022.00BE: can't reset device, 0000:00:02.1-3.3/input0, status -71
Jan 28 17:38:41 www kernel: [152131.489241] hid-generic 0003:04CF:0022.00BE: can't reset device, 0000:00:02.1-3.3/input0, status -71
Jan 28 17:38:41 www kernel: [152131.529243] hid-generic 0003:04CF:0022.00BE: can't reset device, 0000:00:02.1-3.3/input0, status -71
Jan 28 17:38:41 www kernel: [152131.569243] hid-generic 0003:04CF:0022.00BE: can't reset device, 0000:00:02.1-3.3/input0, status -71
Jan 28 17:38:41 www kernel: [152131.609246] hid-generic 0003:04CF:0022.00BE: can't reset device, 0000:00:02.1-3.3/input0, status -71
```

---

