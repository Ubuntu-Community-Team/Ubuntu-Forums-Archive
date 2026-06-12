---
title: "Question about  mixer routing"
date: 2010-06-17
forum: Ubuntu Studio
---

### Post by Tofigh on 2010-06-17
Hi
Lets short the story, I am newbie with all these studio things and due to an academic project need to make my Saffire pro 40 work. In short, I should connect 8 microphones to audio interface and record each of their audio stream in a separate file. I mean 8 audio file for 8 connected microphones should be assigned. 
ffado and jackd has been installed flawlessly and every thing is going smoothly just one thing
I CANT hear or record any thing. I used jack_capture and meterec to record signals but the audio file was just silence. 
These are my ffado-mixer settings. Is there any problem in it (I just connected 2 mic till now)?

---

### Post by cchhrriiss121212 on 2010-06-18
Is jack running OK? Any error messages etc.
Check you have the correct inputs selected to record from in the jack connections window

---

### Post by AutoStatic on 2010-06-18
Hello Tofigh, I think you have to check the internal routing of your Focusrite. And yes, you need ffado-mixer for that, together with [the manual for your device]("http://www.focusrite.com/support/download/saffire_pro_40_user_guide/614").
Unfortunately there's no guide for using ffado-mixer with the Focusrite Saffire Pro 40 yet ([there is one for it's predecessor]("http://subversion.ffado.org/wiki/ffadoMixerGuides")), hence the RTFM :)
Another option would be to ask the ffado guys themselves on IRC (irc.freenode.net #ffado) or to subscribe to [the ffado users mailinglist]("http://ffado.org/?q=contact").

Best,

Jeremy

---

### Post by Tofigh on 2010-06-18
Hi
I checked the connection in jack and it was ok( at least from my point of view there was no problem) however I attached its pic to let you see if there is any problem in it

I guess There is no ffado group at irc.freenod.net  ! 
Cheers

---

### Post by cchhrriiss121212 on 2010-06-18
Does ffado mixer allow you to monitor what levels are showing from your inputs? (I don't have a firewire device) If so do they show any reading?
Have you made sure that you have sufficient gain turned up on the mixer?

---

### Post by AutoStatic on 2010-06-18
> **Tofigh said:**
> Hi
I checked the connection in jack and it was ok( at least from my point of view there was no problem) however I attached its pic to let you see if there is any problem in it

I guess There is no ffado group at irc.freenod.net  ! 
CheersLooks like you have no sound in Ardour (only capture port 5 is directly connected to a system output port). I'm not an Ardour expert unfortunately.
And I'm looking at the #ffado channel right now, 19 users.

---

### Post by Tofigh on 2010-06-18
Hi
@[cchhrriiss121212]("http://ubuntuforums.org/member.php?u=948514"): No it doesn´t  have this option to show any signal level for inputs it just has three different tabs which I have posted  their pics above. 

[@AutoStatic]("http://ubuntuforums.org/member.php?u=746131") : OK. I admit that I couldnt find irc.freenod.net but instead, I found 
[http://webchat.freenode.net/#ffado](http://webchat.freenode.net/#ffado)  
are they similar? :D

BTW, I switched from ardour to timemachine which is another jack aware app for recording. 
Although i still can´t record, i can hear very high frequency noise(like WHISTLE) whenever connecting  the system_capture to timemachine inputs in Jack. 
Does is it help? 
Thanks.

---

### Post by AutoStatic on 2010-06-18
> **Tofigh said:**
> [@AutoStatic]("http://ubuntuforums.org/member.php?u=746131") : OK. I admit that I couldnt find irc.freenod.net but instead, I found 
[http://webchat.freenode.net/#ffado](http://webchat.freenode.net/#ffado)  
are they similar? :DYes, those are the same channels.

You could try installing MeterBridge, start JACK and then MeterBridge and then try connecting your capture ports to MeterBridge to check if you get any input signals.

---

### Post by Tofigh on 2010-06-18
Hi
Good suggestion. These are the pics of its result. Interesting and strange!
they are at the hight level that can be. I also remembered  earlier in ardour I saw such a high level of signal. So I just plug out the microphones and check the MeterBridge and Ardour. Though microphones are pluged out Both of them show a very very strong signal in their input!!!
Just look at the attached pics.
now I am completely confused 
Cheers and have a good weekend ;) seems i should be here at weekend:mad:

---

### Post by AutoStatic on 2010-06-19
So there's something coming in. But do the meters move? Or is it a constant input signal?

---

### Post by Pablo_F on 2010-06-19
I suggest the following:

In ardour, remove the stereo track you seem to have and add 8 mono tracks from, say, audio 1 to audio 8. 

In qjackctl, disconnect all system captures to ardour. Also, disconnect all system captures to system playbacks, if any.

Open ardour mixer (Window, Show Mixer).
In each strip, below "Audio x" and above Record, there is a button. Click on them and choose "in x" (In 1 for Audio 1 and so on).
Arm the tracks. You can do it in the mixer by pushing the record button, or in the Editor Window by pushing the red dot button on each track.
Go to Options -> Monitoring. Select: Ardour does monitoring

You should hear (monitor) the audio inputs as long as the ardour master bus is connected to the correct pair of system_playbacks and all the ardour tracks are connected to the master. This is the default behaviour so you should do nothing more.

Take a look at the connections in qjacktcl. They should make sense now. You can connect / disconnect here or from within ardour. The latter is easier and faster as explained above.

 Just make sure the speakers are connected to the right pair of analog outputs, where the ardour master ports are connected (system: playback_1 represents the first analog output and so on). 

If nothing else happens, you should be able to record the eight tracks (the ones that are "armed to record" in any case) when you push the general record button on the transport, while monitoring (hearing) the recording.

HTH, Pablo

PS: To get started in ardour, search for the FLOSS manual

---

### Post by Tofigh on 2010-06-21
Thanks every one for their helps and special thanks to [AutoStatic]("http://ubuntuforums.org/member.php?u=746131") for his wise advice.
It was solved but how? 
Thanks to the wise suggestion of AutoStatic I checked the input level by MeterBridge and  found that there is a very strong signal exists in my input. But there was no microphone  connected to my device so how? 
After that I discovered that siganl level meter LED in front of the device also shows the highest level of signals in input 3 and 4!!! very strange. So I checked the warnning in ffado and found that there is a warning in ffado-test-streaming which says : there is a loop in receive in 21 out 21. So it seems it was a short circuit between one of the inputs and outputs but how it happens I have no idea. I loaded the device in windows and backed all settings to the factory settings and it was solved!!. 
PS: I am not sure if it is a bug in ffado-mixer or it was my fault!. However most probably it was a bug since it is too dangerous to let the user wiring the internal routs such that makes the short circuits. 
Now I can record every thing fine!.
Thanks again

---

### Post by AutoStatic on 2010-06-21
You're welcome, good to hear that it works now! I had troubles with my Focusrite too when I just got it and had to send the device back for repair. Maybe they should improve their quality control on their outgoing units ;)

---

