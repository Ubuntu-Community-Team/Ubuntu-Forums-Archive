---
title: "Audacity--can't overdub with USB mic"
date: 2010-03-10
forum: Ubuntu Studio
---

### Post by agingric on 2010-03-10
hi all,

i am attempting record my guitar playing using audacity.
 
os--karmic (dual boot with windows xp)
computer--gateway mx6027

i can use my logitech usb mic to record a track, but i cannot record another track while listening to the original.

i'm getting a pop up box telling me:

"Latency Correction setting has caused the recorded audio to be hidden before zero.
Audacity has brought it back to start at zero.
You may have to use the Time Shift Tool (<---> or F5) to drag the track to the right place."

audacity works for this purpose just fine in xp, with no tweaking.  i have used audacity for this purpose in the past using intrepid (and possibly jaunty--can't remember) on a different laptop (which is broken).

i really don't have any reason to boot up in xp other than to use audacity.  i would love to learn how to tweak audacity so i can use it in karmic.  

thanks in advance for any help you can give me.

andy g

---

### Post by agingric on 2010-03-20
bump

---

### Post by raboofje on 2010-03-20
> **agingric said:**
> "Latency Correction setting has caused the recorded audio to be hidden before zero.
Audacity has brought it back to start at zero.
You may have to use the Time Shift Tool (<---> or F5) to drag the track to the right place."

And you keep getting this after Audacity set this back to zero?

That's odd. Perhaps find that option and make it positive?

---

### Post by agingric on 2010-03-21
i have previously tried changing those settings, and i don't get the error message.

however, i am still unable to record a new track while listening to a previously recorded one.  

it seems as though it stops recording almost immediately, or perhaps not at all.  i can't tell.

thanks
andy

---

### Post by tgalati4 on 2010-03-21
I presume you are using the real-time kernel in Ubuntu Studio?  Are you using pulseaudio or Jack for your sound framework?

You might turn off pulseaudio and jack and use ALSA alone.  The audio frameworks can cause latency issues.

You can also try a real-time live CD, dynabolic, (dynabolic.org).  It's a lightweight distro designed for live recording.

---

### Post by agingric on 2010-03-21
i don't currently have rt kernel on this machine.  i did previously and that didn't work.  

alsa is used by default.  

ps.  jack will not start either.  

could there be a problem with my sound card driver?   could i type anything in on the command line to investigate?

when booting up the login sounds are present but it seems like they do not quite sound normal (sounds breaks up sometimes).

thanks
andy

---

### Post by tgalati4 on 2010-03-22
USB is not a syncronous protocol.  Can you record with the internal mic?  Check  your interrupts:

cat /proc/interrupts

---

### Post by sgx on 2010-03-22
> **agingric said:**
> i don't currently have rt kernel on this machine.  i did previously and that didn't work.  

alsa is used by default.  

ps.  jack will not start either.  

could there be a problem with my sound card driver?   could i type anything in on the command line to investigate?

when booting up the login sounds are present but it seems like they do not quite sound normal (sounds breaks up sometimes).

thanks
andy
Hi, ART sell a bundle of a nice TubeMP preamp, MXL mic, boom stand and cable for $99,
check major online retailers. This will meet many recording needs. A souncard/interface will be vastly superior to motherboard soundchips, but
$5 dollar adaptors will do in a pinch, when on a budget, to get things rolling.
Cheers

---

### Post by agingric on 2010-03-22
output of  cat /proc/interrupts
is as follows




0:   12135097    XT-PIC-XT        timer
  1:       5047    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:          1    XT-PIC-XT      
  4:          1    XT-PIC-XT      
  5:      85249    XT-PIC-XT        Intel 82801DB-ICH4
  6:          1    XT-PIC-XT      
  7:          1    XT-PIC-XT      
  8:          0    XT-PIC-XT        rtc0
  9:      45497    XT-PIC-XT        acpi
 10:      19734    XT-PIC-XT        ehci_hcd:usb1, ohci1394
 11:    1032718    XT-PIC-XT        uhci_hcd:usb2, uhci_hcd:usb3, i915, tifm_7xx1, mmc0, mmc1, mmc2, yenta, eth0, b43
 12:    2650349    XT-PIC-XT        i8042
 14:      66723    XT-PIC-XT        ata_piix
 15:     426397    XT-PIC-XT        ata_piix
NMI:          0   Non-maskable interrupts
LOC:          0   Local timer interrupts
SPU:          0   Spurious interrupts
CNT:          0   Performance counter interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:        155   Machine check polls
ERR:          0
MIS:          0

i tested the mic input by using a cheap pair of headphones as a substitute mic.  it did work.  however, i don't own a conventional  mic that i could plug in.  all i have is the usb mic. additionally, this did work on another computer in the past. 

i'm very curious as to why this works in windows and not in ubuntu as well.  

thank you all for your replies and any more information that you can give me.

andy g

---

### Post by tgalati4 on 2010-03-22
Iterrupt 11 looks busy.  You have Intel Graphics, USB, ethernet, wireless, and tifm-7xx1.  Is the ti chip part of your sound hardware?  If so, then under Ubuntu too much graphics, USB or network activity will cause interrupts to the soundchip causing latency.

It's possible under Windows that different interrupts are assigned, or are handled differently making duplex recording/monitoring possible.  Graphics in Windows are handled differently as well.  So it's quite possible that something that works well in Windows may not work so well in linux.  Driver issue, perhaps, but also a completely different operating system framework.

Although audacity can handle multitrack recording, it's really not designed as a realtime recorder/monitor.  It works much better doing passive recording then editing/processing later.  You will notice that audacity lags when drawing the waveform--so it's possible that just drawing the sound track causes latency--based on your high interrupt count on 11.

Some ways around this issue is to play your tracks on an mp3 or ipod and use audacity to do a simple track recording.  Then you can play back both tracks, vocal & guitar, and mixdown or process further.  Listening to an external device will have a slightly different clock speed, so don't be surprised if, after a few minutes, you experience some drift.  This can be corrected in audacity, but it's something to pay attention to.

---

### Post by EricLorenz on 2010-03-23
> **tgalati4 said:**
> I presume you are using the real-time kernel in Ubuntu Studio?  Are you using pulseaudio or Jack for your sound framework?

You might turn off pulseaudio and jack and use ALSA alone.  The audio frameworks can cause latency issues.

You can also try a real-time live CD, dynabolic, (dynabolic.org).  It's a lightweight distro designed for live recording.

Slight Correction (as I went looking for dynabolic.org and couldn't find it)...the website is actually dynebolic.org - the software is called dyne:bolic.

On a side note...looks cool- I will be trying it.

Eric

---

### Post by bandolino on 2012-04-16
This is the way I got around the exact same problem, do not use "usb mic" as the input in Audacity, instead go to sound settings, set your default input device as the mic (on my machine it came up as Qui analog dynamic microphone or something like that) adjust the input volume always from there, set the input device in Audacity as "default" and bob's your uncle... hope it works for others too

---

### Post by nothingspecial on 2012-04-16
Please don't bump old threads to the top.

Closed.

---

