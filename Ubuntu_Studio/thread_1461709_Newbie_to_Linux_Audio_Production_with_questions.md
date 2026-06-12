---
title: "Newbie to Linux Audio Production with questions"
date: 2010-04-24
forum: Ubuntu Studio
---

### Post by isaacj87 on 2010-04-24
Hello all,

First off, let me preface this by saying I'm not new to Linux or audio production, but what I did with Windows is amateurish at best. Back in the day (I say it as if I'm so old), my friends and I would record some of our stuff and it came out fairly decent. We managed some pretty good rough demos.

I've finally got everything working decently. I have my Lexicon Alpha running through Jack/Ardour and I'm busily trying to learn Ardour. However, I have some newbish questions.

1) I'm actually running a RT kernel on OpenSUSE 11.2. I'm not familiar with RT kernels and I'm wondering such thing as: Is using an RT kernel safe for everyday use? Do RT kernels cause damage to CPUs?

2) In Ardour (2.8.7), how do I do a simple overdub? I'm laid down one track and foolish assumed that I could just add another track, arm it, and then record. But, it would seem I'm not getting any sound and if I am, it's extremely quiet.

3) My current latency with JACK is 23.2 ms. I'm assuming that's not very good. I should be somewhere less than 10, correct?

Thank you in advance for any responses. Happy recording all!

---

### Post by AutoStatic on 2010-04-24
Hello isaacj87,

> **isaacj87 said:**
> 1) I'm actually running a RT kernel on OpenSUSE 11.2. I'm not familiar with RT kernels and I'm wondering such thing as: Is using an RT kernel safe for everyday use? Do RT kernels cause damage to CPUs?Yes. No.

> **isaacj87 said:**
> 2) In Ardour (2.8.7), how do I do a simple overdub? I'm laid down one track and foolish assumed that I could just add another track, arm it, and then record. But, it would seem I'm not getting any sound and if I am, it's extremely quiet.I don't use Ardour, so can't help you with that unfortunately.

> **isaacj87 said:**
> 3) My current latency with JACK is 23.2 ms. I'm assuming that's not very good. I should be somewhere less than 10, correct?That should be possible, but I'm not very familiar with your soundcard. What kind of card is it?

---

### Post by isaacj87 on 2010-04-24
> **AutoStatic said:**
> Hello isaacj87,

Yes. No.

I don't use Ardour, so can't help you with that unfortunately.

That should be possible, but I'm not very familiar with your soundcard. What kind of card is it?

AutoStatic,

Hey man, seen you around the forums with some good advice. Good to have you here. :)

I have a Lexicon Alpha. It's a USB Audio Interface. More details here: [http://www.lexiconpro.com/product.php?id=7]("http://www.lexiconpro.com/product.php?id=7")

---

### Post by AutoStatic on 2010-04-24
> **isaacj87 said:**
> Hey man, seen you around the forums with some good advice. Good to have you here. :)Thanks!

> **isaacj87 said:**
> I have a Lexicon Alpha. It's a USB Audio Interface. More details here: [http://www.lexiconpro.com/product.php?id=7]("http://www.lexiconpro.com/product.php?id=7")Looks good! Devices like this should be able to run at latencies way below 10ms. The minimum latency of my Edirol UA-25 is 2ms. What are your current JACK settings? And USB1.1 audio devices prefer latencies that are rounded which you can achieve with a sample rate of 48Khz and a periods/buffer of 3.
But if you want to run it stable (as in practically no xruns) with a latency below 10ms I think you need a RT kernel and maybe some extra tweaking.

---

### Post by Pablo_F on 2010-04-24
>  Originally Posted by isaacj87  View Post
2) In Ardour (2.8.7), how do I do a simple overdub? I'm laid down one track and foolish assumed that I could just add another track, arm it, and then record. But, it would seem I'm not getting any sound and if I am, it's extremely quiet.

