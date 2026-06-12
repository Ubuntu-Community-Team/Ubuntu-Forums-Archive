---
title: "ubuntu studio 64: can't get camcorder recognized to extract miniDV onto computer"
date: 2008-12-22
forum: Ubuntu Studio
---

### Post by JesseDaniel on 2008-12-22
Hello,

I have recently made the transition to linux (ubuntu studio actually installed when ubuntu and mint would not). Overall, I have been excited and pleased with the results, with much of my computer functioning much better than when it was running windows. 

I am currently making a documentary, and have recorded footage onto minidv tape. (Since I cannot afford overpriced adobe software, I made the switch to linux to ensure an ethically sound project from beginning to end).

unfortunately, any program I try I cannot get the camcorder recognized/connected through firewire. 

when I connect the camera, kdenlive insists it is not connected.

I am currently using a budget canon ZR930 with a belkin firewire cable,
with a computer system including:

ubuntustudio 8.10 64bit
2.00 gigahertz AMD Athlon 64 X2 Dual Core
128 kilobyte primary memory cache
512 kilobyte secondary memory cache
1920 Megabytes Installed Memory on 
Board: ASUSTek Computer INC. M2NPV-VM 1.xx
Bus Clock: 200 megahertz

NVIDIA GeForce 6150 [Display adapter]
Default Monitor
ViewSonic VX2235wm-3 [Monitor] (22.0"vis, s/n QCZ0642A2754, October 2006) --connected digitally

ATI Unified AVStream Driver
MPU-401 Compatible MIDI Device
SoundMAX Integrated Digital HD Audio



I would greatly appreciate any and all help to solve a problem that is no doubt simple for many, but one that I have no clear idea how to fix.

Many thanks,

---

### Post by nlz on 2008-12-22
welcome to the club. What you could do to see if the computer actually 'sees' anything is checking if the device shows up in /dev. So open a terminal (Applications > accessories > terminal) 
type: cd /dev
ls

then connect the camcorder, switch it on and do it again so you see if your computer sees something.

Post your findings here, and we'll help you further.

---

### Post by JesseDaniel on 2008-12-22
Thank you for your reply:

the two readouts I get from the terminal are as follows:
```

adsp                ptyd2  ptyt8  ptyze       tty55  ttyp9  ttyvb

audio               ptyd3  ptyt9  ptyzf       tty56  ttypa  ttyvc

block               ptyd4  ptyta  ram0        tty57  ttypb  ttyvd

bus                 ptyd5  ptytb  ram1        tty58  ttypc  ttyve

cdrom               ptyd6  ptytc  ram10       tty59  ttypd  ttyvf

cdrw                ptyd7  ptytd  ram11       tty6   ttype  ttyw0

char                ptyd8  ptyte  ram12       tty60  ttypf  ttyw1

console             ptyd9  ptytf  ram13       tty61  ttyq0  ttyw2

core                ptyda  ptyu0  ram14       tty62  ttyq1  ttyw3

cpu_dma_latency     ptydb  ptyu1  ram15       tty63  ttyq2  ttyw4

disk                ptydc  ptyu2  ram2        tty7   ttyq3  ttyw5

dsp                 ptydd  ptyu3  ram3        tty8   ttyq4  ttyw6

dv1394              ptyde  ptyu4  ram4        tty9   ttyq5  ttyw7

dvd                 ptydf  ptyu5  ram5        ttya0  ttyq6  ttyw8

dvdrw               ptye0  ptyu6  ram6        ttya1  ttyq7  ttyw9

fd                  ptye1  ptyu7  ram7        ttya2  ttyq8  ttywa

full                ptye2  ptyu8  ram8        ttya3  ttyq9  ttywb

fuse                ptye3  ptyu9  ram9        ttya4  ttyqa  ttywc

hidraw0             ptye4  ptyua  random      ttya5  ttyqb  ttywd

hidraw1             ptye5  ptyub  raw1394     ttya6  ttyqc  ttywe

hpet                ptye6  ptyuc  rtc         ttya7  ttyqd  ttywf

initctl             ptye7  ptyud  rtc0        ttya8  ttyqe  ttyx0

input               ptye8  ptyue  scd0        ttya9  ttyqf  ttyx1

kmem                ptye9  ptyuf  sda         ttyaa  ttyr0  ttyx2

kmsg                ptyea  ptyv0  sda1        ttyab  ttyr1  ttyx3

log                 ptyeb  ptyv1  sda2        ttyac  ttyr2  ttyx4

loop0               ptyec  ptyv2  sda5        ttyad  ttyr3  ttyx5

loop1               ptyed  ptyv3  sdb         ttyae  ttyr4  ttyx6

loop2               ptyee  ptyv4  sdb1        ttyaf  ttyr5  ttyx7

loop3               ptyef  ptyv5  sdc         ttyb0  ttyr6  ttyx8

loop4               ptyp0  ptyv6  sdd         ttyb1  ttyr7  ttyx9

loop5               ptyp1  ptyv7  sde         ttyb2  ttyr8  ttyxa

loop6               ptyp2  ptyv8  sdf         ttyb3  ttyr9  ttyxb

loop7               ptyp3  ptyv9  sequencer   ttyb4  ttyra  ttyxc

lp0                 ptyp4  ptyva  sequencer2  ttyb5  ttyrb  ttyxd

MAKEDEV             ptyp5  ptyvb  sg0         ttyb6  ttyrc  ttyxe

mcelog              ptyp6  ptyvc  sg1         ttyb7  ttyrd  ttyxf

mem                 ptyp7  ptyvd  sg2         ttyb8  ttyre  ttyy0

mixer               ptyp8  ptyve  sg3         ttyb9  ttyrf  ttyy1

net                 ptyp9  ptyvf  sg4         ttyba  ttyS0  ttyy2

network_latency     ptypa  ptyw0  sg5         ttybb  ttys0  ttyy3

network_throughput  ptypb  ptyw1  sg6         ttybc  ttyS1  ttyy4

null                ptypc  ptyw2  shm         ttybd  ttys1  ttyy5

nvidia0             ptypd  ptyw3  snapshot    ttybe  ttyS2  ttyy6

nvidiactl           ptype  ptyw4  snd         ttybf  ttys2  ttyy7

oldmem              ptypf  ptyw5  sndstat     ttyc0  ttyS3  ttyy8

parport0            ptyq0  ptyw6  sr0         ttyc1  ttys3  ttyy9

port                ptyq1  ptyw7  stderr      ttyc2  ttys4  ttyya

ppp                 ptyq2  ptyw8  stdin       ttyc3  ttys5  ttyyb

psaux               ptyq3  ptyw9  stdout      ttyc4  ttys6  ttyyc

ptmx                ptyq4  ptywa  tty         ttyc5  ttys7  ttyyd

pts                 ptyq5  ptywb  tty0        ttyc6  ttys8  ttyye

ptya0               ptyq6  ptywc  tty1        ttyc7  ttys9  ttyyf

ptya1               ptyq7  ptywd  tty10       ttyc8  ttysa  ttyz0

ptya2               ptyq8  ptywe  tty11       ttyc9  ttysb  ttyz1

ptya3               ptyq9  ptywf  tty12       ttyca  ttysc  ttyz2

ptya4               ptyqa  ptyx0  tty13       ttycb  ttysd  ttyz3

ptya5               ptyqb  ptyx1  tty14       ttycc  ttyse  ttyz4

ptya6               ptyqc  ptyx2  tty15       ttycd  ttysf  ttyz5

ptya7               ptyqd  ptyx3  tty16       ttyce  ttyt0  ttyz6

ptya8               ptyqe  ptyx4  tty17       ttycf  ttyt1  ttyz7

ptya9               ptyqf  ptyx5  tty18       ttyd0  ttyt2  ttyz8

ptyaa               ptyr0  ptyx6  tty19       ttyd1  ttyt3  ttyz9

ptyab               ptyr1  ptyx7  tty2        ttyd2  ttyt4  ttyza

ptyac               ptyr2  ptyx8  tty20       ttyd3  ttyt5  ttyzb

ptyad               ptyr3  ptyx9  tty21       ttyd4  ttyt6  ttyzc

ptyae               ptyr4  ptyxa  tty22       ttyd5  ttyt7  ttyzd

ptyaf               ptyr5  ptyxb  tty23       ttyd6  ttyt8  ttyze

ptyb0               ptyr6  ptyxc  tty24       ttyd7  ttyt9  ttyzf

ptyb1               ptyr7  ptyxd  tty25       ttyd8  ttyta  urandom

ptyb2               ptyr8  ptyxe  tty26       ttyd9  ttytb  usbdev1.1_ep00

ptyb3               ptyr9  ptyxf  tty27       ttyda  ttytc  usbdev1.1_ep81

ptyb4               ptyra  ptyy0  tty28       ttydb  ttytd  usbdev1.3_ep00

ptyb5               ptyrb  ptyy1  tty29       ttydc  ttyte  usbdev1.3_ep81

ptyb6               ptyrc  ptyy2  tty3        ttydd  ttytf  usbdev1.3_ep82

ptyb7               ptyrd  ptyy3  tty30       ttyde  ttyu0  usbdev1.4_ep00

ptyb8               ptyre  ptyy4  tty31       ttydf  ttyu1  usbdev1.4_ep81

ptyb9               ptyrf  ptyy5  tty32       ttye0  ttyu2  usbdev2.1_ep00

ptyba               ptys0  ptyy6  tty33       ttye1  ttyu3  usbdev2.1_ep81

ptybb               ptys1  ptyy7  tty34       ttye2  ttyu4  usbdev2.4_ep00

ptybc               ptys2  ptyy8  tty35       ttye3  ttyu5  usbdev2.4_ep01

ptybd               ptys3  ptyy9  tty36       ttye4  ttyu6
usbdev2.4_ep82

ptybe               ptys4  ptyya  tty37       ttye5  ttyu7  vcs

ptybf               ptys5  ptyyb  tty38       ttye6  ttyu8  vcs1

ptyc0               ptys6  ptyyc  tty39       ttye7  ttyu9  vcs2

ptyc1               ptys7  ptyyd  tty4        ttye8  ttyua  vcs3

ptyc2               ptys8  ptyye  tty40       ttye9  ttyub  vcs4

ptyc3               ptys9  ptyyf  tty41       ttyea  ttyuc  vcs5

ptyc4               ptysa  ptyz0  tty42       ttyeb  ttyud  vcs6

ptyc5               ptysb  ptyz1  tty43       ttyec  ttyue  vcs7

ptyc6               ptysc  ptyz2  tty44       ttyed  ttyuf  vcs8

ptyc7               ptysd  ptyz3  tty45       ttyee  ttyv0  vcsa

ptyc8               ptyse  ptyz4  tty46       ttyef  ttyv1  vcsa1

ptyc9               ptysf  ptyz5  tty47       ttyp0  ttyv2  vcsa2

ptyca               ptyt0  ptyz6  tty48       ttyp1  ttyv3  vcsa3

ptycb               ptyt1  ptyz7  tty49       ttyp2  ttyv4  vcsa4

ptycc               ptyt2  ptyz8  tty5        ttyp3  ttyv5  vcsa5

ptycd               ptyt3  ptyz9  tty50       ttyp4  ttyv6  vcsa6

ptyce               ptyt4  ptyza  tty51       ttyp5  ttyv7  vcsa7

ptycf               ptyt5  ptyzb  tty52       ttyp6  ttyv8  vcsa8

ptyd0               ptyt6  ptyzc  tty53       ttyp7  ttyv9  xconsole

ptyd1               ptyt7  ptyzd  tty54       ttyp8  ttyva  zero
```



and typing in 'ls' a second time yields:

```
adsp                ptyd2  ptyt8  ptyze       tty55  ttyp9  ttyvb
audio               ptyd3  ptyt9  ptyzf       tty56  ttypa  ttyvc
block               ptyd4  ptyta  ram0        tty57  ttypb  ttyvd
bus                 ptyd5  ptytb  ram1        tty58  ttypc  ttyve
cdrom               ptyd6  ptytc  ram10       tty59  ttypd  ttyvf
cdrw                ptyd7  ptytd  ram11       tty6   ttype  ttyw0
char                ptyd8  ptyte  ram12       tty60  ttypf  ttyw1
console             ptyd9  ptytf  ram13       tty61  ttyq0  ttyw2
core                ptyda  ptyu0  ram14       tty62  ttyq1  ttyw3
cpu_dma_latency     ptydb  ptyu1  ram15       tty63  ttyq2  ttyw4
disk                ptydc  ptyu2  ram2        tty7   ttyq3  ttyw5
dsp                 ptydd  ptyu3  ram3        tty8   ttyq4  ttyw6
dv1394              ptyde  ptyu4  ram4        tty9   ttyq5  ttyw7
dvd                 ptydf  ptyu5  ram5        ttya0  ttyq6  ttyw8
dvdrw               ptye0  ptyu6  ram6        ttya1  ttyq7  ttyw9
fd                  ptye1  ptyu7  ram7        ttya2  ttyq8  ttywa
full                ptye2  ptyu8  ram8        ttya3  ttyq9  ttywb
fuse                ptye3  ptyu9  ram9        ttya4  ttyqa  ttywc
hidraw0             ptye4  ptyua  random      ttya5  ttyqb  ttywd
hidraw1             ptye5  ptyub  raw1394     ttya6  ttyqc  ttywe
hpet                ptye6  ptyuc  rtc         ttya7  ttyqd  ttywf
initctl             ptye7  ptyud  rtc0        ttya8  ttyqe  ttyx0
input               ptye8  ptyue  scd0        ttya9  ttyqf  ttyx1
kmem                ptye9  ptyuf  sda         ttyaa  ttyr0  ttyx2
kmsg                ptyea  ptyv0  sda1        ttyab  ttyr1  ttyx3
log                 ptyeb  ptyv1  sda2        ttyac  ttyr2  ttyx4
loop0               ptyec  ptyv2  sda5        ttyad  ttyr3  ttyx5
loop1               ptyed  ptyv3  sdb         ttyae  ttyr4  ttyx6
loop2               ptyee  ptyv4  sdb1        ttyaf  ttyr5  ttyx7
loop3               ptyef  ptyv5  sdc         ttyb0  ttyr6  ttyx8
loop4               ptyp0  ptyv6  sdd         ttyb1  ttyr7  ttyx9
loop5               ptyp1  ptyv7  sde         ttyb2  ttyr8  ttyxa
loop6               ptyp2  ptyv8  sdf         ttyb3  ttyr9  ttyxb
loop7               ptyp3  ptyv9  sequencer   ttyb4  ttyra  ttyxc
lp0                 ptyp4  ptyva  sequencer2  ttyb5  ttyrb  ttyxd
MAKEDEV             ptyp5  ptyvb  sg0         ttyb6  ttyrc  ttyxe
mcelog              ptyp6  ptyvc  sg1         ttyb7  ttyrd  ttyxf
mem                 ptyp7  ptyvd  sg2         ttyb8  ttyre  ttyy0
mixer               ptyp8  ptyve  sg3         ttyb9  ttyrf  ttyy1
net                 ptyp9  ptyvf  sg4         ttyba  ttyS0  ttyy2
network_latency     ptypa  ptyw0  sg5         ttybb  ttys0  ttyy3
network_throughput  ptypb  ptyw1  sg6         ttybc  ttyS1  ttyy4
null                ptypc  ptyw2  shm         ttybd  ttys1  ttyy5
nvidia0             ptypd  ptyw3  snapshot    ttybe  ttyS2  ttyy6
nvidiactl           ptype  ptyw4  snd         ttybf  ttys2  ttyy7
oldmem              ptypf  ptyw5  sndstat     ttyc0  ttyS3  ttyy8
parport0            ptyq0  ptyw6  sr0         ttyc1  ttys3  ttyy9
port                ptyq1  ptyw7  stderr      ttyc2  ttys4  ttyya
ppp                 ptyq2  ptyw8  stdin       ttyc3  ttys5  ttyyb
psaux               ptyq3  ptyw9  stdout      ttyc4  ttys6  ttyyc
ptmx                ptyq4  ptywa  tty         ttyc5  ttys7  ttyyd
pts                 ptyq5  ptywb  tty0        ttyc6  ttys8  ttyye
ptya0               ptyq6  ptywc  tty1        ttyc7  ttys9  ttyyf
ptya1               ptyq7  ptywd  tty10       ttyc8  ttysa  ttyz0
ptya2               ptyq8  ptywe  tty11       ttyc9  ttysb  ttyz1
ptya3               ptyq9  ptywf  tty12       ttyca  ttysc  ttyz2
ptya4               ptyqa  ptyx0  tty13       ttycb  ttysd  ttyz3
ptya5               ptyqb  ptyx1  tty14       ttycc  ttyse  ttyz4
ptya6               ptyqc  ptyx2  tty15       ttycd  ttysf  ttyz5
ptya7               ptyqd  ptyx3  tty16       ttyce  ttyt0  ttyz6
ptya8               ptyqe  ptyx4  tty17       ttycf  ttyt1  ttyz7
ptya9               ptyqf  ptyx5  tty18       ttyd0  ttyt2  ttyz8
ptyaa               ptyr0  ptyx6  tty19       ttyd1  ttyt3  ttyz9
ptyab               ptyr1  ptyx7  tty2        ttyd2  ttyt4  ttyza
ptyac               ptyr2  ptyx8  tty20       ttyd3  ttyt5  ttyzb
ptyad               ptyr3  ptyx9  tty21       ttyd4  ttyt6  ttyzc
ptyae               ptyr4  ptyxa  tty22       ttyd5  ttyt7  ttyzd
ptyaf               ptyr5  ptyxb  tty23       ttyd6  ttyt8  ttyze
ptyb0               ptyr6  ptyxc  tty24       ttyd7  ttyt9  ttyzf
ptyb1               ptyr7  ptyxd  tty25       ttyd8  ttyta  urandom
ptyb2               ptyr8  ptyxe  tty26       ttyd9  ttytb  usbdev1.1_ep00
ptyb3               ptyr9  ptyxf  tty27       ttyda  ttytc  usbdev1.1_ep81
ptyb4               ptyra  ptyy0  tty28       ttydb  ttytd  usbdev1.3_ep00
ptyb5               ptyrb  ptyy1  tty29       ttydc  ttyte  usbdev1.3_ep81
ptyb6               ptyrc  ptyy2  tty3        ttydd  ttytf  usbdev1.3_ep82
ptyb7               ptyrd  ptyy3  tty30       ttyde  ttyu0  usbdev1.4_ep00
ptyb8               ptyre  ptyy4  tty31       ttydf  ttyu1  usbdev1.4_ep81
ptyb9               ptyrf  ptyy5  tty32       ttye0  ttyu2  usbdev2.1_ep00
ptyba               ptys0  ptyy6  tty33       ttye1  ttyu3  usbdev2.1_ep81
ptybb               ptys1  ptyy7  tty34       ttye2  ttyu4  usbdev2.4_ep00
ptybc               ptys2  ptyy8  tty35       ttye3  ttyu5  usbdev2.4_ep01
ptybd               ptys3  ptyy9  tty36       ttye4  ttyu6  usbdev2.4_ep82
ptybe               ptys4  ptyya  tty37       ttye5  ttyu7  vcs
ptybf               ptys5  ptyyb  tty38       ttye6  ttyu8  vcs1
ptyc0               ptys6  ptyyc  tty39       ttye7  ttyu9  vcs2
ptyc1               ptys7  ptyyd  tty4        ttye8  ttyua  vcs3
ptyc2               ptys8  ptyye  tty40       ttye9  ttyub  vcs4
ptyc3               ptys9  ptyyf  tty41       ttyea  ttyuc  vcs5
ptyc4               ptysa  ptyz0  tty42       ttyeb  ttyud  vcs6
ptyc5               ptysb  ptyz1  tty43       ttyec  ttyue  vcs7
ptyc6               ptysc  ptyz2  tty44       ttyed  ttyuf  vcs8
ptyc7               ptysd  ptyz3  tty45       ttyee  ttyv0  vcsa
ptyc8               ptyse  ptyz4  tty46       ttyef  ttyv1  vcsa1
ptyc9               ptysf  ptyz5  tty47       ttyp0  ttyv2  vcsa2
ptyca               ptyt0  ptyz6  tty48       ttyp1  ttyv3  vcsa3
ptycb               ptyt1  ptyz7  tty49       ttyp2  ttyv4  vcsa4
ptycc               ptyt2  ptyz8  tty5        ttyp3  ttyv5  vcsa5
ptycd               ptyt3  ptyz9  tty50       ttyp4  ttyv6  vcsa6
ptyce               ptyt4  ptyza  tty51       ttyp5  ttyv7  vcsa7
ptycf               ptyt5  ptyzb  tty52       ttyp6  ttyv8  vcsa8
ptyd0               ptyt6  ptyzc  tty53       ttyp7  ttyv9  xconsole
ptyd1               ptyt7  ptyzd  tty54       ttyp8  ttyva  zero
```


thank you again,

Jesse

---

### Post by JesseDaniel on 2008-12-22
(apologies for the poor formatting)

---

### Post by nlz on 2008-12-22
aha there are quite some disk drives present, one of them could be your camera. (Although it would be good if someone would advise who has experience with camera's on ubuntu.)

The disk drives are:
sda1
sda2
sdb
sdc
sdd
sde

but the problem is, they are there before AND after, so not really a change...

---

### Post by JesseDaniel on 2008-12-22
the strange thing is I have an external hdd that I can connect to the very same firewire port and it's recognized by ubuntustudio immediately: I can open and explore the drive contents, transfer files to the desktop etc. The port works fine... I just have no idea to get the camera recognized, and thus record and extract what's on the minidv tapes...

---

### Post by kayosiii on 2008-12-23
firewire should be recognized as at least /dev/raw1394 but there should also be a /dev/dv1394/0 device which is more camera specific.

Most common problem is that for some reason these interfaces can be off limits to users by default. the /dev/dv1394/0 belongs to the group video by default so if the user is a member of that group then you should have access. /dev/raw1394 by default belongs to the group disk which the user will definately not be a member of. There is a tool in the ubuntu-studio settings (control panel?) which will fix this for you.

Things you can try.
1) try to capture with kino - AFAIK it tends to be the best at dealing with capture hardware. if that fails try launching kino as super user - in terminal type "sudo kino" 
2) Install the ubuntu studio control panel and use it to give yourself raw firewire access.
3) type 
lspci 
into a terminal and post the results - this will confirm that the firewire device is being detected properly and give us some idea of what you are dealing with
4) locate and install a program called gscanbus - it will show you graphically what is attached to the firewire bus.

