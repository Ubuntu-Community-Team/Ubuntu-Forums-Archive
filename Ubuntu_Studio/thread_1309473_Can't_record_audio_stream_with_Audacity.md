---
title: "Can't record audio stream with Audacity"
date: 2009-11-01
forum: Ubuntu Studio
---

### Post by Henry Flower on 2009-11-01
Hi, first-time user of karmic koala.

I'm trying to record an audio stream (e.g. from the Internet) with Audacity.   If I select 'Start monitoring' in the input level meter, the bars fill up, but then don't change according to the audio being played.   If I start Audacity recording, no sound is recorded. I've tried selecting different recording devices; for default and pulse, the recording cursor moves very slowly (ie it takes several seconds to show one second as recorded), while for HDA ATI SB... it moves at the right speed, but still doesn't actually record.

Hope someone can help!

---

### Post by nickleus on 2009-11-02
i can't record anything either when jack is running in karmic/amd64. the cursor just stands still even though i've chosen jack in preferences for both recording and playback. i had no problems in jaunty.

---

### Post by Henry Flower on 2009-11-03
Still stuck.   I tried Rezound; it does record, but just a buzzing/static sound.   I'll happily try other software if anyone can do this with anything else.  

There seem to be some programs, like streamripper, specifically for recording Internet streams, but I don't think they work with the one I'm trying to record.   What I'd like is something to record whatever sound the computer is playing, from whatever source.

---

### Post by meho_r on 2009-11-03
Can't say about Audacity, but for recording from web did you try [HTTPRipper?](http://29a.ch/httpripper/) Just use FoxyProxy in Firefox, set a proxy as "localhost" and port "80", press "Record" in HTTPRipper and every sound that comes in your browser will be recorded (actually, downloaded as it is, no reencoding oggs/mp3s and stuff). The best way for recording from a browser I've seen. But use it for legal purposes, please :)

P.S. FoxyProxy is optional. I mentioned it because it's much easier to switch between proxy and direct connection to Internet using it.

---

### Post by meho_r on 2009-11-03
BTW, check sound properties. E.g. in "Hardware" tab, under "Profiles" I've got a lot of "Analog Surround Outputs", like 4.0, 5.0, 7.0, 4.1, 5.1, 7.1 etc. I've discovered that only with "Analog Surround 4.0 Output" recording sound from computer through Audacity or other sound recording programs works fine. If profile is anything else, I got no sound at all or get a crackling one. But still, HTTPRipper is better solution for recording from web pages.

---

### Post by Henry Flower on 2009-11-03
Ah- changing the sound properties fixed it.   Setting Hardware to Analog Stereo Output got it working. Thanks!

---

### Post by nickleus on 2009-11-04
> **Henry Flower said:**
> Ah- changing the sound properties fixed it.   Setting Hardware to Analog Stereo Output got it working. Thanks!
son of a gun you're right! yahoooooo! thank you =)
to answer your question though, another program to record sound with is ardour. that is what i have been using while i couldn't get audacity to record. if you use ardour, do the rerouting of sound using patchage.

how do we mark this thread as [SOLVED]?

---

### Post by nickleus on 2009-11-04
> **nickleus said:**
> how do we mark this thread as [SOLVED]?
or not quite yet i'm afraid. i can record with audacity in non-jack mode, but once i turn on jack and try to record something i get nowhere. in preferences > devices, when i choose jack, i get "no devices found" in the playback and recording dropdown menus.

---

### Post by nickleus on 2009-11-04
> **nickleus said:**
> or not quite yet i'm afraid. i can record with audacity in non-jack mode, but once i turn on jack and try to record something i get nowhere. in preferences > devices, when i choose jack, i get "no devices found" in the playback and recording dropdown menus.
ok, when i open *qjackctl > setup*
then choose **Playback Only** in the *Audio* dropdown box, then i'm able to pick ONE PROGRAM ONLY to record in audacity. i still don't get **system** in the dropdown box in *audacity > preferences > devices > recording*
i only get a list of programs capable of outputing sound, e.g.* zynaddsubfx, hydrogen*, etc.
there's no **system** option (record everything from the sound card)

---

