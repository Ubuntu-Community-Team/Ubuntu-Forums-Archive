---
title: "Audacity &amp; Rakarrack"
date: 2012-09-24
forum: Ubuntu Studio
---

### Post by tnob on 2012-09-24
[FONT="Arial"]Greetings all,

A long-standing wish of mine has been to record the variety of electric string instruments I play (bass, guitar, banjo and ukulele) - so as to create a virtual ensemble. For your information: I'm running **Ubuntu Dream Studio 12.04** - and the console in use is a 2Gb RAM Dell Optiplex desktop. 

So far, I have been staring myself blind on what Ardour has on offer- but I find its multi-faceted splendor rather daunting, to be honest. And not exactly user-friendly, too, at first sight. Besides, Ardour has yet  to produce some sound from my headset, but to this day I still don't get any - in spite of some excellent external help acquired, over the years. I also heard a whisper that UNIX has indeed some drawbacks, with respect to audio. 

Trying for other options for multitracking, I studied various aspects of Audacity - over one weekend - through tutorials on YouTube. Pleased with what I saw, I now believe that Audacity may be very much more suited to my needs: it seems really versatile and rather more straightforward than Ardour.

My idea now is to link up R**akarrack** with **Audacity** - the former for multi-effects in general (and the added bonus of turning the sound of the lower strings of an electric guitar into an electric bass's). On how best to go about here YouTube Google and all the rest, however,let me down. And so I'm hoping, of course, for some helpful suggestions from you lot out there.

My issues recapped:

     - **Ardour**: no sound from headphones, at attempting to insert   string instrument wave; no playback either. 
     - The source of this problem must be somewhere in **Jackctl**, surely. Several people with excellent Ubuntu expertise have tinkered with it, over the years - but to no avail, so far. The fault has been declared fixed several times over now, yet it seems to me that the system consistently "snaps back" to default settings. Can that be?
     - **Audacity & Rakarrack**: how best to set-up those two in order to use them simultaneously? In other words: I'd need those Rakarrack effects in Audacity.

Thank you very much.

tnob[FONT="Arial"][/FONT][SIZE="2"][SIZE="1"][/SIZE][/SIZE]



[/FONT]

---

### Post by orange2k on 2012-09-24
I suggest that you request that a mod moves this thread to ubuntu-studio section of the forum so it would get noticed by people who are better familiar with this topic...

edit: oh I see you use Ubuntu Dream Studio, but still...

---

### Post by sgx on 2012-09-29
> **tnob said:**
> [FONT="Arial"]Greetings all,

A long-standing wish of mine has been to record the variety of electric string instruments I play (
     - **Audacity & Rakarrack**: how best to set-up those two in order to use them simultaneously? In other words: I'd need those Rakarrack effects in Audacity.

Thank you very much.

tnob[FONT="Arial"][/FONT][SIZE="2"][SIZE="1"][/SIZE][/SIZE]

[/FONT]
Hi, select jackd as the audio device in audacity preferences.
Select your soundcard in qjackctl. (see recent jackd topics in this forum) 

For now,
Start a constant sound source, modest volume, and connect it to your soundcard line-in
Start qjackctl, and press the Connect button, on the main screen, lower left.
A panel opens with three tabs, select the Audio tab on the left.

Start  rakarrack, and change it's output preferences to stereo, if desired.
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

This is all simple, after the third or fourth time, but the results are excellent. Well, 20th and 21st, for me :(
Cheers

---

### Post by Precipitous on 2012-10-08
> **sgx said:**
> Hi, select jackd as the audio device in audacity preferences.
Select your soundcard in qjackctl. (see recent jackd topics in this forum) 

For now,
Start a constant sound source, modest volume, and connect it to your soundcard line-in
Start qjackctl, and press the Connect button, on the main screen, lower left.
A panel opens with three tabs, select the Audio tab on the left.

Start  rakarrack, and change it's output preferences to stereo, if desired.
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

This is all simple, after the third or fourth time, but the results are excellent. Well, 20th and 21st, for me :(
Cheers
@sgx:  Excellent tutorial! I am sure that a lot of people will find it to be extremely useful.

@tnob:  I do most of my recording and editing in Audacity, and have had very good results running Rakarrak in real-time with synths, guitars, basses, etc.  From what you are describing it sounds as though this combination will be perfect for you...  **One very important point that can not be stressed enough**, though, is that if you want to record the effected output of Rakarrak in Audacity, you have to set up qjackctl correctly. Pay extra close attention to the following section of sgx's wonderful tutorial: > To record Rakarrack output, connect Rakarrak on the left, to Portaudio on the right.
If you don't want the 'dry' signal also recorded, disconnect System on the left, from Portaudio on the right. Best of luck to you!

---

### Post by sgx on 2012-10-10
Thanks for the kind words!
More music in hard times, is a good thing. :guitar:

Since some respected musicians always record separate wet and dry tracks, so 'lucky riffs' of the dry track, can later be auditioned with various ampsims/fx, I thought I would do a simple experiment.

I set up qjackctl, Calf Monosynth, rakarrack, timemachine,
and audacity. I recorded some bars of monosynth routed to
rakarrack fx with timemachine, and at the same time,
recorded the dry signal, routed to audacity.

Then I named and exported the audacity track, and re-named
the timemachine track with similarity.

Next, quit all apps, and restart audacity
(away from using qjackctl) and import both tracks, zoom in
and trim the beginning points.

The trim need not be identical, and various effects are achieved
by staggering them in different increments. Extra hands for
drummers, anyone? :wink:

Users of Ardour and Qtractor can likely do this all in one
interface, but some may like the simplicity, and rendering
options enabled by exporting multiple tracks in audacity.

Remember when exporting two or more tracks, they get rendered,
and the volume of the individual tracks should be lowered.
as the volume of all tracks will be summed, and can quickly
overload the signal.

Select a track, and use the amplify plugin, with negative values,
to lower it's volume. The more tracks, the greater the negative value. 

So two normalized (full volume) tracks may need a -4.0 value
applied to each, before the export renders the new track, and rudimentary mixing can be done: if one part is desired to be much quieter than another, just give it an appropriate negative value.

A few experiments will get you in the ballpark, and the newly
rendered track can always be amplified again, plus or minus.

The host of ladspa fx are also a boon to audacity renders,
for example, render a track with a phaser panned hard left,
or as mono, and then render the same track again,
but with a flanger, panned hard right or mono.
Import the now varied tracks, and set the desired levels,
to achieve some nicely creative modulations. The sonic sky
knows no limits.
Cheers

---

### Post by Precipitous on 2012-10-10
@sgx - Excellent ideas! Being a huge fan of textures and slowly evolving modulations I am anxious to experiment with them... 

In a similar vein - One of my favorite Audacity tricks that works exceptionally well for ambient music is to select a track (usually washes, drones, etc.), then go to the Edit menu and select Duplicate. This makes a copy of the selected track. I then repeat this process so there are three identical tracks. Next I select one of these tracks and apply the Change Speed effect, set to -50%. This drops the pitch an octave and stretches the track to double the original length. After this I add enough silence to the end of one of the other identical tracks to double its length, then apply a feedback delay (to the entire track) set to anywhere from 15 to 25 seconds. I then run the feedback delay again, this time set to a longer length (usually about 10 seconds longer than was used the first time). I can then set the panning for each track  to separate them in the mix, set the appropriate levels and (usually) time-shift the original track so that it ends at roughly the same time as the two copies that are twice as long....  This makes for an incredibly textural and complex backdrop that will stand wonderfully on its own, or can be used as a canvas upon which to add melodic elements, field recordings, etc.

For more interesting ideas of the types of processes and effects Audacity is great for I would urge you to go to my SoundCloud page: [https://soundcloud.com/occurrences-in-rain](https://soundcloud.com/occurrences-in-rain) then click the individual track titles to bring up their separate pages. I have posted detailed descriptions of the instrumentation, effects, manipulations, etc. for each one...

---

### Post by sgx on 2012-10-10
Thanks for sharing those techniques, I'll happily try them
this weekend, and also try learning some new tricks
from your sound cloud. 'Requiem For Damaged Children'
is exellent. 
Cheers   :popcorn:

---

### Post by Precipitous on 2012-10-11
> **sgx said:**
> Thanks for sharing those techniques, I'll happily try them
this weekend, and also try learning some new tricks
from your sound cloud. 'Requiem For Damaged Children'
is exellent. 
Cheers   :popcorn:
@sgx - Thank you for listening to my material, and for your incredibly kind words!

---

### Post by tnob on 2012-10-18
Greetings all,[FONT="Arial"][/FONT].

Because my hard disk was about to collapse, I haven't revisited this thread for a while. 

I'm the guy who asked the question in the first place - and I'm really, honestly and totally blown away by this multitude of helpful suggestions received.

I'm especially pleased with this extensive manual provided by one contributor. And yes, I agree with another: this will be hugely practical for legions trying to get to grips with Ubuntu Studio (like I am).

Hence, my gratitude to all of you out there knows no bounds!

tnob

---

