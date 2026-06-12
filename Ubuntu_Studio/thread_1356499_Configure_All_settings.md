---
title: "Configure All settings?"
date: 2009-12-16
forum: Ubuntu Studio
---

### Post by vlad_ion on 2009-12-16
Hello, im new to the forum and to ubuntu studio, I previous workt in ubuntu but not in the musical programs just a simple os, now I have something cooking and I need ardour to help me and a program to record from my mic (its a plugged mic near the headphones) so I did my project in ardour but I cant get it to record, tryed to mess around with jack controll but no recording, there are loads of settings about my imput output..I have alsa and Pulse audio, pulse audio auto closes when I click on the volume control, from the volume control (system up in right corner) this is some info
Hardware : vt7108/a [Azalia Hdac] (Via high definition audio controller)
but every time I open the volume control it frozez and auto closes, the same with some programs from the audio production.
About jack : when jack controller is opend and ardour in connect tab i get the next things :
Audio : nothing
Midi : nothing
Alsa : 
Readable clients : 14:Midi through/130:ardour
Writable clients : 14:midi through/128:timidy/130:ardour
Its a total messup aroud here and I need to say its a fresh install (1 day) from the alternative ubuntu studio dvd and I had to install the program from sudo apt-get install ubuntustudio-audio and so on.
Can a guru help me cuz Im really stuck and I dont want to go back to windblows viruses so somebody please help me cuz I really like the multimedia programs in ubuntu.
Thanks!, Vlad.
Edits : 
- sorry about my english, im Romanian.
- I can hear sounds from ardour but when I start jack(button start) and start recording from ardour I nolonger hear the sound.

---

### Post by thorgal on 2009-12-16
> 
- I can hear sounds from ardour but when I start jack(button start) and start recording from ardour I nolonger hear the sound.


not sure what you mean by "start" in jack button start, but in ardour, it means that the session is set to "let the hardware do the monitoring".

So unless your audio hardware has a dedicated monitor channel to which you have connected some speaker or headphones, you will have to use ardour in software monitoring mode.

Look into the options in ardour's main menu bar. You will see something about monitoring. Set it to "ardour does monitoring".

In this way you will hear the audio signal while recording (even with effects if you had put some effects plugins on the track being recorded).

However, you will have some latency that depends on your jack setting. The smaller the buffer size, the shorter the audio latency, but low latency operation is something that can be difficult to achieve, depending on your hardware, kernel, OS tuning, etc.

But first thing first: set ardour to do the monitoring.

---

### Post by panneers740 on 2009-12-17
You can turn on the Pop-up Blocker when you are prompted to do this before the first pop-up window appears.
On the Tools menu
To configure the Pop-up Blocker on the Tools menu, follow these steps: Click Start, point to All Programs, and then click Internet Explorer.
On the Tools menu, point to Pop-up Blocker, and then click Turn On Pop-up Blocker to turn on the Pop-up Blocker, or click Turn Off Pop-up Blocker to turn off the Pop-up Blocker.
Click Start, point to All Programs, and then click Internet Explorer.
On the Tools menu, point to Pop-up Blocker, and then click Turn On Pop-up Blocker to turn on the Pop-up Blocker, or click Turn Off Pop-up Blocker to turn off the Pop-up Blocker.
From Internet Options
To configure the Pop-up Blocker from Internet Options, follow these steps: Click Start, point to All Programs, and then click Internet Explorer.
On the Tools menu, click Internet Options.
Click the Privacy tab, and then select the Block pop-ups check box to turn on the Pop-up Blocker, or clear the Block pop-ups check box to turn off the Pop-up Blocker.
Click Apply, and then click OK.
=====================
[automotive air conditioning compressor](http://www.1airconditioning.com/)
[chicago wedding limo](http://www.chicagolimousine1.com)

---

### Post by vlad_ion on 2009-12-17
[thorgal]("http://ubuntuforums.org/member.php?u=202106")

When I start jack control I wanted to say ..my sound stops from all aplications ex: exile music player.
So is there any option to recrord direct from ardour and to not open jack control?
I set ardour to do the monitoring, and its the same thing, I can hear a background noise all time now and when I hit play in ardour I hear the beat, but still when hitting record no sound and no record.
Should I make a video or something to show you, maybe you can help me.
Thanks!

---

### Post by Joey2058 on 2011-05-07
Hello,

i  do have the same Hardware and of course i do have the same problem.

Sound (output) works fine alsong i dont try to open System > Preferences > Sound. If i open it, the sound stops and the only way to get it running again is to reboot Ubuntu. Loging out and in again wont fix it.

also if i try to use the mic the output stops too. I tried it with Teamspeak 3 and also the "Sound Recorder".

Greetings

Jimmy

---

### Post by Pablo_F on 2011-05-07
The sound system in UbuntuStudio is a bit tricky so be patient and take it easy. 

Basically, there are two so-called sound servers. The default one is pulseaudio. The System Sound Preferences is a pulseaudio front-end. Pulseaudio is made to "just work" and its audience is the "desktop user".

On the other hand, there is the jack server, which is made with music creation in mind. 

Reference:
[http://0pointer.de/blog/projects/when-pa-and-when-not.html](http://0pointer.de/blog/projects/when-pa-and-when-not.html)

So, with regards to your problem, what exactly are you trying to do? Do you start the jack server (via Jack Control) before you experience the issues you describe?

---

### Post by Joey2058 on 2011-05-07
errrrm im not doing much... all i want is the sound working right. well ok its not exactly the same problem, but i guess its caused bc of the same hardware.

Im booting ubuntu i can use "Movie Player" and "Rythbox Music Player" and it plays sound correctly.

I did install Skype and the sounds (.wav) sounds strange with some noise in it. i triied them with the Players and the players can play it correctly, skype wont do it.

I installed Teamspeak 3, 64 bit version, im trying to test the mic and the sound stops.
i can only reboot and sound works again.

Starting Music again.
im going into System > Preferences > Sound    hardware-tab shows to the the right hardware, after a few sec its empty.  Sounds stops again.
"Movie Player" pops up a msg: 
An error occurred
pa_stream_writable_size() failed: Connection terminated

i already tryed something from ubuntuusers.de but i couldnt fix it yet..
is it so hard to get sound running?  i just need a media player, Skype and Teamspeak 3 and i would be happy ><

---

