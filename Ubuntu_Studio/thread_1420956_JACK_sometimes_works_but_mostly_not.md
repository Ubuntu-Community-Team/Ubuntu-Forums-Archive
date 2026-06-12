---
title: "JACK sometimes works but mostly not"
date: 2010-03-03
forum: Ubuntu Studio
---

### Post by simple simon on 2010-03-03
Sometimes jack will work  no xruns and I can connect things together and get sound out, but most of the time it does not.  Sometimes it starts ok and then goes bad - lots of xruns and sound is impossible.

I'm ignoring realtime at the moment as it crashes. I'll tackle that later.

It seems to be IRQ conflict related as when it is not happy and chucking out xruns these are the top processes:

Tasks: 204 total,   1 running, 201 sleeping,   1 stopped,   1 zombie
Cpu(s):  0.8%us, 18.5%sy,  0.0%ni, 79.5%id,  1.2%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1787340k total,   493136k used,  1294204k free,    14464k buffers
Swap:  2104472k total,        0k used,  2104472k free,   228608k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1471 root     -51  -5     0    0    0 S   19  0.0   0:10.15 irq/16-HDA Inte    
  694 root     -80  -5     0    0    0 S    8  0.0   0:06.09 irq/16-ohci_hcd    
  690 root     -81  -5     0    0    0 S    8  0.0   0:05.09 irq/16-ohci_hcd    
 1932 root      20   0  101m  52m  21m S    1  3.0   0:05.61 Xorg               
 4612 mcbrown   20   0  112m  14m  11m S    1  0.9   0:00.41 gnome-terminal     
 4731 mcbrown   20   0 78688  23m  18m S    1  1.4   0:01.08 qjackctl.bin  

and they are not there when jack is running happily.  I have tried stopping CPU scaling but that has no effect. 

Any ideas?  Changing the soundcard is not an option as this is on a laptop (HP 6735s).

Many thanks in anticipation.

Simple Simon.


Various diagnostics are:

mcbrown@koccum:/lib/udev/rules.d$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

mcbrown@koccum:~$ lspci |grep ntel
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

mcbrown@koccum:~$ cat /proc/interrupts
           CPU0       CPU1       
  0:        139          1   IO-APIC-edge      timer
  1:          3        369   IO-APIC-edge      i8042
  7:          1          0   IO-APIC-edge    
  8:          0          1   IO-APIC-edge      rtc0
  9:          3        417   IO-APIC-fasteoi   acpi
 12:         39       6586   IO-APIC-edge      i8042
 16:        145      66241   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb4, HDA Intel
 17:          4        850   IO-APIC-fasteoi   ehci_hcd:usb1, ohci_hcd:usb5, ohci_hcd:usb6, eth2
 18:          0          1   IO-APIC-fasteoi   ohci_hcd:usb7
 19:          0         26   IO-APIC-fasteoi   ehci_hcd:usb2
 20:         36      11473   IO-APIC-fasteoi   ahci
 24:     252954          0  HPET_MSI-edge      hpet2
 28:          0          1   PCI-MSI-edge      eth0
 29:          0          0   PCI-MSI-edge      fglrx[0]@PCI:1:5:0
NMI:          0          0   Non-maskable interrupts
LOC:        796     254274   Local timer interrupts
SPU:          0          0   Spurious interrupts
CNT:          0          0   Performance counter interrupts
PND:          0          0   Performance pending work
RES:      84254       8828   Rescheduling interrupts
CAL:       2814       2755   Function call interrupts
TLB:        584        476   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          1          1   Machine check polls
ERR:          3
MIS:          0

mcbrown@koccum:~$ ps -Leo class,comm,rtprio |grep FF
FF  migration/0         99
FF  sirq-high/0         49
FF  sirq-timer/0        49
FF  sirq-net-tx/0       49
FF  sirq-net-rx/0       49
FF  sirq-block/0        49
FF  sirq-tasklet/0      49
FF  sirq-sched/0        49
FF  sirq-hrtimer/0      49
FF  sirq-rcu/0          49
FF  posixcputmr/0       99
FF  watchdog/0          99
FF  migration/1         99
FF  posixcputmr/1       99
FF  sirq-high/1         49
FF  sirq-timer/1        49
FF  sirq-net-tx/1       49
FF  sirq-net-rx/1       49
FF  sirq-block/1        49
FF  sirq-tasklet/1      49
FF  sirq-sched/1        49
FF  sirq-hrtimer/1      49
FF  sirq-rcu/1          49
FF  watchdog/1          99
FF  events/0             1
FF  events/1             1
FF  irq/9-acpi          50
FF  irq/20-ahci         50
FF  irq/17-ehci_hcd     80
FF  irq/19-ehci_hcd     79
FF  irq/16-ohci_hcd     80
FF  irq/16-ohci_hcd     79
FF  irq/17-ohci_hcd     79
FF  irq/17-ohci_hcd     78
FF  irq/18-ohci_hcd     78
FF  irq/12-i8042        74
FF  irq/1-i8042         75
FF  irq/8-rtc0          90
FF  irq/28-eth0         50
FF  irq/17-eth%d        50
FF  irq/16-HDA Inte     85
FF  irq/29-fglrx[0]     50

