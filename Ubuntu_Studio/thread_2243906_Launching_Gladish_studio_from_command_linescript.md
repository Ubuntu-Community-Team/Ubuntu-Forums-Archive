---
title: "Launching Gladish studio from command line/script"
date: 2014-09-11
forum: Ubuntu Studio
---

### Post by mashaffer on 2014-09-11
I have been playing with Gladish for running virtual pipe organs (jOrgan, jack, other processing applications and interconnections) and it seems just the ticket for this task. Now what I would like to be able to do is launch gladish and a default studio on boot but I have yet to find a way to launch a gladish studio from the command line. Any suggestions?

mike

---

### Post by mashaffer on 2014-09-12
Another odd thing has come up. The jOrgan program supports multiple fluid synth elements so that I can create instruments with more than one stereo output. When using QjackCTL all of these instances are shown in the connections window and can be routed as desired. In Gladish however the application box only one stereo output so I only get one of the fluid synth instances that are running in jOrgan.

If I set up the connections in QjackCTL and then start Gladish, the patchage window shows all of the fluid synth elements and even has them properly named. I figure I must be doing something wrong as I can't imagine folks doing entire recording studios with only one stereo output for each program that is run. Any pointers?

mike

---

### Post by mashaffer on 2014-09-12
Further info... If I start a studio that does not have a command to start jOrgan and then I start jOrgan by hand using the exact same command line as was used in the application setup for gladish then everything works as it should. Of course the negates the point in using gladish in the first place. Why would it be that having gladish launch jOrgan is different? Curious.

mike

---

### Post by mashaffer on 2014-09-13
Well I thought I might have found the problem because when I launched from gladish with a terminal so that I could see any errors I got...

"ERROR: ld.so: object 'libasound.so' from LD_PRELOAD cannot be preloaded: ignored"

I got the error message twice which interestingly enough is the number of "extra" stereo channels.

Which I didn't get when launching by hand I did not get these errors. So I made a symbolic link in /usr/lib to the actual library in the x86 64 bit directory. Alas this got rid of the error message but still didn't fix the problem. However maybe it is a clue as to why the system responds differently when launched by hand.

Apparently gladish is calling for the preload of this library. Is that a clue to what may be going on?

mike

---

### Post by mashaffer on 2014-09-13
OK, so ladish_control is the command line interface. I can get it to  start the studio that I created in gladish and when doing that all the  FS instances appear but only one connects. And whenever I try to connect  or disconnect ports it complains of unknown ports but I use the client  and port names exactly as they appear on patchage. Frustrating... 

> mike@mike-MacBookPro:~$ ladish_control sconnect jOrgan-01 l_00 calf eq8_in_l
--- connect studio port "jOrgan-01":"l_00" to "calf":"eq8_in_l"
DBus exception: org.freedesktop.DBus.Error.InvalidArgs: Cannot connect unknown ports


mike

---

### Post by mashaffer on 2014-09-13
OK. Weird. Patchage labels are not the same as ladish. I have to use the ladish client names. Also Patchage sees all of the fluid synth elements (JO outputs) but they do not appear in the ladish dump thus one can't connect them with ladish... only with patchage. And of course the connections made with patchage can not be saved by ladish. So until I can figure out how to get ladish to recognize the other outputs I guess I am stuck with QjackCTL. Harrumph!

> mike@mike-MacBookPro:~$ ladish_control sgdump
--- dump studio graph
"Hardware Capture"
  "capture_1" [output audio]
  "capture_2" [output audio]
"Hardware Playback"
  "playback_1" [input audio]
  "playback_2" [input audio]
"PulseAudio JACK Sink"
  "front-left" [output audio]
  "front-right" [output audio]
"PulseAudio JACK Source"
  "front-left" [input audio]
  "front-right" [input audio]
"EQ"
  "eq8_in_l" [input audio]
  "eq8_in_r" [input audio]
  "eq8_out_l" [output audio]
  "eq8_out_r" [output audio]
"organ"
  "l_00" [output audio]
  "r_00" [output audio]

4 connections:
"EQ":"eq8_out_l" -> "Hardware Playback":"playback_1"
"EQ":"eq8_out_r" -> "Hardware Playback":"playback_2"
"organ":"r_00" -> "EQ":"eq8_in_r"
"organ":"l_00" -> "EQ":"eq8_in_l"


mike

---