¿Have you connected the audio source to the input of the new track? You can do this in the Mixer, in the track/bus inspector or even in the connections window if qjackctl. 
A trick you can use is moving the recorded region to another track by dragging the region with the mouse, with the button 2 pressed (middle button). This way the recorded region does not move in the timeline and you use the first track again to overdub, as you already have the right connection.
A weird thing you might encounter:
When you try to mute a track, it will probably not mute at all. Right click in the mute button, there are 4 different points for muting and they are not marked by default.

Cheers! Pablo

---

### Post by isaacj87 on 2010-04-24
> **Pablo_F said:**
> ¿Have you connected the audio source to the input of the new track? You can do this in the Mixer, in the track/bus inspector or even in the connections window if qjackctl. 
A trick you can use is moving the recorded region to another track by dragging the region with the mouse, with the button 2 pressed (middle button). This way the recorded region does not move in the timeline and you use the first track again to overdub, as you already have the right connection.
A weird thing you might encounter:
When you try to mute a track, it will probably not mute at all. Right click in the mute button, there are 4 different points for muting and they are not marked by default.

Cheers! Pablo

Thanks Pablo, I managed to get it working. With Linux, I'm getting some of the best recordings I have ever gotten. Eat your heart out Windows and Mac!

---

### Post by isaacj87 on 2010-04-26
> **AutoStatic said:**
> Thanks!

Looks good! Devices like this should be able to run at latencies way below 10ms. The minimum latency of my Edirol UA-25 is 2ms. What are your current JACK settings? And USB1.1 audio devices prefer latencies that are rounded which you can achieve with a sample rate of 48Khz and a periods/buffer of 3.
But if you want to run it stable (as in practically no xruns) with a latency below 10ms I think you need a RT kernel and maybe some extra tweaking.

AutoStatic,

I've posted a screenie of my current config. 23 ms, ouch. Any ideas on getting a better setup?

---

### Post by AutoStatic on 2010-04-26
This is what I use with my USB soundcard:
Frames/Period: 64
Sample Rate: 48000
Periods/Buffer: 3

This should get you a latency of 4ms. If JACK won't start, please post what JACK outputs in the Messages window. If you get a lot of xruns try raising the Frames/Period.
And could you also post the outcome of **lsusb** and **cat /proc/interrupts** with the Lexicon attached?

---

### Post by isaacj87 on 2010-04-27
> **AutoStatic said:**
> This is what I use with my USB soundcard:
Frames/Period: 64
Sample Rate: 48000
Periods/Buffer: 3

This should get you a latency of 4ms. If JACK won't start, please post what JACK outputs in the Messages window. If you get a lot of xruns try raising the Frames/Period.
And could you also post the outcome of **lsusb** and **cat /proc/interrupts** with the Lexicon attached?

I've tried what you suggested. I get terrible xruns and it cracks and skips a lot.

Here's my output of lsusb:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 13b1:000d Linksys WUSB54G Wireless Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1532:000d Razer USA, Ltd 
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 004: ID 1210:000a  

```

cat /proc/interrupts:

```
  CPU0       CPU1       
  0:        168          7    XT-PIC-XT        timer
  1:          0          2   IO-APIC-edge      i8042
  4:          0          2   IO-APIC-edge    
  7:          7         36   IO-APIC-edge      parport0
  8:          0          4   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 16:          0     414846   IO-APIC-fasteoi   nvidia
 20:    3680509        120   IO-APIC-fasteoi   ohci_hcd:usb2
 21:     156900      25848   IO-APIC-fasteoi   sata_nv
 22:     522345       1166   IO-APIC-fasteoi   ehci_hcd:usb1
 23:     112973        646   IO-APIC-fasteoi   sata_nv, HDA Intel
 27:          0          2   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:    2478928    2822179   Local timer interrupts
