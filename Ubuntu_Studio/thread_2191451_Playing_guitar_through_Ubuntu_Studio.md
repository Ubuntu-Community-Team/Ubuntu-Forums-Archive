---
title: "Playing guitar through Ubuntu Studio"
date: 2013-12-02
forum: Ubuntu Studio
---

### Post by artem.morikh on 2013-12-02
i am pretty new but not noob :)
i have m audio solo fast track
and ubuntu studio 13
i want to play my guitar threw it :)
but no succes
tried wine
tried all
search for hours

BUT i can see my guitar output in alsa mixer
i got very close
but its got to difficult :)
plz help

want to kick the window$ out:)

---

### Post by jejeman on 2013-12-03
Give
```
arecord -l
aplay -l
```
What is M-Audio fast solo track?

---

### Post by artem.morikh on 2013-12-03
finaly somebody in this world answer me hhh :)

> **** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: ALC662 rev1 Alt Analog [ALC662 rev1 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Track [Fast Track], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

> 
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Track [Fast Track], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

fast track solo [IMG]http://static.kvraudio.com/i/b/fasttrack_mkii-3qtrltsl.jpg[/IMG]

---

### Post by jejeman on 2013-12-04
Okay, so you want to use USB sound card to play guitar using what software? I see that card has "direct monitor" so you don't need any software to use it as "amp".
Tell us exactly what do you want to achive.

From the output you gave it looks that this USB card is supported. Yes, it is a good sign.

---

### Post by artem.morikh on 2013-12-04
I want to play rakarrack 
I tried hard and this my first help topic
Cant configure what conect to what on qjackctrl
System in?
Where m-audio
:(

---

### Post by jejeman on 2013-12-04
You have two sound cards, so you need to tell JACK which one to use. Choose USB audio. In Qjacktl settings in "interface" line click on the ">" button and select it.
Hardware is always labeled as "system". So, you will never see a sound card brand name.

After JACK is properly set and run, start Rakarrack and connect system: capture_1 (or capture_2) to Rakarrack: in_1 & in_2. --->(this is input connection, capturing the sound from the guitar)
And Rakarrack: out_1 & out_2 to system: playback_1 & playback_2.  ---->(this is output connection. listening sound from Rakarrack on speakers.)

---

### Post by artem.morikh on 2013-12-05
did as you said
but no no luck
[http://www.flickr.com/photos/88301950@N08/11219371564/](http://www.flickr.com/photos/88301950@N08/11219371564/)

so clooose

i hear noises from my pc box that come from rakarrack
but no soundcard 
i tried to change my capture device in alsa mixer but i get kicked out the window

its like the system doesnt want me to play :D

---

### Post by jejeman on 2013-12-05
Don't connect Rakarrack: out_1 to both Playback channels. Just 1 to 1 and 2 to 2.

Connections are all right. But, obviously you didn't choose the right sound card. In alsamixer you can not change/select capture device. You can change input ports on one device, if it has that option (like HDA cards have) but, that is not what you need now. In qjacktl you need to select the input device, as I said in my previous post.
If there is no sound from the USB card, then try the onboard card. You have to determine which card is selected, for which card are those system ports.
Or, for troubleshooting purpose, disable onboard sound card in BIOS. So, USB card will be the only one.

---

### Post by artem.morikh on 2013-12-07
did that 
bios
all around stuff

no luck

my linux dont want this sound card :)

---

### Post by jejeman on 2013-12-08
Give
```
aplay -l
arecord -l
```
with internal soundcard disabled in BIOS.

---

### Post by artem.morikh on 2013-12-12
*** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Track [Fast Track], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Track [Fast Track], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by jejeman on 2013-12-12
It does not look like you disabled the on board card in BIOS.
Check again.

---

### Post by artem.morikh on 2013-12-15
ok

first of all thanks to all the helpers!!!!! really

now

this is the right conf for me

[IMG]http://i41.tinypic.com/14df1iq.png[/IMG]

---

### Post by artem.morikh on 2013-12-15
Gosh!

i did it 

there is that small thing down there

i was so close to put linux down
but
linux is awesome

i chose my soundcard there

[IMG]http://i41.tinypic.com/14vh5z6.jpg[/IMG]

---

### Post by artem.morikh on 2013-12-15
but now there is other Q
how to make it in terminal?

---

### Post by jejeman on 2013-12-15
If you look at post #6 you will see that I said
> click on the ">" button
> but now there is other Q
how to make it in terminal? How to make what?

---

### Post by artem.morikh on 2013-12-16
you rigth
me dumb

you can close

---

### Post by cub on 2013-12-18
A bit off topic, but are you really running Ubuntu Studio 13? The screenshots sure looks like a Mint installation. :) Unless you have changed the looks of the studio installation.

---

### Post by artem.morikh on 2013-12-22
i knew that somebody would see that hhhh :)

