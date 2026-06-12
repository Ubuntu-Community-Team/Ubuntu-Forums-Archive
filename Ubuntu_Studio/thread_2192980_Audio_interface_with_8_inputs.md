---
title: "Audio interface with 8 inputs"
date: 2013-12-10
forum: Ubuntu Studio
---

### Post by imh on 2013-12-10
Hi, 

I was wondering if anyone could recommend an affordable audio interface that works well with Ubuntu. I record on a cassette 8-track and am looking to dump all 8 tracks at once to Audacity or Ardour (I'm open to using whatever) and keep each track separate in the software. 

Thanks!

---

### Post by codenine75a on 2013-12-10
Easy.  I would use a audio jack converter and maybe a few audio cables from the nearest computer store.  Radio shack may have it all.

---

### Post by imh on 2013-12-10
I'm not sure I understand. Currently, I run the main output on my mixer into the input on my soundcard and mix down to Audacity where I end up with one track for the entire recording. I'd like for each of the 8 tracks to be a separate track in Audacity. Can I do that without buying a new soundcard with 8 inputs? I realize I could run each track individually into Audacity but then I would have to sync them manually and the playback speed on the cassette player can vary.

---

### Post by heldal2 on 2013-12-11
You need to find an 8-channel audio-adapter that works with Ubuntu unless you want to deal with alignment issues if you transfer multiple times with just a few tracks at a time.

Ubuntu-studio, like most Linux-distributions, use ALSA-driver for audio. On the alsa-pages there's a [list]("http://www.alsa-project.org/main/index.php/Matrix:Main") that describe compatibility with various cards.

These days multi-channel adapters are mostly USB attached, and in theory all "class compliant" USB-adapters should work. There's also a lot of firewire-adapters, but that requires specific support for each card in the free FW [driver]("http://www.ffado.org/?q=devicesupport/list") 

Many recent models of multi-channel cards ($500+) have built-in DSP that provide low-latency EQ and basic effects for monitoring. Such functions usually involve the use of proprietary mixing-applications which won't run on Linux. There may be an option to control the built-in mixer with a  tablet but even that usually require an additional win/mac machine as there probably isn't network support in the audio-interface itself and control-signals have to be passed over the same USB-cable as the audio requiring proprietary drivers. Recording mostly involve capture of the raw signal coming from mic/line preamps, but real-time low-latency monitoring is a huge help in the recording process. I have heard good things about Presonus 1818VSL (USB) on linux, but you won't be able to fully utilise all its features on Linux. Nor will you be able to run the included Presonus Studio One DAW.

Beware that many multi-channel units require additional preamp-modules to utilise their full capacity. For example Behringer FCA1616 (~$200) is marketed as a low-cost 16in/16 out card (USB2 and FW400), but only has 4-inputs. Additional inputs are attached through ADAT which will cost $150 upwards for 8 channel-strips. It is reported to work with linux though,

I've been using USB-attached digital mixers (Soundcraft, A&H, Behringer), but that's a more costly solution and primarily targeted at live-use.

The affordable solution is to choose one of the older multi-channel cards that are well supported (see urls above) and look for them in the 2nd hand market. The challenge with older cards is monitoring latency, and/or the lack of DSP for mixing/monitoring EQ/effects in soundcards that do offer pass-through hardware monitoring. Among older cards you'll find the lowest latency on PCI-attached cards, but that require the use of a desktop or server PC.

---

### Post by imh on 2013-12-11
Awesome. Thank you for all the info. I am using a desktop so I think I'll look around for a PCI card. Thanks again :)

---

