---
title: "*facepalm* Noob requiring help."
date: 2010-07-02
forum: Ubuntu Studio
---

### Post by lazyrobot47 on 2010-07-02
Oi!
I switched to ubuntu studio, and frankly, i have no CLUE how to go about getting these programs to talk to my sound card right, and how to get the programs to cooperate. or how to use jack or any of that. Im just running a cable off my mixer to my laptop's sound card till i can get something better, it gets the job done for quick demos. Also, Audacity freezes and fails when I go to record a second track. any ideas?!

thanks a pinch!

---

### Post by cchhrriiss121212 on 2010-07-02
So do you want to use jack and jack-related programs or just Audacity?
Jack is a great tool for audio production as it allows you total control over where your sound is going to and from. If you want a a serious multi-track recorder then you should really be using jack+Ardour.

Quick how-to for jack setup:
Add yourself to the audio group in Users & Groups
Put this into a terminal:
 ```
    sudo gedit /etc/security/limits.d/audio.conf 
```
and paste these lines:
 >                                                 @audio - rtprio 99
@audio - memlock unlimited         
                        
Open up jack from the sound and video menu, press start, check message window to see whether it runs OK. Open up patchage to connect up the audio chain to whatever else you want to use, ie Hydrogen. You can decrease the latency by altering the frames in setup, but if you see xruns then you have gone too low.

Let me know if you get stuck on anything.

---

### Post by lazyrobot47 on 2010-07-02
I want to use Audacity for quick demos because it doesn't need jack to run, I can throw down the rough tracks just so i have an idea of how i want to do the song. For the serious recording i will be using jack+ardour.

---

### Post by sgx on 2010-07-02
> **lazyrobot47 said:**
> I want to use Audacity for quick demos because it doesn't need jack to run, I can throw down the rough tracks just so i have an idea of how i want to do the song. For the serious recording i will be using jack+ardour.
If you connect a CD player or some continuous sound source to your line-in, start audacity, use the menu Edit-->Preferences
and choose different devices and record/playback options until things are
to your liking. Audacity can use jackd, and reveals itself in qjackctl as
Portaudio, after the audacity play button is pressed, so press pause, then make qjackctl connections, and press pause again to resume recording.

Hi, heres a good source of pages for jackd connections:

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections).

Maybe ardour used with lashd can get you a saved standard recording session, or perhaps ardour can do that on our own already. lash =

linux
audio
session
handler

Timemachine is a great simple quick recorder once qjackctl is configured.
Cheers

---

### Post by lazyrobot47 on 2010-07-02
The thing is though, is that i dont want to use jack with audacity only ardour. Im not going to be doing anything heavy duty in audacity, 4 tracks tops. Like i said, I just want audacity to be my open up and make a demo fast and jack+ardour to be my final product recording. I don't wanna screw with jack every time i use audacity, because ill be tracking live guitar, live vocal, and live drums in, not using any software synths or anything. Thats all to be saved for when i sit down to actually record the final version of the song.

---

### Post by sgx on 2010-07-02
> **lazyrobot47 said:**
> The thing is though, is that i dont want to use jack with audacity only ardour. Im not going to be doing anything heavy duty in audacity, 4 tracks tops. Like i said, I just want audacity to be my open up and make a demo fast and jack+ardour to be my final product recording. I don't wanna screw with jack every time i use audacity, because ill be tracking live guitar, live vocal, and live drums in, not using any software synths or anything. Thats all to be saved for when i sit down to actually record the final version of the song.

Its an extra option, not a requirement ;) Just follow the basic steps,
using alsa or oss in the preferences, and change settings for monitoring, recording etc
Cheers

edit, I have oss and dev/dsp in audacity preferences to record guitar on the line in.
I can switch to alsa instead of oss, and then choose my soundcard, instead of dev/dsp, and do
the exact same recording/playback, all without jackd.

---

### Post by lazyrobot47 on 2010-07-03
I need help getting Audacity running right. It will not record a second track! It just freezes about a second after i hit record.

---

### Post by sgx on 2010-07-03
> **lazyrobot47 said:**
> I need help getting Audacity running right. It will not record a second track! It just freezes about a second after i hit record.
Hi, it could be a buggy version, it could be you need to assign a tmp
location that has more disk space. Plenty of diskspace for audacity tmp location is good luck, and turning off audio triggering of recording. I know I had a similar issue once. The version I have on this machine is 1.3.12 May 21st, and has some bugs.
You could try reinstalling all of audacities dependencies, and try an older version or two.
Cheers
Pulseaudio and audacity running with portaudio may conflict, so use alsa or oss if portaudio is shown in audacity preferences.

---

### Post by markbuntu on 2010-07-12
Here are some links to help you out. Some of them are a little old so the info might not be exatcly correct but they will give you a good idea how to get things going. I would reccomend using ardour.

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

If you are having trouble setting up jack in UbuntuStudio:

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)



[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)


If you are wondering how to sync applications together through jack:

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)


[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)


good luck,

---

