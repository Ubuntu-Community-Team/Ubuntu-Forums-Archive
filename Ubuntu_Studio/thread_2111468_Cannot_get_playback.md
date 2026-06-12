---
title: "Cannot get playback"
date: 2013-02-02
forum: Ubuntu Studio
---

### Post by Mick8882003 on 2013-02-02
Hi, I installed ubuntu studio today on my laptop. I am using a fender mustang amplifier that has built in usb, so its a recording interface. I have managed to get Ardour to record from the amp, but for the life of me I cannot get Ardour to play the recorded guitar signal back. I am using 12.10 and just cant get the sound to come out of the speakers.

Help!

---

### Post by jejeman on 2013-02-02
Which speakers?

---

### Post by Mick8882003 on 2013-02-02
Either the laptop speakers or the fender mustang (which I am pretty sure its capable of.)

---

### Post by jejeman on 2013-02-02
For laptop speakers you need to set JACK to use onboard soundcard for output, (and Mustang for input).
Check if you have master out from Ardour connected to system playback.

---

### Post by ttoine on 2013-02-02
You can install and check how ardour is connected with "Patchage".

Toine

---

### Post by Mick8882003 on 2013-02-02
Here are my "connect" settings in qjackctl:

[image]("http://imgur.com/olA24fN")

---

### Post by Mick8882003 on 2013-02-02
Ok, well I worked out that the LT's sound was turned off, jee, So I can now export music to a wav file and then play it after it has been recorded, just cant play it in ardour.

Thanks in advance.

---

### Post by Mick8882003 on 2013-02-03
Now I am even more confused, I set the source in jack to default and in pulse to the usb connection, and I couldn't get sound in. Which controls the input, jack or pulse?

Cheers

---

### Post by lupopa on 2013-02-03
> **Mick8882003 said:**
> Hi, I installed ubuntu studio today on my laptop. I am using a fender mustang amplifier that has built in usb, so its a recording interface. I have managed to get Ardour to record from the amp, but for the life of me I cannot get Ardour to play the recorded guitar signal back. I am using 12.10 and just cant get the sound to come out of the speakers.

Help!
Dit you have no help, i have same Problem and released with this page...

[http://www.linuxjournal.com/content/plug-and-fender-mustang](http://www.linuxjournal.com/content/plug-and-fender-mustang)

Sorry for my bad English, i'm German user...

Hope that is what you need :)

Greetings Lupo

---

### Post by ttoine on 2013-02-03
Two possibilities:
 - you use Pulse Audio only
 - you use Jack, and use the virtual jack sound card in Pulse. Please, install et use Patchage for connecting applications, it is more simple and visual !

If you want to use Ardour, it is better to use only one sound card, or at least the same for input and output.

If you want to use Pulse Audio only, you may try Audacity. It is very useful for one track recording, if it is enough for your need.

---

