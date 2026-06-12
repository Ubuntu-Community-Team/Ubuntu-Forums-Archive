---
title: "Total newb, struggling..."
date: 2012-08-23
forum: Ubuntu Studio
---

### Post by aidanandrach on 2012-08-23
Tearing my hair out here guys, please help!

Installed UbuntuStudio, all good.  Trying to get a basic Ardour session up and running, not so good.

I have followed the basic tutorial [https://help.ubuntu.com/community/HowToQjackCtlConnections]("here") and can get sound.  Yay. Can also select my external midi keyboard as an input and also get sound.

Two differences I noted (don't know whether this actually matters)
1. My "Midi" tab is empty - no I/O's to speak of
2. I have an "ALSA" tab that is not in the tut.  Selecting my midi I/O's here is what got me sound.

Next, I ran Ardour, dropped in a .wav and can get it to play.  However, the Jack transport control does not want to connect to it.

Finally, and most critically for what I need, I cannot for the life of me get an audio input into Ardour. 

I've googled for numerous Jack and LADI FAQ's etc, but either I'm thick, or they just ain't too well written for a total linux audio neophyte!

Is someone willing to try to walk me through this, either here or via Skype etc?  I'm very keen to get this working, but I'm getting damn close to giving up and going back to Windows for my audio production :-(

Thanks in advance
Aidan

---

### Post by madinc on 2012-08-23
i don't know about ardour but you can make music with LMMS
using a external midi keyboard and it's easy to configure

---

### Post by aidanandrach on 2012-08-23
Thanks madinc - the midi side seems to be working OK for me at the moment (I think).  This is far less critical to my needs than audio however, and that's the bit I'm having little luck with!

---

### Post by Sylos on 2012-08-23
Hello there.

Not sure what you have tried exactly so far but heres what I do.

Once you have jack up and running open your new ardour session.

Create an empty track (not at my machine so not sure exactly what things you click - its the first drop down menu on the left the "add track/bus" or something like that.

Your new track should then show.

Then go brink up the mixer window (I think by default its hidden so you go to Windows > mixer or something similar - its near the Right hand end of the drop down menus.

With the mixer window open you should see your new track. At the top of it will be some buttons - one says "input". Give it a click and you should get a smaller window opens with your options. On the right hand side of this should be any apps you have open that are jack aware and also any instruments that are available. Select your choice then close the window.

After this press the "record" button below the "input" button. Play your instrument - if it worked the level should go up and down showing the signal.

Sorry for the vague guidance/directions but Im at work and cant visualise the windows properly.

Good luck

EDIT: If your using a midi controller keyboard you will need to connect it to a soft synth to generate sound eg Zynnaddsubfx. This would be done in Jack (so midi controller > Zynnaddsubfx. Then you can connect Zynnaddsubfx in Ardour.

---

### Post by aidanandrach on 2012-08-24
Thanks Sylos. It appears that the Jack - Ardour connection is the bit I struggling with. From what. I can tell, Ardour is accessing the sound card directly, rather than via Jack - I have two USB sound cards (both using the USB Generic Audio driver) , one for playback (Alesis monitor speakers connected via USB) and one for recording (Behringer USB audio interface). Ardour is only seeing the speakers...

Of note is that gladish is not seeing anything either, so something is fishy with my Jack I think....

---

### Post by CrocoDuck on 2012-08-24
Hi. Repost the outputs of this:

```
cat /proc/asound/cards 
```and this:

```
cat .jackdrc 
```Can you repost also your speakers and audio interface models?

---

### Post by Sylos on 2012-08-25
In addition to what crocoduck has posted above can you check your ardour settings to make sure its set to use jack and not just alsa.

When you start ardour it should appear in the jack "connections" window if it is using jack. If using alsa it wont.


Cheers

---

### Post by aidanandrach on 2012-08-29
Thanks guys, much appreciated.

```
cat /proc/asound/cards
```

gives me

```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfa200000 irq 46
 1 [CODEC          ]: USB-Audio - USB Audio CODEC
                      Burr-Brown from TI USB Audio CODEC at usb-0000:00:1a.0-1, full speed
 2 [mini           ]: USB-Audio - MPK mini
                      AKAI PROFESSIONAL,LP MPK mini at usb-0000:00:1d.1-1, full speed
 3 [Cable          ]: USB-Audio - USB Midi Cable
                      USB Midi Cable at usb-0000:00:1a.7-6.2, full speed
 4 [CODEC_1        ]: USB-Audio - USB Audio CODEC
                      Burr-Brown from TI USB Audio CODEC at usb-0000:00:1a.7-6.4, full speed

```

```
cat .jackdrc
```

gives

```
/usr/bin/jackd -p 128 -R -P 60 -T -d alsa -n 2 -r 48000 -p 128 -d hw:1,0 
```

- Speakers are Alesis M1Active 520 USB's (I'm guessing that they are item 1 above as they were plugged in at power up).  They are my primary audio out.
- also installed is a Behringer UCA202 (taking a line out from my analog desk) which is my primary audio in. This is most likely to be item 4 above, as it was not plugged in until after power up.
- others (fairly obvious from output) are a generic MIDI-USB cable and an AKAI MPK Mini midi keyboard (via USB)

Will double check the Ardour settings and post back...

Again, thoroughly appreciate the help :-)

---

### Post by aidanandrach on 2012-08-29
Thanks Sylos, yes, Audacity is appearing in the Jack connections window.

---

### Post by Sylos on 2012-08-29
> **aidanandrach said:**
> Thanks Sylos, yes, Audacity is appearing in the Jack connections window.

I thought you were trying to run Ardour not audacity? Is that just a typo above?

Are you still unable to get any instruments through?

Cheers

EDIT: Can you also give the output of "arecord -l".

---

### Post by aidanandrach on 2012-08-29
> **Sylos said:**
> I thought you were trying to run Ardour not audacity? Is that just a typo above?

Are you still unable to get any instruments through?

Cheers

EDIT: Can you also give the output of "arecord -l".

Oops, typo! Definitely Ardour... Midnight here and all powered down - will give this a crack tomorrow and report back...

---

### Post by CrocoDuck on 2012-08-29
> **aidanandrach said:**
> Thanks guys, much appreciated.

```
cat /proc/asound/cards
```gives me

```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfa200000 irq 46
 1 [CODEC          ]: USB-Audio - USB Audio CODEC
                      Burr-Brown from TI USB Audio CODEC at usb-0000:00:1a.0-1, full speed
 2 [mini           ]: USB-Audio - MPK mini
                      AKAI PROFESSIONAL,LP MPK mini at usb-0000:00:1d.1-1, full speed
 3 [Cable          ]: USB-Audio - USB Midi Cable
                      USB Midi Cable at usb-0000:00:1a.7-6.2, full speed
 4 [CODEC_1        ]: USB-Audio - USB Audio CODEC
                      Burr-Brown from TI USB Audio CODEC at usb-0000:00:1a.7-6.4, full speed

``````
cat .jackdrc
```gives

```
/usr/bin/jackd -p 128 -R -P 60 -T -d alsa -n 2 -r 48000 -p 128 -d hw:1,0 
```- Speakers are Alesis M1Active 520 USB's (I'm guessing that they are item 1 above as they were plugged in at power up).  They are my primary audio out.
- also installed is a Behringer UCA202 (taking a line out from my analog desk) which is my primary audio in. This is most likely to be item 4 above, as it was not plugged in until after power up.
- others (fairly obvious from output) are a generic MIDI-USB cable and an AKAI MPK Mini midi keyboard (via USB)

Will double check the Ardour settings and post back...

Again, thoroughly appreciate the help :-)

I think that jack is not setted correctly to use UCA202 as input. Open Qjackctl, go in the setup tab and try to set Input and Output devices parameters. If the item 1 are really the speakers (seems so), have a try by setting the input at voice "USB audio" for hw:4,x (I expect hw:4,0) and the output at voice " USB audio" for hw:1,x (I expect hw:1,0). If this don't works make some test, you'll find the right configuration. Have a look at the voice "Audio" too. Set it as Duplex. Could happen that using different devices for input and output can bring a lot of xruns. If so repost, I have an idea to solve that hypotetical situation.

---

### Post by aidanandrach on 2012-08-29
Thanks CrocoDuck - have set these accordingly, with no change.  Just for kicks, I tried all the other various combinations available to me with no joy either.

It would also seem that now I'm unable to get ANY sound out of my Alesis monitors!  This includes system sounds / Banshee etc...

AND, it appears that on restart, my HW devices have been reassigned, as arecord -l now gives me:

```
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC889A Analog [ALC889A Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 4: CODEC_1 [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

[edit] Have got system sounds again - opened up the myriad of different mixers (why are so many installed by default anyway??) and with one of them - the XFCE Mixer I believe - system sounds came up as soon as I changed to the other USB Codec...  Why it had changed is beyond me...  Still nothing from Ardour however.

---

### Post by jejeman on 2012-08-30
Card are still in same order as far I can see.

---

### Post by CrocoDuck on 2012-08-30
I think is better to test how things works with just a device. Shut down the computer, unplug the speakers and turn on the computer. In Qjackctl's Setup tab set the UCA 202 in **duplex**, use it for both input and output (I'm usually set USBaudio for both input and output to do this). Try to see if you can route, record, and listen. You can test the output with earphones, plug them in the earphones connector in the UCA.  Sometimes, after a reboot, the names for the devices (hw:a,b) are assigned different form the last session.

---

### Post by Sylos on 2012-08-30
Hello. 

Whilst I dont want to confuse things by giving different avenues to pursue from those given by Crocoduck, I do wonder if you could try starting jack with the following command. Its just an amended command based on what you posted above as being in your jackd.rc file. The last parts of it should specify the cards as you want them (assuming hw1 is the monitors and hw4 is the input card).

```
jackd -p 128 -R -P 60 -T -d alsa -n 2 -r 48000 -p 128 -P hw:1,0 -C hw:4,0
```

If you issue the above in a terminal and then start Qjackctl in the normal way it should (in theory) start the server with the cards as you want them.

As an additional point, does anyone think it could cause an issue if the two USB soundcards are on the same USB hub? Could that cause an access problem?

Cheers (sorry if Im muddying the waters)

---

### Post by sgx on 2012-08-30
shouldn't it be -n3 for usb devices?
(the Periods/buffer setting in qjackctl = 3 for usb)

and just using a usb hub could throw in a spanner,
probably best to try without it if possible, let alone
with two devices on it. Power could also be an odd lot with
a hub, and all hubs are not created equal.
Cheers
:popcorn:

---

### Post by CrocoDuck on 2012-08-30
> **Sylos said:**
> 

As an additional point, does anyone think it could cause an issue if the two USB soundcards are on the same USB hub? Could that cause an access problem?

Cheers (sorry if Im muddying the waters)

Probably. If the UCA202 works correctly (maybe we could have some issue generated by the HDAintel to solve) I think is a good idea to behave like this:

When playing-recording: Setup jack to use the UCA202 in duplex, using earphones to monitor and/or connecting the UCA analog stereo output to the stereo input of the Alesis speakers (Notice that jack is not using the internal audio device of speakers now, speakers will amplify the analog signal coming from UCA).

When mixing/mastering: Setup jack to use as "output only" the Alesis internal soundcard, in order to prevent sound distortion and other noisy issues (this should be the default jack configuration posted by aidanandrach).

I Think that hardware is actually working good. We just need to find the proper configuration.

---

### Post by Sylos on 2012-08-30
> **sgx said:**
> shouldn't it be -n3 for usb devices?
(the Periods/buffer setting in qjackctl = 3 for usb)

and just using a usb hub could throw in a spanner,
probably best to try without it if possible, let alone
with two devices on it. Power could also be an odd lot with
a hub, and all hubs are not created equal.
Cheers
:popcorn:

Sorry - I wasnt clear - I was meaning the root hub on the MB (I think thats the right terminology) - The op hasnt mentioned any external hubs. I was just speculating.

Good spot with the periods needing to be 3.

---

### Post by Sylos on 2012-08-30
> **CrocoDuck said:**
> Probably. If the UCA202 works correctly (maybe we could have some issue generated by the HDAintel to solve) I think is a good idea to behave like this:

When playing-recording: Setup jack to use the UCA202 in duplex, using earphones to monitor and/or connecting the UCA analog stereo out to the stereo input of the Alesis speakers (Notice that jack is not using the internal audio device of speakers now).

When mixing/mastering: Setup jack to use as "output only" the Alesis internal soundcard, in order to prevent sound distortion and other issues (this should be the default jack configuration posted by aidanandrach).

I Think that harware is actually working good. We just need to find the proper configuration.

Maybe worth blacklisting snd-hda-intel for testing purposes?

---

### Post by CrocoDuck on 2012-08-30
> **Sylos said:**
> Maybe worth blacklisting snd-hda-intel for testing purposes?

Of course, If UCA202 doesn't work good alone (in my computer UCA202 works very good without needing for blacklisting... I'll try to bump to 3 the periods/buffer:p).

---

