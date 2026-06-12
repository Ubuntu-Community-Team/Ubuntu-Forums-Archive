---
title: "FFADO and Focusrite Saffire LE"
date: 2010-11-04
forum: Ubuntu Studio
---

### Post by Bi11yy on 2010-11-04
I have UbuStu running on my tower, dual booted  with win7 64. Everythings good except I'm having issues with FFADO and my  firewire audio card, a Focusrite Saffire LE. I've seen lots of success  stories with that card and FFADO says it'll work with, but I'm not one of them. It just doesn't see my FW audio. What should I configure?Anyone can help me? I gots lots of Halloween candy to share!

---

### Post by AutoStatic on 2010-11-05
Which version of Ubuntu Studio?

To set up your system:
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

If it still doesn't work after going through the steps pointed out on the help page then please post the result of:
[LIST]
[*]**lspci | grep 1394**
[*]**cat /proc/interrupts**
[*]**ffado-diag** (you will need to install the ffado-tools package first)[/LIST]

Best,

Jeremy

---

### Post by fatwilly6 on 2010-11-05
I am struggling with the same issue in as much as the SaffireLE is recognised by ffado-mixer but I just can't get jack to work with firewire drivers selected, nor can I get midi or audio inputs to do anything nor can I get the phantom power button to activate nor the mic/line switches on Channels 1 & 2 to work. I have disabled the 'new' firewire stack & this did at least allow ffado-mixer to recognise the box. There are many posts in this section about the new 'JuJu' firewire stack issue with 10.10 studio setups. I am also struggling to get the various studio applications to produce any sound & talk to each other but I am gathering info for another post about those problems.

I have 64 bit 10.10 studio with Creative Soundblaster pci card (emu10k1) & jack2 with AMD FX53 chip. I will post my file results later when I get home.

---

### Post by Bi11yy on 2010-11-06
> **AutoStatic said:**
> Which version of Ubuntu Studio?

To set up your system:
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

If it still doesn't work after going through the steps pointed out on the help page then please post the result of:
[LIST]
[*]**lspci | grep 1394**
[*]**cat /proc/interrupts**
[*]**ffado-diag** (you will need to install the ffado-tools package first)
[/LIST]

Best,

Jeremy

Thanks Jeremy, but I'm still stuck. I'm using UbStu10.10 64bit.

I did all the settings on the page you linked to until I set up Jack, which didn't work because it still hasn't found my FW yet. It basically says "Cannot start, no device found."

My **lspci | grep 1394: **

05:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

My **cat /proc/interrupts**:

           CPU0       CPU1       
  0:         28          2   IO-APIC-edge      timer
  1:          1          1   IO-APIC-edge      i8042
  6:          1          2   IO-APIC-edge      floppy
  8:          1          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          2          2   IO-APIC-edge      i8042
 16:        169      24317   IO-APIC-fasteoi   uhci_hcd:usb3, pata_jmicron, nvidia
 18:         89      43250   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb5, uhci_hcd:usb8
 19:      11795       1575   IO-APIC-fasteoi   ata_piix, ata_piix, uhci_hcd:usb7
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 23:          8          1   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb6, firewire_ohci
 44:        105      11629   PCI-MSI-edge      eth0
 45:        367       1091   PCI-MSI-edge      hda_intel
NMI:          0          0   Non-maskable interrupts
LOC:      34298      45603   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:       3599       2155   Rescheduling interrupts
CAL:        179        123   Function call interrupts
TLB:        501        625   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          4          4   Machine check polls
ERR:          1
MIS:          0


My **Ffado-tools**: 


FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.35-22-generic
FIXME: implement test for RT kernel
   RT patched............... False
  old 1394 stack present.... True
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. True
  /dev/raw1394 permissions.. True
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5
   g++ ............... sh: g++: not found
   PyQt4 (by pyuic4) . sh: pyuic4: not found
   jackd ............. no message buffer overruns
     path ............ /usr/bin/jackd
     flags ........... Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found
   libraw1394 ........ Package libraw1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libraw1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libraw1394' found
     flags ........... Package libraw1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libraw1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libraw1394' found
   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavc1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavc1394' found
     flags ........... Package libavc1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavc1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavc1394' found
   libiec61883 ....... Package libiec61883 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libiec61883.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libiec61883' found
     flags ........... Package libiec61883 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libiec61883.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libiec61883' found
   libxml++-2.6 ...... Package libxml++-2.6 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml++-2.6.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml++-2.6' found
     flags ........... Package libxml++-2.6 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml++-2.6.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml++-2.6' found
   dbus-1 ............ Package dbus-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-1' found
     flags ........... Package dbus-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-1' found
 Prerequisites (static at compile-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.4.4-8ubuntu1) 4.4.5 20100728 (prerelease)
   g++ ............... g++ (Ubuntu/Linaro 4.4.4-8ubuntu1) 4.4.5 20100728 (prerelease)
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.7.4 for Qt version 4.7.0
   jackd ............. sh: jackd: not found
     path ............ 
     flags ........... Package jack was not found in the pkg-config search path.
   libraw1394 ........ 2.0.5
     flags ...........  -lraw1394  
   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
     flags ........... Package libavc1394 was not found in the pkg-config search path.
   libiec61883 ....... 1.2.0
     flags ...........  -liec61883 -lraw1394  
   libxml++-2.6 ...... 2.30.0
     flags ........... -pthread -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -pthread -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0  
   dbus-1 ............ 1.2.24
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include  -L/lib -ldbus-1 -lpthread -lrt  
 Hardware...
   Host controllers:
05:07.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024] (prog-if 10 [OHCI])
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:1000]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (500ns min, 1000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at f7004000 (32-bit, non-prefetchable) [size=2K]
    Region 1: Memory at f7000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394

   CPU info:
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
stepping    : 13
cpu MHz        : 2200.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips    : 4400.41
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
stepping    : 13
cpu MHz        : 1200.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips    : 4400.00
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:           [28, 28], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:             [1, 1], Sched None (priority None), drivers: ['i8042']
 IRQ    6: PID:  None, count:             [1, 1], Sched None (priority None), drivers: ['floppy']
 IRQ    8: PID:  None, count:             [1, 1], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count:             [2, 2], Sched None (priority None), drivers: ['i8042']
 IRQ   16: PID:  None, count:         [169, 169], Sched None (priority None), drivers: ['uhci_hcd:usb3', 'pata_jmicron', 'nvidia']
 IRQ   18: PID:  None, count:           [89, 89], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'uhci_hcd:usb5', 'uhci_hcd:usb8']
 IRQ   19: PID:  None, count:     [13089, 13089], Sched None (priority None), drivers: ['ata_piix', 'ata_piix', 'uhci_hcd:usb7']
 IRQ   21: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['uhci_hcd:usb4']
 IRQ   23: PID:  None, count:             [8, 8], Sched None (priority None), drivers: ['ehci_hcd:usb2', 'uhci_hcd:usb6', 'firewire_ohci']
 IRQ   44: PID:  None, count:         [105, 105], Sched None (priority None), drivers: ['eth0']
 IRQ   45: PID:  None, count:         [367, 367], Sched None (priority None), drivers: ['hda_intel']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This stack is not supported by FFADO. Please use the old stack.

