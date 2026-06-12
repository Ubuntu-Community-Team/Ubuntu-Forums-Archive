---
title: "USB sound card not detected (Behringer UMA25s)"
date: 2016-03-08
forum: Ubuntu Studio
---

### Post by jet74-5 on 2016-03-08
Hi!

New here at ubuntuforums, please let me know if I do anything I shouldn't. Also not very good at linux or very tech savvy but I try as best as I can.

So, running Ubuntu Studio 14.04 on an old laptop and trying to make it work with a Behringer Midi Controller with integrated sound card (UMA25S). It doesn't. The thing is, it used to work. At some point it stopped working and I am at a loss knowing why and and exactly at what point. 

If I do lsusb i get:

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 007: ID 0451:2036 Texas Instruments, Inc. TUSB2036 Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

The texas instruments is the audio card / controller.

If i do cat /proc/asound/cards i get

 ```

0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf4580000 irq 28
```

This is my onboard sound card.

If I do aplay -l i get:

```

**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: Intel [HDA Intel], enhet 0: AD1981 Analog [AD1981 Analog]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
```

Same thing there, no usb audio.

If I do lsmod | grep snd_usb i get nothing.

So seems pretty hopeless, I guess. But the thing is since it did work at one point I might get it to work again somehow. When it did work, Qjackctl used to give me three options:

Hw0 the onboard intel card 
Hw1 UMA25s
Hw2 USB Audio (or somethig similar)

I never got it to run when I selected Hw1, but it did run when i selected Hw2. Perfectly, I might add.

So this really bugs me. Any ideas? Like I said, I don't know a lot about this just trying to get along with what I can glean from forums.

Thanks in advance,

Erik

---

### Post by jet74-5 on 2016-03-08
Oh yeah,

dmesg gives me the following:

```

[ 4436.488041] usb 3-2: new full-speed USB device number 7 using uhci_hcd
[ 4436.639109] usb 3-2: New USB device found, idVendor=0451, idProduct=2036
[ 4436.639116] usb 3-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[ 4436.639120] usb 3-2: Product: General Purpose USB Hub
[ 4436.646160] hub 3-2:1.0: USB hub found
[ 4436.647164] hub 3-2:1.0: 2 ports detected
```

---

### Post by jejeman on 2016-03-08
Is MIDI part working? Give:
```
amidi -l
```

---

### Post by jet74-5 on 2016-03-15
> **jejeman said:**
> Is MIDI part working? Give:
```
amidi -l
```

Thanks for replying! Unfortunately the output is nothing but:

```
Dir Device    Name
```

Sorry for not getting back to the thread earlier. I have now also tried to replace the USB cable (which I should have tried from the start of course) but nothing there either.

I read somewhere that the generic USB sound driver is in the kernel. Could it be that newer kernel versions don't support the device? 

I hardly know what the kernel is so I must confess that this is just speculation. :confused:

---

### Post by jejeman on 2016-03-15
I doubt new kernel dropped support for the device.
Are you sure that this Texas Instrument device is the soundcard? Looks like an USB hub.

Anyway, run Live CD see if it works. Run, old versions, new...

---

### Post by jet74-5 on 2016-03-15
> **jejeman said:**
> 
Are you sure that this Texas Instrument device is the soundcard? Looks like an USB hub.


Well, the Texas Instruments entry is gone if I disconnect the Behringer, so I guess it must be it right?

---

### Post by jejeman on 2016-03-16
Yes, that is the way to inspect that.
Try the Live CD.

---

### Post by Royke on 2016-03-19
> 
Hw0 the onboard intel card 
Hw1 UMA25s
Hw2 USB Audio (or somethig similar)

The Hw1 is de midi unit of the UMA25s device. For the audiocardfunction: just switch usb ports untill it works. It works out of the box and i have several Behringer devices to prove this. Also you have tha same internal chips as here. Remember also that for a soundcard you need a direct connection with the pc. This way its ID will show. 

Good luck!

---

### Post by jet74-5 on 2016-03-28
Thanks for your replies!

I have tried disconnecting and connecting many times through the various USB-ports. No luck.

I have tried running older versions via LiveCD. Also no luck.

Like Royke says, it should work out of the box. It used to. I'm starting to think that the device is broken.

I'll see if I can make it work on windows. If not, I guess it'll have to go in the bin. Pity, it was really great for the money. But maybe durability wasn't all that good...

Thanks anyway everyone! I'll get back to the thread with any results.

---

### Post by jet74-5 on 2016-09-15
Finally updating!

Hardware was broken so Ubuntu Studio is not to blame. Opening the interface/keyboard there was a distinct smell of cats. :oops: Sorry all, and thanks!

---

