---
title: "Adobe Flash Media Live Encoder for ubuntu?"
date: 2009-09-08
forum: Ubuntu Studio
---

### Post by IceDoE on 2009-09-08
Does anyone know how to get Adobe Flash media Live Encoder running on Ubuntu? I'm setting up a college internet radio station, and our server guys want to use a program they already have to stream us through a flash player which will require us to have Adobe Flash Media Live Encoder on our machine, but Adobe doesn't make the Encoder for linux (server stuff yes, this, no). 

I haven't tried under WINE, but I can see that being a problem even if it did work with patching the audio from Internet DJ Console into the encoder on WINE and out, and with memory consumption which will be an issue for live broadcasting. 

If anyone knows of another project or Open Source version of this program that will work in sufficiently the same way to send a signal to a Flash Streaming Server that it will accept like the Flash media Live Encoder signal, that would be great or even preferred. We just need to send the mp3 signal out, not the video signal which the Encoder can also do.

Any other suggestions or work arounds would be appreciated as well.

Edit:
I have just tried installing under WINE. It works for the most part as far as I can tell. It does have a problem of not being able to detect the sound card and input devices, particularly for video (which I am not using). Checked WINE config quickly and it doesn't seem to know the sound card either. Right now it should just be the Onboard Intel Sound Card (There is another advanced 'sound' card, but that is currently not in use).

Again, under WINE is not ideal and I'm not sure how to make it work properly in this setup. WINE says it can use a JACK control though, which is what I would be using with alot of my other applications anyway (IDJC for instance) so anyone know how to configure the JACK control to take input from a program running just on Ubuntu and pipe it into an application on WINE?

---

### Post by afrodeity on 2009-11-12
Wish there was some support from Adobe. Why are we in the dark? Need to make a noise to get heard by Adobe in Linux

---

### Post by AutoStatic on 2009-11-12
You can create Flash movies with ffmpeg. I don't know the exact command and you probably need a version of ffmpeg compiled against liblame to be able to encode the audio to mp3. But there are several howtos out there, I made some Flash movies a few months ago, it took some puzzling with options but in the end I had some really decent Flash movies.

Edit: **ffmpeg -i yourmovie.ext -ar 22050 -ab 32 -f flv -s 320x240 video.flv**
And check **man ffmpeg** for an explanation of all the settings.

---

### Post by Vadi on 2009-11-12
I don't think ffmpeg will help here, this thing also streams the stuff somewhere...

---

### Post by AutoStatic on 2009-11-12
[http://osflash.org/red5](http://osflash.org/red5)
Red5 then maybe? We have a Red5 server running at work, no idea what it does :-\"

---

### Post by brucewagner on 2010-05-21
I have the same need as the original item post author. 

I'm wondering ... What If I just installed Windows in a VirtualBox and installed the Adobe Flash Media Encoder there...?  Would I be able to get the virtual machine to see the FireWire input?

Hmmmm...  Otherwise,  I might just have to go back to a dual-boot situation. 

Even if I find an Ubuntu app that will capture the FireWire video and audio from my camcorder, encode it, and save it to disk.....   I seriously doubt that it will be able to also stream it live up to ustream, like FME does. 

Capturing, encoding, saving to disk is critical. 
Streaming to ustream live is icing on the cake (sorta).

---

### Post by Truthiswithin on 2010-08-25
I think the standard solution is webcamstudio:

[http://www.ws4gl.org/home](http://www.ws4gl.org/home)

Works as a stand-in for FME 2.5, I think.

---

### Post by IceDoE on 2010-09-17
Wow, its been a little while but looks like theres been some activity here. Thanks for the suggestions, but will these properly link audio to a flash media server? The radio station has no control over the server side.

---

### Post by marseille on 2011-07-16
This is a great post. I never really bothered with the video sites but y'all have me going:D

So far I've installed WebcamStudio For GNU/Linux [ [http://www.ws4gl.org/news-flash-](http://www.ws4gl.org/news-flash-) ] and launched it. Now I'm reading the manual to see what it can do.

---

