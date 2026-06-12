---
title: "Diagnose Server &amp; Desktop differences"
date: 2010-06-26
forum: Server Platforms
---

### Post by MartinHansell on 2010-06-26
Hi,

I am struggling to get my wireless usb working on a fresh installation of Ubuntu Server 10.04, but it works just fine on a fresh install of Ubuntu Desktop 10.04.  So I am trying to work out what's causing the discrepancy.  I know the Server version is a "minimal install" of Ubuntu, so something must be missing that affects its overall abilities.

I am planning to compare the file system of a totally fresh Desktop version with a Server version - and would appreciate as much additional brain-power as possible to assist in the plan/execution of what I should be comparing.  I hope this will throw up a solution as to what is NOT installed/configured on the Server version that prevents my wireless from working.  [It will teach me a lot as well :-)]

COMPARISON PLAN
[LIST=1]
[*]All programs installed on both file systems (looking for differences)
[*]Program differences which affect network setup and related hardware (I'm not sure of what this list should have on it)
[*]Related configuration files which might affect connectivity (same here - not sure what configures what at this stage)
    * Do **$lsmod** to look for installed wireless drivers
[*]Miscellaneous tests
   *  Disable security on wireless router to see if security config is the cause
[*]I'm not sure if the kernel build will be different and if so how to establish this... but somehow wonder if this affects the outcome
[/LIST]

If anyone is willing to assist in filling out the gaps in this plan I would really appreciate it.  Or maybe there is a better way?

Many thanks...

---

### Post by tgalati4 on 2010-06-26
Post lsmod from both systems.  It's possible that the server doesn't have wireless drivers.

---

### Post by MartinHansell on 2010-06-26
Thanks tgalait4,

**lsmod for desktop version below.**

I will put that in the list, but I can't query the server yet coz its currently not installed, although I have posted below an lsmod I did before reinstalling the desktop.  I am currently operating off the desktop install, and when I have queried that thoroughly I will reinstall the server to do the differences.

With lsmod, what difference am I looking for?  Which modules affect the working of a wireless usb?

Thanks again.

```

$lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_hda_codec_idt      51914  1 
arc4                    1153  2 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
rt73usb                22434  0 
snd_mixer_oss          13746  1 snd_pcm_oss
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
crc_itu_t               1371  1 rt73usb
softcursor              1189  1 bitblit
snd_seq_dummy           1338  0 
rt2500usb              18141  0 
vga16fb                11385  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
vgastate                8961  1 vga16fb
rt2x00usb               9703  2 rt73usb,rt2500usb
snd_rawmidi            19056  1 snd_seq_midi
rt2x00lib              27509  3 rt73usb,rt2500usb,rt2x00usb
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                  8708  0 
led_class               2864  1 rt2x00lib
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
hid_logitech            7388  0 
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              204922  2 rt2x00usb,rt2x00lib
nouveau               467048  2 
ff_memless              4093  1 hid_logitech
intel_agp              24177  0 
ttm                    49943  1 nouveau
soundcore               6620  1 snd
cfg80211              126485  2 rt2x00lib,mac80211
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
drm_kms_helper         29297  1 nouveau
usbhid                 36110  1 hid_logitech
hid                    67032  2 hid_logitech,usbhid
drm                   162471  4 nouveau,ttm,drm_kms_helper
agpgart                31724  3 intel_agp,ttm,drm
ppdev                   5259  0 
i2c_algo_bit            5028  1 nouveau
parport_pc             25962  1 
psmouse                63245  0 
serio_raw               3978  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
e100                   28211  0 
mii                     4381  1 e100

```

SERVER LSMOD for wireless drivers only
```

$lsmod | grep rt          
rt73usb                22434  0 
crc_itu_t               1371  1 rt73usb
rt2500usb              18141  0 
rt2x00usb               9703  2 rt73usb,rt2500usb
rt2x00lib              27541  3 rt73usb,rt2500usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              204922  2 rt2x00usb,rt2x00lib
cfg80211              126517  2 rt2x00lib,mac80211
parport_pc             26250  1 
parport                32635  3 ppdev,lp,parport_pc
agpgart                31788  3 ttm,drm,intel_agp

```

---

### Post by tgalati4 on 2010-06-26
I presume your USB card is by RealTek, hence anything with rt*usb would be a candidate.

I just checked my Hardy server, it has the rt* drivers:

tgalati4@washme:~$ locate rt73usb
/lib/modules/2.6.24-23-server/kernel/drivers/net/wireless/rt2x00/rt73usb.ko

After you boot your server, open a terminal and page through the dmesg file:

dmesg | more

Look for detection of the rt* card and note any errors.

Also realize that the desktop version has Network Manager.  This is the GUI which scans for wireless networks, handles passwords, and provides for automatic connection.  On the minimal server, you have to manually configure the wireless.  One missing switch and no connection.

---

### Post by MartinHansell on 2010-06-28
> **tgalati4 said:**
> I presume your USB card is by RealTek, hence anything with rt*usb would be a candidate.

It's a TP-Link usb  (TL-WN321G), and yes the drivers were definitely there when I did the installation

> After you boot your server, open a terminal and page through the dmesg file:

dmesg | more

Look for detection of the rt* card and note any errors.

There are what look to be some errors, but I'm not really sure how to resolve them despite several searches.  I have posted the dmesg output below with some other stuff I did before.

> Also realize that the desktop version has Network Manager. This is the GUI which scans for wireless networks, handles passwords, and provides for automatic connection. On the minimal server, you have to manually configure the wireless. One missing switch and no connection.

OK - I will search on how to manually configure wireless...  any clues before I get started?

And thanks a lot for your help...
Martin

```

$iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=10 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

$lsmod | grep rt          
rt73usb                22434  0 
crc_itu_t               1371  1 rt73usb
rt2500usb              18141  0 
rt2x00usb               9703  2 rt73usb,rt2500usb
rt2x00lib              27541  3 rt73usb,rt2500usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              204922  2 rt2x00usb,rt2x00lib
cfg80211              126517  2 rt2x00lib,mac80211
parport_pc             26250  1 
parport                32635  3 ppdev,lp,parport_pc
agpgart                31788  3 ttm,drm,intel_agp

lshw -C network
  *-network DISABLED
       description: Ethernet interface
       product: N10/ICH 7 Family LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 01
       serial: 00:13:20:da:3a:20
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:52000000-52000fff ioport:1000(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 94:0c:6d:e1:b5:72
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

$iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:4C:37:52
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Hansell"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006512c66bf7
                    Extra: Last beacon: 1024ms ago
                    IE: Unknown: 000748616E73656C6C
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 02 - Address: 00:1F:FB:06:DD:EA
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"HAMED"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000231cd6ed1
                    Extra: Last beacon: 576ms ago
                    IE: Unknown: 000548414D4544
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706545720010D10

$dmesg | grep -i rt73

[   22.800930] Registered led device: rt73usb-phy1::radio
[   22.800968] Registered led device: rt73usb-phy1::assoc
[   22.801009] Registered led device: rt73usb-phy1::quality
[   22.801497] usbcore: registered new interface driver rt73usb
[   23.790315] rt73usb 1-4:1.0: firmware: requesting rt73.bin

```

---

### Post by tgalati4 on 2010-06-29
You have to bring up the interface you want to use:

sudo ifconfig wlan0 up

Then you have to configure the wireless card:

man iwconfig

sudo iwconfig wlan0 essid "The Goat Farm" key AEFB1234FB

---

### Post by MartinHansell on 2010-07-03
> **tgalati4 said:**
> You have to bring up the interface you want to use:

sudo ifconfig wlan0 up

Then you have to configure the wireless card:

man iwconfig

sudo iwconfig wlan0 essid "The Goat Farm" key AEFB1234FB

Thanks!  I just reinstalled the server, and with a bit of messing I managed to get it to talk to my router.  I can ping the router successfully...  BUT I cannot successfully update the packages list (and hence the system).  Somehow the internet connection is not yet complete.

I set the IP address for this device to "reserved" on the router so there would be no connection problems (it was one of the tweaks that enabled me to get the thing working).  My router is providing the dhcp service as I haven't yet set that up on the server.

How do I now test my internet connection?

Thanks, once again!

---