---

### Post by JesseDaniel on 2008-12-23
Thank you for your suggestions, Kayosiii:

I have tried each of the solutions you recommend, to no avail.

Ubuntu studio controls does indeed enable raw1394, I seem to have gscanbus installed but cannot find it on the system, and running sudo kino led to "capture failed". 

Here is the readout from typing 'lspci' in the terminal:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
04:08.0 Multimedia controller: ATI Technologies Inc Theater 550 PRO PCI [ATI TV Wonder 550]
04:09.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)


the one firewire that shows up is the external hdd, but I cannot see the camcorder anywhere.

Many thanks, 

Jesse

---

### Post by kayosiii on 2008-12-23
That is perfectly odd - the firewire controller is good ie detected....
and if your firewire hdd is picked up then all the base firewire stuff is working - 

Ok some simple stuff -- Are you trying to daisychain the camera through the hdd? if so can you try a direct connection. Also it would be a good idea to check that the cable you are using for the camera works...

here is some more terminal stuff you can try....
after you plug the camera in type in 
dmesg into a terminal - and have a look at the very last things printed also we should verify that both devices are being created and have usuable permissions

ls -l /dev/raw1394

and 
ls -l /dev/dv1394/0

also if gscanbus is installed - just type gscanbus into a terminal to run it or sudo gscanbus to see if that doesn't show up the camera.