mcbrown@koccum:~/Simon/sound_music$ ./realTimeConfigQuickScan.pl
Checking if you are root... no - good.
Finding current kernel config... found /boot/config-2.6.31-9-rt
Checking for Ingo Molnar's Real-Time Preemption... found - good.
Checking for high-resolution timers... found - good.
Checking for 1000hz clock... found - good.
Checking for High Resolution Timers... found - good.
Checking filesystem types... ok.
Checking tmpfs mounted on /tmp..  not found.
** Warning: no tmpfs partition mounted on /tmp
   For more information, see:
   - [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#tmpfs](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#tmpfs)
   - [http://lowlatency.linuxaudio.org](http://lowlatency.linuxaudio.org)
Checking filesystem 'noatime' parameter... 
** Warning: / does not have the 'noatime' parameter set
   For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems)
** Warning: /media/NTFS_koccum does not have the 'noatime' parameter set
   For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems)
** Warning: /home does not have the 'noatime' parameter set
   For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems)
** Set $SOUND_CARD_IRQ to the IRQ of your soundcard to enable more checks.
   Find your sound card's IRQ by looking at '/proc/interrupts' and lspci.
Checking the ability to prioritize processes with (re)nice... yes - good.
Checking the ability to prioritize processes with rtprio... yes - good.
Checking whether you're in the 'audio' group... yes - good.
Checking for multiple 'audio' groups... no - good.
Checking access to the real-time clock... readable - good.
Checking access to the high precision event timer... not readable.
** Warning: /dev/hpet found, but not readable.
** make /dev/hpet readable by the 'audio' group
   For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#hpet](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#hpet)
Checking sysctl settings:
- checking inotify max_user_watches... too small.
** /proc/sys/fs/inotify/max_user_watches is smaller than 524288
** increase it by adding 'fs.inotify.max_user_watches = 524288' to /etc/sysctl.conf and rebooting
   For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#sysctl.conf](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#sysctl.conf)
Checking for resource-intensive background processes... none found - good.
mcbrown@koccum:~/Simon/sound_music$

---

### Post by AutoStatic on 2010-03-03
Hello Simon, what are your JACK settings? Could you post the contents of *~/.jackdrc* ? And you're using the realtime kernel so you could take a look at [rtirq]("http://ubuntuforums.org/showthread.php?t=1328175") (not just for Firewire, also applies to onboard and USB devices).

---

### Post by trulan on 2010-03-03
You very well might be right about it being an IRQ issue.  Poor IRQ 16 is severely overloaded.  Your rtc and HDA_intel IRQ's have the right real time priority which is great.  But having usb3 and usb4 on the same IRQ as your soundcard is bad news, especially if you have anything plugged in those usb ports.  And since it's a laptop you're stuck with the IRQ layout they gave you.  Bummer.

I don't know what IO-APIC-fasteoi is, but it is also sharing that IRQ.  It could also be a culprit.

You mentioned that you have tried stopping CPU scaling.  This is very important, so make sure your CPU is set to its highest frequency (I don't recommend setting the CPU governor to 'performance' because I have seen that revert to 'on-demand' in Karmic for no apparent reason.)

Also, you can try prioritizing the softirq-tasklet threads by running this command:[FONT=monospace]
[/FONT]```
ps -eLo pid,cmd | grep tasklet| sudo awk '{ system("chrt -f -p 78 " $1)}'
```(Omit the 'sudo' in the middle if you are already root).  Change the 78 to the priority you want to give the tasklet threads.  I don't know for sure that this helps in Karmic, but it might be worth trying.

---

### Post by simple simon on 2010-03-04
> **AutoStatic said:**
> Hello Simon, what are your JACK settings? Could you post the contents of *~/.jackdrc* ? And you're using the realtime kernel so you could take a look at [rtirq]("http://ubuntuforums.org/showthread.php?t=1328175") (not just for Firewire, also applies to onboard and USB devices).

AutoStatic, Thanks for responding. I have upgraded the rtirq as per post.  .jackdrc is

/usr/bin/jackd -p128 -t5000 -dalsa -dhw:0 -r44100 -p256 -n3

I have just had 3 hours of jack working fine, connecting things and making music.  I had to do a restart and now it fails (xruns) straight away.  Maddening!

Simple Simon.

---

### Post by AutoStatic on 2010-03-05
Looks good, besides the fact that I would personally use a Periods/Buffer setting of 3 instead of 2. And I prefer a sample rate of 48000. And maybe you could use *hw:SB* instead of *hw:0* as the Interface. As far as I can see I have the exact same soundcard in my netbook and it should work properly without any xruns with a Frames/Period setting of 128.

---

