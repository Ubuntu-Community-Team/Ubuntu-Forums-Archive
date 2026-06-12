---
title: "HOWTO: Use a Sound Blaster Live to the fullest."
date: 2006-04-17
forum: Tutorials
---

### Post by graigsmith on 2006-04-17
after a long time of fiddling with alsa mixer i finally have everything working perfectly.

in the console type alsamixer to get to the alsa mixer program.
First hit f5.  Then turn up the volume on EVERYTHING. You use the cursors for doing this, press up, and then press right and turn everything up.

If you are having problems, like getting no sound at all.  pay special attention to all the bars to the right of "ac97"  one of the emu10k1 settings in particular needs to be set at 0 otherwise you will get no sound at all.  and some should be enabled.  its best to just disable all of them, and start turning them up till you can hear sound.  if the sound turns off when you start turning the volume on them up, then that is probably one of the ones that needs to be set at zero.

Now. find the "Line" channel, make sure its not muted. hit the spacebar, to enable recording on it.  Scroll over to the caputre channel,  and hit spacebar.  you should now be able to use line in to record in audacity.  yay

Now, Here is the part that took the longest time to figure out.  Find the "Tone" setting, unmute it with m.  Your bass and treble settings should now work.  If turning up bass sounds like a broken speaker with lots of distortion.  just go to the "wave" and set it to 50% or just enuf so that you don't have anymore distortion in the bass.  

mute the microphone channel as well, you get far less noise during playback that way. 

Hope this helps to anyone with a SB live.  :D

Edit, if you are using dapper with a soundblaster live, it's a bit different.
Wave, line-in, cd, and mic, should all be at 50%  Most importantly ac97 should be at 0%, but ac97cap should be at 100%  then you can record off the line in.

---

### Post by morphis on 2006-06-08
Hey !
I got the same sound card as you...that was perfectly working under breezy, After my upgrade to dapper I got that odd sound of broken speaker with distortion as you're talking about. But I tried a lot of differents setting with alsamixer without any succes to get rid of that...How did you succed to do that and where does that strange and anoying sound come from???are the questions ...
thank you for any reply.. cheers

---

### Post by exgsr on 2006-07-15
i with dapper, sblive! value and facing same problem..
"odd sound of broken speaker with distortion"
really hope some1 can unravel this mystery...](*,)

---

### Post by bionnaki on 2006-07-15
how do you mute the mike channel? mine is set at zero, but how do you mute it?

---

### Post by tlaloczint on 2006-07-16
> **exgsr said:**
> i with dapper, sblive! value and facing same problem..
"odd sound of broken speaker with distortion"
really hope some1 can unravel this mystery...](*,)

yeah same here

---

### Post by tlaloczint on 2006-07-16
I used this to temporary fix the distorcion go the terminal and paste this
 
sudo aptitude update && sudo aptitude install alsamixergui

then check in sound and video alsamixergui

then I click on analog front (thats is mine you maybe something else)for the sound then I lower both bars all the way to cero or botton, then I only raise one bar wich is the left side and dindt see a diference the sound came normal for both left and right then I raise the right bar and thats were the distortion started to apear when both bars are in the same level,
so I play a little to see if that will make a diference on wich side will sound louder so I din`t see a diference one bar the left or right will sound the same for both I left the right side all to the botton and the distortion went away now is nice and crispy.

I hope that this will help someone
I don`t know how to post a creenshoot so I can show what I am talking about.

---

### Post by supersrbin2000 on 2006-08-03
i'm posting this in case someone expiriences the same problem i had until now : having a 5.1 speakers, and cannot get them all to work. The solution is to mute that 'sb live analog output' thing in alsamixer, and rear will start playing...i've lost many hours fighting with this, hope that it will now  save someone's time :) In addition, here's the screenshot...cheers

---

### Post by Lord Illidan on 2006-08-03
In my experience distortion is cleared by adjusting PCM and WAVE down...

---

### Post by supersrbin2000 on 2006-08-03
> **Lord Illidan said:**
> In my experience distortion is cleared by adjusting PCM and WAVE down...

Maybe it's because of some kind of clipping problem. anyway,it's not a recommended practice to pump up the volume to max.

