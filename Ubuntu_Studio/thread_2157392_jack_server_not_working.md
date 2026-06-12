---
title: "jack server not working"
date: 2013-06-25
forum: Ubuntu Studio
---

### Post by su:bhatta on 2013-06-25
Hi,
am new to studio(using 13.04).. having used vanilla for sometime wanted to record my home sessions on studio.. on opening the QjackCtl i am getting the following message:
```

15:38:14.145 Patchbay deactivated.
15:38:14.176 Statistics reset.
15:38:14.191 ALSA connection change.
15:38:14.286 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
15:38:14.300 ALSA connection graph change.

```
any help is much appreciated..
also, i want to primarily record my home sessions (an electric guitar, acoustic drumset, LMMS bass loops), any particular helps as to how to go about that..

and.. does compiz work in Ubuntu Studio 13.04, if yes then how.. checked webup8 but only messed up settings and had to comnpletely delete compiz...

regards,
bhatta

---

### Post by zequence on 2013-06-25
Please have a look at this guide on how to start jack [https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro#UbuntuStudio.2BAC8-ProAudioIntro.2BAC8-1204.Starting_Jack](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro#UbuntuStudio.2BAC8-ProAudioIntro.2BAC8-1204.Starting_Jack).

If you still have a problem, please let us know.

---

### Post by su:bhatta on 2013-06-26
> **zequence said:**
> Please have a look at this guide on how to start jack [https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro#UbuntuStudio.2BAC8-ProAudioIntro.2BAC8-1204.Starting_Jack](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro#UbuntuStudio.2BAC8-ProAudioIntro.2BAC8-1204.Starting_Jack).

If you still have a problem, please let us know.

Thanks a ton Zequence. I really had no idea where to find those details. But i really should have checked the 'Ubuntu Studio Information' from Applications link...

Then again, as a musician itz easier to complain and blame it on hardware or in this case S/W !


Got Jack running..:D

now gotta find out how and with what to record the sessions..

Also, any idea how to run compiz in studio??


Thanks again for your time n  help..

---

### Post by jejeman on 2013-06-26
You don't want compiz when working with audio.

---

### Post by su:bhatta on 2013-06-27
> **jejeman said:**
> You don't want compiz when working with audio.

Ok ! Thanks I will keep that in mind.. all i wanted was 'Hot Corners' n 'wobbly windows'... have grown to like them over time..

But, if theres some problem with the compiz n audio recording/editing then i will play safe..
Lovin the XFCE experience btw..

jejeman: how to record in studio? mic my amp or directly plugin the guitar, any particular s/w that helps to record acoustic drums...

thanks a ton...

---

### Post by cub on 2013-06-27
> **bhattabhishek said:**
> how to record in studio? mic my amp or directly plugin the guitar, any particular s/w that helps to record acoustic drums...
Are you going to record the drums and the guitar playing at the same time or will you first record one instrument and then the other?

If you record both at once in the same room it might be a good idea to plug the guitar right in to avoid leakage from the drums into your guitar amp microphone. If not, I would say it depends on what microphone, sound card and guitar amp you have available?
If it's a great sounding amp which will not produce the same sound going direct, mic the amp and record it! If you can't blast the amp to a volume where it sounds the best without neighbors bolting down your door, try to record direct.

But since you would play acoustic drums I assume the neighbors won't be a problem?

As for software, I'm not aware of any special SW for acoustic drums. I would use Ardour for recording and mixing and the EQ, effects and plugins available in there.

---

### Post by su:bhatta on 2013-06-27
> **cub said:**
> Are you going to record the drums and the guitar playing at the same time or will you first record one instrument and then the other?

If you record both at once in the same room it might be a good idea to plug the guitar right in to avoid leakage from the drums into your guitar amp microphone. If not, I would say it depends on what microphone, sound card and guitar amp you have available?
If it's a great sounding amp which will not produce the same sound going direct, mic the amp and record it! If you can't blast the amp to a volume where it sounds the best without neighbors bolting down your door, try to record direct.

But since you would play acoustic drums I assume the neighbors won't be a problem?

As for software, I'm not aware of any special SW for acoustic drums. I would use Ardour for recording and mixing and the EQ, effects and plugins available in there.

For the clarifications:
1) I would be recording both drums n guitar being played at the same time
2) Neighbors ain't no problem
3) My amp is a hybrid (1 Tube preamp + solid state power amp) 60 watt, nothing top range but does the job well (T64RS, WhiteHorse)
4) Wanted to record the weekly jams that goes on in my music room (Lovingly called Studio42, H2G2)..
Also would like to add a 'Marvin' kinda guy will be responsible for actual mixing n EQ part as we play..

