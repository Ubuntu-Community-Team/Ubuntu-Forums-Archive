---
title: "No sound from Sound Blaster Audigy 2"
date: 2011-01-11
forum: Ubuntu Studio
---

### Post by StereoKills on 2011-01-11
I posted about this over in Hardware a few days ago, but no one seems to have any ideas. Hoping it might get better luck in this forum.

Just installed an old Audigy 2 card of mine from a long dead PC. Had it  on loan to a friend for a while and he had it working just a few weeks  ago in his computer running Ubuntu. 

I'm using Desktop 10.10 with the Studio files/programs installed for the  sound suite. I disabled the onboard sound card in BIOS, downloaded  alsamixer and have been fussing with that for some time to no avail. 

Hoping someone has some ideas......

---

### Post by Pablo_F on 2011-01-11
Hi, 

Please, run the alsa-info script so we can see your audio configuration. This command will do it (upload and give the link):

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

Note that you have to configure and launch the jack server to use some of the studio programs.

Cheers! Pablo

---

### Post by StereoKills on 2011-01-12
Hi Pablo,

I've run the script and here is the link to the upload!

[http://www.alsa-project.org/db/?f=c07ec4829e6fba9e79c2e0060be68304f975708e](http://www.alsa-project.org/db/?f=c07ec4829e6fba9e79c2e0060be68304f975708e)

Thanks!

---

### Post by Pablo_F on 2011-01-13
Hi, 

I don't have a SB Audigy2 but I don't see anything wrong with your setup, at low level at least. 

But then, you have to know that there are basically two sound systems in ubuntu that operate at a higher level. They act as audio servers for the applications you normally use.

One of them is called pulseaudio. It is the default audio server and a "general purpose" one. You control it by means of the sound preferences or through a program called "pavucontrol". The default multimedia players are pulseaudio clients so, for example, open rhytmhbox, play a file. Do you hear something? Take a look at Sound Preferences or pavucontrol.

Now, there is another audio server oriented towards music production called JACK (Jack Audio Connection Kit). Studio apps normally use JACK. The app you normally use to start the server (the jackd daemon) is called qjackctl or Jack Control. Once the jackd daemon is started, only jack clients will playback or capture sound. You can make connections between jack clients (including your audio card which is generically called "system") in the connection window of qjackctl or by means of an app called patchage. 

If you elaborate a bit on what you are trying to achieve we can give better help. 

Cheers! Pablo

---

### Post by StereoKills on 2011-01-15
Eventually, I'd like to be able to record music through the inputs on the Audigy2,  however at this point, I'm not getting any sound playback whatsoever. Even using Rythmbox or Youtube. I spent a good deal of time in the Sound Preferences, that all seems to be set correctly, and some time in the various Pulseaudio apps. I can't seem to see anything obvious as to why I'm getting no playback whatsoever.

---

### Post by Pablo_F on 2011-01-16
Hi, 

I think it has to be some setting in alsamixer. Maybe you can give it a try with a graphical alsa mixer like gamix or gnome-alsamixer.

Cheers, Pablo

---

### Post by StereoKills on 2011-01-16
I did just get it working. For some reason there is no output when the master volume is below 30% or so, I had it turned down to about 20% since I have an amplified speaker system set that has no hardware volume built in. Thanks for your help!

---

