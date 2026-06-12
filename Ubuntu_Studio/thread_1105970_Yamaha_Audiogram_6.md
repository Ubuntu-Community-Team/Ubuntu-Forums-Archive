---
title: "Yamaha Audiogram 6"
date: 2009-03-25
forum: Ubuntu Studio
---

### Post by wstout on 2009-03-25
Just wondering if anyone has tried the Yamaha Audiogram 6. Here is a link [http://pro-audio.musiciansfriend.com/product/Yamaha-Audiogram-6-Computer-Recording-System?sku=703328](http://pro-audio.musiciansfriend.com/product/Yamaha-Audiogram-6-Computer-Recording-System?sku=703328) This looks like it would work well for me but I can't seem to find anything in the line of Linux support. I know with several items like that they have suprised me and just worked but before I fork over the $150 bucks I wouldnt' care to know for sure if anyone has any experience.

---

### Post by Stochastic on 2009-03-26
Well according to alsa-project.org, many of Yamaha's USB soundcards are supported: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Yamaha](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Yamaha)

But the Audiogram 6 is not listed, so you can't really be sure.  I'd say either make sure the store you buy it from has a good return policy, phone Yamaha and ask (even if alsa supports it, they'll probably say no, but it's always good to ask them), or find a different card that is officially supported.

If you do end up getting the Audiogram 6 please make sure to report your results to alsa-project.org so that others don't have to go through a trial/error process.

---

### Post by wstout on 2009-03-27
Yeah I checked the alsa page first, but noticed a lot of yamaha stuff is supported I may give it a try. Its a nice looking unit for the money.

---

### Post by b100dian on 2009-04-07
> **wstout said:**
> Yeah I checked the alsa page first, but noticed a lot of yamaha stuff is supported I may give it a try. Its a nice looking unit for the money.

So how was it? does it work? (I hope so)

I plan to get one too, and found this thread:)

---

### Post by heminder on 2009-07-03
yeah, i'd like to know, too...

---

### Post by xeromx on 2009-09-16
Me too

---

### Post by hardcopy on 2009-12-11
anyone tried this yet?

looks like a nice interface

---

### Post by AutoStatic on 2009-12-11
According to the [manual]("http://www2.yamaha.co.jp/manual/pdf/emi/english/xg/audiogram6_en_om_b0.pdf") it's a class compliant device (i.e. for both Mac and Windows no extra drivers are needed) so _in theory_ it should work out of the box.

---

### Post by psiborg999 on 2010-07-04
The device works FLAWLESSLY in Audacity under UBUNTU 10.04 LTS.... Just plug it in, reboot the machine, open Audacity and enable the DEVICE TOOLBAR.  It will be visible as a USB Audio Device.  ENJOY!  :)

---

### Post by xwindowsfan on 2011-01-26
i am considering the Yamaha Audiogram 3 or 6.
especially if it's plug and play out of the box.
i tried Line6 Studio UX1 with no success.
i assume since it was detected as a usb device it is compatible with ubuntu and jackd.
i would also like to know if its compatible with Fedora.

which one to pick though. 
the 6 has more knobs and more inputs, but is it more machine?
i like how they both have line outs.
however the inputs on the 6 are all stereo would i be able to stick a single cable from a guitar into just one side?
any suggestions are appreciated.

---

### Post by xwindowsfan on 2011-03-02
i can confirm Yamaha Audiogram 6 is plug and play, out of the box, no driver install whatever in both ubuntu studio 10.04 and Fedora 14.

it shows in sound preferences under hardware as USB Audio CODEC, as well as under jackd inputs.

i have used it successfully with modeling software and vst plugins.

the usb connection is perfect, however the line-outs had noise in the output when connected to the line-in of the audio card.

any of the stereo inputs easily accept the mono input for a guitar with active pickups. although the point is moot

the controls are very subtle and very good (almost too subtle). unless the guitar is run through a DI box and then to the Mic imput of the Audiogram.  the control settings such as comp and gain then become much more vibrant  especialy the phantom power.

Awesome, awesome sound.

the Audiogram 6 itself has a good weight to it. seems solid and well built. definitely a piece of machine.
the buttons and knobs i confirm are a lil on the cheap side.

---

### Post by stephenstop on 2011-07-29
> **xwindowsfan said:**
> i can confirm Yamaha Audiogram 6 is plug and play, out of the box, no driver install whatever in both ubuntu studio 10.04 and Fedora 14.

it shows in sound preferences under hardware as USB Audio CODEC, as well as under jackd inputs.

i have used it successfully with modeling software and vst plugins.

the usb connection is perfect, however the line-outs had noise in the output when connected to the line-in of the audio card.

any of the stereo inputs easily accept the mono input for a guitar with active pickups. although the point is moot

the controls are very subtle and very good (almost too subtle). unless the guitar is run through a DI box and then to the Mic imput of the Audiogram.  the control settings such as comp and gain then become much more vibrant  especialy the phantom power.

Awesome, awesome sound.

