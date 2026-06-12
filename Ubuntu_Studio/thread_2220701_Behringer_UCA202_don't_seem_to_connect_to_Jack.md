---
title: "Behringer UCA202 don't seem to connect to Jack"
date: 2014-04-29
forum: Ubuntu Studio
---

### Post by stevie5 on 2014-04-29
Hi Folks,

I finally have installed Ubuntu-Studio to my Box and I am happy with it.
Performance is by far better than on M$.

Programs start fine but JACK does not seem to find my Behriger UCA202.

lsusb shows the device:

Bus 005 Device 003: ID 08bb:2902 Texas Instruments Japan

Never the less I won't be able to select the device in the Jack setup-configuration as In/Output-Device.
I would have thought, that the drop down should show something like "hw:0,3"
but it certainly doesn't do that. I do get "hw:0,0" and "hw:0,1" but no more.

What shall I do???

rock on,

Steve

---

### Post by jejeman on 2014-04-29
Give 
```
aplay -l
cat /proc/asound/cards
```

---

### Post by stevie5 on 2014-04-29
> **jejeman said:**
> Give 
```
aplay -l
cat /proc/asound/cards
```

here you go:

aplay -l:
____________________________________________________________

**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: IXP [ATI IXP], Gerät 0: ATI IXP AC97 [ATI IXP AC97]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: IXP [ATI IXP], Gerät 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: CODEC [USB Audio CODEC], Gerät 0: USB Audio [USB Audio]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
_____________________________________________________________

cat /proc/asound/cards:

0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 2 with ALC658D at 0xfe02a000, irq 17
 1 [CODEC          ]: USB-Audio - USB Audio CODEC
                      Burr-Brown from TI USB Audio CODEC at usb-0000:00:13.1-2, full speed


cheers,

Steve

---

### Post by jejeman on 2014-04-29
The USB card is registred, it should work. It is hw:1,0.

---

### Post by stevie5 on 2014-04-29
> **jejeman said:**
> The USB card is registred, it should work. It is hw:1,0.


Ok, the UCA202 works with Audacity. I was able to record something!
But under Ardour 3 I don't seem to get the UCA202 to work.
Where would I have to configure Ardour 3 to get the hw:1,0 to work.

cheers,
Steve

---

### Post by jejeman on 2014-04-29
>  Where would I have to configure Ardour 3 to get the hw:1,0 to work.Nowhere. You need to configure JACK to work with USB card. Ardour just uses JACK configuration.
Give
```
cat ~/.jackdrc
```

---

### Post by stevie5 on 2014-04-30
> **jejeman said:**
> Nowhere. You need to configure JACK to work with USB card. Ardour just uses JACK configuration.
Give
```
cat ~/.jackdrc
```


```
[COLOR=#2E8B57][FONT=Monaco]/usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -C[/FONT][/COLOR]
```

I guess the "-dhw:0" needs to be changed to "-dhw:1" ?

---

### Post by jejeman on 2014-04-30
Yep, and better use 48000Hz and -n3

---

### Post by stevie5 on 2014-05-01
how about the "-S" Option???

---

### Post by jejeman on 2014-05-02
Not important.
Here is my setting for USB device
```
/usr/bin/jackd -t1000 -dalsa -dhw:1 -r48000 -p64 -n3
```
-p64 can be little low, increase it if your CPU can't handle.
-t1000 not important, some time ago I was needed this, so I kept it as default.

---

### Post by stevie5 on 2014-05-02
thank you for your help! I have a AMD64 Processor, with 2GB RAM. Until now I haven't had a problem so far.
Would you know how I would get a peak-meter in audacity or ardour, so I can check wether ther is a signal or not?

---

### Post by jejeman on 2014-05-02
Both Audacitty and Ardour have built in meters. In Audacity you have to turn it on by leftclicking on recording meter. In Ardour is turned on by default. Also you can start meterbridge, a stand alone meter application.

---

