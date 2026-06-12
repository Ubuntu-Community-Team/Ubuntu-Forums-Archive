---
title: "Jack connects to FP10 but no connections in Jack"
date: 2009-12-21
forum: Ubuntu Studio
---

### Post by Grey Melon on 2009-12-21
First I'll say that I'm running Ubuntu Karmic 64bit with an update to Ubuntu-Studio and all the important rt stuff. I have enabled raw1394 in ubuntu-studio-controls and have set jack to use firewire instead of freebob.

When I open Jack Control and start the server it seems to connect to my Presonus FP10 as the blue light comes on and there are no errors in the message window.

However when I open the Connections window there is nothing. Also no in/out shows up for the FP10 in any app's that I may try(Ardour, Audacity).

I've scoured these forums and followed FFADO's installation guide. Nothing appears to be wrong except for nothing is recognizing the FP10's in/out's.

I'll be happy to run commands and provide screenshots upon request. Thanks.

As a side note this FP10 is problematic under Windows 7 as well. Presonus has been dragging their feet on updated drivers and the usual "I'm switching to MOTU" has ensued. Good times.

---

### Post by trulan on 2009-12-21
Hmm...I never ran into that.  I wonder if the problem is the FP10, the firewire card, or Jack?

Two things you could try would be a different firewire cable, or updating the firmware of the FP10 (you'd have to do that in windows).  I did have one of mine act really weird on a cheap firewire cable - not like this though but who knows?

Also, you could test the unit on a different computer or with a different firewire card to eliminate those possibilities.  I don't know - just throwing out ideas.  What kind of firewire card are you using?

---

### Post by Grey Melon on 2009-12-22
Hi Trulan,

I've read many of your helpful posts in my search to correct this problem. Thanks for coming in on this thread.

I have a dual boot Win7/Ubuntu Karmic 64bit machine. The firewire is on the motherboard. I tried updating the firmware during the process of making the FP10 work in Win7. I kept getting an error immediately after double clicking the firmware executable. When I initially installed the Vista drivers I never got a message saying that firmware was about to be updated.

I had this FP10 working a few months ago from within Ubuntu Jaunty 64bit but it stopped functioning one day and I had so many problems editing H264 video that I bit the bullet, bought Win7 and was editing video that day straight from the .MTS files. I put the audio on the back burner until recently.

Now with my luck Presonus has not, to date, released Win7 drivers and I couldn't get it to work with the Vista drivers so I thought I'd do this again from Ubuntu.

Here I sit all broken hearted...

---

### Post by trulan on 2009-12-22
Interesting.  I did briefly have my firepod working under Win7, using ntrack.  I don't remember what drivers I used.  (The firepod is supposed to be identical to the FP10, just a name change to avoid legal trouble).  But my trial period ended on ntrack (I was a registered user of several old versions but I haven't kept up to date) and my 'trial period' of Win7 has 'expired' as well, so I can't really test that anymore.  But I know I did the firmware updates under WinXP (home of the original pops and clicks firewire recording setup!)

Sad to say, PreSonus is probably focusing every ounce of their efforts on the new FireStudio line, and the discontinued items we are using will likely get neglected...

On another note, how many input and output channels are set in Jack Control?  Did you try setting them to 8 or 10?

Maybe a screenshot of your Jack settings would be enlightening as well.

---

### Post by Grey Melon on 2009-12-22
Screenshot 01 - Jack Control Settings

[IMG]http://greymelon.com/photos/Jack-Settings.png[/IMG]

Screenshot 02 - Jack appears to be connected but nothing showing up

[IMG]http://greymelon.com/photos/Jack-Running.png[/IMG]

---

### Post by AutoStatic on 2009-12-23
Hello Grey Melon,

Could you post the outcome of
- **lspci**
- **cat /proc/interrupts**

---

### Post by trulan on 2009-12-23
Nice screen shots!  I have to restrain myself from clicking your refresh button.

What's the "subgraph starting at qjackctl timed out" error?  That's the only thing that looks immediately out of place.

