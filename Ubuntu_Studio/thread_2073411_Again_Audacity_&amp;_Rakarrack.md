---
title: "Again: Audacity &amp; Rakarrack"
date: 2012-10-19
forum: Ubuntu Studio
---

### Post by tnob on 2012-10-19
[FONT="Arial"][/FONT] Greetings all,

Below is sgx's helpful tutorial, of recently, on how to connect Rakarrack to Audacity. Happily giving it a try, I fell at the first hurdle: at "*select jackd as the audio device in audacity preferences*".

Here is sgx's contribution in full, once more:
[FONT="Arial"][/FONT]
(Quote:) [I]Hi, select jackd as the audio device in audacity preferences.
 Select your soundcard in qjackctl. (see recent jackd topics in this forum) 

 For now,
 Start a constant sound source, modest volume, and connect it to your soundcard line-in
 Start qjackctl, and press the Connect button, on the main screen, lower left.
 A panel opens with three tabs, select the Audio tab on the left.

 Start rakarrack, and change it's output preferences to stereo, if desired.
 (You open it's preferences, select by mouseclick the un-highlighted half of the output.)
 Press Rakarrack 'FX On' button under the file menu, to start the fx.

 Back in qjackctl Audio panel, select System on the left half,
 and select Rakarrack on the right half, and press connect,
 (on this Connection panel, not on the opening gui) a line is drawn
 to designate connection. (If you now click the > widget by System,
 the System outputs will be fully exposed, and you will see
 lines are displayed for both left and right of stereo signals)

 Select Rakarrack on the left half, and System on the right half, and press connect,
 again, a line is drawn. (If you clicked the > widget mentioned above, you must
 now manually connect the other half of the stereo pair)

 Now your constant sound should be played, in stereo, through rakarrack,
 into your soundcards speakers or headphones,
 4 lines crisscrossing the gui indicating connection.

 To record, start Audacity, but don't create a track, just press record,
 and it automatically connects in qjackctl, creates a track, and begins recording
 the dry, unaffected sound, using the nikname 'portaudio', on the right side of the panel.
 (Now 6 lines are drawn in the qjackctl gui.)

 To record Rakarrack output, connect Rakarrak on the left, to Portaudio on the right.
 If you don't want the 'dry' signal also recorded, disconnect System on the left,
 from Portaudio on the right. The choice is yours.

 Pressing pause in audacity, just pauses recording until you press
 pause a second time. Pressing 'stop', and pressing record again, launches a new
 track to record on. Use the option best suited to your work.

 (the latestversion of Audacity I have is 2.02)

 I prefer the simple timemachine for basic high quality recording,
 and import the tm-xx-xx-xx.w64 recordings into audacity, for editing, conversion, and export.

 Media players like aqualung, vlc, xmms, xine etc with the jackd module installed by synaptic,
 can play an audio file into timemachine, using the same connections process,
 while you record a second part, with the first, a simple but quality 24 bit overdub.

 Some media players only appear in qjackctl
 when you press play, so press play, then press pause in the player, make your connections,
 press Record in timemachine, and press play again (or pause a second time, depending
 on the players implementation.) and you are rwadt to overdub.

 This is all simple, after the third or fourth time, but the results are excellent. Well, 20th and 21st, for me 
[/I] (Unquote)

I went to Prefences easily enough, but was slightly baffled that no mention of jackd was not anywhere to be found: not under Devices, not under Interface. I tried the entire list and every drop-down menu on my way - but no luck.

This must look really stupid, I know - but there's more of the musician than the IT boffin in me. So I thought of asking once again...

tnob

---

### Post by sgx on 2012-10-19
Hi, you have to start jackd first, so it can be seen
in the device options. If it is not running, alsa and oss
are the choices. In my case, when jackd is already running,
and I start audacity, it is chosen as default, and shows no other options.

Then, press record button in audacity, and it appears in qjackctl
as 'portaudio', on the right side of the Audio tab.

This is using V2.02 of audacity, and libportaudio.so.2

One must admit, this all seems a bit too convoluted.
But there may be a purpose to the madness, from the coders
point of view, that we musicians do not know.
Cheers

---

