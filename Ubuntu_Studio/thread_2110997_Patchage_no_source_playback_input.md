---
title: "Patchage no source playback input"
date: 2013-01-31
forum: Ubuntu Studio
---

### Post by fisch246 on 2013-01-31
I know I won't have enough info for you guys to work with, so please ask for what you need me to dig up. The problem is what it is says in the title. I can get jack source, and jack sink to show up, but not the system playback to show up. I have a Realtek sound card, and I have a USB headset. Basically I'm trying to capture audio from my system sound. This is unbelievably impossible to do on windows so I figured I'd try on Ubuntu. No such luck at all. I have been having tons of problems on windows when it comes to capturing audio. Since I'm using a USB headset, I can't use stereo mix, without getting myself echoed through, then I tried VAC, and that crashed on install every time. Man was I annoyed. So I went to look on Ubuntu forums to find out if there was an alternative to VAC. No responses to any posts at all. So I did some digging, found out there was an alternative. Jackd. So I set it, and it worked right out of the box. If my source playback had shown up, hell all I would to have done is install it, and I'd be off. I was really impressed. So now I'm stuck with trying to get the source playback to show up. I'm using 12.04 desktop not studio (figured this was still the best place to post) , usb headset, realtek sound card, and I do have something plugged into the back port. So if it needed something plugged into the soundcard, there is. Any thoughts?

---

### Post by dannyboy79 on 2013-01-31
what app are you using to record? i don't completely understand what all sources you're trying to record, are you trying to record the computers sounds as well as your usb mic? this can all be done with pulseaudio, pavucontrol,

I know it can be done because I create Let's Plays of the computer game Shank 2. kazam screencasting software allows me to record the game sounds as well as my webcam (usb) mic all into 1 mp4 file.

---

### Post by fisch246 on 2013-01-31
Yea kazam is great! I've used that before :) However right now I'm trying to play polynomial, and using the sound capture feature. However the problem is... it only looks for input devices. Kind of annoying if you ask me. It works with the jack sink. Works perfectly in fact. I send spotify to Jack Sink and tell the game to look there, and it reacts to my music. Now my problem is I can't hear it. So if I can just get it to send back to my speakers with Jack Source I can hear what I'm listening to. If I can get this to work... well... I'll have better luck than I ever did in windows.

---

### Post by dannyboy79 on 2013-01-31
oh boy, i have no idea what you're trying to do. sorry can't help

---

### Post by ttoine on 2013-01-31
hey.

Before using Jack, you have to choose the sound card to use with. The usb headset is a sound card, the integrated realtec is another one.

Once you checked that the headset is selected in qjackctl setup, you can start jack and then record with any application like Ardour.

Otherwise, you can simply use the sound preferences, select the headset (usb audio, or something like that) as the input, set an input level and it will works. I use that for Skype and the microphone of the webcam. Works great and very easy to setup.

---

