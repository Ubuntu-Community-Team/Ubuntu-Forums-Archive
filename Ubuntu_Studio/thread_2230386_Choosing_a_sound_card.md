---
title: "Choosing a sound card"
date: 2014-06-19
forum: Ubuntu Studio
---

### Post by sam271828 on 2014-06-19
Hi all, 

I've been developing some music software that relies on real time MIDI IO, and I'm pretty unhappy with the latency and quality of FluidSynth and TiMidity that I've been experiencing. I think it's time to shell out for a real sound card, but I want to make sure it's 100% compatible with linux (I'm using Ubuntu Studio realtime) before buying anything. Can any of you recommend a good sound card that works without too much hassle? I mostly just want the ability to render high quality piano samples in real-time as I play on my MIDI keyboard. I'm willing to pay a few hundred dollars for it if necessary.

EDIT: I'm working on a desktop so an internal sound card is fine.

Thanks!

Sam

---

### Post by Nistegmos on 2014-06-20
I have had luck in Ubuntu Studio v14.04 LTS with the Alesis M1 Active 320 USB Speakers/Interface.  The system is USB Class Compliant, so it doesn't need drivers installed manually on any system.  The downside is that the interface is only 16-bit and not 24-bit.  It does go up to 48 kHz though.  

I also had good luck using the Alesis Q49 USB MIDI Keyboard which is also USB Class Compliant.  

I think if you go the USB route, as long as it's USB Class Compliant, it should be OK.  

I also have the ZOOM R8 USB MIDI Control Surface/Sampler/Interface and it's card reader component seems USB Class Compliant, but the interface/control surface isn't.  But the 32-bit drivers do install OK into Wine v162 and I had some success using it in REAPER v462 with WASAPI and PulseAudio.  The downside of the R8 is that you have to turn on the Audio Inferface/Control Surface function every time you use it, manually pressing a button on the hardware.  It's not so hard, but I wish it only needed to just be plugged in and on.  Also, on Windows 7 it was a bit slower than the Alesis speakers, even with ASIO4ALL.  But it did work OK.  

There is also the Alesis M1 Active 520 USB Speakers/Interface which are bigger speakers with more bass.  It costs more.  I found the 320s actually to be a bit too boomy until I stuck a sock into each of the acoustic ports on the back.  

Good Luck.  

P.S.-I would probably shy away from M-Audio cards.  I used to use 2 Delta Audiophile 2496 24-bit PCI SoundCards.  They were fabulous in Windows XP, but there's not much support for them in Linux and even where there is support, it's indirect.  Also, even in Windows, they are somewhat tricky to install.  And also AVID/M-Audio has been suffering from decreased tech support over the last few years.  But they do sound good and can get extremely low latency.  I think PCI cards would offer the lowest latency, but if you are a developer, you may want to work with something more mainstream, mainly USB or Firewire interfaces.

---

### Post by eddie5 on 2014-06-22
> IP.S.-I would probably shy away from M-Audio cards.  I used to use 2  Delta Audiophile 2496 24-bit PCI SoundCards.  They were fabulous in  Windows XP, but there's not much support for them in Linux and even  where there is support, it's indirect.  Also, even in Windows, they are  somewhat tricky to install.  And also AVID/M-Audio has been suffering  from decreased tech support over the last few years.  But they do sound  good and can get extremely low latency.  I think PCI cards would offer  the lowest latency, but if you are a developer, you may want to work  with something more mainstream, mainly USB or Firewire interfaces. 		

I have 2Xenvy24 sound cards (M-Audio) i can control them extremely well with Mudita24,input,output and gain are all perfectly controllable.
Got them of Fleabay for peanuts.

---