---

### Post by spaced.alien on 2006-10-29
I can't seem to get any sound and I've followed all the post here I can find on the subject but to no avail.  I noticed in the top post it says "pay special attention to all the bars to the right of ac97".  Mine stops at ac97, with nothing else to the right.  Not sure what this means.  I really want to get this resolved.  The issue of sound is the only reason I still use windoze.  Please help!

p.s. I just updated to Edgy Eft and still have the problem.

---

### Post by Madmoose on 2007-02-11
Hello, 

I'm have a Sound Blaster Audigy, and I'm not getting ANY sound. I've already gone in, and tried to make the EMU10K1 driver work by putting in 

> sudo modprobe snd_emu10k1. 
It didn't work, so I looking into this thread. 

When I typed alsamixer, and the sound thing came up I noticed that it says:

> Card: Intel ICH5
Chip: Analog Devices AD1985
View: [Playback] Capture all
Item: Master

Does this mean that it's looking at my MB's default card, and not my  Sound Blaster Audigy?

Can someone please help me?! I'm about to pull out my hair! :cry:

---

### Post by vultaire on 2007-03-24
First off, a disclaimer: I haven't tried this on Ubuntu.  The SB Live issues drove me to try Debian Testing (Etch) in hopes that upstream some of these problems wouldn't exist.  They do in Debian as well.  However, I've finally had some success.

Primary issue for me was not being able to mute the microphone.  This is how I've dealt with it, though the solution admittedly may be imperfect.

1. Gnome Volume Control: Go to File->Change Device->TriTech TR28602 (OSS Mixer).
2. Go to the capture tab.  Make sure you can see the option for Microphone.  If not, enable it through Edit->Preferences.
3. The Microphone mute button DOES NOT WORK in the OSS Mixer here.  (Does anyone know a proper workaround for this?)  So, to make the microphone stop playing back on your speakers, you have to mute the microphone's output or drop its volume to 0.

The rest of the steps can be done in Gnome's Volume Control or using alsamixer, but alsamixer is probably easier.  Just do "sudo alsamixer" to start, "sudo alsactl store" to save changes.  "?" brings up help in alsamixer.

4. Set AC97 output to 0 and AC97 capture to 100.  Might not be necessary, but it doesn't seem to hurt anything.  Just try it.
5. Enable the microphone as the capture device.  The original poster said line in, but maybe he wasn't trying to record off a mic.  The regular mic in -should- work.
6. If the sound output is funny - under Ubuntu it was, under Debian it strangely was not, but it could have just been a difference in my procedure - try the Tone trick mentioned in the first post.  Sound was okay before setting tone, and is great after setting tone and bass/treble.

Now, audacity works fine, I don't get any bloody microphone feedback when using my headset, and probably I can use Skype without annoying the heck out of myself now.  In fact, I think I'll go do that.

Sources with information which helped me:
- First few posts of this thread
- [http://alsa.opensrc.org/Emu10k1#General_mixer_settings_for_emu10k1]("http://alsa.opensrc.org/Emu10k1#General_mixer_settings_for_emu10k1"))

- Paul Goins

---

### Post by Steve H on 2007-04-16
I´ve got a Soundblaster Live! and everything is working fine except the Mic, I´ve tried everything on this thread, but to no avail.....still i can use Teamspeak or Sound Recorder.I can hear myself on the headphones, just nothing seems to actually record.

---

### Post by mobileguy on 2007-04-21
Thank you this fixed my low volume in Ubuntu 7.04  - the Feisty Fawn - for my soundblaster card

In a terminal type alsamixer to get to the alsa mixer program.
First hit f5. Then turn up the volume on EVERYTHING. You use the cursors for doing this, press up, and then press right and turn everything up.  Use M to unmute tone  etc  (see first post) :)

---

### Post by knightnet on 2007-04-28
Hi, I have a Live 1024 card which is no longer working properly.

The main problem is that alsamixer doesn't do anything! I can set anything and nothing is changed.

I think that the only output I am getting is from oss and not ALSA - I'm using Feisty Kubuntu.

Also, I am only getting output on my rear speakers!

Any ideas?

Cheers, J.