### Post by stevie5 on 2014-05-05
Hi,

thx again for your help! After I returned yesterday to our Bandroom to test some things, I could not get to work anything with the UCA202 I have tried to 
set settings as they were before, but nothing worked. Neither in audacity nor in ardour. I think I need to run through the settings that do a fixed setup 
of everything. Also would you happen to know, whether the **edirol UA101** works with UBUNTU? It offers more channels for a recoding...

---

### Post by jejeman on 2014-05-05
I never used  edirol UA101.

Audio cards can shuffle, so you need to check their order.

---

### Post by stevie5 on 2014-05-05
okay, my audio cards are in the same order than they used to be before. But never the less, I do not seem to get any signal 
I have hooked up a Macbook and recorded with Garageband with no problem. But Ubuntu-Studio doesn't.
Jack has selected  hw1 [CODEC          ]: USB-Audio - USB Audio CODEC. But still no effect!
The only change that I have made is still in .jackdrc which was 

/usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -C

and now is:

/usr/bin/jackd -dalsa -dhw:1 -r48000 -p1024 -n3 -C

could that have something to do with it?

---

### Post by jejeman on 2014-05-06
No, your settings are correct. You can experiment with sample rate, to see if there is any difference.

---

### Post by luctor on 2014-05-06
Easy method : install qjackctl and configure jackd from there.

IMHO better but a little more work : install kxstudio repos and use the AWESOME cadence utils.
read all about it at [http://kxstudio.sourceforge.net/Repositories](http://kxstudio.sourceforge.net/Repositories)

Setting up linux audio can be, I admit, a bit of a hassle.

more good reading
[http://wiki.linuxaudio.org/faq/start](http://wiki.linuxaudio.org/faq/start)
there a section about ordering the soundcards

---

### Post by stevie5 on 2014-05-06
> **jejeman said:**
> No, your settings are correct. You can experiment with sample rate, to see if there is any difference.

I really don't get it! It worked fine the first time and now? Where should I start looking for errors?

---

### Post by CrocoDuck on 2014-05-06
That is weird. I show to you what I'm used to do to work with my UCA202. Install Qjackctl, it is installed by default on Ustudio. Plug the card and turn on the computer. Launch Qjackctl and click on the setup button. Go to the Input Device and Output Device fields. Click on the tick symbols next to the device names:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=252913&d=1399375381[/IMG]

Select USB Audio for both of them:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=252912&d=1399375381[/IMG]

That works great for me.

---

### Post by stevie5 on 2014-05-06
> **CrocoDuck said:**
> That is weird. I show to you what I'm used to do to work with my UCA202. Install Qjackctl, it is installed by default on Ustudio. Plug the card and turn on the computer. Launch Qjackctl and click on the setup button. Go to the Input Device and Output Device fields. Click on the tick symbols next to the device names:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=252913&d=1399375381[/IMG]

Select USB Audio for both of them:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=252912&d=1399375381[/IMG]

That works great for me.

okay, I will try that and will let you know, what the outcome was!

By the way, what are your settings in AUDACITY to get it to work (settings in Device-Toolbar)

---

### Post by CrocoDuck on 2014-05-06
> **stevie5 said:**
> By the way, what are your settings in AUDACITY to get it to work (settings in Device-Toolbar)

If you are running jack just select JACK audio in the device host field. The output and input device will show the socket to connect. If you choose system audicity will use audio streamed from and to the soundcard.

---

### Post by stevie5 on 2014-05-06
> **CrocoDuck said:**
> If you are running jack just select JACK audio in the device host field. The output and input device will show the socket to connect. If you choose system audicity will use audio streamed from and to the soundcard.

I think it would be just best to reset all settings, or maybe delete the auda-city config-file, to start from scratch...

---

### Post by stevie5 on 2014-05-08
Hi everyone!

I got everything up and running! Both AudaCity and Ardour are working. Thx to the community!

So This Thread should be closed!

---

