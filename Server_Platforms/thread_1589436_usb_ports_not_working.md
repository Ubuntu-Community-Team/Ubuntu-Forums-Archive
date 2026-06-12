---
title: "usb ports not working"
date: 2010-10-06
forum: Server Platforms
---

### Post by 1Robomaker on 2010-10-06
Just installed ubuntu 10.4 server 64 on my system. Everything seems to  have gone fine. I installed the desktop from the command line.  Everything has gone perfect thus far I am very excited! However none of  my usb ports are working at all. worked fine when I had windows 7 on  this box. please help with some direction. I desperatly want to start  using this powerful os!
 
Thanks

---

### Post by arrrghhh on 2010-10-06
Well, for one why did you install the desktop from the cli?

If you want the desktop edition, it's best to just install the desktop edition ;)

With that said, nothing you did should have effected USB.  If you do a ```
lsusb
``` does it produce any useful output?

FYI, if you want a cli-based server, install server.  If you want a DE (desktop environment), install desktop!

---

### Post by 1Robomaker on 2010-10-06
Server is the only version that would install. all other live cd's would make my screen go black "no signal"
Figured would be good to learn ubuntu server anyway.

To answer your question about lsusb in terminal, I recieve this responce:

toby@ubuntu:~$ lsusb
toby@ubuntu:~$ 

Nothing... just a little direction would be appreciated.
Thank you for your help by the way:)

---

### Post by arrrghhh on 2010-10-06
Hrm, usb definitely does not seem to be working at all.  If you say all other live cd's would make your screen go black!?!?

Perhaps there's something about your hardware that Ubuntu doesn't like...  Can't really help you there, perhaps the alternate installer?

---

### Post by 1Robomaker on 2010-10-06
Please forgive my ignorance, but how would that help??
Still a newbe to linux. been working on MS for 10 yrs ready to jump ship......

---

### Post by dtfinch on 2010-10-06
A quick search for "lsusb no output" led me to [http://ubuntuforums.org/showthread.php?t=403487](http://ubuntuforums.org/showthread.php?t=403487) , where they had accidentally disabled their usb ports by resetting their bios settings.

---

### Post by 1Robomaker on 2010-10-06
I wish that was the case. I have a separate hdd with windows 7 on it and when I switch to that one usb ports work perfectly.
That situation is very similar to mine though with the output I have been receiving from terminal.
Any other thoughts??
Thanks again for your help. I have been searching for 3 days now and all I get is stupid usb live install threads...

---

### Post by arrrghhh on 2010-10-06
> **1Robomaker said:**
> Please forgive my ignorance, but how would that help?

I assume you're talking about the alternate install disc?  It's for low-end systems that don't play nice with the full LiveCD...

---

### Post by 1Robomaker on 2010-10-06
ah i see, maybe I should give that a shot and see what happens. The only way I can get the live cd's to work is to select noapic from F6 options. Still won't install with out giving me a black screen at reboot and usb still does not work, but the live cd works.

---

### Post by arrrghhh on 2010-10-06
I'm... kinda lost here.

Can you post a thorough list of the hardware specs?

---

### Post by 1Robomaker on 2010-10-06
**Hardware****Base processor ** Athlon 64 3700+ 2.2 GHz 

[LIST]
[*] 2000 MT/s (Mega Transfers/second)
[*]Socket 939
[/LIST]


**Chipset**ATI Radeon XPress 200

**Motherboard**
[LIST]
[*]Manufacturer: ASUS
[*]Motherboard Name: A8AE-LE
[*]HP/Compaq motherboard name: AmberineM-GL6E
[/LIST]


**Memory**ComponentAttributesMemory Installed1 GB (2 x 512)Maximum allowed4 GB* (4 x 1 GB) requires the replacement of the installed 512 MB DIMMs

*Actual available memory may be lessSpeed supportedPC3200 MB/secType184 pin, DDR SDRAMDIMM slotsFourOpen DIMM slotsTwo

**Hard drive**
[LIST]
[*]200 GB SATA
[*] 7200 rpm
[/LIST]


**16x DVD(+/-)R/RW (+/-)R DL LightScribe drive**
[LIST]
[*]must use Double-Layer media discs in order to take advantage of the DL technology
[*]must use LightScribe-enabled media discs and supporting software in order to take advantage of the LightScribe technology
[/LIST]

typeAttributesDVD-R DL Write Once4XDVD+R DL Write Once2.4XDVD+R Write Once16XDVD+RW Rewritable4XDVD-R Write Once8XDVD-RW Rewritable4XDVD ROM Read16XCD-R Write Once40XCD-RW Rewritable24XCD-ROM Read40X

**CD ROM**                     Maximum speed                     48X                 

**Modem**PCI K56flex data/fax modem

**Video graphics**Integrated graphics 

**Sound/audio**
[LIST]
[*]Controller: AC97 audio
[*]Location: Integrated
[/LIST]


**Network (LAN)**Integrated 10/100 Base-T networking interface



**External I/O ports**I/O ports on  the front panel

Port typeQuantity9-in-1 (4 slot) + 1 USBOneIEEE 1394One  USB (2.0)Two  HeadphoneOne  Line-inOne  MicrophoneOne
I/O ports on the back panel

Port typeQuantityPS/2 (keyboard, mouse)Two (one each)VGA (monitor)One  ParallelOne  USB (2.0)FourIEEE 1394OneLANOne  AudioOne each  (line-in, line-out, microphone)    

**Expansion slots**Slot typeQuantityPCIThree (two available)  PCI ExpressOne (available)DIMM Four (two available)  

**Drive bays**Bay typeQuantity5.25-inch, externalTwo (occupied)3.5-inch, externalTwo (one available)3.5-inch, internalOne (occupied)

**Keyboard and mouse**
[LIST]
[*]HP PS/2 multimedia  keyboard
[*]Quebec Keyboard Kit (French Canada only)
[*]HP PS/2 scroller mouse
[/LIST]

---

### Post by 1Robomaker on 2010-10-06
Thank you for your help anything is much appreciated......

---

### Post by 1Robomaker on 2010-10-06
To all concerned:
Thank you for your help in troubleshooting this matter. After research on the meaning of noapic nolapic I found the answer.
Those were the only options that would allow me to install or view live cd but with no usb ports.

Turns out that my bios needed to be updated, after updating my bios all is well!
I am enjoying the use of my usb once again.

Thanks all for being newbe friendly :)

---

### Post by arrrghhh on 2010-10-06
> **1Robomaker said:**
> To all concerned:
Thank you for your help in troubleshooting this matter. After research on the meaning of noapic nolapic I found the answer.
Those were the only options that would allow me to install or view live cd but with no usb ports.

Turns out that my bios needed to be updated, after updating my bios all is well!
I am enjoying the use of my usb once again.

Thanks all for being newbe friendly :)

Interesting... That's a new one for me. Glad to hear you got it working!!

There is a "Thread Tools" menu, if you could use that and mark this thread [SOLVED] that would be awesome!  Thanks, and hopefully others will learn from this thread!

---

