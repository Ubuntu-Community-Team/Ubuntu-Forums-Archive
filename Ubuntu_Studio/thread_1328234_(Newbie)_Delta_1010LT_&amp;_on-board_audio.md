---
title: "(Newbie) Delta 1010LT &amp; on-board audio"
date: 2009-11-16
forum: Ubuntu Studio
---

### Post by wofting on 2009-11-16
I made the mistake of recommending Ubuntu Studio 9.10 & Delta 1010LT to a friend without fully researching.  My problem is she wants to be able to use her onboard audio, with her nice Logitech 5.1 speaker system she bought, and the 1010LT which I installed later.

SYSTEM:
AMD Phenom X4 9750 Quad Core Processor - 2.40GHz
Biostar TA790GX 128M Motherboard - AMD 790GX, AM2+ 128MB DDR2 Side-Port, ATI Hybrid, CrossFire, PCIe 2.0, Gigabit, USB2.0, RAID, HDMI/DVI


If I load JACK and set it to all <Default> I only get 2 capture devices but 8 playback.
If I go into setup and make the Input device hw:2 (the delta) and the output device hw:0 (HDA ATI SB ) I get 12 capture & 8 playback.  
my /proc/asound/cards looks like this
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe8f4000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfeae8000 irq 19
 2 [M1010LT        ]: ICE1712 - M Audio Delta 1010LT
                      M Audio Delta 1010LT at 0xe800, irq 21

I can start hydrogen or other apps and get audio out of the speakers through playback1 & 2.  I tried connecting one of the RCA pairs from the 1010LT to my surround system last night and tried every connection in JACK but got no audio.  Before I left my friends place yesterday I was unable to get any input at all (not even the USB Yamaha Keyboard).  I think that in my quest to make this work I have broken it more.

I guess I am looking for a bit of guidance here.  This audio stuff is all new to me but am comfortable with the linux stuff.  A system rebuild a possibility.  I actually wondered about that since I built the system then added the Delta 1010LT later.  Any configs that will help I am happy to provide.

Thank You

(Feeling awful recommending,  $$ spent and not being able to use)

---

### Post by thorgal on 2009-11-16
hi there,

don't worry, this is a fine h/w setup.
All you need is to NOT run jack on 2 different sound cards (-C and -P alsa driver options on two different hw:n)

This is a limitation of jack. 

BUT, and there's a big BUT here, the latest jack (0.118 ) has alsa_in and alsa_out so all your h/w IOs can be visible in one single jack graph.

jack needs to be compiled with libsamplerate so that alsa_in and alsa_out are usable as jack tools.

Try to google a bit about these tools. They are neat and they will serve you right if properly used.

The other thing is: 

jack can use hardware device aliases instead of index (hw:0 or hw:1 can be volatile, if not fixed in some module configuration file, meaning that e.g. hw:0 could be the onboard in one boot session, and the Delta in another). 

It is therefore better to use aliases.

Look at /proc/asound/cards for names and use these names in your jack setup.

I can check tonight at home for the precise syntax.


Oh yeah, by the way, for the 1010LT, you will need envy24control, the dedicated mixer GUI.
You will then be able to use the ADC and DAC faders for each channel, so you can hear something or capture something at some decent level :)

---

