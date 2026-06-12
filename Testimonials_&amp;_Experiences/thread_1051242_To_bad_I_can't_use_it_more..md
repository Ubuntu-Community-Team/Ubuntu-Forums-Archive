---
title: "To bad I can't use it more."
date: 2009-01-26
forum: Testimonials &amp; Experiences
---

### Post by reeko124 on 2009-01-26
My experience thus far is a mix of good and bad. I have had no problem installing ubuntu as a dual boot. Runs flawlessly and is pretty easy to navigate for a Windows user. Its rather nice to look at. As most people say its nice not to see the blue you get with MS systems. I liked the cursors so much I even put them on my XP install. I started this paragraph to be the good and another one for the bad but I have to explain the bad so you understand the good that came out of it. I hope that made sense.

     The one problem I did have and its major to me at the moment was setting up my internal modem. Without it my use for ubuntu will be next to none. That is the bad part. I tried and I tried to get it setup but it just wouldn't work right I tried for nearly a week. The first time I tried to set it up I was so far off on how to do it then after awhile I got it to dial out but it was stuck at "waiting for carrier". I was proud of myself for getting it that far. I searched and read thread after thread but no one seems to have answers to people that have the same problem. So at that point I have since given up on trying to get it to work. So that is why I haven't gotten deeper into the workings of ubuntu. Which is bad becasue I want to lol.

    Good thing has come from my problem though. After searching and trying to figure it out by reading I now know how to copy, make directories, remove stuff that I installed and how to get to it from terminal fairly easy. So when I do eventually go back to it I will know the basics to help me with other problems I am bound to have. Its funny just from that problem I learned stuff without even trying.

     I just wanted to add that I only tried it because I got bored of Windows and not because I hated it or had problems with it. I guess you got to take care of it more then ubuntu? Alot of people have the problems because they don't take care of it properly I think. Trust me I have seen people have problems with Windows. Maybe ubuntu is better for those people? I nlited XP down to 420mb fully installed and there wasn't much left to do and I wanted a new challenge. I will give ubuntu another try thats for sure.

---

### Post by kingmonkey on 2009-01-26
What modem do you have?

---

### Post by solwic on 2009-01-26
> **reeko124 said:**
> 
     I just wanted to add that I only tried it because I got bored of Windows and not because I hated it or had problems with it. I guess you got to take care of it more then ubuntu? Alot of people have the problems because they don't take care of it properly I think. Trust me I have seen people have problems with Windows. Maybe ubuntu is better for those people? I nlited XP down to 420mb fully installed and there wasn't much left to do and I wanted a new challenge. I will give ubuntu another try thats for sure.

In the end, if you stick with it long enough, you'll find that Ubuntu is the more intuitive of the two systems.  I recently re-installed Windows XP on my Ubuntu-only system (to play a game), and when Xp loaded the first time, it was the only OS on the disk.  I seriously considered just leaving it that way; use the unpartitioned, unformatted space I had set aside for Linux as a data backup, in case I had to reinstall Windows, and just go with it.

It took about two hours for that idea to expose itself for the terrible thing it was.  I loaded Ubuntu back up, and I think I've booted XP three times in as many days, and never for more than an hour or so at a time.  

Take some time and get your head around Ubuntu.  Once you do, you'll wonder why you ever had an issue with which OS to use.  :)

---

### Post by reeko124 on 2009-01-26
Nice to see a fellow Buckeye fan lol. Pryor grew up less then a mile from me BTW.

---

### Post by solwic on 2009-01-26
> **reeko124 said:**
> Nice to see a fellow Buckeye fan lol. Pryor grew up less then a mile from me BTW.

Very cool.  :)  He's going to be really good next season.  Hell, he was really good *this* season.  

:biggrin:

---

### Post by reeko124 on 2009-01-26
> **kingmonkey said:**
> What modem do you have?

Agere System HDA. I got it to dial out but it keeps "waiting for carrier." Anyone else that has had that problem haven't found a solution or they did and just didn't update that they did. I was happy to get that far though.

---

