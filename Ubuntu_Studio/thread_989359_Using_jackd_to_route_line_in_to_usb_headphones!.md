---
title: "Using jackd to route line in to usb headphones!"
date: 2008-11-21
forum: Ubuntu Studio
---

### Post by aughmed on 2008-11-21
Hello everyone!

 I have a question about using jackd. I want to be able to route line in from my onboard soundcard to my usb headphones. Is using jackd the way to go or is there another way?? No matter what I do, the sound just gets routed to the output on the onboard. I can hear everything else on the usb headphones. Using Ubuntu 8.10. 
 
   Output from:lsmod|grep snd
snd_usb_audio         107776  2          
snd_usb_lib            27264  1 snd_usb_audio
snd_hwdep              16904  1 snd_usb_audio
snd_hda_intel         489392  5
snd_pcm_oss            52608  0
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  5 snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0
snd_seq_oss            42368  0
snd_seq_midi           15872  0
snd_rawmidi            34176  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  23 snd_usb_audio,snd_hwdep,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
usbcore               175632  9 lirc_mceusb2,snd_usb_audio,snd_usb_lib,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd

( if it helps!! )

        Thanks to all who can help!

---

### Post by thorgal on 2008-11-21
as far as I know, jackd can only handle one device at a time. This may change with jack2.

You maybe have options though :
1- redirect the onboard output (to which you line in input goes) to your USB input

2- use some tools that come with netjack called alsa_in and alsa_out. Find out more here : [http://trac.jackaudio.org/wiki/WalkThrough/User/AlsaInOut](http://trac.jackaudio.org/wiki/WalkThrough/User/AlsaInOut)

I think option 2 is your best bet.

---

### Post by aughmed on 2008-11-21
Thank you thorgal!!! Thats the kind of info I was looking for!!!!!! Option 2 is indeed my best bet. I have no line in on my usb headphones. I'm going to try option 2 right now!!!!!

---

