---
title: "problems with audacity"
date: 2009-02-17
forum: Ubuntu Studio
---

### Post by underdog512 on 2009-02-17
I am having two problems with Audacity.

1. I am using the onboard line in port on my laptop to record from a phone which I am using as an mp3 player. The recording volume is extremely low.  My goal is to hook my laptop into the soundboard at my church to record the services for podcasting. I am just testing with the phone.  

2. I am unable to play back what little it records. I get an error message.  "error while opening sound device. please check the output device settings and the project sample rate".  I have the playback device set to "Alsa Default". I am assuming that is my built in speakers.

I am a noob when it comes to recording. however I figured it would be pretty straight forward.  guess not

---

### Post by alexandari on 2009-02-17
Hello there! You say your recording volume is extremly low? Have you checked the Mic Boost on the Volume Control? Mine is sometimes at the bottom,and no one can hear me when I`m talking :D be sure it`s raised to the top. The recording volume can also be raised from Audacity. I can`t tell you how exacly cuz I don`t have it atm...
2 - I was having this error message also when I was playing audio with Amarok for example,no matter if both were with Alsa (strange). So,be sure you`r not using anything that can threaten you`r recording.
3- you can try this thing called "alsa-oss" package. It actually channels OSS applications through ALSA, making them them work more or less like regular ALSA programs. You can find it in your Synaptic package manager (or sudo apt-get install alsa-oss) 
~~just installed audacity it records and plays everything with no problem when I`m listening to other music and...stuff :)~~
so,you should start audacity with alsa-oss by typing:

[COLOR="MediumTurquoise"]aoss audacity[/COLOR] in the terminal. 

There you have it :)

---

### Post by underdog512 on 2009-02-18
I didn't see anything in volume control that said mic boost.  I looked for that earlier because I had read about it in some alsa documentation and have yet to find

I installed the alsa-oss package and am still unable to playback.  I am getting the same error.

---

### Post by Reeman on 2009-02-19
Same problem different computer try the alsamixer by launching it with the sound device not the sound server. In a terminal try **alsamixer -c 0**then your mike level should show up. By default Ubuntu sends alsamixer off to pulse instead of the actual sound device. 

This is something that the developers should strongly reconsider changing! This about the 20th post I have seen where the poor user cannot control the onboard soundcard correctly at all because of the use of the pulse audio server!:p

---

### Post by underdog512 on 2009-02-20
I have enabled the mic but all I am getting in Audcity is some kind of feedback.

Still can't playback in audacity.

also noticed that if I export whatever it recorded, the file will not playback in any player.  I tried exporting it as a mp3 and an ogg.  No errors or anything.  It just will not playback.

---

### Post by Reeman on 2009-02-20
> **underdog512 said:**
> I have enabled the mic but all I am getting in Audcity is some kind of feedback.

Still can't playback in audacity.

also noticed that if I export whatever it recorded, the file will not playback in any player.  I tried exporting it as a mp3 and an ogg.  No errors or anything.  It just will not playback.
Well in that case your onboard mike is feeding back into the laptop speakers! Just turn down the master volume out and watch the audacity consol for monitoring the recording instead of listening to the output. Either that or if you can shut off the laptop speaker and use a set of ear buds. Plugging in ear buds into the line out usually signals the laptop chip to shutdown the speakers. If it does not then you will have to check your laptops particulars to see if it possible. It would be silly if the volume control for the speakers was the same as the master out. But stranger things have happened in the wonderfull world of PC lap tops!

Failing all this advice in audacity/edit/preferences turn off play back while recording. You should still see the metering and be able to monitor the level of input without listening.

Could be that the file is a dump of silence? So the mp3 that you just created is of dead air. You most likely just need to have actual sound data getting to the audacity engine. Do you see any activity in the mike level meters? This is the one below the function buttons second from the left in my screen shot.

---

