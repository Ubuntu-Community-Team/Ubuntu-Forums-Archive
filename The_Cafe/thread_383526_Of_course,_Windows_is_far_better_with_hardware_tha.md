---
title: "Of course, Windows is far better with hardware than Linux..."
date: 2007-03-13
forum: The Cafe
---

### Post by darrenm on 2007-03-13
Windows supports all the new hardware properly because the manufacturers provide drivers and Linux developers have to reverse engineer everything and work from patchy specs.

Thats why on my laptop I can't get Bluetooth to work in Windows XP stably using the correct drivers to connect to my Nokia 6280 for dial-up networking but in Feisty I just edited a couple of files and it just works and is stable.

As of Feisty I declare that Ubuntu really really rocks.

---

### Post by tribaal on 2007-03-13
Didn't have the courage to install Feisty on my laptop (where my only bluetooth adapter lies), but your post makes me want to try :)

Nice to hear it works out so well :)

- trib'

---

### Post by darrenm on 2007-03-13
Do it! :D Power management ALL works, Wifi with network-manager works brilliantly, CPU stepping works perfectly. I'm very happy :D

---

### Post by Lord Illidan on 2007-03-13
Is network-manager out of the box with Feisty? I hear it wasn't in Edgy, right?

---

### Post by darrenm on 2007-03-13
It wasn't installed by default in Edgy. It is now 0.7 in Feisty which supports roaming and works better than I ever imagined. pam-keyring really helps too ;)

---

### Post by Quillz on 2007-03-13
> **tribaal said:**
> Didn't have the courage to install Feisty on my laptop (where my only bluetooth adapter lies), but your post makes me want to try :)

Nice to hear it works out so well :)

- trib'
Even builds as early as Herd 4 have been very stable for me. I use it on a virtual machine and nothing has crashed.

---

### Post by Lord Illidan on 2007-03-13
Does it work with broadcom wifi?

---

### Post by maniacmusician on 2007-03-13
> **Lord Illidan said:**
> Does it work with broadcom wifi?
now, now, that's like asking for miracles :)

I highly doubt it. When I installed Herd4 (on my main computer, no less), I had to use ndiswrapper for my broadcom card.

---

### Post by compiledkernel on 2007-03-13
The Idea that Windows has more driver support than Linux is kind of a catch22. There is a ton of older hardware that linux supports that builds like xp and vista wont know what to do with. Most of this stuff is enterprise level equipment (backup tape drives,etc). But I feel that consumer hardware is pretty much neck and neck. And really, does Microsoft support those drivers out of the box? no. The manufacturer supplies the drivers. 

Its more a matter of getting OEMs to build proper drivers (and it would even be better if they developed open drivers, but that might be a pipe dream).

---

### Post by Mateo on 2007-03-13
Shouldn't this probably be moved?  If someone started a thread critical of Linux hardware support it would definitely be moved to the "Desktop readiness thread".

---

### Post by prizrak on 2007-03-13
I started off with Herd 2 and haven't had a single issue. 
darrenm,
How did you get DUN working, I got BT working but when I try to find my laptop with my cell it says "service not supported".
> Shouldn't this probably be moved? If someone started a thread critical of Linux hardware support it would definitely be moved to the "Desktop readiness thread".
It's exactly where it belongs, if people criticize Linux for not working with Broadcom Wi-Fi that would be a pointless and useless waste of kilobytes. Since it's not something Linux (Ubuntu) can do anything about. Maybe this should be in the Testimonials section if anything but definetly not "Desktop readiness"

---

### Post by karellen on 2007-03-13
my oldy configuration (p4 at 2.4 512 md ddram 60 gb ide hdd)  is perfectly supported by ubuntu...an by any other major distro like opensuse or fedora :D

---

### Post by darrenm on 2007-03-13
> **prizrak said:**
> I started off with Herd 2 and haven't had a single issue. 
darrenm,
How did you get DUN working, I got BT working but when I try to find my laptop with my cell it says "service not supported".


