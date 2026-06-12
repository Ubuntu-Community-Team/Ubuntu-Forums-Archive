---
title: "Fedora on bonp5"
date: 2012-03-03
forum: System76 Support
---

### Post by mchauber on 2012-03-03
This is a question that has come up numerous times, and it was a determining factor for me.  I spent over a year (almost two) mulling over different options before I came to the decision of buying this laptop (In truth, I kept coming back thinking, "damn, that's a bad-a55 laptop!)

So far, all is well.  I have Fedora 16 installed with no issues (proprietary nvidia necessary because of cooling, but that's with any nvidia card AFAIK).

I'm hosting 9 virtual machines from a secondary hard drive (replicates my server farm, and only one of them has a gui installed), composing from RoseGarden with over two gigs of soundfonts in the library, watching video, Libre Office, code::blocks, eclipse, anjuta...  it won't slow down!  I Love it!

A big chunk of money, but I got what I paid for, so it was money well spent (I actually didn't have to exchange hardware quality for a M5 bully-tax)...  All I can say is "You go System76!  Dill and HiPpie are far below you, and so long as they continue to prison-wrap their customers with their M5-tax, I will never buy from them again."  System76 is the new god on the block.

So for a final answer, "**_Yes!_  Fedora 16 works _flawlessly_ on my bonp5**!"  And if you're reading this while thinking about getting one for yourself, don't waste two years thinking about it...  that's time you won't get back.

YAY!  :)

---

### Post by smarmytime on 2012-03-03
Wow, that thing is a monster.

Yeah, I've also been using a different linux distro - Arch, and it works fantastically well on my PanP7, which I credit to System76 putting all the right hardware together.

---

### Post by BBQdave on 2012-03-04
> **mchauber said:**
> So for a final answer, "**_Yes!_  Fedora 16 works _flawlessly_ on my bonp5**!"  And if you're reading this while thinking about getting one for yourself, don't waste two years thinking about it...  that's time you won't get back.

YAY!  :)

Thanks for the information. Getting the Lemur Ultra soon and would like to run Fedora 16. Once I have run the Lemur Ultra for awhile with F16, I will give feedback on my experience.

IMO: researched new hardware the past couple of months and System76 is a good bargain on good components in their notebooks. Plus you are supporting a smaller vendor and not paying M$ tax  :D

---

### Post by mchauber on 2012-03-07
Looks like I spoke too soon.  Everything works but the fingerprint scanner.  It's no big deal, and I still wouldn't have used it (haven't played with them long enough to trust it).  I still would have liked to play with it, though.

```


$ fprintd-enroll
list_devices failed: No devices available

$ lsusb | grep Upek
Bus 002 Device 003: ID 147e:1001 Upek

# lsusb -v -d 147e:1001
Bus 002 Device 003: ID 147e:1001 Upek 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x147e Upek
  idProduct          0x1001 
  bcdDevice            0.43
  iManufacturer           1 TouchStrip        
  iProduct                2 Fingerprint Sensor   
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)


```

---

