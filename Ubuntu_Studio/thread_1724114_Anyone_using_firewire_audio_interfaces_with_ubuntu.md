---
title: "Anyone using firewire audio interfaces with ubuntu?"
date: 2011-04-07
forum: Ubuntu Studio
---

### Post by Olivier 22 on 2011-04-07
I'm curious about which audio interfaces,software etc work with ubuntu. Firewire,USB PCI?

---

### Post by AutoStatic on 2011-04-08
Yes, I use FireWire audio devices with Ubuntu.

Best,

Jeremy

---

### Post by Olivier 22 on 2011-04-08
> **AutoStatic said:**
> Yes, I use FireWire audio devices with Ubuntu.

Best,

Jeremy

Really? Which one? I haven't made the change to Ubuntu studio yet, I'm using Ubuntu.
I'm using Focusrite Liquid Mix and Saffire Liquid Saffire 56  with Windows and  Mac.
The standard Ubuntu does not recognize these.

---

### Post by AutoStatic on 2011-04-08
> **Olivier 22 said:**
> Really? Which one?Focsurite Saffire Pro 10 IO, Focusrite Saffire Pro 40 and Focusrite Saffire Pro 24.

> **Olivier 22 said:**
> I'm using Focusrite Liquid Mix and Saffire Liquid Saffire 56  with Windows and  Mac.
The standard Ubuntu does not recognize these.Ubuntu Studio probably won't recognize them either: [http://www.ffado.org/?q=devicesupport%2Flist&filter0=focusrite&filter1=&op2=OR](http://www.ffado.org/?q=devicesupport%2Flist&filter0=focusrite&filter1=&op2=OR)

Best,

Jeremy

---

### Post by Olivier 22 on 2011-04-08
> **AutoStatic said:**
> Focsurite Saffire Pro 10 IO, Focusrite Saffire Pro 40 and Focusrite Saffire Pro 24.

Ubuntu Studio probably won't recognize them either: [http://www.ffado.org/?q=devicesupport%2Flist&filter0=focusrite&filter1=&op2=OR](http://www.ffado.org/?q=devicesupport%2Flist&filter0=focusrite&filter1=&op2=OR)

Best,

Jeremy

Thanks,

It's a shame really it's a stable OS.

---

### Post by swedstal on 2011-04-08
Yeah. I'm using the Phonic Helix Board 18 MkII which is a firewire interface. I believe most of the boards in this line will work with UbuntuStudio. I have had my share of troubles with Ubuntu (I actually can't even connect to my wireless right now) but this interface was a snap to get functioning.

---

### Post by Olivier 22 on 2011-04-08
> **swedstal said:**
> Yeah. I'm using the Phonic Helix Board 18 MkII which is a firewire interface. I believe most of the boards in this line will work with UbuntuStudio. I have had my share of troubles with Ubuntu (I actually can't even connect to my wireless right now) but this interface was a snap to get functioning.The Phonic Helix has amazingly stable drivers,I even had mine working with the dreaded sis MB chip. I used to own one before I got my Focusrite.

---

### Post by bluesscream on 2011-04-08
I'm using edirol fa101, very linux-ubuntu-studio-ffado-jack compatible, but it's no longer available from the main dealers here in Germany

---

### Post by AutoStatic on 2011-04-09
> **Olivier 22 said:**
> It's a shame really it's a stable OS.Yes, but there are simply too little people with the devices you own that have ever considered using Ubuntu or Linux in general. So maybe it's an idea to post some reply on the FFADO site about these devices and getting them to work on Linux. Focusrite is a very Linux friendly company namely. If enough people with Saffire 56's or Liquid Mix's post on the FFADO site asking for support Focusrite might consider providing the FFADO devs these devices.

Best,

Jeremy

---

### Post by Olivier 22 on 2011-04-09
> **AutoStatic said:**
> Yes, but there are simply too little people with the devices you own that have ever considered using Ubuntu or Linux in general. So maybe it's an idea to post some reply on the FFADO site about these devices and getting them to work on Linux. Focusrite is a very Linux friendly company namely. If enough people with Saffire 56's or Liquid Mix's post on the FFADO site asking for support Focusrite might consider providing the FFADO devs these devices.