the Audiogram 6 itself has a good weight to it. seems solid and well built. definitely a piece of machine.
the buttons and knobs i confirm are a lil on the cheap side.
hey man dont know if youll get this hope so,I was thinking of getting a yamaha audiogram because i run guitars into my powered mixer but i cant get good sounds into my comp,but you said noise is a problem from the line outs which is where u run your sound into your comnput3er right?what kinda sound?is it from too loud of volume.Is it worth the price?Thanks

---

### Post by sgx on 2011-07-30
Hi, you need a preamp, like this

[http://www.musiciansfriend.com/pro-audio/m-audio-audio-buddy-2-channel-preamp](http://www.musiciansfriend.com/pro-audio/m-audio-audio-buddy-2-channel-preamp)

[http://www.musiciansfriend.com/pro-audio/presonus-tubepre-microphone-preamp](http://www.musiciansfriend.com/pro-audio/presonus-tubepre-microphone-preamp)

or any dedicated guitar interface that sends proper signal levels.

I have A Fender Mustang usb amp that sends a pristine usb signal to
linux fx, or it's line-out/headphone-out combo jack sends a slightly
hotter signal, to the soundcard line-in, and uses the amps hardware volume control, both sound excellent.

[http://www.musiciansfriend.com/guitars/fender-mustang-i-20w-1x8-guitar-combo-amp/h61791000001000](http://www.musiciansfriend.com/guitars/fender-mustang-i-20w-1x8-guitar-combo-amp/h61791000001000)

Cheers

---

### Post by xwindowsfan on 2011-07-31
it could have been the sound card I had the stereo output connected to. it could have been my ubuntu configuration. it could have been the 'Y' cable I was using (2 1/4" to mini 1/8"). it could have had something to do with mono input - stereo output. but just remember Audiograms primary connection to pc is USB. also, according to the manual the stereo outputs are for powered speakers not a connection to a soundcard. I suggest downloading a copy of the manual to become more familar with the layout.

as far as the noise, i can't remember exactly what it was. lil pops, maybe a lil hiss. it was not 100% clean and that's bad. of course it was only the sound output, I did not test if it comes through a recording.

I have recently upgraded my pc, and switched Linux distros' as well. so I will test it out again in the next few days as I have yet to do that with my current setup. I really believe it was more of a problem with my configuration not the fault of the Audiogram. as it is a nice lil piece of equipment.

best wishes

---

### Post by xwindowsfan on 2011-08-14
I'm sorry I have not had time yet to test it, but I still will.

will post results.

---

### Post by xwindowsfan on 2011-11-29
> **stephenstop said:**
> hey man dont know if youll get this hope so,I was thinking of getting a yamaha audiogram because i run guitars into my powered mixer but i cant get good sounds into my comp,but you said noise is a problem from the line outs which is where u run your sound into your comnput3er right?what kinda sound?is it from too loud of volume.Is it worth the price?Thanks

I have since tested the Audiogram line outputs. with the Y cable I was able to go through the stereo output but not through the mono outputs. as a note: you still have to have the USB cable connected to "power" the unit. with the USB connections I get x-runs but I have not tested with a RT Kernel. however with the stereo output run through an Asus Xonar ST line-in there was no extra noise interference, no hiccups, and the overall output was stronger. I set Jack to use the sound card as both output/input and can switch between USB and line-in.

forgive me for the extremely late response, I have been busy. perhaps this will help others as well. as far as inexpensive interfaces the audiogram is still first rate.

---

### Post by qwentin355 on 2012-01-06
Here' the deal, I've tried the Audiogram6 on ubuntu studio 10.04, and it is recognized and able to record into audacity, and so far I've only got it to record in audacity, now if you want it to play music from your computer into your headphones, this involves work that I cannot do, but if you simply want to monitor your self while recording, it works fine for that, but playback I have to do from the on board sound card, but vocals and guitar and electric violin and piano all record well on it with not hassle, but I repeat, playback is something that I cannot get working, If someone has figured this out please help me because I want to keep this device and linux.

---

### Post by qwentin355 on 2012-01-06
I take it back, I got it working, I don't know what I changed but it just up and worked after I unplugged my headphones and plugged them back in, don't ask me it doesn't make sense, It works great.

---

### Post by sgx on 2012-01-07
Are they usb headphones? usb devices can swap IDs when various items are hotplugged, or the system is rebooted with things in different usb slots.
Look at the qjackctl wiki for links 4 and 8, to configure jackd, and qjackctl.
The screenshots are a big help. Youtube videos for ardour, hydrogen,
zynaddsubfx, rakarrack, often cover basic qjackctl connections, so
you will be able to record with many other softwares in addition to audacity. Install ladspa, and select sound in audacity, like word processing, the the effects menu comes alive, and you can some schmalz
to your recordings.

timemachine is good for live recording, with sound routed through fx like
rakarrack, guitarix2, calf-plugins etc  all set up with qjackctl
virtual in/out cables. Audacity imports the default .w64 extension files

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)
produced by timemachine, and exports in the other common formats.
Cheers

---

### Post by Dagon^ on 2013-03-08
I own a Yamaha Audiogram 3 and I never got it to work under any *nix distro but I might just give it a try again after reading this thread.
I'll report back in a few days!

---

### Post by wildmanne39 on 2013-03-14
Old thread closed!

---

