---
title: "FA-66 configuration won't work"
date: 2012-12-25
forum: Ubuntu Studio
---

### Post by CaseyCaseyCasey on 2012-12-25
Hi

Purchased an Edirol FA-66 about four years ago and have been trying to get it to work on and off since then.  

I have installed Ubuntu Studio recently and checked to see I am part of the Audio group.

In a previous installation of Ubuntu Studio I attempted to remove Pulse Audio with apt-get purge, but the problem of the interface hanging and no audio coming out when it is up persists.  In my current set up I have left Pulse there.

The FA66 works in windows, which to my mind eliminates hardware/cable faults.

Lately, the Message/Status window shows a lot of "D-BUS: JACK Server could not be started." messages.

I'm determined to get this to work, but I just can't see where I'm going wrong.  I've followed a few guides to configuring JACK, and I did ONCE get it to work and play test sounds.  But it stopped working again just as mysteriously.  

What could be the issue?  All other applications work fine on my computer.

---

### Post by jejeman on 2012-12-25
I've bought mine also four years ago, late 2008.

Okay, the card is fully suported by FFADO and it works on my systems. There can be some issues. Lets try to see why is not working.

First, is the firewire card recognized?
Give
```
ls /dev/fw*
```
```
dmesg | grep fw
```

---

### Post by CaseyCaseyCasey on 2012-12-25
Hi jejeman

Thanks for replying, here are the outputs:

fool-fool@foolbox:~$ ls /dev/fw*
/dev/fw0  /dev/fw1  /dev/fw2

fool-fool@foolbox:~$ dmesg | grep fw
[    2.125205] firewire_core 0000:00:07.0: created device fw0: GUID 0011d800004bdf21, S400
[    2.130096] firewire_core 0000:00:07.0: created device fw1: GUID 0040ab0000c34f87, S400
[    2.176137] firewire_core 0000:00:0b.0: created device fw2: GUID 00309500a002a9e4, S400
fool-fool@foolbox:~$

---

### Post by jejeman on 2012-12-26
That looks okay
give
```
lsb_release -drc
```Just to see what you have installed.
```
lsmod | grep fire
```
It seams that you have 2 firewire devices connected, right?

---

### Post by CaseyCaseyCasey on 2012-12-26
yep, 2 Firewire devices.  One is the FA-66 connected to the on-board Firewire port, the other is a PCI Firewire card that gives me 3 more Firewire ports.  

Out:

fool-fool@foolbox:~$ lsb_release -drc
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal

fool-fool@foolbox:~$ lsmod | grep fire
firewire_ohci          40401  0 
firewire_core          64368  11 firewire_ohci
crc_itu_t              12707  1 firewire_core
fool-fool@foolbox:~$

---

### Post by jejeman on 2012-12-26
Aha, you have two firewire controler cards. 
I'm guessing this is the FA-66:  
[ 2.130096] firewire_core 0000:00:07.0: created device fw1: GUID 0040ab0000c34f87, S400
Okay, the new firewire stack is loaded and active, the FA is recognized and registred as /dev/fw1. That should be all fine.
Give
```
cat /proc/interrupts | grep fire
```
Last thing let's see your JACK configuration. This is mine in Qjacktl

---

### Post by CaseyCaseyCasey on 2012-12-26
Sorry about the late reply, I've been trying to get Qjackctl running to the point where I could screen capture the Config settings.  The application isn't even loading it's buttons now and after a while I get a message saying that it isn't responding.

here is the out:

fool-fool@foolbox:~$ cat /proc/interrupts | grep fire
 16:         28       2495   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb7, firewire_ohci, firewire_ohci, 0000:00:09.0
fool-fool@foolbox:~$

---

### Post by jejeman on 2012-12-26
Qjacktl is not needed to run JACK, you can run it from command line, something like
```
/usr/bin/jackd -dfirewire -r48000 -p128 -n3
```
Anyway, it is up to you to figure out, I can only give you my story.

I've purged pulseaudio-jack-sink it tends to bug JACK.
I've turned off pulseaudio, I don't need it, and it can give trouble. You can do it with this command:
```
echo "autospawn = no" > ~/.pulse/client.conf && pulseaudio -k
```
I've turned off JACK Dbus in Qjacktl settings, it tends to bug JACK.

Now, I run FA-66 on three different desktops and one laptop. On desktops I've use Ubuntu Studio 12.04, on laptop a had to use AVLinux because of IRQ issues (VGA card shares same IRQ as firewire controler) and overall laptop strenght.
For those three desktops I've had different experiences. On two it worked fine, even with one that has IRQ issue. On the third one I had following problems: 
- JACK2 bug it self and wont start with firewire
- card won't work if not powered up before OS boots
I've resolved 'em by instaling JACK1 and turning on card before OS boots.

So, here is the summary of my story:
- purged pulseaudio-jack-sink
- turned off pulseaudio
- turned off JACK Dbus
- installed JACK1
- powering up card before OS boots

You can try AVLinux Live and see how it works. It is more optimised (for audio) than UStudio.

p.s.
I've didn't mentioned, but it is obvius that you have to use the same samplerate you have set on the card. ;)

---

### Post by CaseyCaseyCasey on 2012-12-27
Thanks for all your help jejeman, the problem appears to be solved now.

Somehow it relates to that extra Firewire card I have on the PCI slot.  When I unplug the FA-66 from the on-board Firewire port and try it on one of the ports on the PCI card, JACK functions normally.

I'm not at all sure what causes this problem, and I haven't tried the on-board port sans the PCI card, but I will.

---