Still confused. :(:(:(. FFADO Tools says I'm missing all these libraries, but I searched my computer and found them, like the first one it says jackd is not in /usr/bin, but it is!!

---

### Post by AutoStatic on 2010-11-06
> **Bi11yy said:**
> The new FireWire kernel stack is loaded. 
This stack is not supported by FFADO. Please use the old stack.This is weird, I thought the new stack worked: [http://ubuntuforums.org/showpost.php?p=10018081&postcount=2](http://ubuntuforums.org/showpost.php?p=10018081&postcount=2)
But I was already doubting this because by the time 10.10 was frozen FFADO 2.999.0 (so not 2.0.1 which has support for the new stack) did not have support for the new stack afaik. Is your install fully updated?
You can try disabling the new stack and enable the old stack. You do this by editing the */etc/modprobe/blacklist-firewire.conf* so that it looks like the one on Lucid:```
# Select the legacy firewire stack over the new CONFIG_FIREWIRE one.

#blacklist ohci1394
#blacklist sbp2
#blacklist dv1394
#blacklist raw1394
#blacklist video1394

blacklist firewire-ohci
blacklist firewire-sbp2
```After that run **sudo update-initramfs -u -k all** and reboot. That should enable the old stack.

Best,

Jeremy

---

### Post by Bi11yy on 2010-11-06
Well about a month ago, before I was 10.10, I was using 9.04 with the old stack and had same prob. It was one of the reason I moved to 10.10, I heard the new stack made things easier. :( Do you have a Saffire? If so, let me ask you, when you plug it in, does it stay on the orange lights or click to green?

---

### Post by AutoStatic on 2010-11-06
I have two Saffires, but no LE.
And it's not the same problem I think, ffado-diag is pretty clear about that. So please try with the old stack and run ffado-diag again.

---

### Post by trulan on 2010-11-06
**Edit:**  the last thing I want to do is add to the confusion currently surrounding this issue.  Disregard my post unless you want to do some experimenting with the new firewire stack.


I get that message about ffado not supporting the new stack here too, as well as a similar string of "package not found" errors.  But it works anyway (presonus firepod).  With all the trouble people seem to be having with the new stack I keep testing mine on 10.10 (64bit) and it keeps working...to check which firewire stack is loaded, do:
```
lsmod | grep 1394
```and
```
lsmod | grep firewire
```the first command will show modules from the legacy stack, the second will show modules from the JuJu stack.  Only one stack can be loaded at a time.  also, raw1394 should not be loaded when using the new stack.  Your ffado-diag report shows that /dev/raw1394 is active and it should not be if you want to use the new stack.  To remove it, do:
```
sudo rmmod raw1394
```You'll probably also need to do:
```
sudo rmmod ieee1394
```I must say, it makes no difference to me if you use the legacy stack or the JuJu stack, it just boggles my mind that it works here with no trouble at all, and I seem to be about the only one...

---

### Post by Bi11yy on 2010-11-06
Autostatic: Ok one prob: That file is at root, and Im not root. How should take control to edit it?
EDIT: NM, I got it, gedit is my friend, but you got the dir wrong. It's Modprobe.*d*. At least on my sys!

EDIT: Thanks Trulan, Im trying this now. One question: Disabling raw1394 like that (command line) is that the same as disabling it under UbuntuStudio Controls?

---

### Post by trulan on 2010-11-06
> **Bi11yy said:**
> Thanks Trulan, Im trying this now. One question: Disabling raw1394 like that (command line) is that the same as disabling it under UbuntuStudio Controls?
Not exactly.  But first - do either what I recommended or what Autostatic recommended **but not both at the same time.**

Okay, now to answer your question:  Ubuntu Studio Controls sets some things in your config files to give you access to raw1394 (which needs root privileges, hence the warning it gives you when you check 'allow').  The command I posted actually removes the module from operation, and it will come back after you reboot unless it is removed from the config files.

I suspect that Ubuntu Studio Controls is actually causing the problem here, now that I think about it.  If the new firewire stack is to be used, you do not want raw1394 enabled.  If you enable raw1394, as we are accustomed to doing, it will also load the ieee1394 module, and now you've got half of the legacy stack loaded on top of the JuJu stack and that's just not going to work.

In summary:
**Option 1:  **To use the new JuJu firewire stack, disable raw1394 in Ubuntu Studio Controls and reboot.  Then, make sure non of the legacy firewire stack is loaded.  (lsmod | grep 1394 should return no output).

**Option 2:**  To use the legacy firewire stack, follow Autostatic's directions in post above.  Then, enable raw1394 in Ubuntu Studio Controls and reboot.

**Both ways should work.**  Ffado support should be the same for any device on either stack - but YMMV.

---

### Post by Bi11yy on 2010-11-06
Annnndddd I'm back.

Thanks for the reply Trulan. Here's what I wound up doing: just as you said not to, I did both methods and royally messed up my stack. Luckily I had my install imaged so I just re-imaged and now I'm back, fresh and clean. Ok, since this is a fresh install, updated and fairly untouched, I did a FFado-diag and got this:
FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.35-22-generic
FIXME: implement test for RT kernel
   RT patched............... False
  old 1394 stack present.... True
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. False


and at the bottom:

=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This stack is not supported by FFADO. Please use the old stack.


Now, from what I can tell only the new stack is loaded, but what you seem to be saying is that only one stack can be loaded at a time. FFADO is saying that, but its also saying the old stack is present, but not loaded or doing anything. Currently, my FW isnt working. Earlier today, after doing what you said about removing the old modules, I messed things up because I wasn't sure how to restore the old stack modules to get things back and try with the old stack. I'm going to try with the old stack since that's just me editing the .conf file.

---

### Post by Bi11yy on 2010-11-06
Okay, I tried the old stack first, blacklisting like Autostaic noted, and enabling Raw1394. Rebooted. Nothing. did 'lsmod | grep 1394' everything was there (1394raw 1394ohci, 1394ieee). FFADO reported perfect 1394 status, but no FW audio for me. ok.
Now I'm trying the new stack, but I seem to have lost my files. I re-edited my blacklist-firewire.conf file back. I even rm'd all the old stack files. 'lsmod | grep firewire' reports nothing! I'm stuck, again.
Yup, I've lost my JuJu stack!

---

### Post by Bi11yy on 2010-11-06
I got my JuJu back! Alright I'm getting this, but doing both methods, I have no firewire. Doesn't make sense. 

 Autostatic, when I asked you about your Saffire, what I was asking, though it didn't come out right, was how long did you wait for your orange lights to go off and the green lights to come on? Longer than a minute, because I'm waiting and waiting with both methods (old and new stack) and getting nothing. This doesn't make sense. Something should work, right? Old or new, I'm making sure I have no conflict in FFADO, if I'm using one, the other is blacked out, still nothing. 
$#@$##&&^%$@@$#W&*^*&^)*&(%^^%$!!!!!!!!!

 Man I need help with this.

 Should I leave the Saffire plugged in, because what I'm doing now is unplugging it, rebooting (after I change methods), then plugging it back in when I reboot. Also I have onboard audio, would that cause interference? The way I use it in Win7 is that I use the onboard audio for a third mixer channel when I dj at home, and use the Saffire as my main audio interface. Also since the Saffire cant monitor its own channels (stupid Focusrite), I use the onboard audio Spdif for sampling movies and audio sources. So its essential to my setup, and I'd hate to see it go, but I can disable it through the BIOS. I guess I'll try that to make sure it isn't running interference. *sigh*

---

### Post by trulan on 2010-11-06
I would let it plugged in (especially if you're on the old stack - man this is getting confusing!  Sorry...).  I would set things up for the old stack (everybody's going to be a lot more familiar with troubleshooting that) and reboot with the Saffire plugged in and turned on.  This sometimes helps to get /dev/raw1394 loaded correctly, or at least that's been my experience.  Then make sure that this:
```
ls -al /dev/raw1394
```includes 'root audio' in its report and not 'root root'.  Also make sure that
```
groups
```includes 'audio' in its report.

Then, fire up Jack Control on the 'firewire' driver, and post whatever it serves up in the messages window.  Who knows?  maybe something useful will happen.

From your /cat/proc/interrupts you posted earlier, your onboard sound card (hda_intel) is on a different irq than your firewire controller, so that shouldn't cause any problems.  Your firewire card is sharing its irq with a usb hub though, so it would be good to make sure nothing is plugged in there.

I am seriously gonna have to do a fresh install of 10.10 Ubuntu Studio and see if I can figure out better what is going on here.

---

### Post by Bi11yy on 2010-11-06
> **trulan said:**
> I would let it plugged in (especially if you're on the old stack - man this is getting confusing!  Sorry...).  I would set things up for the old stack (everybody's going to be a lot more familiar with troubleshooting that) and reboot with the Saffire plugged in and turned on.  This sometimes helps to get /dev/raw1394 loaded correctly, or at least that's been my experience.  Then make sure that this:
```
ls -al /dev/raw1394
```includes 'root audio' in its report and not 'root root'.  Also make sure that
```
groups
```includes 'audio' in its report.

Then, fire up Jack Control on the 'firewire' driver, and post whatever it serves up in the messages window.  Who knows?  maybe something useful will happen.

From your /cat/proc/interrupts you posted earlier, your onboard sound card (hda_intel) is on a different irq than your firewire controller, so that shouldn't cause any problems.  Your firewire card is sharing its irq with a usb hub though, so it would be good to make sure nothing is plugged in there.

I am seriously gonna have to do a fresh install of 10.10 Ubuntu Studio and see if I can figure out better what is going on here.

I got it! Woooooooo!. I got it, I got, yeah bitch I got IT! I got, yeah, I'm crying now... lol!
Finally!

 EDIT: Lol, I forgot to say what I did, and frankly, thats cause I have no idea. I just kept messing around with the conf file, double checking to make I did all the steps right, and I guess I finally got it right. Talk about confusing!!!



I GOT IT!! FINALLY! Wooooo!

---

### Post by Bi11yy on 2010-11-06
Aw damn, got happy too early. I saw the status led's change and figured all was good (when status leds on Saffires panel change from orange to green it means the device is working.) I didn't put music through it yet. My prob now seems I don't know what to choose to get audio through the Saffire. The FFADO mixer panel  shows all my levels up, and same on the front of the device, levels up, so i should hearing something playing through vlc, but cant.  What do I need to configure now?

 EDIT: Ok
I got Hydrogen to plays some beats, so I know sound is working. But how do I get to hear vlc playing?

---

### Post by AutoStatic on 2010-11-07
Install the vlc-plugin-jack package.
And cool that it's working now!

And I always power on my FireWire soundcards before booting, not necessary though. When the device has trouble coming up you can always try a **ffado-test BusReset** and try starting JACK again.

---

### Post by trulan on 2010-11-07
...and I would definitely open Patchage so you can get a better picture of how things are being connected in the Jack audio chain, if you're not hearing anything that will let you see why.

Good job on hanging in there and getting it working.  It's not supposed to be this confusing...I'll try to work at the how-to wiki over the next few days so maybe others can be spared some of the grief you experienced.:)

Oh, FWIW, I have found it necessary when daisychaining my firepods to power them up before booting.  When running just one it doesn't matter, but getting two of them to sync up is a different story.  Also it seems to be necessary to boot up at least once with the device on when setting up a new system - I have no idea why.

---

### Post by Bi11yy on 2010-11-07
Thanks guys. Ya'll are awesome! 
 Ok, i got JACK for vlc, installed and set vlc to use JACK but still having problems. I just cant hear it. checked all my levels made sure everything's up so i can hear, all's good there. Jacks started, running fine. I seem to be missing something.

 Also, the config I'm using isn't exactly the config I want to use. I would rather have my onboard audio take care of menial audio tasks like system sounds and mp3s and such, routing that audio through my Saffire on one channel and Ardour and Hydrogen through another channel. Is this routing setup possible? I dont see anyway to rout by channel in Ardour or Hydrogen, everything just uses JACK, but no specific channel.
 I'll keep working with it, see what happens. Man now if I could only get Ableton through Ubuntu, I would be set!

---

### Post by Bi11yy on 2010-11-07
Jesus, its pretty amazing what you gotta go through to get stuff to work in Linux! I got vlc to work now, yay me, but its using JACK and I really want to know how to get my onboard to talk to my Saffire. Post em if you got em!

---

### Post by fatwilly6 on 2010-11-08
> **Bi11yy said:**
> Lol, I forgot to say what I did, and frankly, thats cause I have no idea. I just kept messing around with the conf file, double checking to make I did all the steps right, and I guess I finally got it right. Talk about confusing!!!
 My experience with this problem & my Saffire LE mirrors that of Bi11y. I have found that it will only work with the old stack & even then is somewhat temperamental. I have been unable to get much other than Hydrogen to make a noise through the Saffire headphone outputs despite connecting 'everything to everything' in Patchage. I have a PCi Creative Soundblaster installed & on board audio disabled and would like to use that for audio output and the Saffire for Midi & Audio input but again can't seem to get jack outputs to connect to the Soundblaster while running jack in Firewire mode. Also in Patchage the Midi connections for the Saffire are red not green & won't seem to allow any connections at all! I have about a dozen synth ptogrammes installed but not got a peep out of a single one yet whether I am running jack in firewire or alsa mode with either the Saffire or Soundblaster midi inputs . . It's a steep learning curve & thanks to all those who have helped . . I am determined not to go back to Windows & my hooky Cubase . . .

---

### Post by AutoStatic on 2010-11-08
> **Bi11yy said:**
>  Also, the config I'm using isn't exactly the config I want to use. I would rather have my onboard audio take care of menial audio tasks like system sounds and mp3s and such, routing that audio through my Saffire on one channel and Ardour and Hydrogen through another channel. Is this routing setup possible?So you want to use your onboard card for mp3's and system sounds and route that to one channel of your Saffire?

---

### Post by AutoStatic on 2010-11-08
And to use your onboard card and the Saffire at the same time you will need the **alsa_in** and **alsa_out** tools as FFADO doesn't use ALSA as it's driver backend.

---

### Post by fatwilly6 on 2010-11-08
> **AutoStatic said:**
> And to use your onboard card and the Saffire at the same time you will need the **alsa_in** and **alsa_out** tools as FFADO doesn't use ALSA as it's driver backend.
So to be clear these are tools to get jack in firewire mode to talk to alsa devices thru patchage??

---

### Post by trulan on 2010-11-08
To solve the red vs. green midi boxes issue, you need to have a2jmidid running.  It should be installed already if you are using Studio - just open a terminal and enter a2jmidid, and let the terminal open.  There are ways to automate this too but I usually just run it in a terminal.

---

### Post by AutoStatic on 2010-11-08
> **fatwilly6 said:**
> So to be clear these are tools to get jack in firewire mode to talk to alsa devices thru patchage??Yes. Check **[man alsa_in]("http://manpages.ubuntu.com/manpages/lucid/man1/alsa_in.1.html")** and [http://trac.jackaudio.org/wiki/WalkThrough/User/AlsaInOut](http://trac.jackaudio.org/wiki/WalkThrough/User/AlsaInOut). And with Patchage you can indeed connect anything to these alsa devices.

---

### Post by Bi11yy on 2010-11-09
> **AutoStatic said:**
> And to use your onboard card and the Saffire at the same time you will need the **alsa_in** and **alsa_out** tools as FFADO doesn't use ALSA as it's driver backend.
Nah, actually what I did was, just use PulseAudio and manually route the digital output of my onboard to my Saffire. Bam! It's the way I have it setup in Windows, works but there is one shitty aspect: for some reason PulseAudio sums up left and right channels to my right speaker, so I get zero stereo image, just two channels playing! I have to turn one input channel down on the Saffire to get equal volume, but the stereo image is gone. Sucks, but I'm trying to get that worked out.

Other than that, thanks for all your help, you and Trulan were awesome! As it turns out, I was the one screwing things up, as when I reinstalled UbStu to replicate what I did, I found that UbStu was set properly for my Saffire, I don't think I ever started JACK (which I didn't realize I had to, why isn't it enabled to start by default??), and therefore thought my setup was broken! Of course the self-help webpages didn't help, because they were mainly outdated using methods that relied on the old FW stack, which I had no clue of either, and started using old methods to correct that which was already fine! Seems to be common in the world of Linux, with so many distros, theres lots of info but most of it is outdated, with no frame of reference as to which version the help applies to. Sucks.

---

### Post by Bi11yy on 2010-11-09
> **fatwilly6 said:**
> So to be clear these are tools to get jack in firewire mode to talk to alsa devices thru patchage??
 Before you start patching with Patchage or even making connections with JACK, try routing you out of your onboard to your Saffire, and make sure your Saffire is being used only by your music programs, and your mp3's and systems sounds should be using your onboard through PulseAudio. Its works almost perfect for me (PulseAudio isn't exactly perfect, neither is JACK!)
 Also, JACK does work well with our Saffires RIGHT OUT A FRESH INSTALL (not yelling just making point!). You literally just need to set JACK up right (On JACK's 'settings' tab, RealTime checked, priority between 50-70, frames/period at 128, 44.1k, and 2-3 periods/Buffer. Interface at default, 6 input channels, 6 outputs. If i noted a range, I'm still experimenting, but it works at either. My latency is 5.78-8.71, which isn't exactly spectacular, but as I said I'm still experimenting. Also on the 'Misc' tab, check anything that applies to JACK starting when you boot) and reboot. JACK doesn't always start at boot, I'm not sure why, but when it does, its great feeling!
 If you don't have a fresh install, I recommend starting over, re-installing, and once its finished, set up JACK, then reboot, if JACK doesn't start, start it manually. It should 'click', lights go green and you're good to go!

 I'm not sure if Autostatic means to route your onboard internally using ALSA or JACK, I'm not that advanced, but I know routing manually (with cable) works!

---

### Post by orionhedges on 2010-11-09
Am also having issues with saffire LE.  As per the posts above I have identified that my version (10.04) is loading the old stack.  Which doesn't work.

How do I diable the old stack and enable the new one?

also when I load the ffado mixer it says "can't establish any connection to the dbus service of FFADO"

any thoughts on these issues would be appreciated.

---

### Post by AutoStatic on 2010-11-09
> **orionhedges said:**
> Am also having issues with saffire LE.  As per the posts above I have identified that my version (10.04) is loading the old stack.  Which doesn't work.It does :)

> **orionhedges said:**
> How do I diable the old stack and enable the new one?You don't need to disable the old stack. Besides, 10.04 comes with a version of FFADO that doesn't support the new stack.

> **orionhedges said:**
> also when I load the ffado mixer it says "can't establish any connection to the dbus service of FFADO"That is probably because your card is not being recognized, did you go go through the steps mentioned here: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire) ?

Best,

Jeremy

---

### Post by trulan on 2010-11-09
> **AutoStatic said:**
> Did you go go through the steps mentioned here: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire) ?
I took some time this evening to add a section to this wiki with some (hopefully helpful) information on the firewire stacks and the surrounding confusion.  Take a look at it and let me know if anything is misleading or missing.

Thanks,
Trulan

---

### Post by mango42 on 2010-11-11
Grateful thanks, **trulan** - it's my firewire 'bible', despite the inevitable confusion amongst UbuntuStudio versions :KS

I feel a Saffire connection coming on, *real soon now* ;-)

---

