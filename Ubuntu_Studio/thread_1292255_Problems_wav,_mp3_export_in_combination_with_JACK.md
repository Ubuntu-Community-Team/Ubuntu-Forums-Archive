---
title: "Problems wav, mp3 export in combination with JACK"
date: 2009-10-15
forum: Ubuntu Studio
---

### Post by jackuss on 2009-10-15
Hello,

I'm having a bit of a weird thing going on.

I created some music and mixed it in Ardour, when I tried to export it, there was a Wav file but without any sound. I asked in the Ardour forums what this problem could be (for the complete thread see [here]("http://www.ardour.org/node/3033") ). Ofcourse I tried to troubleshoot the problem after I posted my question. 

After a couple of days I tried to record my music through JACK, from Ardour, in Audacity. It worked after I changed the Audacity record and playback settings to JACK. When I tried to export an mp3 (from Audacity) there still was no sound at all :cry:. 

I think that the problem has something to do with JACK/ALSA in combination with Ardour/Audacity.

My questions are:
- Has anyone had similar problems?
- How can this be solved?

Thanks in advance

Kind regards,

Jackuss

---

### Post by sgx on 2009-10-15
If you have both a motherboard soundchip, and another soundcard, the i/o could be mixed up, and the output going somewhere without speakers. 

If you reload the exported sound into audacity, you should see the waveforms, and hear the playback.

If there are no waveforms, you might remove all mp3 libraries, then reinstall just one. And install aoss fffor good luck.

Run 
sudo alsaconf 

to configure sound, and see if that changes things.

If still no joy, reinstall with a separate /home partition
and  get totally rid of all things pulseaudio. And do a total system update on the fresh install. If on dialup, change synaptic to store the rpm files in the /var/cache/apt/archives folder. Collect these, and back them up, this can save you time in future reinstall/modifications.

Cheers

---

### Post by trulan on 2009-10-15
Well, the first few times I tried to export to a WAV from Ardour , I had no sound, because I didn't check the boxes telling it to send Master Out 1 to Left and Master Out 2 to Right in the 'export' window.  I felt pretty foolish when I figured out where I had messed up.  That may not be where your problem is, that's just what happened to me.

Edit:  Okay , I read your thread after I posted and see you have already tried that.  I was going to delete my post but I decided to let it here for the benefit of anyone else who comes along. ;)

---

### Post by jackuss on 2009-10-17
@ Trulan,

No problem, it is always good when a solution can be found on multiple websites accross the internet :)

@ sgx

I only have 1 (on-board) soundcard, so I don't think that can be a problem, but thanks for pointing it out. When I open the file in Audacity I do see the waves, but when I want to play it in Audacity, nothing happens. The meter doesn't move a bit. When I want to do things in Audacity, almost all my options are grayed out :???:

At the moment I have a (temporary) workaround. I found out that I can't hear my export when the Ardour Audio Setup is set up to ALSA. When I switch to Dummy, I can hear sound in my export. The downside is that I can't hear sound in Ardour then :???: 

Anyone have any other ideas?

Thanks in advance.

---

### Post by martinistudio on 2009-10-17
Export it from Ardour the right way, and then play the file with a jack aware application, like vlc or alsaplayer with the jack plugins of those apps installed.

When saying it simply, when Jack is running you can't use the default desktop sound server for playback.

If you want more info, you might want to pm me.

---

### Post by kayosiii on 2009-10-17
My advice would be to install patchage and use it to check that the audio outputs of whatever you are trying to load the file into are connected to the physical outs on your soundcard.

---

### Post by sgx on 2009-10-17
Hi, most choices in audacity are greyed out because no part of the waveform has been selected. Thats how it protects the sound from
evil mice.  I've been back and forth between audacity and Hydrogen
today, having used Timemachine to record the drums playing, then making them into mp3s to load into Reaper as media files. You can export the
audio whole without selecting it, select a portion, and export that, and
if the whole thing is already selected, you can export that, saving a step.

Cheers

---

### Post by sgx on 2009-10-18
I just did a test recording with audacity. Qjackctl had zynaddsubfx routed into rakarrack, and hydrogen drum machine ready to play. I opened audacity, and chose rakarrack as the audio source, hit the record button, then hit the pause button. Now in qjackctl, I could see the audacity 'portaudio' connection, and it was already hooked up to rakarrack, as per my earlier selection. I also connected hydrogen to portaudio, hit the pause button on audacity again to restart recording, hit the play button on Hydrogen, watched the waveforms appear in the audacity track, and started playing zynaddsubfx, using the jaunty beat. When done recording,
I exported the file as a .wav, and a .mp3, quit audacity, restarted it, and loaded and played the mp3 file...everything worked OK. This was audacity V 1.39
in a pclinuxos 2009 minime linux distribution, about 300 meg in size, before adding a few audio apps,  wine, and vsts.
Cheers

---

### Post by jackuss on 2009-11-30
Thanks Everyone, I solved this problem by installing the latest version of UbuntuStudio.

Greetings and Tux on :)

Jacukuss

---