i got angry on ubuntustudio (which is pretty buggy)
and switch back to mint

i knew if i get is work one distro
will work in other

and i wish i could change the looks
i am so noob that i even dont read the manuals

---

### Post by dennis13 on 2014-01-07
Glad you got it working and welcome to the wonderful world of Linux audio, that is. Make sure you save your configuration in qjackcntrl's settings once it's working.

If you want try out patchage for managing the Jack connections. It's so much more comfortable than qjackctrl in that regard.

Usually I use qjackctrl to start the Jack server only and then switch to patchage for the connections.

Another good program you might want to try is zita-mu1 which gives you a VU meter and a big fat volume knob. I mainly use it to turn down the volume which would otherwise blast me. The connections then go from "rackarack out" to "zita-mu1 in1" and from "zita-mu1 out1" to "playback".

Best, Dennis

---

### Post by cub on 2014-01-08
> **artem.morikh said:**
> i got angry on ubuntustudio (which is pretty buggy)

i am so noob that i even dont read the manuals
Not reading any instructions and then maybe not doing the right steps doesn't mean the distribution is buggy.

---

### Post by su:bhatta on 2014-01-08
> **dennis13 said:**
> Glad you got it working and welcome to the wonderful world of Linux audio, that is. Make sure you save your configuration in qjackcntrl's settings once it's working.

If you want try out patchage for managing the Jack connections. It's so much more comfortable than qjackctrl in that regard.



Agree, with Dennis, 100%, Patchage is really nice to manage the connections.

Also, You really dont have to feel bad about giving up on Ubuntu Studio, linux is fun in all that, you can customize your own OS.
E.g. I add all the UbuntuStudio metas on top of Ubuntu Gnome as well as Elementary OS. Have done the same previously on Mint too.

BTW,  did you install the Low-latency kernel too in the Mint set-up or just the Softwares? With Studio packages, a low-latency kernel always helps.

But, Ubuntu Studio 13.10, buggy? Seems to run pretty solid.

Also, the global menu, that comes with 13.10 Studio, is really neat as I get that Studio custom menu working in Ubuntu Gnome!

---

### Post by dennis13 on 2014-01-09
I remember how eagerly I was awaiting the first Ubuntu Studio release. It was in 2007 for sure and I seem to remember it was based upon Ubuntu 7.04. Back then I was using 64Studio which was based upon Debian but never really took off.

Ubuntu Studio is nicely done and for me one if not the best "pro-audio" distro I tried.

---

### Post by su:bhatta on 2014-01-10
> **dennis13 said:**
> I remember how eagerly I was awaiting the first Ubuntu Studio release. It was in 2007 for sure and I seem to remember it was based upon Ubuntu 7.04. Back then I was using 64Studio which was based upon Debian but never really took off.

Ubuntu Studio is nicely done and for me one if not the best "pro-audio" distro I tried.

+1 To you again.

For the last year I've tried out various audio OS's! AVLinux, 64Studio, Musix, Tango Studio &  even this one from Fedora called Jam Spin !

Nothing comes close to Ubuntu Studio! It is the best that is out there. Really great work by the team. 

Never gonna give it up.

Also, Cubs comments are very justified !

---

