---
title: "Ubuntu Studio - how do I connect and configure a midi keyboard - self confessed idiot"
date: 2008-10-20
forum: Ubuntu Studio
---

### Post by Jose Catre-Vandis on 2008-10-20
I have the latest Ubuntu Studio installed, Jack works fine, I can make sounds with Hydrogen and Rosegarden using software synths and the Zabb synth virtual keyboard thing also makes noises.

I have a Casio CTK 611 keyboard, with an Evolution USB adapter. If I plug this in (or have it plugged in on boot) Rosegarden recognises it, and it shows up in lsusb.

How the heck do I configure things to play the keyboard and hear sounds on the PC? I guess I need to patch it or load up a bank/soundfont but do not know where to start.

Ideal solution would be:

When plugging in keyboard (or from boot) I can play sounds on the PC quite easily

I can step record or record my tunes from the keyboard into Rosegarden

I can load up different instruments/banks whatever for the keyboard to play


Not sure why I can't figure this all out myself, guess there are too many different parameters on offer for my small confused brain. I really need a step by step idiots guide for this, the Rosegarden help files assume too much knowledge! :)

Thanks in advance

---

### Post by Royke on 2008-10-20
Hello Jose Catre-Vandis, i hope this helps for you or is a way to set it up easy(eventually:lolflag:): When you have started the Jack Control-application or whatever soundmanager you run with your keyboard, you somehow have to connect one source in(your CasioCTK 611:guitar:) and one or more out with each other. I think it may work this simple with the Jack Control interface. Just press the connect-button and click you connection for you in/out-puts. It Should recognize Hydrogen, Rosegarden (a what, try lmms too)and you keyboard should be in the midi-tab. First left-click CasioCTK 611 and then the output-source(s) (alsa, oss,..)

Pleae say it works now :-k

---

### Post by Jose Catre-Vandis on 2008-10-20
> **Royke said:**
> Hello Jose Catre-Vandis, i hope this helps for you or is a way to set it up easy(eventually:lolflag:): When you have started the Jack Control-application or whatever soundmanager you run with your keyboard, you somehow have to connect one source in(your CasioCTK 611:guitar:) and one or more out with each other. I think it may work this simple with the Jack Control interface. Just press the connect-button and click you connection for you in/out-puts. It Should recognize Hydrogen, Rosegarden (a what, try lmms too)and you keyboard should be in the midi-tab. First left-click CasioCTK 611 and then the output-source(s) (alsa, oss,..)

Pleae say it works now :-k

OK did the connect for in and out in Jack but still nothing in Rosegarden.Also couldn't find anywhere to select the output source. External device is showing up though

---

### Post by Royke on 2008-10-21
You could try perhaps to make a connection (with Jack Control) from your Casio(MIDI-out) to Rosegarden(in) and from rosegarden to audio out. Left-click in and right-click out and connect to make a wire between them. Try first starting Jack-engine before starting Rosegarden if you don't see Rosegarden in the connect box. I hope this helps, don't give up :redface:

---

### Post by markbuntu on 2008-10-21
You need to have the midi output go through an emulator to get audio out. Something like timdity or the ZynAddSubFX Software Synthesizer. I just run Rosegarden midi out to ZynAddSubFX and then the output from that to an audio input. 

I use patchage to make the connections. If you do not have patchage, you should get it.

---

### Post by Jose Catre-Vandis on 2008-10-21
Thanks for all the help, though I may have to come back for more guidance. I tried the keyboard out in Windows and still got no sound, so my problem could be more fundemental? 

Just to do a real dummies check, do I connect the midi OUT port on the keyboard to the midi OUT port on the adapter (and similarly for the IN ports) or are these reversed?

---

### Post by Jose Catre-Vandis on 2008-11-12
Right, been busy of late on other things, but had another go at it tonight. Sorted out my midi cables, in to out and out to in, and started making progress. Realised that you needed to open up the apps in order to make connections in the jack connection boxes! (doh!)  and was able to get sound playing notes on my keyboard having connected it to ZynAddSubFX.

Tried patchage and could see the drag and drop functionality and could again acheive a connection between the keyboard and ZynAddSubFX, but have no idea how to tie it up with Rosegarden, and lots of connections are automatically made.

By chosing a synth plugin in Rosegarden I got sound from the keyboard playing in Rosegarden and was able to record! However, when I tried to do it again it wouldn't work. Will I get the tones on my keyboard played back on the PC or do I have to use soft synths (I do not have a fancy sound card with all that, just on board sound)

In essence though I know I now have a connection, I am still at a loss as to the settings I need to successfully play, record and playback in Rosegarden, or even how to record the sounds being made with the connection that seems to work with ZynAddSubFX.

I have read the Rosegarden tut but it seems to assume I know how to connect up.

---

### Post by markbuntu on 2008-11-13
Here are some more links that may be helpful:

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

---

### Post by Jose Catre-Vandis on 2008-11-15
Thanks markbuntu, will keep me quiet for a while :)

---

