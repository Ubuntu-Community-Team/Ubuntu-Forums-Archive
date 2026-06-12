---
title: "ART USB Dual Preamp as audio output"
date: 2011-05-21
forum: Ubuntu Studio
---

### Post by AnarchistForPrez on 2011-05-21
Hey everybody, i'm trying to get my DAW up and running correctly in Ubuntu. I have an ART USB Dual Pre, and i want to use it as an audio output for all available audio functions, and run the CPU speakers through there.

My current audio setup looks like this,

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I don't know is this is enough information to get the help i need, so if i am oblivious and have overlooked something, i'll get the information. If anyone can help me i'd really appreciate it. I haven't recorded anything since i switched over to Ubuntu and have a bunch of new material to work on. Please keep in mind that i am a musician, not a programmer. I do however have a great fondness for open source. Thanks in advance.

---

### Post by cchhrriiss121212 on 2011-05-22
I think some more info would help, perhaps start with what you have setup already, then move on to what it is you want to ultimately achieve. Hopefully myself or someone else can fill in the blanks for you.

I will just throw some questions out here and you can reply to whichever ones are applicable:

What is the software you want to use? Does it make use of WINE or is this a Linux program? Or do you want recommendations for software? If so, what features do you need?

If you do not know where to start try installing jack and patchage, open up the jack control setup window and select your USB card as the interface, then press start. Now you can try using Ardour or Qtractor or any other jack programs, use patchage to connect the audio where you want it to go. Then post back if you get stuck.

---

### Post by AnarchistForPrez on 2011-05-26
Thanks [cchhrriiss121212]("http://ubuntuforums.org/member.php?u=948514"), As it goes, i currently am attempting to use the ART USB Dual Pre as an audio interface with Ardour GTK2. I have JACK installed already, and have been able to successfully import my previous audio takes from SONAR as wav files into Ardour and have gotten playback through my pc speakers. 

Right now, I haven't even considered amp modeling software at all, but am thrilled to getting any suggestions you may have. My main concern is getting the basic recording process down. So all i want is to send the guitar signal in, and record it. But i want to plug my pc speakers into the interface and send ALL available audio functions from my cpu into it.

I however had not installed patchage, which conceptually makes sense to me for routing signals. So thank you for that.

I'm trying in JACK to set the usb as the "interface" and these are the options i see and the results i get...

(default)      -  Runs properly, delivers no audio 

/dev/dsp      -  Error: Jack Audio connection kit -  p, li { white-space: pre-wrap; }                       Cannot connect to server socket err = No such file or directory


/dev/audio   -  Error: Jack Audio connection kit -  p, li { white-space: pre-wrap; }                       Cannot connect to server socket err = No such file or directory


hw:1            - Error: Jack Audio connection kit -  p, li { white-space: pre-wrap; }                       Cannot connect to server socket err = No such file or directory


hw:0            - Runs Properly, but delivers no audio

plughw:0      - Error: Jack Audio connection kit -  p, li { white-space: pre-wrap; }                       Cannot connect to server socket err = No such file or directory


hw:1,0         - Runs properly, delivers no sound


This last option hw:1,0 is also labeled (USB Audio) which leads me to believe that it is the correct setting. 

but option hw:0 is labeled (USB audio codec)

and nothing delivers me any sound, even when using hw:1,0 as interface, input, and output. which is in theory what i want it do, work as input and output. i specifically bought this model as it was reviewed as being plug and play with ALSA by ubuntu studio users at [http://www.linuxstudiopro.com/](http://www.linuxstudiopro.com/)

I realize that i now have have more questions then i started with, despite your giving me very clear, concise and reasonable suggestions.  But i am extremely grateful for all of your help. Thanks again.

---

### Post by RaumTrug on 2011-05-26
well, eh...have you tried fireing an alsamixer onto that thing? open a terminal window, and enter something like "alsamixer -c 1", or install something like "gnome-alsamixer". many not-so-really-common audio devices are defaulted to volume 0% on all channels...

---

### Post by djcj on 2011-07-16
Hello all, I believe this is an old thread but I just spent half a day trying to figure this problem out so thought I might post the solution to help somebody else encountering the same problems out.

I'm currently running DreamStudio, which is basically Ubuntu 10.10 with Audacity and Ardour already set up

[http://dream.dickmacinnis.com/forum/](http://dream.dickmacinnis.com/forum/)

and just bought a ART USB Dual Pre and could not record or hear any audio but after reading this thread, got a few ideas and here's how I got it working.

First off, go to Jack cntrl, go to setup, go the Interface and click the > button right next to it and change it from default to USB Audio, which for me was hw:1,0.  Now, if you want to use Ardour, should be all set to go, if not, go to Jack, make sure it's started, click on Connect, make sure Ardour is routed to system and vice versa.  If you want to use Audacity, go to Edit > Preferences > Devices - change it to Jack Audio Connection Kit.

Now if you're still not hearing any audio in either Ardour or Audacity, check to see if your tracks are mono or stereo.  And check where your guitar cable is plugged into the USB Dual Pre and change it to the other input.  I spent a few hours stressing out why I couldn't record any audio and then realized my guitar cable was plugged into the right channel of the interface but since I initially had mono tracks set to record on Audacity and Ardour, wasn't hearing anything.  But after I created some stereo tracks, finally saw the signal being recorded.  Or as mentioned earlier, just plugged my guitar cable into the other input on my USB Dual Pre.

Here was the biggest discovery for me.  To actually hear the audio, I had to go to Applications > Sound and Video > Audio Production > Hardware Control > Gnome ALSA Mixer, open up the ALSA mixer and go to the USB Mixer tab and uncheck the Mute clickbox (why was it even checked??)  Thnx to Raum Trug, the previous poster, for noting to look there.  I spent a few hours trying to figure out why I couldn't hear any audio.

Also, when I go to Terminal and type in lsusb, this is what I get:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 08bb:29b0 Texas Instruments Japan 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I tried checking and I couldn't find any relation between Texas Instruments and ART USB Dual Pre so by the looks of it, my system isn't detecting the interface on my laptop but I'm still able to record and hear the sound.

Hope this helps someone else here and save you some time.

---