### Post by alexthunder on 2010-02-15
Install  PulseAudio  Volume Control and you will be able to record
[http://stream-recorder.com/forum/showpost.php?p=15384](http://stream-recorder.com/forum/showpost.php?p=15384)

As for HTTPRipper, it supports HTTP streams only. Besides I don't think it is the best solution for downloading audio streams. You can try some dowloaders from here
[http://all-streaming-media.com/record-video-stream/all-streaming-video-recording-software.htm](http://all-streaming-media.com/record-video-stream/all-streaming-video-recording-software.htm)

---

### Post by nickleus on 2010-02-15
thank you!!!

---

### Post by tophill on 2010-05-25
> **Henry Flower said:**
> Ah- changing the sound properties fixed it.   Setting Hardware to Analog Stereo Output got it working. Thanks!

This (changing Sound Preferences / Hardware / Settings from "Analog Stereo Duplex" to "Analog Stereo Output") worked for me too.  Thanks.

---

### Post by sgx on 2010-05-25
> **nickleus said:**
> or not quite yet i'm afraid. i can record with audacity in non-jack mode, but once i turn on jack and try to record something i get nowhere. in preferences > devices, when i choose jack, i get "no devices found" in the playback and recording dropdown menus.
The odd-duck about audacity with jackd, is that it only appears AFTER
you press the audacity 'record' button, and it is labelled portaudio,
instead of audacity. So press record, press pause, go to your connections gui, make the connections, press pause again when ready to record.

Hopefully this longstanding nonsense has, or will get fixed.:popcorn:

---

### Post by dwpbike on 2010-07-03
> **meho_r said:**
> BTW, check sound properties. E.g. in "Hardware" tab, under "Profiles" I've got a lot of "Analog Surround Outputs", like 4.0, 5.0, 7.0, 4.1, 5.1, 7.1 etc. I've discovered that only with "Analog Surround 4.0 Output" recording sound from computer through Audacity or other sound recording programs works fine. If profile is anything else, I got no sound at all or get a crackling one. But still, HTTPRipper is better solution for recording from web pages.

dead on, dude, with the "surround".  been fighting this on fedora and now ubuntu.  doesn't make sense, but it works.  tanks

---

### Post by mango42 on 2010-07-04
Not sure whether this is relevant but for us nutters on flaky wifi out in the stix, the best approach I've found for streaming net sound or video is just let the whole stream buffer then, *before looking or listening to anything else*, go to the /tmp folder in your file system and copy/paste the latest mp3/flv/whatever file before it gets overwritten.

Then load it into your favorite editor and carve to taste.

---

### Post by Subito Piano on 2011-05-28
Kudos, Henry FLower -- this was costing me WAY too much time, but i found your post.  Happy camper once again.  :-)

---

### Post by demarshall on 2011-06-22
> **alexthunder said:**
> Install  PulseAudio  Volume Control and you will be able to record
[http://stream-recorder.com/forum/showpost.php?p=15384](http://stream-recorder.com/forum/showpost.php?p=15384)

As for HTTPRipper, it supports HTTP streams only. Besides I don't think it is the best solution for downloading audio streams. You can try some dowloaders from here
[http://all-streaming-media.com/record-video-stream/all-streaming-video-recording-software.htm](http://all-streaming-media.com/record-video-stream/all-streaming-video-recording-software.htm)

It was actually steps 3 to 5 on this page that solved my problem...

[COLOR="Red"]3. Open PulseAudio Volume Control ("Applications" -> "Sound & Video" -> "PulseAudio Volume Control") and leave it open.
The first time you use a recording program you need to to edit the recording settings of PulseAudio Volume Control. It should remember your settings after rebooting.
4. Open Audacity and hit the "Record" button.
5. While Audacity is recording, open PulseAudio Volume Control and select the "Recording" tab. It will show "Alsa plug-in Audacity. Alsa capture from" and a combo-box. Choose the "Monitor of internal audio..." if you use an internal sound card. [/COLOR]

---

### Post by Flaggmann on 2011-06-22
To have inputs on jack available one probably has to open the qjackctl window and access the connections panel and drag and drop a connection between the source application and the capture or record ports on the opposite side of the connections page. 

To be able to do that you might have to be sure that the program prefs for playing the music are set to use jack as well otherwise the sources won't show up in the jack connections window. Some players won't show until the play button is pressed, even though the application is open on the screen.

---

