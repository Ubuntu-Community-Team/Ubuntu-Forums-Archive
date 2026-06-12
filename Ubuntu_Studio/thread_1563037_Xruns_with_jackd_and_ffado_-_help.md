---
title: "Xruns with jackd and ffado - help"
date: 2010-08-28
forum: Ubuntu Studio
---

### Post by DARKAD on 2010-08-28
I would work on a song after latest system update on ubuntustudio 10.04, but jackd shows many xruns.
(Any suggestion would be greatly appreciated)

Intel core 2 duo t8100 ram 4GB

$ uname
Linux ubuntu 2.6.32-24-preempt #41-Ubuntu SMP PREEMPT Thu Aug 19 03:55:01 UTC 2010 x86_64 GNU/Linux

/usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p512 -n2 -i3 -o2

jackd 0.118.0

Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    3018570

no message buffer overruns

JACK compiled with System V SHM support.

SSE2 detected

libffado 2.0.0 built Mar 31 2010 16:21:44

$ groups
adm dialout cdrom floppy tape audio dip video plugdev lpadmin netdev admin sambashare

$ ls -al /dev/raw1394
crw-rw---- 1 root audio 171, 0 2010-08-28 18:21 /dev/raw1394

$ ffado-test ListDevices
Version: 2.0.0
=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x002241fffef10fb2  0x00002241  0x00000000   Linux - ohci1394  - 
   1       0x0014960004000000  0x00001496  0x00000000   Phonic - FireFly 302
no message buffer overruns

/etc/default/rtirq
RTIRQ_NAME_LIST="rtc0 ohci1394 snd usb i8042"

# Highest priority.
RTIRQ_PRIO_HIGH=90

# Priority decrease step.
RTIRQ_PRIO_DECR=5

# Whether to reset all IRQ threads to SCHED_OTHER.
RTIRQ_RESET_ALL=0

# On kernel configurations that support it,
# which services should be NOT threaded 
# (space separated list).
RTIRQ_NON_THREADED="rtc0 ohci1394 snd"

/etc/security/limits.conf
@audio          -       rtprio          99

@audio - memlock 2414856
@audio - nice -19

p.s. "cpu frequency applet is set on performance"

---

### Post by AutoStatic on 2010-08-28
Hello DARKAD,

Could you post the output of:
[LIST]
[*]**cat /proc/interrupts**
[*]**lspci | grep1394**
[*][realTimeConfigQuickScan]("http://code.google.com/p/realtimeconfigquickscan/") (if possible, you need the packages mercurial and perl-tk for this)
[/LIST]

Thanks!

---

### Post by DARKAD on 2010-08-29
Many thanks for the script you suggested.
I changed many things.

1) I didn't change the cpufreq, because I'm afraid about cpu temperature.
2) Can you give me just a little help more to set the $SOUND_CARD_IRQ (FireFly 302 is on the 19 ?) ?

-----------------
-----------------
ffado-test ListDevices
Version: 2.0.0
=== 1394 PORT 0 ===
Node id GUID VendorId ModelId Vendor - Model
0 0x002241fffef10fb2 0x00002241 0x00000000 Linux - ohci1394 - 
1 0x0014960004000000 0x00001496 0x00000000 Phonic - FireFly 302
-----------------
-----------------
cat /proc/interrupts
            CPU0       CPU1       
   0:        136          2   IO-APIC-edge      timer
   8:          1          0   IO-APIC-edge      rtc0
   9:        158        157   IO-APIC-fasteoi   acpi
  16:         51       3910   IO-APIC-fasteoi   uhci_hcd:usb4, uhci_hcd:usb5, eth1
  18:      13709       1430   IO-APIC-fasteoi   ata_piix, uhci_hcd:usb6
  19:         46         47   IO-APIC-fasteoi   ohci1394
  20:        583      74635   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb3, HDA Intel
  21:        156      37325   IO-APIC-fasteoi   ata_piix, ehci_hcd:usb1, uhci_hcd:usb7
  27:          0          1   PCI-MSI-edge      eth0
  28:       3862         94   PCI-MSI-edge      i915
 NMI:          0          0   Non-maskable interrupts
 LOC:    2347891    2356671   Local timer interrupts
 SPU:          0          0   Spurious interrupts
 CNT:          0          0   Performance counter interrupts
 PND:          0          0   Performance pending work
 RES:       1981       1358   Rescheduling interrupts
 CAL:         64         68   Function call interrupts
 TLB:       3136       3252   TLB shootdowns
 TRM:          0          0   Thermal event interrupts
 THR:          0          0   Threshold APIC interrupts
 MCE:          0          0   Machine check exceptions
 MCP:          8          8   Machine check polls
 ERR:          1
 MIS:          0
