---
title: "Line 6 POD XT not recognised"
date: 2015-03-24
forum: Ubuntu Studio
---

### Post by peccancy on 2015-03-24
Hi,
I am totaly new to ubuntu world - I installed ubuntu studio one my machine, cause I am musician and I like all the opportunities of the system. As far as I am very happy with using studio so far, I failed to achieve connecting my POD XT to the computer.

For those who are not familiar with line6 products - POD XT is USB connectable guitar device. [http://line6.com/legacy/podxt/](http://line6.com/legacy/podxt/)

Connecting and turning on POD does not seem to do any thing. I cant find it under sound card in sound preferences, JACK, audacity atc.
I thought POD would be recognised by studio natively. Anyway, I tried to install the Line6 POD USB driver I found there: [http://packages.ubuntu.com/lucid/line6-usb-source](http://packages.ubuntu.com/lucid/line6-usb-source), but without making any difference.

Any ideas what can be issue here? 

As a total newbie, I seem to be totaly hopeless, even after reading through most of the info I was able to find online. It is more or less the last thing I need to get through to enjoy my new system. Thank you very much for any kind of help.

---

### Post by oldfred on 2015-03-25
Your link is for source code from 10.04 or 5 year old system which is now obsolete.

I do not see anything in 14.04 related to line6 or PODxt, but it may have been integrated into various other packages. 

You can check if recognized by USB, but may still need drivers.
 If issues, plug in device and see if shown or error in syslog, contol+c to exit tail listing
lsusb
tail -f /var/log/syslog

Not involved with guitar or music so cannot  help otherwise.

---

### Post by peccancy on 2015-03-25
Thank you very much for help. I uninstalled the old driver and installed new version, but still no success.

POD is recognised by USB:
   vladimir@vladimir-HP-655-Notebook-PC:~$ lsusb  

 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 004 Device 032: ID 0cf3:311d Atheros Communications, Inc.  

 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 002: ID 04f2:b2f4 Chicony Electronics Co., Ltd  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 003 Device 003: ID 0e41:5044 Line6, Inc. PODxt  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  

There seems to be some problem shown is syslog:
   
vladimir@vladimir-HP-655-Notebook-PC:~$ tail -f /var/log/syslog  
 Mar 25 17:43:25 vladimir-HP-655-Notebook-PC kernel: [17691.960558] line6usb 3-1:1.0: Line6 PODxt now disconnected  
 Mar 25 17:43:32 vladimir-HP-655-Notebook-PC kernel: [17699.274772] usb 3-2: new full-speed USB device number 3 using ohci-pci  
 Mar 25 17:43:32 vladimir-HP-655-Notebook-PC kernel: [17699.454772] usb 3-2: New USB device found, idVendor=0e41, idProduct=5044  
 Mar 25 17:43:32 vladimir-HP-655-Notebook-PC kernel: [17699.454785] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0  
 Mar 25 17:43:32 vladimir-HP-655-Notebook-PC kernel: [17699.454791] usb 3-2: Product: PODxt  
 Mar 25 17:43:32 vladimir-HP-655-Notebook-PC kernel: [17699.454796] usb 3-2: Manufacturer: Line 6  
 Mar 25 17:43:32 vladimir-HP-655-Notebook-PC kernel: [17699.456847] line6usb 3-2:1.0: Line6 PODxt found  
 Mar 25 17:43:32 vladimir-HP-655-Notebook-PC kernel: [17699.458986] line6usb 3-2:1.0: Line6 PODxt now attached  
 Mar 25 17:43:32 vladimir-HP-655-Notebook-PC mtp-probe: checking bus 3, device 3: "/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2"  
 Mar 25 17:43:32 vladimir-HP-655-Notebook-PC mtp-probe: bus: 3, device: 3 was not an MTP device  

I tried to google this, but i am still lost.
Any idea what does it mean and how to solve it?
Thank you very much

---

### Post by oldfred on 2015-03-25
Totally different device with same error.  
Needed an entry or device is so old that it is not mtp:
[http://askubuntu.com/questions/505932/ubuntu-14-04-mtp-error](http://askubuntu.com/questions/505932/ubuntu-14-04-mtp-error)

[http://en.wikipedia.org/wiki/Media_Transfer_Protocol](http://en.wikipedia.org/wiki/Media_Transfer_Protocol)

---

### Post by peccancy on 2015-03-27
I am totaly lost:)

I tried to connect the device to another PC running live version of ubuntu studio. It has been corretly set under sound cards and worked with one USB port, but didnt work with the other. Here is syslog of the working one:
```
ubuntu-studio@ubuntu-studio:~$ tail -f /var/log/syslog
Mar 26 16:48:31 ubuntu-studio kernel: [  125.762572] usb 2-1.4: New USB device found, idVendor=0e41, idProduct=5044
Mar 26 16:48:31 ubuntu-studio kernel: [  125.762578] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Mar 26 16:48:31 ubuntu-studio kernel: [  125.762582] usb 2-1.4: Product: PODxt
Mar 26 16:48:31 ubuntu-studio kernel: [  125.762585] usb 2-1.4: Manufacturer: Line 6
Mar 26 16:48:31 ubuntu-studio mtp-probe: checking bus 2, device 6: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4"
Mar 26 16:48:31 ubuntu-studio mtp-probe: bus: 2, device: 6 was not an MTP device
Mar  26 16:48:31 ubuntu-studio kernel: [  125.781057] line6usb: module is  from the staging directory, the quality is unknown, you have been  warned.
Mar 26 16:48:31 ubuntu-studio kernel: [  125.781663] line6usb 2-1.4:1.0: Line6 PODxt found
Mar 26 16:48:31 ubuntu-studio kernel: [  125.782570] line6usb 2-1.4:1.0: Line6 PODxt now attached
Mar 26 16:48:31 ubuntu-studio kernel: [  125.782594] usbcore: registered new interface driver line6usb

I tried to check my machine and it seems POD is working the same way with one of my USB ports. 
                        vladimir@vladimir-HP-655-Notebook-PC:~$ tail -f /var/log/syslog  
 Mar 27 16:06:12 vladimir-HP-655-Notebook-PC kernel: [ 7217.178253] usb 3-2: New USB device found, idVendor=0e41, idProduct=5044 
 Mar 27 16:06:12 vladimir-HP-655-Notebook-PC kernel: [ 7217.178271] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0 
 Mar 27 16:06:12 vladimir-HP-655-Notebook-PC kernel: [ 7217.178281] usb 3-2: Product: PODxt 
 Mar 27 16:06:12 vladimir-HP-655-Notebook-PC kernel: [ 7217.178289] usb 3-2: Manufacturer: Line 6 
 Mar 27 16:06:12 vladimir-HP-655-Notebook-PC mtp-probe: checking bus 3, device 2: "/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2" 
 Mar 27 16:06:12 vladimir-HP-655-Notebook-PC mtp-probe: bus: 3, device: 2 was not an MTP device 
 Mar 27 16:06:12 vladimir-HP-655-Notebook-PC kernel: [ 7217.421972] line6usb: module is from the staging directory, the quality is unknown, you have been warned. 
 Mar 27 16:06:12 vladimir-HP-655-Notebook-PC kernel: [ 7217.424050] line6usb 3-2:1.0: Line6 PODxt found 
 Mar 27 16:06:12 vladimir-HP-655-Notebook-PC kernel: [ 7217.425845] line6usb 3-2:1.0: Line6 PODxt now attached 
 Mar 27 16:06:12 vladimir-HP-655-Notebook-PC kernel: [ 7217.425995] usbcore: registered new interface driver line6usb 

But device is still not set as audio card:
                        
vladimir@vladimir-HP-655-Notebook-PC:~$ cat /proc/asound/cards 
  0 [Generic        ]: HDA-Intel - HD-Audio Generic 
                       HD-Audio Generic at 0x90344000 irq 44 
  1 [Generic_1      ]: HDA-Intel - HD-Audio Generic 
                       HD-Audio Generic at 0x90340000 irq 16 

lsusb says it couldnt open the device:
                        
vladimir@vladimir-HP-655-Notebook-PC:~$ lsusb -d 0e41:5044 -v 

  
 Bus 003 Device 002: ID 0e41:5044 Line6, Inc. PODxt 
 Couldn't open device, some information will be missing 
 Device Descriptor: 

   bLength                18 
   bDescriptorType         1 
   bcdUSB               1.00 
   bDeviceClass          255 Vendor Specific Class 
   bDeviceSubClass         0  
   bDeviceProtocol         0  
   bMaxPacketSize0         8 
   idVendor           0x0e41 Line6, Inc. 
   idProduct          0x5044 PODxt 
   bcdDevice            0.01 
   iManufacturer           1  
   iProduct                2  
   iSerial                 0  
   bNumConfigurations      1 
   Configuration Descriptor: 
     bLength                 9 
     bDescriptorType         2 
     wTotalLength          105 
     bNumInterfaces          1 
     bConfigurationValue     1 
     iConfiguration          0  
     bmAttributes         0xc0 
       Self Powered 
     MaxPower               98mA 
     Interface Descriptor: 
       bLength                 9 
       bDescriptorType         4 
       bInterfaceNumber        0 
       bAlternateSetting       0 
       bNumEndpoints           2 
       bInterfaceClass       255 Vendor Specific Class 
       bInterfaceSubClass      0  
       bInterfaceProtocol      0  
       iInterface              0  
       Endpoint Descriptor: 
         bLength                 7 
         bDescriptorType         5 
         bEndpointAddress     0x01  EP 1 OUT 
         bmAttributes            1 
           Transfer Type            Isochronous 
           Synch Type               None 
           Usage Type               Data 
         wMaxPacketSize     0x0000  1x 0 bytes 
         bInterval               1 
       Endpoint Descriptor: 
         bLength                 7 
         bDescriptorType         5 
         bEndpointAddress     0x82  EP 2 IN 
         bmAttributes            1 
           Transfer Type            Isochronous 
           Synch Type               None 
           Usage Type               Data 
         wMaxPacketSize     0x0000  1x 0 bytes 
         bInterval               1 
     Interface Descriptor: 
       bLength                 9 
       bDescriptorType         4 
       bInterfaceNumber        0 
       bAlternateSetting       1 
       bNumEndpoints           0 
       bInterfaceClass       255 Vendor Specific Class 
       bInterfaceSubClass      0  
       bInterfaceProtocol      0  
       iInterface              0  
     Interface Descriptor: 
       bLength                 9 
       bDescriptorType         4 
       bInterfaceNumber        0 
       bAlternateSetting       2 
       bNumEndpoints           0 
       bInterfaceClass       255 Vendor Specific Class 
       bInterfaceSubClass      0  
       bInterfaceProtocol      0  
       iInterface              0  
     Interface Descriptor: 
       bLength                 9 
       bDescriptorType         4 
       bInterfaceNumber        0 
       bAlternateSetting       3 
       bNumEndpoints           0 
       bInterfaceClass       255 Vendor Specific Class 
       bInterfaceSubClass      0  
       bInterfaceProtocol      0  
       iInterface              0  
     Interface Descriptor: 
       bLength                 9 
       bDescriptorType         4 
       bInterfaceNumber        0 
       bAlternateSetting       4 
       bNumEndpoints           0 
       bInterfaceClass       255 Vendor Specific Class 
       bInterfaceSubClass      0  
       bInterfaceProtocol      0  
       iInterface              0  
     Interface Descriptor: 
       bLength                 9 
       bDescriptorType         4 
       bInterfaceNumber        0 
       bAlternateSetting       5 
       bNumEndpoints           4 
       bInterfaceClass       255 Vendor Specific Class 
       bInterfaceSubClass      0  
       bInterfaceProtocol      0  
       iInterface              0  
       Endpoint Descriptor: 
         bLength                 7 
         bDescriptorType         5 

         bEndpointAddress     0x01  EP 1 OUT 
         bmAttributes            1 
           Transfer Type            Isochronous 
           Synch Type               None 
           Usage Type               Data 
         wMaxPacketSize     0x00f0  1x 240 bytes 
         bInterval               1 
       Endpoint Descriptor: 
         bLength                 7 
         bDescriptorType         5 
         bEndpointAddress     0x82  EP 2 IN 
         bmAttributes            1 
           Transfer Type            Isochronous 
           Synch Type               None 
           Usage Type               Data 
         wMaxPacketSize     0x00fc  1x 252 bytes 
         bInterval               1 
       Endpoint Descriptor: 
         bLength                 7 
         bDescriptorType         5 
         bEndpointAddress     0x03  EP 3 OUT 
         bmAttributes            3 
           Transfer Type            Interrupt 
           Synch Type               None 
           Usage Type               Data 
         wMaxPacketSize     0x0020  1x 32 bytes 
         bInterval              10 
       Endpoint Descriptor: 
         bLength                 7 
         bDescriptorType         5 
         bEndpointAddress     0x84  EP 4 IN 
         bmAttributes            3 
           Transfer Type            Interrupt 
           Synch Type               None 
           Usage Type               Data 
         wMaxPacketSize     0x0020  1x 32 bytes 
         bInterval              10 
```

How is it possible the device works just with one computer and some specific USB port? Could it be some hardware issue?

---

### Post by oldfred on 2015-03-27
Please use code tags for long terminal or text.

Do not know about USB ports other than some can be booted and some not. 
Or is one port USB2 and the other USB3? May be just enough difference in driver to make it work or not.

---

### Post by peccancy on 2015-03-30
Sorry about not using code tags. None of the USB ports used is USB 3. Anyway, problem might be very complex. POD is not officially supported for Linux and the only driver available is this one made by a good guy from Austria: [http://www.tanzband-scream.at/line6/](http://www.tanzband-scream.at/line6/). So I guess the driver might not work with all the computers or devices correctly. I will try to get more info, but until I find out something better, I got simple solution:
I will plug the output from POD directly into soundcard and hopefully I will be able to monitor the sound through headphones plugged into PC. It means I will lose all the advantages of using POD as an external sound card, but that is all I am able to do right now. I will write if this solution is useful.
 Anyway, thank you very much for all the advices.

---