another question:
How to get so many Audio Jacks as input to the computer?

Thanx in advance

sorry if I bother u with these questions, but being a noob, I hav no clue as to how to go about recording my stuff at home...

---

### Post by cub on 2013-06-27
From the specs I found online on the guitar amp it doesn't have any line out feature so I would put a mic in front of it. As it's seems more like recording the jams for future references rather than recording a demo or putting something out on SoundCloud and/or YouTube I would keep it simple and just put one mic in good spot in the room where you get a nice balance between the drums and guitar. We even did demo recordings like that which produced a nice raw sound to it. It depends on the room and sound you're after of course.

How many mics do you have? How many inputs does your sound card have? That pretty much sets a limit on how advanced you can be during the live recording. If you have like 8 inputs to your soundcard you could put up more mics on the drums, one on the guitar, one for the room and so on. But if it's just two inputs you could make use of those. It's not always the case that more mics are better. The good stuff comes from how you use what you have available.

I'm not sure how to solve the LMMS bass lines for you since you would need to be able to hear that through headphones at the same time as you're playing. It's kind of up to sound card again and what other headphone equipment you have available.

I can recommend checking out [http://therecordingrevolution.com/](http://therecordingrevolution.com/) and his YouTube channel for good pointers on home studio recording. It's not linux based but the audio ideas transfer to whatever medium you are using for recording.

---

### Post by jejeman on 2013-06-27
> **bhattabhishek said:**
> jejeman: how to record in studio? mic my amp or directly plugin the guitar, any particular s/w that helps to record acoustic drums...Cub has already said all that I would suggest.

---

### Post by su:bhatta on 2013-06-27
Hey Cub,
Thanx a ton for taking your time out..
Yes, u r absolutely right, these recording r gonna be for references only n no professional purposes! definitely gonna try ur 'one mic in the sweet spot' idea! I believe in things like that! (Thats how people  like Robert Jhonson got recorded mostly) 

Also i have no clue what soundcard my laptop has! I dont know how to check that on Linux either, so gonna hav to boot to windows to find out, but i think it will be a simple one...
n am gonna check the link too...

live long n prosper...:guitar:

---

### Post by cub on 2013-06-27
You might want to look into getting a cheap external sound card (Myself I use an Edirol UA25-EX connected to the USB port) since you will have some trouble to connect the microphone directly to the laptop.

---

### Post by jejeman on 2013-06-27
To check which soundcard you have, just run
```
aplay -l
```

---

### Post by su:bhatta on 2013-06-27
> **jejeman said:**
> To check which soundcard you have, just run
```
aplay -l
```

jejeman: here is what i found:
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


an atheros sound card i think.. no specialised device as i foretold...

i was thinking of using 1 shure mic by converting 1/8' to 1/4' ... and following Cub's method of putting it in sweetspot

---

### Post by su:bhatta on 2013-06-27
> **cub said:**
> You might want to look into getting a cheap external sound card (Myself I use an Edirol UA25-EX connected to the USB port) since you will have some trouble to connect the microphone directly to the laptop.

Thats a nice idea cub. I read in another post where jejeman gav a Behringer's usb mixer..
checked that piece of hardware n was thinking to try something like that... 

external sound card i had no clue about so dug into that...n found it costs quiet a bit in india.. the same cakewalk 25-ex u mentioned.. so gonna hav to look to for alternatives....

in case the '1 mic in the sweetspot' didn't cut the deal...

---

### Post by su:bhatta on 2013-06-30
How to mark this thread as closed??

All problems resolved...

---

### Post by Iowan on 2013-06-30
> **bhattabhishek said:**
> How to mark this thread as closed??

All problems resolved...

Hopefully, one of these will help:
[http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)
[http://ubuntuforums.org/showthread.php?t=2151638](http://ubuntuforums.org/showthread.php?t=2151638)

---

### Post by su:bhatta on 2013-06-30
It aint workin... in the 'Go advanced' I am not getting the "Prefix"... cant do it...

---

### Post by cub on 2013-07-01
> **bhattabhishek said:**
> It aint workin... in the 'Go advanced' I am not getting the "Prefix"... cant do it...
Did you edit the first post in the thread then? I just tried it on a thread I started and the prefix dropdown showed the "SOLVED" choice, but only if I edit the very first post.

---

### Post by su:bhatta on 2013-07-01
Thanks...I am trying it out now!!

---

