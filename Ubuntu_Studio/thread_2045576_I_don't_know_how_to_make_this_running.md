---
title: "I don't know how to make this running"
date: 2012-08-21
forum: Ubuntu Studio
---

### Post by Carlosll on 2012-08-21
Hello

I have an roland edirol ua-25ex. 

kernel:

Linux carlos-laptop 3.0.0-19-lowlatency #33~lucid1 SMP PREEMPT Fri Apr 20 14:30:35 UTC 2012 x86_64 GNU/Linux

the computer is a thoshiba satellite.

well, every time I try to make music with ardour I have Xruns or worst.  I have instaled the realTimeConfigQuickScan.pl with most of all the checks right. and also the Rui Nuno Capella wich order IRQ (rtirq-init). 

I can make one track, but not more than 2 tracks because the Xruns flow into the music. 

I think that there is some conflict, because I have three sound cards in total:

carlos@carlos-laptop:~$ **aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: UA25EX [UA-25EX], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


and I have, multiple things in the IRQ of the sound card, I supose, because I'm a musician not a linux adm. I'm lost:

here is:

carlos@carlos-laptop:~$ **lsusb**
Bus 002 Device 008: ID 0582:00e7 Roland Corp. 
Bus 002 Device 007: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 006: ID 046d:c31d Logitech, Inc. 
Bus 002 Device 005: ID 0458:002e KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 004: ID 0930:0214 Toshiba Corp. 
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 10f1:1a2a  
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



and more: 

carlos@carlos-laptop:~$ **cat /proc/interrupts**

           CPU0       CPU1       CPU2       CPU3       
  0:        139          1          6          7   IO-APIC-edge      timer
  1:          3            2          2          2   IO-APIC-edge      i8042
  8:          0            0          1          0   IO-APIC-edge      rtc0
  9:          0            0          0          0   IO-APIC-fasteoi   acpi
 12:         50         50         34         39   IO-APIC-edge      i8042
 16:         35         35         46         46   IO-APIC-fasteoi   ehci_hcd:usb1, mei
 19:       6253       5354       8217       8528   IO-APIC-fasteoi   ata_piix
 21:       5180       4730      16361      16023   IO-APIC-fasteoi   ata_piix, ips
 23:      11167      10647     103824      97729   IO-APIC-fasteoi   ehci_hcd:usb2
 41:       7634       4232        737        626   PCI-MSI-edge      radeon
 42:         33         33         32         31   PCI-MSI-edge      hda_intel
 43:          7          7          8          8   PCI-MSI-edge      hda_intel
 44:         11      26290         14         14   PCI-MSI-edge      eth0
NMI:          0          0          0          0   Non-maskable interrupts
LOC:    6831091    6807143    6803464    6820334   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
IWI:          0          0          0          0   IRQ work interrupts
RES:    3275122    3024744     366751     284118   Rescheduling interrupts
CAL:        301        516        480        506   Function call interrupts
TLB:       2559       4520        481        441   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:         24         24         24         24   Machine check polls
ERR:          0
MIS:          0

**this was the output with the rtirq ran before. **


and here:

carlos@carlos-laptop:~$ **lspci**
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
03:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

I really don't know what I have to do.

Some people has told me that as longer as I have the HDMI I will not expect to get it better. but I have search a lot and I can't find hot to disable it (via bios included). and also, I don't know if that's right.

I can't make any questions because I don't understand really the IRQ, the lspci, or the **tree**:


