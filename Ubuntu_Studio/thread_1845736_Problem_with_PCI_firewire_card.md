---
title: "Problem with PCI firewire card"
date: 2011-09-17
forum: Ubuntu Studio
---

### Post by scubasean on 2011-09-17
I've dipped in  and out of using Ubuntu so pretty much a total novice. I bought a  Dynamode PCI-3PFW firewire card and installed it on my desktop which was  running under 9.04. I bought the card to download videos from a Samsung  SCD303 camcorder. The camcorder itself has an icon that pops up to say  if it is connected to a computer. This appears. But yet my card does not  appear on hardware listings when I use lspci.
 
I've assumed this to be a driver issue but can't find drivers and have  fully upgraded Ubuntu in a vain attempt to see if the drivers were on  newer versions. All to know avail. Can anybody help me please? When I  use lspci I get:

00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)


Thanks

Sean

---

### Post by jejeman on 2011-09-17
Here is youre card
> 00:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)Give us the output of command
```
lsmod
```
Wich version of ubuntu are you running now?

---

### Post by scubasean on 2011-09-22
Jejeman,

Thanks for the reply. I assumed that was to do with an onboard setting as it is a Via chipset/motherboard.

When I entered lsmod I got:

Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
nls_utf8               12493  1 
isofs                  39571  1 
arc4                   12473  2 
snd_hda_codec_via      56765  1 
binfmt_misc            13213  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
zd1211rw               52419  0 
nvidia               9766978  28 
mac80211              257001  1 zd1211rw
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
cfg80211              156212  2 zd1211rw,mac80211
ppdev                  12849  0 
snd_timer              28659  2 snd_pcm,snd_seq
psmouse                73312  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32111  1 
serio_raw              12990  0 
snd                    55295  13 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 32345  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_viapro             12969  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
floppy                 60032  0 
firewire_ohci          31504  0 
pata_via               13368  1 
sata_via               13464  2 
via_rhine              27131  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

Thanks again

Sean

---

### Post by scubasean on 2011-09-22
Sorry, I am running 11.04 at the mo.

Sean

---

### Post by jejeman on 2011-09-22
Firewire device is listed by lspci, and kernel modules for firewire are loaded
> firewire_ohci 31504 0 
firewire_core 56138 1 firewire_ohci
crc_itu_t 12627 1 firewire_coreSo what is the problem? It should be working.
You want to transfer video from camcoder? Did you try to do it with Kino?

---

### Post by maul9999 on 2011-09-22
> **scubasean said:**
> I've dipped in  and out of using Ubuntu so pretty much a total novice. I bought a  Dynamode PCI-3PFW firewire card and installed it on my desktop which was  running under 9.04. I bought the card to download videos from a Samsung  SCD303 camcorder. The camcorder itself has an icon that pops up to say  if it is connected to a computer. This appears. But yet my card does not  appear on hardware listings when I use lspci.
 
I've assumed this to be a driver issue but can't find drivers and have  fully upgraded Ubuntu in a vain attempt to see if the drivers were on  newer versions. All to know avail. Can anybody help me please? When I  use lspci I get:

00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)


Thanks

Sean

You will want to check up with website by google for hardware that support linux.  Some PCI's and PCI E's chip doesn't support linux.

---

