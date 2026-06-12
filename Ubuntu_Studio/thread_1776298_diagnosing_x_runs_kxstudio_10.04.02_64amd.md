---
title: "diagnosing x runs kxstudio 10.04.02 64amd"
date: 2011-06-05
forum: Ubuntu Studio
---

### Post by ken78724 on 2011-06-05
my asustek PC with kxstudio 10.04.02 often has xruns. A Linux-based system engineer recommends two solutions.

1. see IRQ in /proc/interrupts
2. use HPET as system clock source

IRQ have a various meanings but in this case it means device input/output. you can see IRQ with the command 'cat /proc/interrupts'. Example below,
 
k78724@Kproductions:~$ cat /proc/interrupts
           CPU0       
  0:        181   IO-APIC-edge      timer
  1:        384   IO-APIC-edge      i8042
  4:          2   IO-APIC-edge    
  6:          5   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          1   IO-APIC-edge      rtc0
  9:          0   IO-APIC-fasteoi   acpi
 12:     127749   IO-APIC-edge      i8042
 14:     146139   IO-APIC-edge      ata_piix
 15:          0   IO-APIC-edge      ata_piix
 16:      47177   IO-APIC-fasteoi   i915
 17:         20   IO-APIC-fasteoi   uhci_hcd:usb3
 18:          0   IO-APIC-fasteoi   uhci_hcd:usb4
 19:          0   IO-APIC-fasteoi   uhci_hcd:usb5
 20:     514572   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
 23:     102170   IO-APIC-fasteoi   ata_piix
 42:       1460   PCI-MSI-edge      hda_intel
 43:      65384   PCI-MSI-edge      eth0
NMI:          0   Non-maskable interrupts
LOC:   13636033   Local timer interrupts
SPU:          0   Spurious interrupts
PMI:          0   Performance monitoring interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:         42   Machine check polls
ERR:          0
MIS:          0

can anyone see what causes my xruns from these terminal output? i have no firewire connected. a firewire device is driven by firewire_ohci. is the test responses connected with my USB mouse or keyboard to uhci_hcd:usb5 or uhci_hcd:usb8. I do not know if my xruns are keyboard related, USB device related, the clocksource in my low latency kernel or whatever causes FFADO XRUNs.

xruns may come once or twice daily or every couple of days.

your comments/help will be most appreciated.
Kenneth :popcorn:

---

### Post by jejeman on 2011-06-06
You didn't say what is your jack settings and sound card.

---

### Post by ken78724 on 2011-06-06
> **jejeman said:**
> You didn't say what is your jack settings and sound card.

how do i report those values

---

### Post by cchhrriiss121212 on 2011-06-06
Try this:
```
cat ~/.jackdrc && aplay -l
```

---

### Post by ken78724 on 2011-06-14
> **cchhrriiss121212 said:**
> Try this:
```
cat ~/.jackdrc && aplay -l
```

K78724@Kproductions:~$ cat ~/.jackdrc && aplay -l
/usr/bin/jackd -doss -r44100 -p1024 -n2 -w16
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
thanks cchhrriiss121212

---

### Post by cchhrriiss121212 on 2011-06-15
Is there any reason you use OSS over ALSA?
You could try running jack in synchronous mode, just add an "-S" to the server path in qjackctl setup, like this:
/usr/bin/jackd -S

I think this only works for jack2, I don't know which version you are using.

---

### Post by ken78724 on 2011-06-15
> **cchhrriiss121212 said:**
> Is there any reason you use OSS over ALSA? 

back amidst 9.04 I used OSS and thought I went back to ALSA. Guess it has been there ever since. What must I do to replace OSS with ALSA? 

let me try the gjackctl setup your recommend. I presume this means to open terminal and merely run /usr/bin/jackd -S right? 

Then, how do I verify the jack2 version in my OS? 

Truly, I'm not schooled. 
Many thanks!
Kenneth

---

### Post by ken78724 on 2011-06-15
Hi: 
here's a terminal report
k78724@Kproductions:~$ /usr/bin/jackd -S
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns

usage: jackdmp [ --no-realtime OR -r ]
               [ --realtime OR -R [ --realtime-priority OR -P priority ] ]
      (the two previous arguments are mutually exclusive. The default is --realtime)
               [ --name OR -n server-name ]
               [ --timeout OR -t client-timeout-in-msecs ]
               [ --loopback OR -L loopback-port-number ]
               [ --port-max OR -p maximum-number-of-ports]
               [ --midi OR -X midi-driver ]
               [ --verbose OR -v ]
               [ --clocksource OR -c [ c(ycle) | h(pet) | s(ystem) ]
               [ --replace-registry ]
               [ --silent OR -s ]
               [ --sync OR -S ]
               [ --temporary OR -T ]
               [ --version OR -V ]
         -d backend [ ... backend args ... ]
               Available backends may include: alsa, dummy, freebob, firewire or net

       jackdmp -d backend --help
             to display options for each backend

So, since I see alsa listed, does this remove oss and delete the issues involved? Or, are there several additional steps I need to take?

Kenneth

---

### Post by cchhrriiss121212 on 2011-06-15
You don't need to use the terminal at all if you don't want to, but yes you can start jack that way. The user interface for jack is called qjackctl, which you should see listed in your menu as "JACK Control", and you can set everything up from there.

Once you have it open, click on "setup". Here you can change the driver setting to ALSA (I don't actually know whether this will be an improvement, I've never tried using OSS). You can also add that "-S" option to the "Server Path:" box.

If you open synaptic package manager you can search for jackd, and you will see whether you have jackd1 or jackd2 installed.

---

### Post by ken78724 on 2011-06-15
gotta mention before proceeding, a walked away minutes and came back to an x-run. My immediate response was to go to system app log file viewer and found this: 
Could not open the following files:

/var/log/syslog.0: Error stating file '/var/log/syslog.0': No such file or directory

/var/log/user.log.0: Error stating file '/var/log/user.log.0': No such file or directory

/var/log/daemon.log.0: Error stating file '/var/log/daemon.log.0': No such file or directory

/var/log/messages.0: Error stating file '/var/log/messages.0': No such file or directory

/var/log/kern.log.0: Error stating file '/var/log/kern.log.0': No such file or directory

/var/log/lpr.log.0: Error stating file '/var/log/lpr.log.0': No such file or directory

/var/log/debug.0: Error stating file '/var/log/debug.0': No such file or directory

/var/log/auth.log.0: Error stating file '/var/log/auth.log.0': No such file or directory

Admit, I do not follow what it is I'm to try to do. Is it that Jack Control causes the xruns? 

I'll post this and go back.

---

### Post by akavir on 2011-06-15
Part of your problem with Xruns is probably due to a stock intel sound card it looks like you are using.  Secondly, no matter what hardware you have, you must expect some xruns, but if you are experiencing a lot, then there is a problem.  Are you running any of the optional kernels, like the rt?  Is this a problem that just started occuring, or something that has been going on for some time?  Last thing, try reducing your buffer size in Qjackctl.

The last thing I must ask, is why are you still running 10.04.2?  .3 was released some time ago, and now there's just the repositories that contain a much cooler set of tools, exclusive to KXStudio, that will help you change Jack settings, among other things.

---

### Post by ken78724 on 2011-06-16
Many thanks but I do not follow jack control or qjackctl. If I am not into music productions do I need more than Xjadero 0.6.0~rc7-0, which is video player with JACK sync? 

my synaptic package manager  search for jackd shows I have 
        jackd but not jackd1 or jackd2
        JACK Audio Connection Kit v2 (FFADO backend)
        PulseAudio sound server
        jackd modules for PulseAudio sound server
        jackd modules for PulseAudio sound server debugging symbols
        Xjadero 0.6.0~rc7-0, which is video player with JACK sync

Relative to this, I'm like a noobie in trying to figure where to go.

ken

---

### Post by akavir on 2011-06-16
So than the bigger question is, why are you using kxstudio if not for music production?  What purpose does JACK actually serve for you?

---

### Post by ken78724 on 2011-07-10
cchhrriiss121212, tonight I search for jackd. nothing in the list showed OSS. But, after reading on my question, I'll just accept the xruns I have are not really severe as I grunt about. in time I can probably buy/insert a card that overcomes the problem. C Wilson recommended that alternative when I update falkTX's kxstudio ppas so I'd have kxstudio 10.04.03. am looking at that in another thread. plus, the Texas heat has me saying,,, mellow out. 

thanks for bearing with me. back to this another day.
ken

---