**/sys/bus/usb/drivers/usb/**
|-- 1-1 -> ../../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1
|-- 1-1.3 -> ../../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3
|-- 2-1 -> ../../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1
|-- 2-1.2 -> ../../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2
|-- 2-1.3 -> ../../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3
|-- 2-1.3.2 -> ../../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.2
|-- 2-1.3.3 -> ../../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.3
|-- 2-1.3.4 -> ../../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.4
|-- 2-1.6 -> ../../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6
|-- bind
|-- uevent
|-- unbind
|-- usb1 -> ../../../../devices/pci0000:00/0000:00:1a.0/usb1
`-- usb2 -> ../../../../devices/pci0000:00/0000:00:1d.0/usb2

Can't anybody help me? i'm lost.

thank you.

---

### Post by Sylos on 2012-08-21
Hello.

I cant give you too much info on most of your output but if you want to get rid of the HDMI then you could blacklist the driver module for that card. This would obviously mean you couldnt use that card but if you dont mind using the edirol for all your sound needs it might work.

I think the module would be snd-hda-intel.

Just add:

```
blacklist snd_hda_intel
```

to the bottom of your /etc/modprobe.d/blacklist.conf file.

If that helps then at least you have something to work with.

Cheers

---

### Post by CrocoDuck on 2012-08-21
Hi, I had a similar issue, here the thread with solution: [http://ubuntuforums.org/showthread.php?t=1976254](http://ubuntuforums.org/showthread.php?t=1976254) . As you know, at the page  [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf) you find a script for "Disabling everything you don't need" . You could try to run the script you find at that section commenting the line

```
echo -n "0000:00:13.0" > /sys/bus/pci/drivers/ohci_hcd/unbind # Unbind a USB port, this one interferes with my onboard soundcard
```and the lines

```
# The following section is for kernels < 2.6.39. Kernels > 2.6.39 do not have a tasklet daemon.
TASKLETPR=76 # Define a variable TASKLETPR and set it to 76

ps -eLo pid,cmd | grep [t]asklet | awk '{ system("chrt -f -p '$TASKLETPR' " $1)}' # Do some greppy awky stuff and set the prio of the tasklet daemon
```

---

### Post by Carlosll on 2012-08-21
thank you Sylos and Crocoduk. 

I have blacklisted the 
snd_hda_intel
and it works!!!

I have recorded the fourth track with no xruns. I'm still trembling.

may I ask you, how do I know what modules and what takes this modules about Has the computer running?

because, I Have tried, time ago, that script and there were error in the modules that the computer use. or they were dependents in other modules that finally I couldn't remove. 

I think, in my ignorance, that script is too old.

but anyway, thank you both of you. music to you!!!

that's what the script sends

```
FATAL: Error removing ppdev (/lib/modules/3.0.0-19-lowlatency/kernel/drivers/char/ppdev.ko): Operation not permitted
FATAL: Error removing lp (/lib/modules/3.0.0-19-lowlatency/kernel/drivers/char/lp.ko): Operation not permitted
FATAL: Error removing uvcvideo (/lib/modules/3.0.0-19-lowlatency/kernel/drivers/media/video/uvc/uvcvideo.ko): Operation not permitted
FATAL: Module videodev is in use.
FATAL: Module btusb is in use.
modem-manager(729): Operation not permitted
 * Deconfiguring network interfaces...       modem-manager: no process found
                                                                                 * Stopping Common Unix Printing System: cupsd       wpa_supplicant(835): Operation not permitted
                                                                                start-stop-daemon: warning: failed to kill 947: Operation not permitted
                                                                         [ OK ]
wpa_supplicant: no process found
```
```
carlos@carlos-laptop:/bin$ Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop network-manager
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.54" (uid=1000 pid=2002 comm="stop) interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
pkill: 913 - Operation not permitted
ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
```


that's what I was talking about. none of the commands of the script are up to date. I don't know what happens.

sorry, I have realized that the script must be run with root privileges. "SUDO".

that's what the output of the script tells:

```
FATAL: Module btusb is in use.
 * Stopping Common Unix Printing System: cupsd                                   * Deconfiguring network interfaces...                                   [ OK ] 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop network-manager
carlos@carlos-laptop:/bin$ network-manager stop/waiting
Ignoring unknown interface eth0=eth0.
```

So, next days I'm going to test the results of the changes done. Thank you very much to Sylos and Crocoduck.

---

### Post by CrocoDuck on 2012-08-22
> **Carlosll said:**
> sorry, I have realized that the script must be run with root privileges. "SUDO".

that's what the output of the script tells:

FATAL: Module btusb is in use.
 * Stopping Common Unix Printing System: cupsd                                   * Deconfiguring network interfaces...                                   [ OK ] 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop network-manager
carlos@carlos-laptop:/bin$ network-manager stop/waiting
Ignoring unknown interface eth0=eth0.



So, next days I'm going to test the results of the changes done. Thank you very much to Sylos and Crocoduck.


\\:D/ So happy that you have no more xruns. If everything is ok just by blaklisting the intel hda, I think you can forgive the script. When I use it (everytime I make music) I'm usually login as superuser with:

```
su
```as I configured a root user. Then I set cpus to performance and then I call the script... But, as I said, if everything is ok you can go on without the script.

---

### Post by Carlosll on 2012-08-23
Yes!

I have recorded a four tracks song without any xruns. Yes!

Believe or not I have been trying to make this up for a year.

But here it is! blacklisting the intel hda driver of the sound car the problem was solved.

I have run the machine with the script of "Disambling everything you don't need" with some modifications: I don't run the lines Crocoduck told me, I don't run the line about the midi that I don't use, and I make the shutdown of the services as the output of the script tells.

"cd ......

sudo sh script.sh"

After this I run the Rui Nuno Capella (rtirq)

"sudo /etc/init.d/rtirq start"

And that's all. 

Thank you very much. Crocoduck and Sylon, and to other people making this posible. I will make a song to the epic adventure of free sound and friendship.
thank you  very much!!!

---

