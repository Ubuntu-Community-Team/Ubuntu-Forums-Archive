---
title: "Jack makes mad Xruns! &gt;:("
date: 2008-11-17
forum: Ubuntu Studio
---

### Post by mysticofjesus on 2008-11-17
I have all the Ubuntu Studio stuff installed on Ubuntu eee on my Eee PC 1000H. I've got the Realtime kernel, and

```
sudo cat /etc/security/limits.conf
```

does return the lines:

```
@audio - rtprio 99
@audio - nice -10
@audio - memlock 250000
```

But, jack is still making a disgusting number of bad Xruns, the the point that a note from ZynAddSubFX sounds like a cheese grater on concrete.

Does anybody know what's going on?

---

### Post by warbread on 2008-11-18
Do you have realtime enabled in Jackd?

---

### Post by thorgal on 2008-11-18
I vaguely heard on the jackaudio mailing list that this kind of PC suffers from "interference" between RT operations and power management processes or system watchdogs. I can try to copy/paste some relevant messages.

From the jackaudio mailing list :

> 
Jonatan Liljedahl wrote:
> I'm having trouble running jack (0.109.2) on my EeePC, I get periodic
> dropouts, once every 10 seconds or so. It affects both audio and midi.
>
> It's happening both with the internal soundcard (snd-hda-intel) and an
> external (usb audio). It happens even when only Jack and QJackctl is
> running, no other clients. It's running in realtime mode. I've tried
> raising the realtime priority but it doesn't help.
>
> Any ideas?

I found it! Unloading the **iTCO_wdt and iTCO_vendor_support** kernel
modules did the trick.

> What do those modules do (just curious).

It's a driver for intels TCO watchdog timer, which is used to reboot the
system if the watchdog hasn't been fed for N seconds. Quite useless on a
laptop anyway, I guess it's meant for servers and industrial stuff where
one wants the machine to reboot if it hangs.

So, all Eee users out there, put these modules in your modprobe
blacklist and you'll get drop-out-free realtime audio. (They might very
well affect other machines too...)


> On my ubuntu 7.10 machine they are also present, thanks for figuring
> this out.

Unfortunately I might have been too hasty, at the next boot (with the
modules above in my blacklist) I got periodic drop-outs again! :(
It happens at almost exactly 10 sec interval. I'll investigate further..
It's quite frustrating to know that it *can* work glitch-free but not
knowing how or why.

> I never heard about such an error, but because I'm not a fan of CPU
> frequency policy settings for DAWs: Have you checked the CPU speed?

I have no cpu freq manegment modules loaded.

> Is an audio device sharing an IRQ with 10 other devices etc.?

I think so, my /proc/interrupts says

16:       8255   IO-APIC-fasteoi   uhci_hcd:usb4, pciehp, HDA Intel,
i915@pci:0000:00:02.0

But I don't know how to change the IRQ's, there's no BIOS settings for
stuff like that on the Eee.

> Maybe there isn't any bug, but a combination of disadvantageous
> coincidences, that sometimes take effect and sometimes not.

I've found some more: unloading the iTCO_* modules seems to work as long
as you're on AC-power, but on battery the drop-outs are back. But then,
unloading the 'battery' kernel module stops them! (then of course you
can't see the battery status).
So, on my Eee I have 'sudo rmmod battery' in my QjackCtl on-startup
shellscript.

Some onboard ethernet adaptors try and connect to a non-existent
network at regular intervals when they aren't plugged in. I found
this on one of my cheaper motherboards when I noticed it spamming
the syslog at intervals of almost exactly 10 seconds. Could
something like this be the problem?

> Hi Jonatan,
>
> Please, if you finally solve the audio problems, could you explain as
> your experience using this machine for audio/midi?  It's realtime
> capable? Which minimum buffer size can handle without xruns?
>
> In theory this machines are designed to make basic stuff, but as they
> are so light they could be very convenient for musicians in live
> performances.
>
> Regards,
> Jorge
>   

There's a hardware blacklist (Greylist) at
[http://www.64studio.com/node/69](http://www.64studio.com/node/69). To post your experiences there might be
a good idea. I'm only using Linux, unfortunately I get to times hardware
that isn't fine with pro-audio for Linux, even thought I did heavy
research. I can do audio recordings but any MIDI sequencer isn't fine.



---

