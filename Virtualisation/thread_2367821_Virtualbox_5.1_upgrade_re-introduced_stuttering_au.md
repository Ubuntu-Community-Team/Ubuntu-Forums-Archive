---
title: "Virtualbox 5.1 upgrade re-introduced stuttering audio?"
date: 2017-08-03
forum: Virtualisation
---

### Post by lammert-nijhof on 2017-08-03
I have upgraded Virtualbox from 5.1.18 to 5.1.26 around the same time I have upgraded my CPU from a 2-core AMD Phenom II X2 B59 (3.4GHz) to a 4-core AMD Phenom II X4 B97 (3.2GHz). The result of one of those two upgrades is, that as soon as I use Virtualbox, the music in both the Guests (3 Windows VMs and 7 Linux Distros) and Host system (Ubuntu 16.04) start stuttering. I have to close all VMs to be able to listen to not distorted music. One of the other effects has been that AC97 emulation of Vbox did give a completely terrible result, changing the audio to Intel HD Audio did improve the situation considerably, but occasionally say once per minute it stutters again for a few seconds. I don't have the problem on my laptop, that still runs Vbox 5.1.18 on a 2C/4T Intel 2520M. Both processors run 4 threads, so it does not seem to be a parallel processing issue. 

I have investigated the issue and the same problem has been present in earlier versions of Virtualbox 5.1. They did solve it by going back to the 5.0 audio and re-implemented that in 5.1. Anybody know whether that has been changed again?

For the moment I assume the problem is introduced by the upgrade of Virtualbox, did anybody else notice the same problem? The solution seems clear to me, I have to return to Virtualbox 5.1.18, sorry WRONG SOLUTION. Any other suggestion?

---

### Post by lammert-nijhof on 2017-08-03
I tried going back to Virtualbox 5.1.18, but it did not help. The music on both host and guests still stutters even if I have one VM started running idle. If I close that VM the music on the host sounds OK again. It is an annoying problem, since normally I have one or two VMs active and often I want to play music in the background. In the past I did use Win XP to play my music. 
On my laptop with exactly the same software and VMs installed, everything works fine.

---

### Post by ajgreeny on 2017-08-03
Not seeing the problem here on any of my VMs (Windows and various *ubuntu systems) all running in VBox 5.1.26 on a Xubuntu 16.04-64bit host.

However, I am interested to know why you bother to run a VM, with all the resources it uses, just to play music when you could easily play the music in the background on the host OS; it seems to be very expensive in resource usage terms just to listen to music.

I know this does not solve your current problem but I am simply curious.

---

### Post by lammert-nijhof on 2017-08-03
@ajgreeny: I know, it sounds strange, but I like Windows Media Player with the WOW and TruBass effects. It makes my relatively cheap speakers sound somewhat better. I have 8GB of memory so 1GB for XP and 5% CPU occupation on ONE CPU does not sound as a large sacrifice. But now also the music played by the host stutters, if I have any VM idling.
Back to the issue:
I tried going back to Virtualbox 5.1.18, but it did not help. The music on both host and guests still stutters even if I have one VM started running idle. If I close that VM the music on the host sounds OK again. It is an annoying problem, since normally I have one or two VMs active and often I want to play music in the background.
On my laptop with exactly the same software and VMs installed, everything works fine.

To summarize:
I have upgraded both systems to the same Ubuntu 16.04 version, both run Linux 4.10.0-30. Both run Virtualbox 5.1.18. Rhythmbox (on my host with the AMD Phenom II X4 B97) stutters, as soon as I load one VM. In my i5 2520M I have no stuttering. I even can play the music using a VM like Windows XP. The VMs on both machine are the same, in June I copied the VMs from desktop to laptop. XP and Vista have not been updated at all anymore.

It looks like the problem is related to the combination of Virtualbox and this AMD Phenom II X4 B97 processor, that I installed yesterday. I did not have any problems with the AMD Phenom II X2 B59 in the past. This B97 is recognized by the BIOS, while the previous B59 has not been recognized by the BIOS. The BIOS reported my previous CPU as an unknown 2-core AMD processor, because it has been introduced after the last update of the HP dc5850 BIOS. The 2-core B59 has been working perfectly, but it has half the CPU power of the 4-core B97. I like to stick to the B97, because including transport to the Dominican Republic I paid $50

The AMD desktop audio:
>         *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:f3200000-f3203fff

The Intel laptop audio:
>         *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:41 memory:d4820000-d4823fff

Any ideas? If you think it is related to the audio driver, I could try an old PCI sound card, I have lying around. The motherboard has one classical PCI slot.

---

### Post by lammert-nijhof on 2017-08-03
The AMD desktop audio shows > configuration: driver=snd_hda_intel latency=32
I looked in 'Pulseaudio Volume Control' in the 'Output Devices' tab. I pressed advanced settings and that displayed the Latency and it was showing 0. Checking lshw again I did see > configuration: driver=snd_hda_intel latency=0 And that solved my problem for 80%. It was by accident, but I'm happy now. I run the VM; Win XP again with WMP, playing a famous Dutch Singer: Andre Hazes :)

The music still halts for some msecs or so, but it does not stutter too much anymore. 
To get it completely stutter-free I have to keep  'Pulseaudio Volume Control' loaded all the time. Sad :(

---