Did you try specifying your hardware, instead of using 'default'?

Also, another idea:  The rtirq script is broken in Karmic (this can cause issues, for instance if your real time priority for Jack is higher than some important system processes).  This usually presents as pops, clicks, and instability, but who knows?  You can update it as outlined here:
[http://ubuntuforums.org/showpost.php?p=8347114&postcount=5](http://ubuntuforums.org/showpost.php?p=8347114&postcount=5)

---

### Post by Grey Melon on 2009-12-23
> **AutoStatic said:**
> Hello Grey Melon,

Could you post the outcome of
- **lspci**
- **cat /proc/interrupts**

AutoStatic,

[IMG]http://greymelon.com/photos/result-lspci.png[/IMG]

and

[IMG]http://greymelon.com/photos/result-interrupts.png[/IMG]

---

### Post by Grey Melon on 2009-12-23
> **trulan said:**
> Nice screen shots!  I have to restrain myself from clicking your refresh button.

What's the "subgraph starting at qjackctl timed out" error?  That's the only thing that looks immediately out of place.

Did you try specifying your hardware, instead of using 'default'?

Also, another idea:  The rtirq script is broken in Karmic (this can cause issues, for instance if your real time priority for Jack is higher than some important system processes).  This usually presents as pops, clicks, and instability, but who knows?  You can update it as outlined here:
[http://ubuntuforums.org/showpost.php?p=8347114&postcount=5](http://ubuntuforums.org/showpost.php?p=8347114&postcount=5)


I hadn't seen that error before but it seems to have preempted the overrun so I pretty much wrote it off as the immediate problem.

I have tried all 4 of the hardware options that were present under Jack Setup. The only one's that connect are "default" and "hw:0". The others are "plughw:0", "/dev/audio" and "/dev/dsp". I didn't want to assume that default and hw:0 were the same thing but they could be.

I found your post about rtirq previously and did the update so I should be good there.

---

### Post by AutoStatic on 2009-12-23
Thanks Grey Melon! You have the same onboard Firewire controller as I do I think. It shares an IRQ with your card reader and an USB port. So you have to make sure that when you're using the Presonus that you don't have anything plugged in that specific USB port. And maybe you could try blacklisting or unloading the card reader driver (**sudo modprobe -r jmb38x_ms**), I think it's the jmb38x_ms module. Could you also post the output of **lsusb** ? You can copy any text in a terminal with ctrl+shift+c and paste it with ctrl+v.

---

### Post by Grey Melon on 2009-12-23
> **AutoStatic said:**
> Thanks Grey Melon! You have the same onboard Firewire controller as I do I think. It shares an IRQ with your card reader and an USB port. So you have to make sure that when you're using the Presonus that you don't have anything plugged in that specific USB port. And maybe you could try blacklisting or unloading the card reader driver (**sudo modprobe -r jmb38x_ms**), I think it's the jmb38x_ms module. Could you also post the output of **lsusb** ? You can copy any text in a terminal with ctrl+shift+c and paste it with ctrl+v.

Here's the result of lsusb:

qhale001@qhale001-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0d49:7310 Maxtor 
Bus 001 Device 003: ID 5986:0303 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
qhale001@qhale001-laptop:~$ 

I don't have experience with blacklisting but if you point me in the right direction I'll give it a shot. If I unload that module and it doesn't fix things how would I reload it?

Thanks for your help

---

### Post by AutoStatic on 2009-12-23
Thanks!
```
Bus 008 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
```
You should plug that device in another port, it is now on a usb port ( usb8 ) that shares an IRQ with the Firewire chipset.
Unloading a module: **sudo modprobe -r module_name**
(Re)loading a module: **sudo modprobe module_name**

---

### Post by Grey Melon on 2009-12-23
> **AutoStatic said:**
> Thanks!
```
Bus 008 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
```You should plug that device in another port, it is now on a usb port ( usb8 ) that shares an IRQ with the Firewire chipset.
Unloading a module: **sudo modprobe -r module_name**
(Re)loading a module: **sudo modprobe module_name**

Now I see what you're talking about.

I unloaded that module and moved the USB device. After double checking the interrupts and ports I started Jack Control but still no in/out's show up.

Is there a way I can probe the FP10 to see if something is wrong with the firmware?

---

### Post by AutoStatic on 2009-12-23
Yes you can. Therefore you should install the **ffado-tools** package which contains the **ffado-test** app:
```
jeremy@soushi:~$ ffado-test --help
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 1.999.43
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

Usage: ffado-test [OPTION...] OPERATION
FFADO -- a driver for Firewire Audio devices (test application)

OPERATION: Discover
           SetSamplerate samplerate
           SetClockSource [id]
           BusReset
           ListDevices
           SetSplitTimeout timeout_usec
           GetSplitTimeout

  -c, --cache=enable         Use AVC model cache
  -n, --node=id              Node to use
  -p, --port=nr              IEEE1394 Port to use
  -q, -s, --quiet, --silent  Don't produce any output
  -v, --verbose=level        Produce verbose output
  -?, --help                 Give this help list
      --usage                Give a short usage message
  -V, --version              Print program version

Mandatory or optional arguments to long options are also mandatory or optional
for any corresponding short options.

Report bugs to <ffado-devel@lists.sf.net>.
```

You can also monitor if your system detects the Presonus by opening a terminal, entering the command **tail -f /var/log/syslog** and switching on the Presonus.

And another thing, do you use the power adapter that comes with the Presonus?

---

### Post by Grey Melon on 2009-12-23
> **AutoStatic said:**
> Yes you can. Therefore you should install the **ffado-tools** package which contains the **ffado-test** app:
```
jeremy@soushi:~$ ffado-test --help
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 1.999.43
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

Usage: ffado-test [OPTION...] OPERATION
FFADO -- a driver for Firewire Audio devices (test application)

OPERATION: Discover
           SetSamplerate samplerate
           SetClockSource [id]
           BusReset
           ListDevices
           SetSplitTimeout timeout_usec
           GetSplitTimeout

  -c, --cache=enable         Use AVC model cache
  -n, --node=id              Node to use
  -p, --port=nr              IEEE1394 Port to use
  -q, -s, --quiet, --silent  Don't produce any output
  -v, --verbose=level        Produce verbose output
  -?, --help                 Give this help list
      --usage                Give a short usage message
  -V, --version              Print program version

Mandatory or optional arguments to long options are also mandatory or optional
for any corresponding short options.

Report bugs to <ffado-devel@lists.sf.net>.
```You can also monitor if your system detects the Presonus by opening a terminal, entering the command **tail -f /var/log/syslog** and switching on the Presonus.

And another thing, do you use the power adapter that comes with the Presonus?

Well, I get little feedback when using ffado-test Discover
```
qhale001@qhale001-laptop:~$ ffado-test Discover
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.0.0
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

no message buffer overruns
qhale001@qhale001-laptop:~$ 
```here's ffado-test ListDevices
```
qhale001@qhale001-laptop:~$ ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.0.0
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x000a9200c8100574  0x00000A92  0x00010066   Presonus  - PreSonus FP10
   1       0x8ef5900015582d68  0x008EF590  0x00000000   Linux - ohci1394  - 
no message buffer overruns
qhale001@qhale001-laptop:~$ 

```and tail -f /var/log/syslog contains an ominous message
```
Dec 23 14:29:25 qhale001-laptop kernel: [19500.830061] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
Dec 23 14:29:26 qhale001-laptop kernel: [19501.850065] ieee1394: Error parsing configrom for node 0-00:1023
Dec 23 14:29:26 qhale001-laptop kernel: [19501.850186] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
Dec 23 14:29:27 qhale001-laptop kernel: [19503.385320] doh, someone wants to mess with state set
Dec 23 14:29:28 qhale001-laptop kernel: [19503.642786] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[000a9200c8100574]
```Yes I use the power adapter that came with the unit. I'm dying to hear about it's relevance, as my brow is now indicating.

---

### Post by trulan on 2009-12-23
Wow, thanks Autostatic.  More for me to learn!

For reference, ffado-test Discover yields a whole screenful of messages for me (firepod turned on, jack running or not running).  Even with the firepod off it yields a few 'debug' lines and shows my 1394 controller.  It would seem that something is amiss here, with no output at all.

I also have the "doh, someone wants to mess with state set" message in my syslog (along with the node error messages) so I don't think that's a problem.  It does make me wonder who put 'doh' in the syslog...

Edit:  What happens, Grey Melon, if you run sudo ffado-test Discover?  It's a long shot, but if the results are different than what you are seeing now it might indicate some strange permissions problem.

---

### Post by AutoStatic on 2009-12-24
It's weird that Discover yields nothing but that ListDevice does output that there is a FP10 connected. And the syslog is clear too, something is detected and initialized. These are weird warnings though:
```
Dec 23 14:29:25 qhale001-laptop kernel: [19500.830061] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
Dec 23 14:29:26 qhale001-laptop kernel: [19501.850065] ieee1394: Error parsing configrom for node 0-00:1023
```
I've googled a bit but only found Firewire harddrive related information. But from that information I can deduce that it could have something to do with the combination of your Firewire chipset and the FP10.
And concerning the power adapter, if you have a 4-pin Firewire port on your PC then you must attach it otherwise the FP10 won't work at all. If you have a 8-pin port then it's not necessary but I recall reading somewhere that in order to get the device working properly you do need to attach it when using it with Linux.

You said you enabled raw1394, but just to be sure, what is the content of */etc/modules* and the output of **lsmod** ?
And what are the exact specs of the Firewire chipset? Could you post the outcome of **sudo lspci -vvv** and then the stanza that contains all the information on the Firewire chipset? It should look someting like this:
```
06:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30f4
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at da000000 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at da000d00 (32-bit, non-prefetchable) [size=128]
	Region 4: Memory at da000c80 (32-bit, non-prefetchable) [size=128]
	Region 5: Memory at da000c00 (32-bit, non-prefetchable) [size=128]
	Capabilities: [44] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME+
	Capabilities: [80] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 unlimited
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: fffffffc  Data: 0000
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394
```

---

### Post by Grey Melon on 2009-12-24
> **trulan said:**
> Wow, thanks Autostatic.  More for me to learn!

For reference, ffado-test Discover yields a whole screenful of messages for me (firepod turned on, jack running or not running).  Even with the firepod off it yields a few 'debug' lines and shows my 1394 controller.  It would seem that something is amiss here, with no output at all.

I also have the "doh, someone wants to mess with state set" message in my syslog (along with the node error messages) so I don't think that's a problem.  It does make me wonder who put 'doh' in the syslog...

Edit:  What happens, Grey Melon, if you run sudo ffado-test Discover?  It's a long shot, but if the results are different than what you are seeing now it might indicate some strange permissions problem.

Before I get too wrapped up in this problem I do want to thank you guys for the great help and depth of info so far. It makes a huge difference.

Adding sudo to discover was a good idea unfortunately it produces the same nothingness

```
qhale001@qhale001-laptop:~$ sudo ffado-test Discover
[sudo] password for qhale001: 
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.0.0
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

no message buffer overruns
qhale001@qhale001-laptop:~$ 
```

---

### Post by Grey Melon on 2009-12-24
> **AutoStatic said:**
> It's weird that Discover yields nothing but that ListDevice does output that there is a FP10 connected. And the syslog is clear too, something is detected and initialized. These are weird warnings though:
```
Dec 23 14:29:25 qhale001-laptop kernel: [19500.830061] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
Dec 23 14:29:26 qhale001-laptop kernel: [19501.850065] ieee1394: Error parsing configrom for node 0-00:1023
```I've googled a bit but only found Firewire harddrive related information. But from that information I can deduce that it could have something to do with the combination of your Firewire chipset and the FP10.
And concerning the power adapter, if you have a 4-pin Firewire port on your PC then you must attach it otherwise the FP10 won't work at all. If you have a 8-pin port then it's not necessary but I recall reading somewhere that in order to get the device working properly you do need to attach it when using it with Linux.

You said you enabled raw1394, but just to be sure, what is the content of */etc/modules* and the output of **lsmod** ?
And what are the exact specs of the Firewire chipset? Could you post the outcome of **sudo lspci -vvv** and then the stanza that contains all the information on the Firewire chipset? It should look someting like this:
```
06:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 30f4
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at da000000 (32-bit, non-prefetchable) [size=2K]
    Region 1: Memory at da000d00 (32-bit, non-prefetchable) [size=128]
    Region 4: Memory at da000c80 (32-bit, non-prefetchable) [size=128]
    Region 5: Memory at da000c00 (32-bit, non-prefetchable) [size=128]
    Capabilities: [44] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME+
    Capabilities: [80] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 unlimited
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Address: fffffffc  Data: 0000
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394
```

Hmm, I don't have a /etc/modules path. The closest thing is /etc/modprobe.d
Here's **lsmod**
```
qhale001@qhale001-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_si3054     5856  1 
arc4                    2144  2 
ecb                     3296  2 
snd_hda_codec_realtek   277860  1 
iwlagn                124832  0 
iwlcore               133312  1 iwlagn
mac80211              209912  2 iwlagn,iwlcore
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 13088  0 
jmb38x_ms              11300  0 
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
dv1394                 21096  0 
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
nvidia              10316904  38 
memstick               12528  1 jmb38x_ms
sdhci_pci               8928  0 
sdhci                  20484  1 sdhci_pci
led_class               5256  2 iwlcore,sdhci
snd                    77096  18 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              109144  3 iwlagn,iwlcore,mac80211
psmouse                57124  0 
serio_raw               6596  0 
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
lirc_ite8709            7876  0 
lirc_dev               13928  1 lirc_ite8709
raw1394                29096  0 
lp                     11908  0 
parport                40528  2 ppdev,lp
usb_storage            65984  1 
ohci1394               33780  1 dv1394
r8169                  38884  0 
mii                     6368  1 r8169
ieee1394              100896  3 dv1394,raw1394,ohci1394
usbhid                 43968  0 
intel_agp              32816  0 
video                  23612  0 
output                  3680  1 video
qhale001@qhale001-laptop:~$ 
```and the relevant portion of **sudo lspci -vvv**
```
04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (prog-if 10)
    Subsystem: CLEVO/KAPOK Computer Device 0481
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at f3200000 (32-bit, non-prefetchable) [size=2K]
    Region 1: Memory at f3201000 (32-bit, non-prefetchable) [size=128]
    Region 4: Memory at f3200c00 (32-bit, non-prefetchable) [size=128]
    Region 5: Memory at f3200800 (32-bit, non-prefetchable) [size=128]
    Capabilities: [44] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME+
    Capabilities: [80] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 unlimited
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Address: fffffffc  Data: 0000
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394
```

Oh boy. To my eyes it doesn't appear that the FP10 has been "bricked". At the same time there is a lot of info here that is beyond me so I'm speculating.

---

### Post by AutoStatic on 2009-12-28
Thanks Grey Melon!
/etc/modules is a file, not a directory. But I think it's ok, I see raw1394 is loaded. And you have a slight different onboard Firewire chipset, I'll try googling it to see if I can find anything.

---

### Post by Grey Melon on 2009-12-28
> **AutoStatic said:**
> Thanks Grey Melon!
/etc/modules is a file, not a directory. But I think it's ok, I see raw1394 is loaded. And you have a slight different onboard Firewire chipset, I'll try googling it to see if I can find anything.

Thanks AutoStatic,

Ah yes I see now the modules file does indeed show the following:

lp
raw1394
rtc

I'll keep searching as well.

Quinn

---

