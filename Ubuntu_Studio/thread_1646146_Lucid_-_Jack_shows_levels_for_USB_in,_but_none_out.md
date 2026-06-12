---
title: "Lucid - Jack shows levels for USB in, but none out."
date: 2010-12-15
forum: Ubuntu Studio
---

### Post by SantoPeligro on 2010-12-15
Hi, I've been using Ubuntu based multimedia distros like APODIO for about a year now. Finally, was time to do a clean install and jumped into Ubuntu Studio. To be honest, APODIO, though quirky, involved a lot less setup.

So I've been tweaking away for about a week, finally got Jack cooperating and not crashing. Finally got it to recognize my ART USB Tube Preamp, and register levels in. But the settings Jack requires to show levels for the USB in, no longer produces sound out of my internal soundcard.

This setting is INTERFACE= USB device (either hw:1 or hw:1.0 work) which makes sense that no sound would come out if that were the case, but its the only way it shows levels coming in.

Then,
Input= hw:1
Output= (default)

I've tried lots of different combinations. Realtime has been crashing, so I haven't been using that. Force 16bit doesn't help.

I've tried cranking everything in alsamixer.

What should I do? I'm at a loss.

Is this one of those instances where I have to make Pulseaudio and Jack play nice?

---

### Post by Pablo_F on 2010-12-16
Hi,

You can select the usb interface, then use alsa_out with the onboard. Or use the onboard audio card and use alsa_in with the usb card. 

I will try to explain it more clearly and give you a (hopefully) working solution if you copy here the terminal output of:

arecord -l && aplay -l

Or just take a look at "man alsa_out"

Cheers, Pablo

---

### Post by SantoPeligro on 2010-12-16
output of arecord -l && aplay -l :


**** List of CAPTURE Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 1: Intel ICH - MIC ADC [Intel ICH6 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 2: Intel ICH - MIC2 ADC [Intel ICH6 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 3: Intel ICH - ADC2 [Intel ICH6 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


In this instance, the usb device doesn't seem to show up. And now, since plugging in this command, Jack no longer sees the usb device either, but shows the "new" hw:0,1 hw:0,2 & hw:0,3

Thanks for the help! Though the plot now thickens.

---

### Post by SantoPeligro on 2010-12-16
curiously, switched to a new usb slot, and now is recognized.

New printout:

**** List of CAPTURE Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 1: Intel ICH - MIC ADC [Intel ICH6 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 2: Intel ICH - MIC2 ADC [Intel ICH6 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 3: Intel ICH - ADC2 [Intel ICH6 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
saintdanger@ubuntuskull:~$ arecord -l && aplay -l
**** List of CAPTURE Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 1: Intel ICH - MIC ADC [Intel ICH6 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 2: Intel ICH - MIC2 ADC [Intel ICH6 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 3: Intel ICH - ADC2 [Intel ICH6 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I'll be trying swapping out usb slots, and see if I can get a proper 2-way connection with jack.

Thanks

---

### Post by Pablo_F on 2010-12-17
Hi, 

Using card names instead of numbers is recommended (note that this needs writing down the names instead of selecting options from the drop down menu). In your case, you have two cards:

hw:ICH6  (the onboard one)
hw:default   (not to be confused with (default), the USB one)


You can try using one device for capture and another one for playback. 

For example: 

Input device: hw:default,0 (or just hw.default).
Output device: hw:ICH6,0  (or just hw:ICH6).

However, a better idea might be using one only interface in jack, and use alsa_out for the other. So you leave input and output devices as (default) and write down "hw:default" (without the quotes) in the interface field. Once jack is up and running you can use something like:

alsa_out -jonboard -dhw:ICH6,0

Then connect the apps (or system: captures if you just want to route sound from the usb input to the onboard outputs) that make sound to "onboard: playbacks" rather than to "system: playbacks". Use patchage or the connection window of qjackctl.

Cheers, Pablo

---

### Post by SantoPeligro on 2010-12-17
WOW! Thanks Pablo!

I started tinkering around with the alsa_in/out last night, and sure enough, it works GREAT! In fact for some reason, I was unable to use the RT-kernel UNTIL I routed the the output through alsa_out.

This I just kind of did without entering the NAMES of cards, just hw:0 etc. Does it just run more smoothly if I used the full name?

I'll also play around with entering the full name in qjackctl, however, I'm very happy with how alsa_out workaround panned out.

Can't believe alsa in/out slipped by me!

Thanks again!

---

### Post by Pablo_F on 2010-12-17
Cool!

Entering the card names is better because card numbers are not consistent in different reboots. Even if, usually, the onboard will be hw:0, this is not guaranteed. Your case is even worse, as you explained that the usb card is not always seen by alsa, depending on the USB socket you plug it. 

alsa_in and alsa_out are great!  Thanks Torben Hohn =D>

---

