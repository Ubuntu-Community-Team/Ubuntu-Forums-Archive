---
title: "Audi drivers and applications mess! PA/ALAS/Jack"
date: 2010-03-15
forum: Ubuntu Studio
---

### Post by kazakore on 2010-03-15
No I am not looking for drivers of Audi cars, that's obviously a mistake ;)


I have also posted this on the Renoise forum as I know there are a few Linux users there, although not as many as I would like.



Recently installed Ubuntu Studio 9.10 and while i have most things working OK it is still bugging me in many ways, mainly related to audio and multiple applications.

Now I can get audio out of my machine from just about any application with a bit of messing around. Had to install Jack as it doesn't seem to come as standard any more.

To be honest I have probably messed things up more than help but trying to follow a few instruction of the 'net, such as [this one]("http://sync-signal.com/2009/12/configuring-jack-and-pulseaudio-on-ubuntu-9-10/") without being 100% sure of what I was doing (but it is my first install and still learning so if it doesn't last that long so be it.)

Right, so if I start qjackctl but leave it stopped I seem to be able to use most applications. Renoise works in both Jack and ALSA mode, VLC and Movie Player both give audio.

If I do not start qjackctl then VLC and MP work but Renoise will not see either driver (even though I had the settings of VLC set to use ALSA rather than default so you would think that, if it can use ALSA, then so should Renoise be able to.)

If I start the Jack Server then Renoise works but the other apps will not.

I have just noticed that something I have done recently has stopped the volume controls working and they seem to be set at a very low level as is normal on my headphones with it maxed in VLC (think it's frozen it at the level it was rather than make it a default, 0 level.)


What I really want is to be able to use multiple programs that want to process audio at the same time, whether it be Renoise while composing then just play a track or two in VLC while I take a breather without having to close down Renoise and tweak other things, or using multiple audio applications at once. I thought I had understood that this is what Jack is for (or at least part of it.) What am I doing wrong? Couldn't really understand the Connect and Patchbay parts of qjackctl...


EDIT: OK, so main output level has now been set by the Mater in GNOME ALSA Mixer (is that the best choice out of the three offered? Went for it as has highest "Popularity" out of them.) Still means I can't use the keyboard Fn+ shortcuts though.

---

### Post by cchhrriiss121212 on 2010-03-15
Jack is made for pro audio use (Renoise etc) and so is not ideal for regular usage (playing a few mp3s or watching video in firefox). Pulse audio is installed with ubuntu to handle all this stuff, but it is not suited for pro audio. So when you have an ubuntu OS designed for pro audio you have an initialy confusing sound setup. Gnome alsa mixer is the best choice for sound levels in my experience.

> What I really want is to be able to use multiple programs that want to process audio at the same time, whether it be Renoise while composing then just play a track or two in VLC while I take a breather without having to close down Renoise and tweak other things, or using multiple audio applications at once. I thought I had understood that this is what Jack is for (or at least part of it.) What am I doing wrong?

Jack will handle this fine, you have done nothing wrong. Install alsa player for your listening to tracks or download the jack+vlc package from synaptic. Then you select jack under audio device in vlc and you can use it with jack the way you wanted.

> Couldn't really understand the Connect and Patchbay parts of qjackctl...

The connections window allows you total control over where sound goes from every jack compatible program to your sound outputs/inputs. You just make a connection of where you want the sound to go, eg. Hydrogen>EQ>Ardour. Patchage is a separate program which does this job in a much easier way and it remembers where you had things connected last time.
Patchbay allows you to save a set of connections as a small config file that you can load up from a drop down list.

What I think most people do is use jack for recording/producing music, then just use pulse for movie player and stuff as it will work out of the box (in your case).

---

### Post by kazakore on 2010-03-15
Nice one! Can now get Renoise and VLC working together at least :)

Is there a Jack plug-in for Firefox at all? Or another browser you can recommend that does?

Also noticed something strange. Some things seem to treat the Surround fader in the ALSA Mixer as being the main output, some seem to treat it as the Front one. Front makes most sense and seems to have come up now (maybe they are all there now but earlier did mute everything but Surround, PCM and Master to have audio output with minimum noise.) Something a little strange anyway...

---

### Post by kazakore on 2010-03-15
I think I have now somehow killed pulseaudio and can not get sound from my browser or programs that don't use Jack/ALSA.

"pulseaudio -k" (kill process) gives a response of "E: main.c: Failed to kill daemon: No such process"

"pulseaudio -D" and pulse-session both give "E: main.c: Daemon startup failed."

"ls -l" of both show that I have left them with read and execute for all (plus write for owner) which I believe is standard.


What would be the next thing to try?

---