Best,

Jeremy
Yes that's a good idea for the hardware. The other thing is the software. I use Reason/Record which I love and Cubase for mixing and editing.Also I'm using a Boss GT 10 for all of my guitar work and it has a software that can be used also and a M Audio Ozone and Trigger Finger for my midi stuff.

It wasn't that long ago that it was a real challenge to do anything with computer recording. The computers were too slow, the drivers and OS too unstable and all kinds of hardware and  software compatibility issues. Now most of those issues have been ironed out with PC's and Macs but in a perfect world I would be able to use Linux for all of my musical projects.

I'm really impressed with Linux but still at beginner's level with it. It reminds me of a Mac without the huge price tag. You can put together a quad core Intel system like mine for pretty cheap vs a new Mac.

---

### Post by rusk911 on 2011-04-09
I read that ffado temporary not works with new kernel. They said that we should use rt kernel, which contains old firewire stack.

I may be wrong, I haven't fw device.

---

### Post by AutoStatic on 2011-04-10
> **rusk911 said:**
> I may be wrong, I haven't fw device.Then don't post confusing information like this ;)
True, there was an issue with DICE-based devices (like the newer Focusrite Saffire Pro devices) and the new JuJu FireWire stack, they could record fine but playback didn't work. That has been solved about two or three weeks ago. All other FireWire devices worked just fine with the new stack.

Best,

Jeremy

---

### Post by kayosiii on 2011-04-10
> **rusk911 said:**
> I read that ffado temporary not works with new kernel. They said that we should use rt kernel, which contains old firewire stack.

I may be wrong, I haven't fw device.

I do - there was an issue with 11.04 - there still are some. Basically RT was screwed due to some kernel options that were enabled. The LowLatency variant of the kernel doesn't have these limitations. However I could not get jackd to run in RT mode with the firewire interface (I could get it to work with the alsa back end). I then switched to using jackdbus and that seemed to work - though It may just be that an update fixed my problems in the meantime.

Long story short I have a firewire soundcard working fairly well with Kubuntu 11.04. If only i could reliably get the card to reliably survive session start and get flash and miro to route to the right soundcard I would say perfectly.

---

### Post by AutoStatic on 2011-04-11
> **kayosiii said:**
> I do - there was an issue with 11.04 - there still are some. Basically RT was screwed due to some kernel options that were enabled.Which has nothing to do with FireWire but everything with the cgroups stuff: [http://jackaudio.org/linux_group_sched](http://jackaudio.org/linux_group_sched)

Best,

Jeremy

---

### Post by kayosiii on 2011-04-11
> **AutoStatic said:**
> Which has nothing to do with FireWire but everything with the cgroups stuff: [http://jackaudio.org/linux_group_sched](http://jackaudio.org/linux_group_sched)

Best,

Jeremy

Yeah, I am on the LAU and LAD mailing lists :) - sorry I wasn't clear about that. I was having an additional issue which was just with the firewire drivers the alsa backend was letting me run realtime and the firewire driver was not. Not sure what that was about but everything is working for me now.

---

### Post by matthewearl on 2011-04-27
> **AutoStatic said:**
> Then don't post confusing information like this ;)
True, there was an issue with DICE-based devices (like the newer Focusrite Saffire Pro devices) and the new JuJu FireWire stack, they could record fine but playback didn't work. That has been solved about two or three weeks ago. All other FireWire devices worked just fine with the new stack.

Best,

Jeremy

i been looking all over to get my saffire pro 24 to work with us 10.10.  if these issues have been fixed is it just a package update that needs to be done, or is ffado svn action need to happen?

TIA

---

### Post by paneo on 2011-07-02
> **AutoStatic said:**
> Then don't post confusing information like this ;)
True, there was an issue with DICE-based devices (like the newer Focusrite Saffire Pro devices) and the new JuJu FireWire stack, they could record fine but playback didn't work. That has been solved about two or three weeks ago. All other FireWire devices worked just fine with the new stack.

Best,

Jeremy

I can't playback with my Saffire Pro 40.

---