### Post by stalkingwolf on 2009-01-26
I have never had any luck with internal modems of any kind. just couple months ago however I set up two laptops with external modems. one a serial
one a usb. I had both set up and on line in less than 15 min.  I think I
paid 10.00 for one and 15.00 for the other.

---

### Post by albinootje on 2009-01-26
> **reeko124 said:**
>  The one problem I did have and its major to me at the moment was setting up my internal modem. 

What modem is it ?
You do know that "win-modems" exist, no ?

Please post :
```

lspci
lsusb
dmesg | grep -i tty

```

More about "win-modems" : [http://linmodems.org/](http://linmodems.org/)

---

### Post by albinootje on 2009-01-26
Which program are you using to connect ?
kppp could simplify your setup.
> 
$ apt-cache search kppp
kppp-kde4 - modem dialer and ppp frontend for KDE 4
kppp - modem dialer and ppp frontend for KDE


---

### Post by reeko124 on 2009-01-26
> **albinootje said:**
> Which program are you using to connect ?
kppp could simplify your setup.

I was using wvdial and it dials out and but it doesn't connect right so everything is right up to that point.

---

### Post by Old *ix Geek on 2009-01-26
As someone else has already mentioned, there are external modems--cheap!--that will work with Linux.  Honestly, if the modem is the only issue stopping you from using Linux...why not get an external modem? :confused:

---

### Post by 3rdalbum on 2009-01-27
Check the US Robotics website - they have a USB-based hardware modem, works out-of-the-box on Linux.

Or take a look at ADSL; I know it's a bit more to pay each month, but honestly it's worth it.

---

### Post by Maverick1385 on 2009-01-27
Hi guys,same experience here. I have my Ubuntu installed flawlessly and was even able to configure it to my liking. The only thing I can't use now it my TV Tuner. Its a TM5600 TV Tuner and I have been trying and trying to make it work.

I've read hundreds of posts and visited most of the sites I find that talks about installing a TV Tuner on Ubuntu. I even tried compiling the "exeprimental" driver I found on the net for TM5600 TV Tuners to no avail.

Im a techy guy myself but I guess this is too advanced for me. If you guys have any idea how to do this? I'd appreciate the help. 

Thanks!

---

### Post by cariboo on 2009-01-28
Maverick1385

What chipset does your device use? Check:

```
lspci
```

to see.

Jim

---

### Post by Maverick1385 on 2009-01-28
> **cariboo907 said:**
> Maverick1385

What chipset does your device use? Check:

```
lspci
```

to see.

Jim

hi Jim, thanks for the response. im at work right now so i can't try the command you posted. however, i do know that the device' main chipset is the Trident 5600 video decode.

its a cheapo TV Tuner but im hoping to make it work as i had it going on my previous XP/Vista machine. now that im in ubuntu, i hoped for the same results.

here is the product page if you want to know more about it. 
[http://www.bastan-t.com/tva3.html]("http://www.bastan-t.com/tva3.html")


thanks

---

### Post by Maverick1385 on 2009-01-28
bu the way, its a USB TV Tuner so I don't thing the command would detect it. maybe a similar command for USB would work.

thanks

---

### Post by 3rdalbum on 2009-01-28
> **Maverick1385 said:**
> bu the way, its a USB TV Tuner so I don't thing the command would detect it. maybe a similar command for USB would work.

thanks

```
sudo lsusb -v
```

---

### Post by Maverick1385 on 2009-01-28
hi, thanks for the reply. i tried the command you suggested and here's what i got. i guess this is the important part.

```
Bus 005 Device 060: ID 6000:0001  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x6000 
  idProduct          0x0001 
  bcdDevice            0.01
  iManufacturer          16 Trident
  iProduct               32 TVBOX
  iSerial                64 2004090820040908
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           78
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration         48 2.0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
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
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0002
  (Bus Powered)
  Remote Wakeup Enabled

```

it is a Trident TVBox that I have. im glad that Ubuntu was able to see it but my problem is i don't know how to make it work. maybe you guys can help me out. i think we're already straying from the topic but i really need your help if you have any. any input is very much welcome.

thanks guys!

---