---

### Post by JesseDaniel on 2008-12-23
Thank you for your reply, kayosiii:

I have 2 firewire ports, 1 at the front side of the tower and one in the back. While both ports recognize the hdd, neither recognizes the camera directly plugged into it.

after plugging the hdd into the back and the camcorder into the front side, typing 'dmesg' produces the following:
```

[    0.812056] system 00:01: ioport range 0x2000-0x207f has been reserved
[    0.812059] system 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.812062] system 00:01: iomem range 0x78000000-0x7fffffff could not be reserved
[    0.812070] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.812073] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.812075] system 00:02: ioport range 0x290-0x297 has been reserved
[    0.812087] system 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.812095] system 00:0b: iomem range 0xf0000-0xf3fff could not be reserved
[    0.812097] system 00:0b: iomem range 0xf4000-0xf7fff could not be reserved
[    0.812100] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[    0.812103] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[    0.812107] system 00:0b: iomem range 0xfefff000-0xfefff0ff could not be reserved
[    0.812110] system 00:0b: iomem range 0x77ef0000-0x77efffff could not be reserved
[    0.812113] system 00:0b: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.812116] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.812119] system 00:0b: iomem range 0x100000-0x77eeffff could not be reserved
[    0.812122] system 00:0b: iomem range 0x77f00000-0x7fefffff could not be reserved
[    0.812125] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.812128] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.812131] system 00:0b: iomem range 0xfefff000-0xfeffffff could not be reserved
[    0.812134] system 00:0b: iomem range 0xfff80000-0xfff80fff could not be reserved
[    0.812137] system 00:0b: iomem range 0xfff90000-0xfffbffff could not be reserved
[    0.812140] system 00:0b: iomem range 0xfffed000-0xfffeffff could not be reserved
[    0.817677] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.817680] pci 0000:00:02.0:   IO window: 0xa000-0xafff
[    0.817683] pci 0000:00:02.0:   MEM window: 0xfd800000-0xfd8fffff
[    0.817686] pci 0000:00:02.0:   PREFETCH window: 0x000000fd700000-0x000000fd7fffff
[    0.817690] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02
[    0.817693] pci 0000:00:03.0:   IO window: 0x8000-0x8fff
[    0.817695] pci 0000:00:03.0:   MEM window: 0xfde00000-0xfdefffff
[    0.817698] pci 0000:00:03.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.817702] pci 0000:00:04.0: PCI bridge, secondary bus 0000:03
[    0.817704] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
[    0.817707] pci 0000:00:04.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.817710] pci 0000:00:04.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
[    0.817714] pci 0000:00:10.0: PCI bridge, secondary bus 0000:04
[    0.817717] pci 0000:00:10.0:   IO window: 0x9000-0x9fff
[    0.817721] pci 0000:00:10.0:   MEM window: 0xfda00000-0xfdbfffff
[    0.817724] pci 0000:00:10.0:   PREFETCH window: 0x000000f8000000-0x000000f9ffffff
[    0.817735] pci 0000:00:02.0: setting latency timer to 64
[    0.817740] pci 0000:00:03.0: setting latency timer to 64
[    0.817745] pci 0000:00:04.0: setting latency timer to 64
[    0.817749] pci 0000:00:10.0: setting latency timer to 64
[    0.817752] bus: 00 index 0 io port: [0, ffff]
[    0.817755] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.817757] bus: 01 index 0 io port: [a000, afff]
[    0.817759] bus: 01 index 1 mmio: [fd800000, fd8fffff]
[    0.817761] bus: 01 index 2 mmio: [fd700000, fd7fffff]
[    0.817762] bus: 01 index 3 mmio: [0, 0]
[    0.817764] bus: 02 index 0 io port: [8000, 8fff]
[    0.817766] bus: 02 index 1 mmio: [fde00000, fdefffff]
[    0.817768] bus: 02 index 2 mmio: [fdd00000, fddfffff]
[    0.817770] bus: 02 index 3 mmio: [0, 0]
[    0.817772] bus: 03 index 0 io port: [b000, bfff]
[    0.817774] bus: 03 index 1 mmio: [fdc00000, fdcfffff]
[    0.817776] bus: 03 index 2 mmio: [fd900000, fd9fffff]
[    0.817778] bus: 03 index 3 mmio: [0, 0]
[    0.817780] bus: 04 index 0 io port: [9000, 9fff]
[    0.817781] bus: 04 index 1 mmio: [fda00000, fdbfffff]
[    0.817783] bus: 04 index 2 mmio: [f8000000, f9ffffff]
[    0.817785] bus: 04 index 3 io port: [0, ffff]
[    0.817787] bus: 04 index 4 mmio: [0, ffffffffffffffff]
[    0.817802] NET: Registered protocol family 2
[    0.856139] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.857137] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.859090] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.859598] TCP: Hash tables configured (established 262144 bind 65536)
[    0.859601] TCP reno registered
[    0.868110] NET: Registered protocol family 1
[    0.868234] checking if image is initramfs... it is
[    1.617050] Freeing initrd memory: 8813k freed
[    1.623397] audit: initializing netlink socket (disabled)
[    1.623411] type=2000 audit(1230052055.620:1): initialized
[    1.629327] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.632661] VFS: Disk quotas dquot_6.5.1
[    1.632764] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.632892] msgmni has been set to 3763
[    1.633040] io scheduler noop registered
[    1.633042] io scheduler anticipatory registered
[    1.633045] io scheduler deadline registered
[    1.633209] io scheduler cfq registered (default)
[    1.633225] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.633267] pci 0000:00:02.0: Enabling HT MSI Mapping
[    1.633278] pci 0000:00:03.0: Enabling HT MSI Mapping
[    1.633289] pci 0000:00:04.0: Enabling HT MSI Mapping
[    1.633299] pci 0000:00:05.0: Boot video device
[    1.633321] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.648055] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.648066] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    1.648076] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.648089] pci 0000:00:10.1: Enabling HT MSI Mapping
[    1.648252] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.648276] pcieport-driver 0000:00:02.0: found MSI capability
[    1.648299] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.648362] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.648451] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.648475] pcieport-driver 0000:00:03.0: found MSI capability
[    1.648494] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.648553] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.648643] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.648666] pcieport-driver 0000:00:04.0: found MSI capability
[    1.648685] pci_express 0000:00:04.0:pcie00: allocate port service
[    1.648745] pci_express 0000:00:04.0:pcie03: allocate port service
[    1.695561] hpet_resources: 0xfefff000 is busy
[    1.695641] Linux agpgart interface v0.103
[    1.695646] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.698448] brd: module loaded
[    1.698539] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.698770] PNP: No PS/2 controller found. Probing ports directly.
[    1.699199] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.699207] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.721376] mice: PS/2 mouse device common for all mice
[    1.721566] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.721603] rtc0: alarms up to one year, y3k, hpet irqs
[    1.721664] cpuidle: using governor ladder
[    1.721666] cpuidle: using governor menu
[    1.722098] TCP cubic registered
[    1.722378] registered taskstats version 1
[    1.722550]   Magic number: 4:633:138
[    1.722559] block ram3: hash matches
[    1.722710] rtc_cmos 00:05: setting system clock to 2008-12-23 17:07:36 UTC (1230052056)
[    1.722714] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.722716] EDD information not available.
[    1.722756] Freeing unused kernel memory: 536k freed
[    1.723020] Write protecting the kernel read-only data: 4348k
[    1.932058] fuse init (API version 7.9)
[    2.008101] fan PNP0C0B:00: registered as cooling_device0
[    2.008110] ACPI: Fan [FAN] (on)
[    2.044406] processor ACPI0007:00: registered as cooling_device1
[    2.044487] processor ACPI0007:01: registered as cooling_device2
[    2.047578] thermal LNXTHERM:01: registered as thermal_zone0
[    2.048123] ACPI: Thermal Zone [THRM] (40 C)
[    2.684447] usbcore: registered new interface driver usbfs
[    2.684541] usbcore: registered new interface driver hub
[    2.684724] No dock devices found.
[    2.686783] usbcore: registered new device driver usb
[    2.686939] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    2.687557] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    2.687570] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    2.687575] forcedeth 0000:00:14.0: setting latency timer to 64
[    2.687610] nv_probe: set workaround bit for reversed mac addr
[    2.719484] SCSI subsystem initialized
[    2.721484] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.739867] libata version 3.00 loaded.
[    3.208708] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:18:f3:e2:74:4d
[    3.208713] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[    3.210960] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[    3.210974] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 22 (level, low) -> IRQ 22
[    3.210991] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    3.210994] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    3.211058] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    3.211090] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xfe02f000
[    3.267192] usb usb1: configuration #1 chosen from 1 choice
[    3.267229] hub 1-0:1.0: USB hub found
[    3.267242] hub 1-0:1.0: 8 ports detected
[    3.474505] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    3.474519] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    3.474534] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    3.474537] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    3.474583] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    3.474619] ehci_hcd 0000:00:0b.1: debug port 1
[    3.474624] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    3.474653] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xfe02e000
[    3.648040] usb 1-1: new low speed USB device using ohci_hcd and address 2
[    3.661019] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.661677] usb usb2: configuration #1 chosen from 1 choice
[    3.662154] hub 2-0:1.0: USB hub found
[    3.662165] hub 2-0:1.0: 8 ports detected
[    3.716029] hub 1-0:1.0: unable to enumerate USB device on port 1
[    3.869281] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    3.869490] sata_nv 0000:00:0e.0: version 3.5
[    3.870069] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[    3.870082] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
[    3.870085] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    3.870116] sata_nv 0000:00:0e.0: setting latency timer to 64
[    3.870289] scsi0 : sata_nv
[    3.871484] scsi1 : sata_nv
[    3.871745] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 20
[    3.871748] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 20
[    4.344047] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.388024] usb 1-1: new low speed USB device using ohci_hcd and address 3
[    4.391758] ata1.00: ATA-7: ST3250620AS, 3.AAE, max UDMA/133
[    4.391761] ata1.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    4.458396] ata1.00: configured for UDMA/133
[    4.602768] usb 1-1: configuration #1 chosen from 1 choice
[    4.908023] usb 1-3: new low speed USB device using ohci_hcd and address 4
[    4.932045] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.978262] ata2.00: ATA-7: ST3250620AS, 3.AAE, max UDMA/133
[    4.978265] ata2.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    5.044902] ata2.00: configured for UDMA/133
[    5.044957] isa bounce pool size: 16 pages
[    5.045047] scsi 0:0:0:0: Direct-Access     ATA      ST3250620AS      3.AA PQ: 0 ANSI: 5
[    5.045209] scsi 1:0:0:0: Direct-Access     ATA      ST3250620AS      3.AA PQ: 0 ANSI: 5
[    5.048758] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[    5.048763] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
[    5.048767] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    5.048810] sata_nv 0000:00:0f.0: setting latency timer to 64
[    5.048977] scsi2 : sata_nv
[    5.050135] scsi3 : sata_nv
[    5.050407] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 23
[    5.050411] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 23
[    5.120179] usb 1-3: configuration #1 chosen from 1 choice
[    5.379504] ata3: SATA link down (SStatus 0 SControl 300)
[    5.706500] ata4: SATA link down (SStatus 0 SControl 300)
[    5.707334] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    5.707348] ohci1394 0000:04:05.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    5.757131] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fdbff000-fdbff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.766558] pata_amd 0000:00:0d.0: version 0.3.10
[    5.766608] pata_amd 0000:00:0d.0: setting latency timer to 64
[    5.769517] scsi4 : pata_amd
[    5.769635] scsi5 : pata_amd
[    5.770613] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[    5.770616] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[    5.807022] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.807082] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    5.816467] usbcore: registered new interface driver hiddev
[    5.822464] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb1/1-1/1-1:1.0/input/input1
[    5.828845] Driver 'sd' needs updating - please use bus_type methods
[    5.829025] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    5.829054] sd 0:0:0:0: [sda] Write Protect is off
[    5.829057] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.829105] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.829210] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    5.829235] sd 0:0:0:0: [sda] Write Protect is off
[    5.829238] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.829285] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.829290]  sda:<6>input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:0b.0-1
[    5.847602]  sda1 sda2 <<6>input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb1/1-1/1-1:1.1/input/input2
[    5.865870]  sda5 >
[    5.866051] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.869775] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[    5.869827] sd 1:0:0:0: [sdb] Write Protect is off
[    5.869830] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.869871] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.869963] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[    5.869984] sd 1:0:0:0: [sdb] Write Protect is off
[    5.869987] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.870023] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.870027]  sdb:<6>input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-1
[    5.881195] usbcore: registered new interface driver usbhid
[    5.881198] usbhid: v2.6:USB HID core driver
[    5.884245]  sdb1
[    5.884401] sd 1:0:0:0: [sdb] Attached SCSI disk
[    5.932411] ata5.00: ATAPI: HL-DT-STDVD-RAM GSA-H22N, 1.00, max UDMA/66
[    5.932425] ata5: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
[    5.948343] ata5.00: configured for UDMA/66
[    6.119400] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H22N 1.00 PQ: 0 ANSI: 5
[    6.119605] scsi 4:0:0:0: Attached scsi generic sg2 type 5
[    6.143625] Driver 'sr' needs updating - please use bus_type methods
[    6.148814] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.148819] Uniform CD-ROM driver Revision: 3.20
[    6.148923] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    6.387782] PM: Starting manual resume from disk
[    6.387786] PM: Resume from partition 8:5
[    6.387788] PM: Checking hibernation image.
[    6.387933] PM: Resume from disk failed.
[    6.426780] kjournald starting.  Commit interval 5 seconds
[    6.426793] EXT3-fs: mounted filesystem with ordered data mode.
[    7.033206] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d8000100e0d1]
[   11.239914] udevd version 124 started
[   11.558871] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   11.580062] ACPI: Power Button (FF) [PWRF]
[   11.580206] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   11.612035] ACPI: Power Button (CM) [PWRB]
[   11.697793] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.736881] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.831924] parport_pc 00:08: reported by Plug and Play ACPI
[   11.831954] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   12.805560] nvidia: module license 'NVIDIA' taints kernel.
[   13.088746] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[   13.088761] nvidia 0000:00:05.0: PCI INT A -> Link[APC7] -> GSI 16 (level, low) -> IRQ 16
[   13.088767] nvidia 0000:00:05.0: setting latency timer to 64
[   13.091615] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct  1 14:43:46 PDT 2008
[   13.095277] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   13.095309] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   13.124668] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   13.135626] wlan: 0.9.4
[   13.141643] ath_pci: 0.9.4
[   13.142308] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   13.142321] ath_pci 0000:04:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   13.832087] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   13.866846] ath_rate_sample: 1.2 (0.9.4)
[   13.867489] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   13.867495] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   13.867506] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   13.867513] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   13.867518] wifi0: mac 7.9 phy 4.5 radio 5.6
[   13.867522] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   13.867524] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   13.867527] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   13.867528] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   13.867531] wifi0: Use hw queue 8 for CAB traffic
[   13.867533] wifi0: Use hw queue 9 for beacons
[   13.872204] wifi0: Atheros 5212: mem=0xfdbe0000, irq=17
[   13.893457] input: Wacom Graphire4 4x5 as /devices/pci0000:00/0000:00:0b.0/usb1/1-3/1-3:1.0/input/input6
[   14.015123] usbcore: registered new interface driver wacom
[   14.015129] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
[   14.505196] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   14.505203] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   14.505225] HDA Intel 0000:00:10.1: setting latency timer to 64
[   15.198555] loop: module loaded
[   15.236438] lp0: using parport0 (interrupt-driven).
[   15.290985] ieee1394: raw1394: /dev/raw1394 device initialized
[   15.476623] Adding 5646808k swap on /dev/sda5.  Priority:-1 extents:1 across:5646808k
[   16.045553] EXT3 FS on sda1, internal journal
[   17.142139] type=1505 audit(1230052072.069:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4357
[   17.321224] type=1505 audit(1230052072.249:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4362
[   17.321450] type=1505 audit(1230052072.249:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4362
[   17.508126] ip_tables: (C) 2000-2006 Netfilter Core Team
[   18.781327] NET: Registered protocol family 17
[   20.865712] ACPI: WMI: Mapper loaded
[   21.250414] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (2 cpu cores) (version 2.20.00)
[   21.251194] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xe
[   21.251198] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x10
[   21.251200] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   22.238971] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   22.440938] ppdev: user-space parallel port driver
[   24.346236] Bluetooth: Core ver 2.13
[   24.347286] NET: Registered protocol family 31
[   24.347297] Bluetooth: HCI device and connection manager initialized
[   24.347301] Bluetooth: HCI socket layer initialized
[   24.364745] Bluetooth: L2CAP ver 2.11
[   24.364756] Bluetooth: L2CAP socket layer initialized
[   24.387217] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.387227] Bluetooth: BNEP filters: protocol multicast
[   24.404050] Bluetooth: RFCOMM socket layer initialized
[   24.405066] Bluetooth: RFCOMM TTY layer initialized
[   24.405072] Bluetooth: RFCOMM ver 1.10
[   24.415316] Bridge firewalling registered
[   24.415533] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   24.442507] Bluetooth: SCO (Voice Link) ver 0.6
[   24.442514] Bluetooth: SCO socket layer initialized
[   26.000031] Clocksource tsc unstable (delta = -249429510 ns)
[   29.947792] NET: Registered protocol family 10
[   29.950058] lo: Disabled Privacy Extensions
[   40.440025] eth0: no IPv6 routers present
[  107.838424] Too big adjustment 32
[  107.869800] Too big adjustment 32
[  163.968388] ppdev0: registered pardevice
[  164.016359] ppdev0: unregistered pardevice
[  164.062265] ppdev0: registered pardevice
[  164.108425] ppdev0: unregistered pardevice
[  164.275994] ppdev0: registered pardevice
[  164.324060] ppdev0: unregistered pardevice
[ 2332.632137] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[ 2333.584113] ieee1394: Error parsing configrom for node 0-00:1023
[ 2333.584242] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[ 2339.426978] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0050770e00071002]
[ 2339.440279] scsi6 : SBP-2 IEEE-1394
[ 2339.441744] ieee1394: sbp2: Workarounds for node 0-00:1023: 0x20 (firmware_revision 0x012804, vendor_id 0x005077, model_id 0x000001)
[ 2340.445797] ieee1394: sbp2: Logged into SBP-2 device
[ 2340.446089] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2340.447126] scsi 6:0:0:0: Direct-Access-RBC ST325062 0A                    PQ: 0 ANSI: 4
[ 2340.448402] sd 6:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[ 2340.448868] sd 6:0:0:0: [sdc] Write Protect is off
[ 2340.448877] sd 6:0:0:0: [sdc] Mode Sense: 11 00 00 00
[ 2340.449518] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2340.451058] sd 6:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[ 2340.451416] sd 6:0:0:0: [sdc] Write Protect is off
[ 2340.451424] sd 6:0:0:0: [sdc] Mode Sense: 11 00 00 00
[ 2340.452773] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2340.453442]  sdc: sdc1
[ 2340.476809] sd 6:0:0:0: [sdc] Attached SCSI disk
[ 2340.477068] sd 6:0:0:0: Attached scsi generic sg3 type 14
[ 3617.152044] ieee1394: Error parsing configrom for node 0-01:1023
[ 3617.832049] ieee1394: Error parsing configrom for node 0-02:1023
[ 3618.112851] ieee1394: sbp2: Reconnected to SBP-2 device
[ 3618.113469] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 3620.096264] ieee1394: Node added: ID:BUS[0-01:1023]  GUID[0000850001ac8832]
[ 3620.097214] ieee1394: Node changed: 0-01:1023 -> 0-02:1023
[ 3620.098021] ieee1394: sbp2: Reconnected to SBP-2 device
[ 3620.098815] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 3620.209368] NOTE: The dv1394 driver is unsupported and may be removed in a future Linux release. Use raw1394 instead.
[ 3665.236504] ieee1394: Node changed: 0-02:1023 -> 0-01:1023
[ 3665.238504] ieee1394: sbp2: Reconnected to SBP-2 device
[ 3665.238827] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 3665.238848] ieee1394: Node suspended: ID:BUS[0-01:1023]  GUID[0000850001ac8832]
[ 3682.368148] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[ 3682.369828] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0050770e00071002]
[ 3682.384895] sd 6:0:0:0: [sdc] Synchronizing SCSI cache
[ 3682.386600] sd 6:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3682.386614] sd 6:0:0:0: [sdc] Stopping disk
[ 3682.390616] sd 6:0:0:0: [sdc] START_STOP FAILED
[ 3682.390625] sd 6:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[23341.892180] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[23342.172462] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[0050770e00071002]
[23342.174441] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[23342.176175] scsi7 : SBP-2 IEEE-1394
[23342.179831] ieee1394: sbp2: Workarounds for node 0-00:1023: 0x20 (firmware_revision 0x012804, vendor_id 0x005077, model_id 0x000001)
[23343.185833] ieee1394: sbp2: Logged into SBP-2 device
[23343.187441] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[23343.189962] scsi 7:0:0:0: Direct-Access-RBC ST325062 0A                    PQ: 0 ANSI: 4
[23343.196193] sd 7:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[23343.198286] sd 7:0:0:0: [sdc] Write Protect is off
[23343.198296] sd 7:0:0:0: [sdc] Mode Sense: 11 00 00 00
[23343.201291] sd 7:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[23343.203974] sd 7:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[23343.206202] sd 7:0:0:0: [sdc] Write Protect is off
[23343.206214] sd 7:0:0:0: [sdc] Mode Sense: 11 00 00 00
[23343.209192] sd 7:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[23343.211339]  sdc: sdc1
[23343.233992] sd 7:0:0:0: [sdc] Attached SCSI disk
[23343.236276] sd 7:0:0:0: Attached scsi generic sg3 type 14
[36563.560035] ieee1394: Error parsing configrom for node 0-01:1023
[36564.240032] ieee1394: Error parsing configrom for node 0-02:1023
[36564.520876] ieee1394: sbp2: Reconnected to SBP-2 device
[36564.521361] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[36566.493684] ieee1394: Node resumed: ID:BUS[0-01:1023]  GUID[0000850001ac8832]
[36566.494409] ieee1394: Node changed: 0-01:1023 -> 0-02:1023
[36566.495038] ieee1394: sbp2: Reconnected to SBP-2 device
[36566.495317] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[36592.520622] ieee1394: Node changed: 0-02:1023 -> 0-01:1023
[36592.522710] ieee1394: sbp2: Reconnected to SBP-2 device
[36592.523100] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[36592.523119] ieee1394: Node suspended: ID:BUS[0-01:1023]  GUID[0000850001ac8832]
[36662.472031] ieee1394: Error parsing configrom for node 0-01:1023
[36663.152040] ieee1394: Error parsing configrom for node 0-02:1023
[36663.432811] ieee1394: sbp2: Reconnected to SBP-2 device
[36663.433239] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[36665.405792] ieee1394: Node resumed: ID:BUS[0-01:1023]  GUID[0000850001ac8832]
[36665.406373] ieee1394: Node changed: 0-01:1023 -> 0-02:1023
[36665.407088] ieee1394: sbp2: Reconnected to SBP-2 device
[36665.407456] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]

```