---

### Post by Tumpster on 2007-05-07
Yes, but how can you set it all so that all 5 speakers or at least 4 are on the same page, so when you turn the volume up you're turning em all up???

---

### Post by onno on 2007-06-12
I got the Sound Blaster Live! 24 bit card to work under Ubuntu Feisty (7.04). 

To sum up the solution:
1. disable default onboard card in BIOS
2. create /home/your_username/.asoundrc

Save .asoundrc with:

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}


Here's how I got there (describing this here so you won't have to go through the same trouble):

My computer has two sound chipsets:

onno@onno-desktop:~$ asoundconf list
Names of available sound cards:
ICH6
CA0106

CA0106 is the Sound Blaster Live! 24 bit card, the other is the onboard sound card.

If I use the command:

asoundconf set-default-card CA0106

- then after the FIRST reboot, the Sound Blaster is now the default card. You can check this in the alsamixergui. Unfortunately, it seems as though, after a SECOND reboot, the default switches back to the onboard card.

No wait, upon testing this, I notice that the command doesn't seem to have any effect at all, not even after the first reboot. I have now disabled the onboard card in the BIOS.

Now, only the front boxes are playing any music in Amarok, while in Rhythmbox only the rear boxes are playing!

Also, issuing the command "asoundconf set-default-card CA0106", as I did earlier, has the effect that this file is created:

/home/onno/.asoundrc.asoundconf

This file ruins everything!

1. delete the file
2. create a file /home/onno/.asoundrc
3. put this in it and save it:

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}


To sum up the solution:
1. disable default onboard card in BIOS
2. create /home/onno/.asoundrc

---

### Post by Magneto on 2007-06-12
Soundblaster Live user here. Had to turn on wave surround to get sound.

---

### Post by skattyadz on 2007-08-27
Thanks!

Lowering PCM definitely made a difference. I also noticed my speakers are controlled by wave, wave lfe, wave center and wave surround.

So with a bit of tinkering its all good apart from when I change the volume with my keyboard it changes all the sliders together. I like to have the rear louder (as the speakers are further away) but when i change the overall volume it puts all channels on the same level. Any ideas?

Thanks =]

Edit: Don't worry, I can change volume levels on the speaker system.

---

### Post by Xebec on 2007-09-01
Unfortunately none of the advices helped me in Feisty :( Sound feedback is there, recording is not

---

### Post by Guitar John on 2007-10-31
> **onno said:**
> I got the Sound Blaster Live! 24 bit card to work under Ubuntu Feisty (7.04). 

To sum up the solution:
1. disable default onboard card in BIOS
2. create /home/your_username/.asoundrc

Save .asoundrc with:

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}


Here's how I got there (describing this here so you won't have to go through the same trouble):

My computer has two sound chipsets:

onno@onno-desktop:~$ asoundconf list
Names of available sound cards:
ICH6
CA0106

CA0106 is the Sound Blaster Live! 24 bit card, the other is the onboard sound card.

If I use the command:

asoundconf set-default-card CA0106

- then after the FIRST reboot, the Sound Blaster is now the default card. You can check this in the alsamixergui. Unfortunately, it seems as though, after a SECOND reboot, the default switches back to the onboard card.

No wait, upon testing this, I notice that the command doesn't seem to have any effect at all, not even after the first reboot. I have now disabled the onboard card in the BIOS.

Now, only the front boxes are playing any music in Amarok, while in Rhythmbox only the rear boxes are playing!

Also, issuing the command "asoundconf set-default-card CA0106", as I did earlier, has the effect that this file is created:

/home/onno/.asoundrc.asoundconf

This file ruins everything!

1. delete the file
2. create a file /home/onno/.asoundrc
3. put this in it and save it:

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}


To sum up the solution:
1. disable default onboard card in BIOS
2. create /home/onno/.asoundrc

THANK YOU! THANK YOU!! THANK YOU!!!  :KS
This got my surround working like it should.  And the sound quality is much better than on the integral Intel motherboard soundcard.

---

### Post by CaptainShanks on 2007-10-31
Thank you so much onno! My friend has been running Ubuntu for the first time on his Laptop and now he'll finally be able to use his card! I'll post results later.