SPU:          0          0   Spurious interrupts
CNT:          0          0   Performance counter interrupts
PND:          0          0   Performance pending work
RES:     220675     713713   Rescheduling interrupts
CAL:        834        929   Function call interrupts
TLB:       4376       5757   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:         25         25   Machine check polls
ERR:          1
MIS:          0

```

uname -a: 

```
Linux linux-7r6j 2.6.31-rc8-rt9-3-rt #1 SMP PREEMPT RT 2009-09-03 21:06:06 +0200 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by rlameiro on 2010-04-27
try to bump up the frames to 128, maybe your device cant communicate good. also, you may have a lot of things on the same usb ub
try it without the wireless adapter. I had, sometime ago, a problem like yours, when i had connected a bluetooth dongle, maybe they shared the same USB lane. You are talking about fast data transmission, and you cant afford to lose packetes in the middle, hence the XRUNS. avoid using usb stuff connected and see if it helps

---

### Post by isaacj87 on 2010-04-27
> **rlameiro said:**
> try to bump up the frames to 128, maybe your device cant communicate good. also, you may have a lot of things on the same usb ub
try it without the wireless adapter. I had, sometime ago, a problem like yours, when i had connected a bluetooth dongle, maybe they shared the same USB lane. You are talking about fast data transmission, and you cant afford to lose packetes in the middle, hence the XRUNS. avoid using usb stuff connected and see if it helps

Thanks for the tips, but unfortunately, I wasn't able to make anything better by removing USB devices. 

A question however...In a best case scenario with a latency under 10 ms, does one still get the occasional xrun from time to time? Or do people have setups that are completely xrun free?

---

### Post by AutoStatic on 2010-04-28
> **isaacj87 said:**
> Thanks for the tips, but unfortunately, I wasn't able to make anything better by removing USB devices.I guess the device with ID 1210:000a is the Lexicon. You only have two USB busses though and it's a bit crowded. With the help of lsusb you should be able to 'free' one of the busses so that your Lexicon sits alone on its own bus.
And another thing: what kind of USB cable are you using? Decent cables can make such a difference. 

> **isaacj87 said:**
> A question however...In a best case scenario with a latency under 10 ms, does one still get the occasional xrun from time to time? Or do people have setups that are completely xrun free?I barely encounter xruns, even if I run my USB Edirol UA-25 at a 2ms latency. Of course I can't do any heavy realtime effect processing, then I do get xruns. But with the settings I've mentioned above I have a pretty stable setup. And if I do encounter xruns then I raise the number of frames like rlameiro already suggested.

---

### Post by isaacj87 on 2010-04-28
> **AutoStatic said:**
> I guess the device with ID 1210:000a is the Lexicon. You only have two USB busses though and it's a bit crowded. With the help of lsusb you should be able to 'free' one of the busses so that your Lexicon sits alone on its own bus.
And another thing: what kind of USB cable are you using? Decent cables can make such a difference. 

I barely encounter xruns, even if I run my USB Edirol UA-25 at a 2ms latency. Of course I can't do any heavy realtime effect processing, then I do get xruns. But with the settings I've mentioned above I have a pretty stable setup. And if I do encounter xruns then I raise the number of frames like rlameiro already suggested.

WOW. What a difference that made! I swapped the original cable for my Lexicon and tried using a printer cable (USB 2.0) and I'm not getting any xruns on 128/3/44100. Isn't my Lexicon a USB 1.1 though? Does the Lexicon Alpha actually utilize USB 2.0 in Linux?

**EDIT:** I just read up on my manual and it says the Lexicon Alpha supports USB 2.0, but does it actually use it?

---

### Post by AutoStatic on 2010-04-28
USB2 has a higher bandwidth so the USB2 cables need better shielding. USB1.1 devices like your Lexicon benefit from that also, sending audio data pretty much maxes out the available bandwidth for USB1.1. And the Lexicon can be hooked up to USB2 ports, it supports that, I think that is what the manual is trying to say.

---

