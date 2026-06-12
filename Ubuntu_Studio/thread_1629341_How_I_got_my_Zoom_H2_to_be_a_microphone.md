---
title: "How I got my Zoom H2 to be a microphone"
date: 2010-11-23
forum: Ubuntu Studio
---

### Post by hsweet on 2010-11-23
(This is in Kxstudio, but should be the same in Ubuntu Studio.)

I have a Zoom H2 which can be set up as a high quality computer mic.  Nothing I tried quite worked until today.  

First I ran ```
arecord -l
``` which showed me my capture devices
```

**** List of CAPTURE Hardware Devices ****                                                                                                                                            
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]                                                                                                                    
  Subdevices: 0/1                                                     
  Subdevice #0: subdevice #0                                                                                                                                                          
card 0: Intel [HDA Intel], device 2: ALC888 Analog [ALC888 Analog]                                                                                                                    
  Subdevices: 1/1                                                                                                                                                                     
  Subdevice #0: subdevice #0
card 1: H2 [H2], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

So with my Zoom plugged in and set as recording device, it shows up as Device 1:0 while my sound card is Device 0

Then, in qjackctrl I set my Input Device to be hw:1,0

Confusingly, Jack showed my H2  as hw:1, which it is, but I was confused by that.

Anyhow, it makes a fantastic mic and saved me having to go out and spend more $.

---

### Post by JC Cheloven on 2010-11-26
That's cool! 
Just a question: the H2 has 4 mic heads. Did you find a way to stream them independently to the computer? I mean, to separate tracks in ardour or whatever.

---

### Post by rjdaggett on 2011-03-25
The hardware only allows :front 90 deg , rear 120 deg, or 2ch surround (one of each) stereo.

---