Used this howto as reference [http://www.ubuntuforums.org/showthread.php?t=316517&highlight=bluetooth+modem](http://www.ubuntuforums.org/showthread.php?t=316517&highlight=bluetooth+modem) 

The main steps I remember doing were installing some Bluez stuff, running hcitool scan and pairing the device by editing /etc/bluetooth/rfcomm.conf. I managed to pair it to the laptop fine but I think it needs gnome-bluetooth installed (you need the bluetooth icon in the notifications area)

---

### Post by H.E. Pennypacker on 2007-03-13
> **maniacmusician said:**
> now, now, that's like asking for miracles :)

I highly doubt it. When I installed Herd4 (on my main computer, no less), I had to use ndiswrapper for my broadcom card.

LOL....everyone hates Broadcom.

---

### Post by darrenm on 2007-03-13
> **maniacmusician said:**
> now, now, that's like asking for miracles :)

I highly doubt it. When I installed Herd4 (on my main computer, no less), I had to use ndiswrapper for my broadcom card.

As I understand it, everything but the BCM4318 is supported by the bcm43xx module using firmware extracted by bcm43xx-fwcutter (which when installed downloads the firmware for you.) If you have a BCM4318 you have to use ndiswrapper. Everyone should just ditch their Broadcom rubbish and get an Intel adapter (like I have ;) ).

---

### Post by Lord Illidan on 2007-03-13
I'm not criticizing Linux...If anything, I would criticize Broadcom, but it affects me as I sometimes like to use a live Cd on my uncle's laptop...and the wifi never works. Everything else does, though. I think I could get it working through ndiswrapper, however.

---

### Post by maniacmusician on 2007-03-13
> **Lord Illidan said:**
> I'm not criticizing Linux...If anything, I would criticize Broadcom, but it affects me as I sometimes like to use a live Cd on my uncle's laptop...and the wifi never works. Everything else does, though. I think I could get it working through ndiswrapper, however.
yeah, it's pretty easy after you've done it a few times. I've had to use ndiswrapper every single time, so I'm well used to it. I can do it in under 5 minutes because I've got the whole process memorized, it's ridiculous. 

@darrenm: I understood that I'd have more limitations with bcm43xx-fwcutter. I'm actually not really sure if I have BCM4318; how do I check again?

and I would love to get an Intel adapter, but I just bought the PCI wireless cards last year (before I started using Linux all the time) and I'd hate for them to have to go to waste

---

### Post by prizrak on 2007-03-13
darrenm,
Thanks, doesn't seem to work for the Verizon castrated E815 but was a good place to start either way.
Actually I believe that Broadcom will work with the new Wi-Fi subsystem that is actually part of Ubuntu's kernel tree. So perhaps Feisty+1 will be incorporating out of the box Broadcom support.

---

### Post by darrenm on 2007-03-13
```
lspci | grep Broad
```

Prizrak - I think the problem is still the firmware. Its Broadcoms IP and very dodgy ground for Ubuntu to ship by default.

---

### Post by prizrak on 2007-03-13
> **darrenm said:**
> ```
lspci | grep Broad
```

Prizrak - I think the problem is still the firmware. Its Broadcoms IP and very dodgy ground for Ubuntu to ship by default.

Don't you just hate it when legal issues get in the way of progress?

---

### Post by maniacmusician on 2007-03-13
> **darrenm said:**
> ```
lspci | grep Broad
```

Prizrak - I think the problem is still the firmware. Its Broadcoms IP and very dodgy ground for Ubuntu to ship by default.
hmm, I have 4306

---

### Post by DoctorMO on 2007-03-13
> I understood that I'd have more limitations with bcm43xx-fwcutter. I'm actually not really sure if I have BCM4318; how do I check again?

Do I have to remind you to use dohickey, that should tell you at least the lspci name :-P

---

### Post by hardyn on 2007-03-13
Does broadcome sell a cheap wifi chipset? 

it seems that they are the most common wireless chipset in 'commercial' notebooks (hp/compaq, toshiba etc.)  where you start to see more intel used in higher end notebooks (dell, ibm, quanta based (sys76, asus , seager etc)).

---

### Post by prizrak on 2007-03-13
> **hardyn said:**
> Does broadcome sell a cheap wifi chipset? 

it seems that they are the most common wireless chipset in 'commercial' notebooks (hp/compaq, toshiba etc.)  where you start to see more intel used in higher end notebooks (dell, ibm, quanta based (sys76, asus , seager etc)).
Actually in my experience non Intel based laptops tend to have Bcom and Intels normally use Intel wi-fi. Dell is pretty much the only exception I know of.

---

### Post by %hMa@?b&lt;C on 2007-03-13
my bluetooth usb dongle works perfectly with edgy.

---