------------------------------------
------------------------------------
lspci | grep 1394
04:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)
------------------------------------
------------------------------------
== GUI-enabled checks ==
Checking if you are root... no - good
Checking filesystem 'noatime' parameter... 2.6.31 kernel - good
(relatime is default since 2.6.30)
Checking CPU Governors... CPU 0: 'ondemand' CPU 1: 'ondemand'  - not good
Set CPU Governors to 'performance' with 'cpufreq-set -c <cpunr> -g performance'
See also: [http://linuxmusicians.com/viewtopic.php?f=27&t=844](http://linuxmusicians.com/viewtopic.php?f=27&t=844)
Checking swappiness... 10 - good
Checking for resource-intensive background processes... none found - good
Checking checking sysctl inotify max_user_watches... >= 524288 - good
Checking access to the high precision event timer... readable - good
Checking access to the real-time clock... readable - good
Checking whether you're in the 'audio' group... yes - good
Checking for multiple 'audio' groups... no - good
yes - good.
Checking the ability to prioritize processes with rtprio... yes - good
== Other checks ==
Finding current kernel config... found /boot/config-2.6.31-11-rt
Checking for Ingo Molnar's Real-Time Preemption... found - good.
Checking for high-resolution timers... found - good.
Checking for 1000hz clock... found - good.
Checking for High Resolution Timers... found - good.
Checking filesystem types... ok.
ok.
** Set $SOUND_CARD_IRQ to the IRQ of your soundcard to enable more checks.
   Find your sound card's IRQ by looking at '/proc/interrupts' and lspci.

---

### Post by AutoStatic on 2010-08-29
> **DARKAD said:**
> Many thanks for the script you suggested.
I changed many things.

1) I didn't change the cpufreq, because I'm afraid about cpu temperature.
2) Can you give me just a little help more to set the $SOUND_CARD_IRQ (FireFly 302 is on the 19 ?) ?You really need to set cpufreq to a fixed governor because JACK totally doesn't like scaling CPU's. It's not the governor, it's the scaling itself afaik. So if you set it to Conservative for example? And what kind of system is this about? And don't worry about the IRQ of the soundcard, the output of the script looks great, so except for the CPU scaling you should have a very decent real-time setup.

---

### Post by DARKAD on 2010-08-29
Before I'll work with jack and ardour I will try on terminal:

cpufreq-set -c 0 -g conservative
cpufreq-set -c 1 -g conservative

but it's the same.

I'll try 'performance'.

The system is a MacBook 13" t8100 dual core duo:
[URL="http://www.everymac.com/systems/apple/macbook/stats/macbook-core-2-
duo-2.1-white-13-early-2008-penryn-
specs.html"]http://www.everymac.com/systems/apple/macbook/stats/macbook-
core-2-duo-2.1-white-13-early-2008-penryn-specs.html[/URL]

I have ubuntustudio 10.04 in dual boot with leopard.

Thank you!

---

### Post by c0rrupt0r on 2010-12-02
> **AutoStatic said:**
> Hello DARKAD,

Could you post the output of:
[LIST]
[*]**cat /proc/interrupts**
[*]**lspci | grep1394**
[*][realTimeConfigQuickScan]("http://code.google.com/p/realtimeconfigquickscan/") (if possible, you need the packages mercurial and perl-tk for this)
[/LIST]

Thanks!

Hello, 
I have run all the above steps other then I am not using firewire but I am running ALSA and have been gathering some xruns while I am streaming with Jackd and IDJC and gathering disconnects about every 30 Minutes, here is my info I have gathered.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=177216&stc=1&d=1291324730[/IMG]

I have also fixed all issues that QuickScan has given me info on. thank you for that script for sure was great info.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=177215&stc=1&d=1291324261[/IMG]

After all this testing and so on I have also come to find out. when I change my Sound card settings in qjackctl to "Default" (which is my Intel onboard soundcard), instead of using my Plantronics usb wireless 995H headset It all works with no xruns and no disconnections. Please help here, I do not wish to use my default onboard sound card, I enjoy using my headset. Thank you in advanced. 

BTW I am also Running Ubuntu Studio 10.10

I did not realize this was marked as Solved. so maybe thats why I am not gathering any help. I have now created another thread on this with all the same info. hope I now can gather some help and wish there was some more info on this thread here to why or how this was solved.

---