ls -l /dev/raw1394 produces: 
crw-rw---- 1 root disk 171, 0 2008-12-23 12:07 /dev/raw1394

while ls -l /dev/dv1394/0 produces:

crw-rw---- 1 root video 171, 32 2008-12-23 13:07 /dev/dv1394/0

typing 'gscanbus' produces:

couldn't get handle: Permission denied
This probably means that you don't have raw1394 support in the kernel or that
you haven't loaded the raw1394 module.

while typing 'sudo gscanbus' produces:

a windows with a graphical icon of the linux mascot (with ochi1394 written beneath), connected by a blue line to a cd icon (with S400 prolific combo device written beneath), and another blue line connecting the linux icon to a boxed eye icon (with S100 Canon written beneath). 

the last could indeed be the camera?

---

### Post by kayosiii on 2008-12-24
ok that tells me that the camera is being seen but you do not have permission to use it - which means the ubuntustudio control thing failed for raw1394. I can see that /dev/raw1394 is owned by the group disk and /dev/dv1394/0 by the group video.

I am guessing that you belong to neither group type in the command 
'groups' to confirm this. Probably the one you want to be accessing is dv1394 which means you need to be in the video group.

I am not overly familiar (Kubuntu user here) but I think there should be something that lets you do that in the user settings panel in Ubuntu. Otherwise you can try the following on the command line