### Post by jejeman on 2011-09-23
> I assumed that was to do with an onboard setting as it is a Via chipset/motherboard.When you look the card itself you can see VIA chip on it
[http://brain.pan.e-merchant.com/1/0/00853901/l_00853901.jpg](http://brain.pan.e-merchant.com/1/0/00853901/l_00853901.jpg)
> You will want to check up with website by google for hardware that support linux. Some PCI's and PCI E's chip doesn't support linux. I think this card is suported. VIA chips are supported.

---

### Post by scubasean on 2011-09-23
Jejeman,

Sorry, I was being very slow. I assumed the Via entry was my onboard controller. But I have noticed the PCI card has a Via chipset too.

The short answer is, Kino does not appear to be linking to the camcorder. When I turn on the camera and open kino there is no sign of identification. When I open Kino and turn the camera on, there is no identification.

However, the camera itself has an icon that appears on its screen to say it is connected.

Are there any known faults with kino? I've looked around and can't see anything.

Thanks so much for your help

Sean

---

### Post by jejeman on 2011-09-24
In kino when you select capture tab, what is the message on status line at the bottom?

Sometimes it's writing premission problem. Check the permissions on firewire device node in /dev

this can help:
[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

---

### Post by scubasean on 2011-09-24
Jejeman,

Again, I'm feeling really dumb now. Just noticed it says:

WARNING: raw1394 kernal module not loaded or failure to read/write/dev/raw1394!

Looks like that's the problem!

Thanks again for your patience and help.

Sean

---

### Post by scubasean on 2011-09-24
Just looked and this seems to be a common problem with Natty. The old stacks aren't available. Still looking for a comprehensive answer to the problem though.

Sean

---

### Post by jejeman on 2011-09-24
The modules are loaded, so it is the permissons thing.
Just for test, you can run Kino as root, and see if you have acess to camcoder. If you do, than it is defenetly permission problems.
to run Kino as root use this command
```
gksudo kino
```
You can see in which group is the firewire node
```
ls -l /dev/raw1394
```
and than add youreself to that group, or follow the instructions in the help page.
In few days I will be able to see how is this set on my machine. If you don't resolve the problem by then.

---

### Post by trulan on 2011-09-24
/dev/raw1394 is a relic from the old firewire driver stack, it **should not** be there on a fully upgraded Ubuntu, your lsmod output obviously shows the new firewire stack being loaded, so you can disregard anything about raw1394 or permissions for raw1394, all that stuff is obsolete, unless you are using Ubuntu Lucid 10.04 or older.  Ubuntu Maverick 10.10 or newer uses the new firewire stack, and it uses the libraw1394 package rather than the old /dev/raw1394 which had the troublesome permissions settings requirements.

---

### Post by scubasean on 2011-09-25
Thanks Jejeman. I'll try that, but from what Trulan seems to be saying that is an obsolete stack.
 
So, the problem is, Kino is trying to access a stack that doesn't exist in Natty, that is the problem?
 
Sean

---

### Post by scubasean on 2011-09-25
When I set up Kino as root I get a different error in Kino:

"No AV/C compliant cam or not switched on"

On looking for this error I found this thread:

[http://ubuntuforums.org/showthread.php?t=918822](http://ubuntuforums.org/showthread.php?t=918822)

It was suggested to give permissions I use:

**sudo modprobe raw1394**
**sudo chown** username **/dev/raw1394**

On entering the first line I get "FATAL: Module raw1394 not found."

So, like Trulan says the raw1394 stack isn't installed. Should I install it or should the new stack suffice and if it does, how to sort it?

Thanks again

Sean

---

### Post by jejeman on 2011-09-25
So, here it is on my computer with Xubuntu 11.04

```
$lsmod|grep fire
firewire_ohci          39788  0 
firewire_core          56451  1 firewire_ohci
crc_itu_t              12347  1 firewire_core
```
```
$dmesg|tail
[  339.077493] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[  339.585428] firewire_core: created device fw1: GUID 0080458011923651, S100
```
```
$ ls -l /dev/|grep fw
crw-------  1 root root      251,   0 2011-09-25 21:57 fw0
crw-rw----+ 1 root video     251,   1 2011-09-25 22:02 fw1
```
```
$ groups
username adm dialout cdrom plugdev lpadmin admin sambashare vboxusers
```

In kino on status line it writes: AV/C controls enabled

So, new stack is working. I have control over camcoder transport, although I'm not a member of video group.
After you turn on the camcoder, system should create new device.

---

### Post by scubasean on 2011-09-26
Thanks again Jejeman.

When I use dsmesg | tail I get the following:

[   87.939664] wlan0: authenticate with 00:26:44:44:12:cb (try 1)
[   87.941617] wlan0: authenticated
[   87.958671] wlan0: associate with 00:26:44:44:12:cb (try 1)
[   87.961189] wlan0: RX AssocResp from 00:26:44:44:12:cb (capab=0x411 status=0 aid=1)
[   87.961197] wlan0: associated
[   87.961972] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   88.183735] Intel AES-NI instructions are not detected.
[   88.218249] padlock_aes: VIA PadLock not detected.
[   98.512023] wlan0: no IPv6 routers present
[  299.988019] [Hardware Error]: Machine check events logged

No sign of firewire references.

Sean

---

### Post by jejeman on 2011-09-26
Try to use another cable. Or check if camcoder is set correctly for dv transfer.

I don't have any other ideas.

---

### Post by scubasean on 2011-09-26
Didn't have the camera on before. When I turn the camera on I get a something different:

 87.961972] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   88.183735] Intel AES-NI instructions are not detected.
[   88.218249] padlock_aes: VIA PadLock not detected.
[   98.512023] wlan0: no IPv6 routers present
[  299.988019] [Hardware Error]: Machine check events logged
[ 2374.854081] handle_rx_packet: invalid, small RX packet : 1
[ 3936.905715] handle_rx_packet: invalid, small RX packet : 1
[ 4313.231173] handle_rx_packet: invalid, small RX packet : 1
[ 4934.856222] handle_rx_packet: invalid, small RX packet : 1
[ 4994.201071] handle_rx_packet: invalid, small RX packet : 1

Thanks ever so much for your help anyway!

Sean

---

### Post by jejeman on 2011-09-26
There are no messages for firewire. That last messages are probably from wifi.

---

### Post by scubasean on 2011-09-26
Yet, when I plug the Firewire cable to the camera an icon appears on its screen to say it is connected. So, it is at least picking up power from the card. No such icon appears when the cable is connected to the camera and not the card.

I have found another thread with a number of people with similar problems. But no solution..

Thanks ever so much for your help jejeman.

Sean

---

