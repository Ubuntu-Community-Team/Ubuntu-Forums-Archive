---
title: "Guitar Recording Basic Questions"
date: 2013-08-04
forum: Ubuntu Studio
---

### Post by mark2741 on 2013-08-04
I have been using Ubuntu for quite some time now but have not tried using it to record guitar with. I'm an intermediate level player that mainly just likes to record a backing track and then solo track(s) over top of that, primarily for practice.

Once in a great while I'll get motivated to try adding in 3rd-party drum loops, bass lines, etc. but not too often.

I am comfortable with and use Audacity during my day job sometimes (I'm an e-learning developer and use Audacity to record and edit voiceover audio). 

Up until now, I've been using my iPhone with Garageband to do recording with. I have an Apogee Jam USB device that I plug my guitar into, then it plugs into the iPhone, and I can then use any number of effects/processing apps, Garageband, etc.

So last night I plugged in the Jam into my Ubuntu PC and was surprised to see it seems to work! So my questions now are:

1. I'd love to be able to use the apps on my iPhone as processors/effects. Has anyone tried going from guitar -> Jam - > JamUp Pro XT (or some other iOS effects app/amp sim) - > Ubuntu (Audacity or some DAW)? I assume this could only be done via the line in on my soundcard (really my motherboard as I have built-in sound).

2. If the above option is not possible or won't come with good results: are there are any easy to use, Ubuntu-friendly 'amp sim' or 'effects processors' similar to the apps on iOS that I can use with Ubuntu and Audacity (or any other audio recording software)?

3. Should I stick with Audacity or move to something else? I like the speed and simplicity of Audacity and am unfamiliar with other recording software, but am open to others if the learning curve is not too steep.

Thanks

---

### Post by pepsifx357 on 2013-08-04
Do you have Jack running?

I would highly reccomend Guitarix

```
sudo apt-get install guitarix
```

Audacity is fine, but you'd be better off learning the basics of Ardour.

```
sudo apt-get install ardour
```

...but again, this is all assuming you have Jack installed and running.

Here's the Ubuntu Studio Preparation Guide.

[https://help.ubuntu.com/community/UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation")

---

### Post by mark2741 on 2013-08-04
Thanks. I went ahead and installed JACK and Ardour. I'm able to record from the Apogee JAM into a track, but I'm not hearing anything when playing it back. 

I've been a linux guy for a whiile now and love to fiddle and fix problems, but have never had the patience for dealing with audio/recording stuff as it just kills the creative process : (

---

### Post by mark2741 on 2013-08-04
A follow-up to this in case anyone else runs into it - 

I'm on Ubuntu (not Ubuntu Studio) 13.04 64-bit, and getting the Apogee JAM to work with Ardour was surprisingly simple once I figured out the problem: 

On my system, whenever I start up JACK, the "Interface" dropdown selector is not enabled. To get it so that I could enable it to select the JAM device (HW 1), I had to click on the Alsa setting as if I were going to change it to another audio type (like Pulse, etc.) but then leave it at ALSA. Once I do that, the Interface dropdown is enabled and I can select the JAM. So, for my system, it is a simple matter of doing the following steps to have a working, basic multitrack setup with the Apogee JAM:

1. Install qjackctl (aka JACK)
2. Install Ardour
3. Plug in the Apogee JAM into a USB port
4. Start up JACK
5. Click on the ALSA selection (upper-right of the window) as if you are going to change it, but just click on ALSA again.
6. Click on the arrow to the right of the Interface selector and choose the JAM.
7. For the Output device, select your usual soundcard output. For me, it was HW0,0 (my motherboard's analog output). 
8. Start up Ardour, add a new track, and record away!

---

