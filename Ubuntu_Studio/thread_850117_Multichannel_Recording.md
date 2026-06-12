---
title: "Multichannel Recording"
date: 2008-07-05
forum: Ubuntu Studio
---

### Post by lexen on 2008-07-05
Hello, I am looking for a way to record audio in multiple channels, preferably using the mic and line-in inputs simultaneously.  I have heard that this may be impossible, so is there a way to use two audio cards, or maybe a USB device that works well in Hardy?

     I could really use any help I can get.  The way I am getting two tracks is by using the mic input and splitting it so I can plug two things into it and utilize the stereo track.  I would love to find a solution like that to get me more then two tracks.



Thanks,
Lexen

---

### Post by edm1 on 2008-07-05
Best thing will be to buy a new audio interface. [=perfect"]These firewire devices]("http://www.ffado.org/?q=devicesupport%2Flist&filter0=&filter1=&op2=OR&filter2[) are currently fully supported. To see what USB soundcards are supported go to the ALSA website. My recommendation would be one of the edirol or echo devices on the page i linked to.

---

### Post by lexen on 2008-07-05
Thanks for the reply.  I would really rather use a USB device.  I couldn't find a list of supported USB devices, but if I did, would audacity work with it?  Is there a device that you would recommend?



Thanks again,
Lexen

---

### Post by edm1 on 2008-07-06
I cant recommend a device as i've never tried any usb ones. Yes audacity would work but i would recommend looking at Ardour as it has many more features and a nicer interface.

---

### Post by eldragon on 2008-07-06
for multitrack audio processing, you should check ardour

its open source too, kinda like protools. but with source code too.

---

### Post by Capoeira on 2008-07-12
> **lexen said:**
> Hello, I am looking for a way to record audio in multiple channels, preferably using the mic and line-in inputs simultaneously.  I have heard that this may be impossible, so is there a way to use two audio cards, or maybe a USB device that works well in Hardy?

     I could really use any help I can get.  The way I am getting two tracks is by using the mic input and splitting it so I can plug two things into it and utilize the stereo track.  I would love to find a solution like that to get me more then two tracks.



Thanks,
Lexen

well u can use two audio-cards and record in two programs simultaneously. for example: ardour and audacity

---

### Post by lexen on 2008-07-13
> well u can use two audio-cards and record in two programs simultaneously. for example: ardour and audacity 

I thought about that, but would the audio line up?  I know when I try recording audio and video separate, there are little hick ups that make the two grow more and more out of sink.  I'll try it and see what happens though.  Thanks.

---

### Post by thorgal on 2008-07-13
unless you can sync the two cards, this is not a good idea. They have two different internal clocks. If one card can take over the clocking of the other, then it's a possibility. You will need to link the cards externally. But it depends whether they support this operation.

---