sudo usermod -a -G video [your user name]

you will then need to log out and back in again (or restart). hope that helps

---

### Post by RedRat on 2008-12-24
I am having the exact same problem. I have a Canon HD30 High Def camera that connects its tape drive via a 1394 cable. Running kino I get the same message and messages about loading the 1394 libraries. I am much interested in the resolution to this problem. I will also try the command
"sudo kino" and 
gksudo kino
and see if this makes any difference. I do have under the \dev\dev1394\0
so it appears that the 1394 is attaching.

---

### Post by RedRat on 2008-12-24
In my case kino, when run under "gksudo kino" correctly identifies my camera. I am outputting as HD1080i output. Can kino handle this kind of HD output??? Perhaps not?

---

### Post by kragh on 2008-12-30
acpi       ptyc3  ptyr1  ptyvf  ram7        tty55  ttye1  ttysb  ttyx9
adsp       ptyc4  ptyr2  ptyw0  ram8        tty56  ttye2  ttysc  ttyxa
agpgart    ptyc5  ptyr3  ptyw1  ram9        tty57  ttye3  ttysd  ttyxb
audio      ptyc6  ptyr4  ptyw2  random      tty58  ttye4  ttyse  ttyxc
audio1     ptyc7  ptyr5  ptyw3  rtc         tty59  ttye5  ttysf  ttyxd
bus        ptyc8  ptyr6  ptyw4  scd0        tty6   ttye6  ttyt0  ttyxe
cdrom      ptyc9  ptyr7  ptyw5  scd1        tty60  ttye7  ttyt1  ttyxf
cdrw       ptyca  ptyr8  ptyw6  sda         tty61  ttye8  ttyt2  ttyy0
console    ptycb  ptyr9  ptyw7  sda1        tty62  ttye9  ttyt3  ttyy1
core       ptycc  ptyra  ptyw8  sda2        tty63  ttyea  ttyt4  ttyy2
disk       ptycd  ptyrb  ptyw9  sda3        tty7   ttyeb  ttyt5  ttyy3
dri        ptyce  ptyrc  ptywa  sda5        tty8   ttyec  ttyt6  ttyy4
dsp        ptycf  ptyrd  ptywb  sequencer   tty9   ttyed  ttyt7  ttyy5
dsp1       ptyd0  ptyre  ptywc  sequencer2  ttya0  ttyee  ttyt8  ttyy6
dvd        ptyd1  ptyrf  ptywd  sg0         ttya1  ttyef  ttyt9  ttyy7
dvdrw      ptyd2  ptys0  ptywe  sg1         ttya2  ttyp0  ttyta  ttyy8
fd         ptyd3  ptys1  ptywf  sg2         ttya3  ttyp1  ttytb  ttyy9
fd0        ptyd4  ptys2  ptyx0  shm         ttya4  ttyp2  ttytc  ttyya
full       ptyd5  ptys3  ptyx1  snapshot    ttya5  ttyp3  ttytd  ttyyb
fuse       ptyd6  ptys4  ptyx2  snd         ttya6  ttyp4  ttyte  ttyyc
hpet       ptyd7  ptys5  ptyx3  sndstat     ttya7  ttyp5  ttytf  ttyyd
initctl    ptyd8  ptys6  ptyx4  sr0         ttya8  ttyp6  ttyu0  ttyye
input      ptyd9  ptys7  ptyx5  sr1         ttya9  ttyp7  ttyu1  ttyyf
kmem       ptyda  ptys8  ptyx6  stderr      ttyaa  ttyp8  ttyu2  ttyz0
kmsg       ptydb  ptys9  ptyx7  stdin       ttyab  ttyp9  ttyu3  ttyz1
log        ptydc  ptysa  ptyx8  stdout      ttyac  ttypa  ttyu4  ttyz2
loop0      ptydd  ptysb  ptyx9  tty         ttyad  ttypb  ttyu5  ttyz3
lp0        ptyde  ptysc  ptyxa  tty0        ttyae  ttypc  ttyu6  ttyz4
MAKEDEV    ptydf  ptysd  ptyxb  tty1        ttyaf  ttypd  ttyu7  ttyz5
mem        ptye0  ptyse  ptyxc  tty10       ttyb0  ttype  ttyu8  ttyz6
mixer      ptye1  ptysf  ptyxd  tty11       ttyb1  ttypf  ttyu9  ttyz7
mixer1     ptye2  ptyt0  ptyxe  tty12       ttyb2  ttyq0  ttyua  ttyz8
net        ptye3  ptyt1  ptyxf  tty13       ttyb3  ttyq1  ttyub  ttyz9
null       ptye4  ptyt2  ptyy0  tty14       ttyb4  ttyq2  ttyuc  ttyza
nvidia0    ptye5  ptyt3  ptyy1  tty15       ttyb5  ttyq3  ttyud  ttyzb
nvidiactl  ptye6  ptyt4  ptyy2  tty16       ttyb6  ttyq4  ttyue  ttyzc
oldmem     ptye7  ptyt5  ptyy3  tty17       ttyb7  ttyq5  ttyuf  ttyzd
parport0   ptye8  ptyt6  ptyy4  tty18       ttyb8  ttyq6  ttyv0  ttyze
port       ptye9  ptyt7  ptyy5  tty19       ttyb9  ttyq7  ttyv1  ttyzf
ppp        ptyea  ptyt8  ptyy6  tty2        ttyba  ttyq8  ttyv2  urandom
psaux      ptyeb  ptyt9  ptyy7  tty20       ttybb  ttyq9  ttyv3  usbdev1.1_ep00
ptmx       ptyec  ptyta  ptyy8  tty21       ttybc  ttyqa  ttyv4  usbdev1.1_ep81
pts        ptyed  ptytb  ptyy9  tty22       ttybd  ttyqb  ttyv5  usbdev1.2_ep00
ptya0      ptyee  ptytc  ptyya  tty23       ttybe  ttyqc  ttyv6  usbdev1.2_ep81
ptya1      ptyef  ptytd  ptyyb  tty24       ttybf  ttyqd  ttyv7  usbdev1.3_ep00
ptya2      ptyp0  ptyte  ptyyc  tty25       ttyc0  ttyqe  ttyv8  usbdev1.3_ep81
ptya3      ptyp1  ptytf  ptyyd  tty26       ttyc1  ttyqf  ttyv9  usbdev2.1_ep00
ptya4      ptyp2  ptyu0  ptyye  tty27       ttyc2  ttyr0  ttyva  usbdev2.1_ep81
ptya5      ptyp3  ptyu1  ptyyf  tty28       ttyc3  ttyr1  ttyvb  usbdev3.1_ep00
ptya6      ptyp4  ptyu2  ptyz0  tty29       ttyc4  ttyr2  ttyvc  usbdev3.1_ep81
ptya7      ptyp5  ptyu3  ptyz1  tty3        ttyc5  ttyr3  ttyvd  usbdev4.1_ep00
ptya8      ptyp6  ptyu4  ptyz2  tty30       ttyc6  ttyr4  ttyve  usbdev4.1_ep81
ptya9      ptyp7  ptyu5  ptyz3  tty31       ttyc7  ttyr5  ttyvf  usbdev4.6_ep00
ptyaa      ptyp8  ptyu6  ptyz4  tty32       ttyc8  ttyr6  ttyw0  usbdev4.6_ep81
ptyab      ptyp9  ptyu7  ptyz5  tty33       ttyc9  ttyr7  ttyw1  usbdev4.6_ep82
ptyac      ptypa  ptyu8  ptyz6  tty34       ttyca  ttyr8  ttyw2  usbdev5.1_ep00
ptyad      ptypb  ptyu9  ptyz7  tty35       ttycb  ttyr9  ttyw3  usbdev5.1_ep81
ptyae      ptypc  ptyua  ptyz8  tty36       ttycc  ttyra  ttyw4  vcs
ptyaf      ptypd  ptyub  ptyz9  tty37       ttycd  ttyrb  ttyw5  vcs1
ptyb0      ptype  ptyuc  ptyza  tty38       ttyce  ttyrc  ttyw6  vcs2
ptyb1      ptypf  ptyud  ptyzb  tty39       ttycf  ttyrd  ttyw7  vcs3
ptyb2      ptyq0  ptyue  ptyzc  tty4        ttyd0  ttyre  ttyw8  vcs4
ptyb3      ptyq1  ptyuf  ptyzd  tty40       ttyd1  ttyrf  ttyw9  vcs5
ptyb4      ptyq2  ptyv0  ptyze  tty41       ttyd2  ttys0  ttywa  vcs6
ptyb5      ptyq3  ptyv1  ptyzf  tty42       ttyd3  ttyS0  ttywb  vcs7
ptyb6      ptyq4  ptyv2  ram0   tty43       ttyd4  ttys1  ttywc  vcs8
ptyb7      ptyq5  ptyv3  ram1   tty44       ttyd5  ttyS1  ttywd  vcsa
ptyb8      ptyq6  ptyv4  ram10  tty45       ttyd6  ttys2  ttywe  vcsa1
ptyb9      ptyq7  ptyv5  ram11  tty46       ttyd7  ttyS2  ttywf  vcsa2
ptyba      ptyq8  ptyv6  ram12  tty47       ttyd8  ttys3  ttyx0  vcsa3
ptybb      ptyq9  ptyv7  ram13  tty48       ttyd9  ttyS3  ttyx1  vcsa4
ptybc      ptyqa  ptyv8  ram14  tty49       ttyda  ttys4  ttyx2  vcsa5
ptybd      ptyqb  ptyv9  ram15  tty5        ttydb  ttys5  ttyx3  vcsa6
ptybe      ptyqc  ptyva  ram2   tty50       ttydc  ttys6  ttyx4  vcsa7
ptybf      ptyqd  ptyvb  ram3   tty51       ttydd  ttys7  ttyx5  vcsa8
ptyc0      ptyqe  ptyvc  ram4   tty52       ttyde  ttys8  ttyx6  watchdog
ptyc1      ptyqf  ptyvd  ram5   tty53       ttydf  ttys9  ttyx7  xconsole
ptyc2      ptyr0  ptyve  ram6   tty54       ttye0  ttysa  ttyx8  zero
This is what I get.I have a sony handycam hsc-40.

---