UPDATE:
Having problems again. The sound card is not being detected by the laptop. It's a real pain. >.>

---

### Post by Tha_Guru on 2007-12-26
Hello everybody, I'm new to Linux, I've a sound blaster live 5.1 on Ubuntu 7.10 and following the post I was able to make the rear left and right and the center speakers work properly. The problem is I'm not hearing any sound from the front left and front right speaker.. Pretty strange in my opinion maybe someone can help me and tell me what should I change in alsa mixer.. I'll post a screen shot of my alsamixer
Thanks a lot.

---

### Post by zFb on 2008-01-18
Im brand new to Ubuntu (I have 7.10). When I first installed Ubuntu on my computer the sound played from my Sound Blaster Live card. For some reason now it will only play through my onboard. I want the sound to work on my Sound Blaster again... I've tried about everything i can find... Any help?

---

### Post by MethosCR on 2008-01-19
> **tlaloczint said:**
> I used this to temporary fix the distorcion go the terminal and paste this
 
sudo aptitude update && sudo aptitude install alsamixergui

then check in sound and video alsamixergui

then I click on analog front (thats is mine you maybe something else)for the sound then I lower both bars all the way to cero or botton, then I only raise one bar wich is the left side and dindt see a diference the sound came normal for both left and right then I raise the right bar and thats were the distortion started to apear when both bars are in the same level,
so I play a little to see if that will make a diference on wich side will sound louder so I din`t see a diference one bar the left or right will sound the same for both I left the right side all to the botton and the distortion went away now is nice and crispy.

I hope that this will help someone
I don`t know how to post a creenshoot so I can show what I am talking about.


I have an Athlon, 512MB RAM, AGP ATI Radeon 9200, Hauppage TV Capture PCI Card, a PCI SoundBlaster Live! and Ubuntu 7.10 (Gutsy).

I had the noise problem... I hear the system sounds, mp3 and so on, but a strong noise in the background. I did what you said... to get the ALSA Mix GUI, then I mute the SB Live Analog Output Jack.. and NOISE IS GONE!! :-)

Thanks a lot, **tlaloczint**. =D>

---

### Post by onno on 2008-04-25
I'm running into problems with my Sound Blaster Live under Hardy Heron (Ubuntu 8.04).

I've got only one speaker blurting out my music: the front left speaker (out of a 5.1 setup). All the other channels are silent.

According to the Volume Control app, this is used for music playback:
ALSA PCM on front:1(CA0106) via DMA (PulseAudio Mixer).

Is anyone familiar with this problem? Is there a solution to it? If not, how do you revert to the old (non Pulseaudio) setup from 7.04?

EDIT:

I came across a solution from nstamoul: [http://ubuntuforums.org/showthread.php?t=759147](http://ubuntuforums.org/showthread.php?t=759147)

nstamoul has posted a deb package containing an audiopulse configuration utility. It works like a charm! Do not forget to login again [ctrl-alt-backspace] after running the configuration utility.



Cheers,
Onno

---

### Post by Ariccanfly on 2008-07-28
> **Madmoose said:**
> Hello, 

I'm have a Sound Blaster Audigy, and I'm not getting ANY sound. I've already gone in, and tried to make the EMU10K1 driver work by putting in 

. 
It didn't work, so I looking into this thread. 

When I typed alsamixer, and the sound thing came up I noticed that it says:


Does this mean that it's looking at my MB's default card, and not my  Sound Blaster Audigy?

Can someone please help me?! I'm about to pull out my hair! :cry:

Disable your onboard card in the BIOS and then reinstall.. (the package, and if that dosnt work, the os)

---

### Post by taurusvip on 2010-05-03
many thanks,  you saved me to spent more 2 hours around this :)  

regards
J.Ladeira

---

### Post by nicosafull on 2011-09-18
I have 2 sound cards, Sb Live! Value installed, it worked fine, when I disabled default sound card onboard thorugh BIOS (not SB onboard) never had sound again, any.. I did and tried all, still no sound on my Xubuntu... can anyone tell me pliz, how they configured their SB live! Value on Xubuntu pliz!! need sound!!!

---