### Post by darrenm on 2007-03-14
> **prizrak said:**
> Actually in my experience non Intel based laptops tend to have Bcom and Intels normally use Intel wi-fi. Dell is pretty much the only exception I know of.

And my Lenovo was Broadcom by default. 4319 I think. Its now sitting in a drawer at home. I would sell it on eBay but I wouldn't get much and I wouldn't want to inflict it on some poor unsuspecting person.

---

### Post by prizrak on 2007-03-14
> **darrenm said:**
> And my Lenovo was Broadcom by default. 4319 I think. Its now sitting in a drawer at home. I would sell it on eBay but I wouldn't get much and I wouldn't want to inflict it on some poor unsuspecting person.

That's weird I always thought Lenovo's were Linux friendly, or was it before they got the Thinkpad brand? If you have no need for the lappy and don't feel like selling, see if you can donate it somewhere. Schools tend to need hardware all the time, maybe an orphanage so that the kids may play some silly games.

---

### Post by 3rdalbum on 2007-03-14
And open-source software is buggier and less polished than proprietry software - that's why a Windows flight game I bought the other day keeps crashing and freezing up the controls, and I never get a crash out of Flight Gear.

---

### Post by DoctorMO on 2007-03-14
> And open-source software is buggier and less polished than proprietry software - that's why a Windows flight game I bought the other day keeps crashing and freezing up the controls, and I never get a crash out of Flight Gear.

No they usualy are more polished, but what you get after you polish excrement doesn't require a mega brain of Sqanzilla Zeta. most games that have worked their way into open source world the code spends the first few years just being cleaned up because while it may _work_ it certainly is never very good.

---

### Post by darrenm on 2007-03-14
> **prizrak said:**
> That's weird I always thought Lenovo's were Linux friendly, or was it before they got the Thinkpad brand? If you have no need for the lappy and don't feel like selling, see if you can donate it somewhere. Schools tend to need hardware all the time, maybe an orphanage so that the kids may play some silly games.

I meant the Broadcom card is gathering dust ;) I'm still using the Lenovo laptop and loving it. Everything now works on it (except the card reader, looking into that) I think Lenovos are Linux friendly-ish but this is a bottom spec and they save a few quid by putting a Broadcom POS in rather than Intel.

---

### Post by DoctorMO on 2007-03-14
> Broadcom POS

Broadcom do point of sales systems?

> except the card reader

That is odd, normaly they appear on the usb side as usb mass storage devices, is this one pci, ide or some other daft bus?

---

### Post by prizrak on 2007-03-14
> **DoctorMO said:**
> Broadcom do point of sales systems?



That is odd, normaly they appear on the usb side as usb mass storage devices, is this one pci, ide or some other daft bus?

I think he meant a piece of crap (substitute crap with the other word)

Actually the card reader doesn't seem to work on my Acer either. Well last time I tried it, it didn't. I use it all of.... well never really I just tested it once  so I don't care a whole lot. I'm sure if I were into photography it would make a difference but I am not so it doesn't matter.

---

### Post by darrenm on 2007-03-14
Yep. Not Point Of Sale lol.

This is the card reader in lspci -vv:

```
01:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
        Subsystem: Lenovo Unknown device 2079
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 128 (250ns min, 1000ns max), Cache Line Size: 16 bytes
        Interrupt: pin B routed to IRQ 5
        Region 0: Memory at c0000000 (32-bit, non-prefetchable) [size=128]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

01:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
        Subsystem: Lenovo Unknown device 2077
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 128 (8000ns min, 18000ns max), Cache Line Size: 16 bytes
        Interrupt: pin B routed to IRQ 23
        Region 0: Memory at c0000100 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

01:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
        Subsystem: Lenovo Unknown device 2078
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 128 (8000ns min, 18000ns max), Cache Line Size: 16 bytes
        Interrupt: pin B routed to IRQ 5
        Region 0: Memory at c0000200 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

```
But when the card is put in nothing happens, nothing gets logged etc. just strangely a little blip from the HDD. I have a camera that GPhoto supports fine though so its not an issue.

---

### Post by raidlost on 2007-03-14
Second curtian

no luck with the needed server after so many hours
no docs to do the trick
not enough sleep

and my boss walks in with red hat enterprise, now if that is not a hint

my heart goes out to ubuntu so if any one can help soon i might be able
to restore whatever reputation there is 

please check the threads i have

ps sorry for doing this..... you have the highest views

---

