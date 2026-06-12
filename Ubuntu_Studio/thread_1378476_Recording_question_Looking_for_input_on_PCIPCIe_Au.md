---
title: "Recording question: Looking for input on PCI/PCIe Audio Interface"
date: 2010-01-11
forum: Ubuntu Studio
---

### Post by Th3Professor on 2010-01-11
So I have a firewire mixer that is not currently supported. I'm going to revert back and swap it out for an analog (only) mixer and use a PCI or PCIe card (audio interface).

I understand M-Audio and RME are the most supported brands for cards.

I am curious what interface would work well with recording/playback of:

2 microphones
1 hi-z guitar
1 hi-z bass
1 midi in
1 midi out/thru
2+ TRS(1/4")

The idea is, I'd like to connect all of the instruments into a mixer (either Mackie or Yamaha), and connect that analog mixer into the PCI/PCIe audio interface, then setup JACK/Ardour and other programs to record those instruments.

I'd like to be able to do the following:
Singer, guitarist, bassist, drummer (midi or trs), and optional usb/midi keyboard, all simultaneously perform their music while each instrument records simultaneously as *separate* tracks into the computer. I'd also like to be able to record a track or tracks and play them back while simultaneously recording a new track(s).

Also, are there any recommended analog mixers that would work well with this set-up? (Mackie or Yamaha brands only.)

Thank you!

---

### Post by Th3Professor on 2010-01-12
<bump>

---

### Post by trulan on 2010-01-12
Hi Professor, (me again),

I can't recommend any PCI cards, but I can give a little input on a mixer.  Pretty much any mixer will work.  I've hooked up my firepod to record live a few times, to our old EV mixboard, and our band just bought this one
[http://pro-audio.musiciansfriend.com/product/Yamaha-MG206C-Mixer?sku=630272](http://pro-audio.musiciansfriend.com/product/Yamaha-MG206C-Mixer?sku=630272)
But I haven't had a chance to use it yet.  Basically, you pull your signal off the insert of each channel, with a 1/4" TRS to dual 1/4" insert cable.  The guy in our band actually found a 'recording snake', four insert cables in one.  And if you want signal coming out of your mains, hook the line out of your soundcard back into the channel's insert.  Using this setup I have recorded several hour-plus gigs of ours, but it's been more of an expetiment thus far and I haven't produced anything this way.  But it works very well.

So you can use any mixer that has inserts on each channel, and I'm sure any Mackie or Yamaha or other respectable analog mixboard will meet that criteria.  Just so enough of channels have inserts for the number of channels you want to record.  (The Yamaha we got has 12).

---

### Post by Th3Professor on 2010-01-13
Hey there, thanks for the input.

My recent mixer purchase was a mistake, incompatible firewire. I am hoping to not repeat that. :(

That's why I'm reverting to an analog only mixer and an audio interface that works with Linux and also works with the analog mixer given the specific instruments I need to record.

But I need something in between the computer and mixer that works.

You've mentioned your Presonus Firepod before. The fact that it's firewire is pretty scary for me, personally, considering I recently dropped a significant chunk of $$$ on a firewire mixer that I thought was compatible but it actually isn't (even after getting another firewire PCI card). Speaking of firewire, in addition to my motherboard firewire (which is compatible with Linux), I also have [ [this firewire card]("http://www.amazon.com/dp/B000A2813G"). ]

If there is a PCI or PCIe audio interface that would work well for my instrumentation/set-up, I'll go for that. I don't mind breakout cables/box. But to record *more* than 2 simultaneous tracks, would I need to connect all of them directly into that audio interface? Or could I connect them into the mixer and mixer into the interface and still get more than 2 simultaneous tracks?

As far as mixers go I prefer either Mackie or Yamaha. I've looked at the ones you mentioned, I'm considering a variation of one of those.

Though, I'm not going to select a mixer until I know exactly which "audio interface" I will be using in between my computer and mixer. And I need an interface that will allow for simultaneous recording/playback of more than 2 tracks.

I will have 2 basic recording scenarios:
1. Recording alone, playing all of the instruments (guitars, bass, drumset, keys, etc.) one at a time, and will need to playback tracks while simultaneously recording new tracks.
2. Recording in a group, multiple people playing all of the instruments (guitars, bass, drumset, keys, etc.) all at the same time, and will need for those instruments to each simultaneously record as separate tracks into the computer.

Right now I am only sure of one thing, the instruments-
2 XLR (acoustic guitars)
2 hi-z 1/4" (electric guitar & bass guitar)
2 TRS 1/4" (electronic drumset "live" via TRS 1/4")
1 MIDI (electronic drumset or keyboard as midi)
1 USB/MIDI keyboard (M-Audio Axiom 49 via USB)

Next is finding an audio interface that works in Linux.

Then it'll be time to select the mixer.

Are there any specific RME or M-Audio (or other brand (similar to e-mu 1616m?)) audio interfaces that work well with the 8 specific instruments mentioned above and are also 100% compatible/supported in Linux?

It sounds like I'd do fine with an 8 channel mixer, though if I can get away with getting more channels in the mixer that will come in handy later on down the road.

The actual audio interface, however, can be only 8 channels for now.

I don't mind having the extra strips/channels on a mixer (they will come in handy for live performances). 8 of those strips = 8 channels in the audio interface. The big question, however, is what interface fits my specific instrumentation?

Also, this might sound weird but, in order for the analog mixer to record into the computer with more than 2 simultaneous tracks, would I need to connect all mixer channels into the "audio interface"? (AKA, getting a mixer that has lots of busses/outs?) The way I understand it is, and I'm guessing here, that if I just use the 2 main outs from the analog mixer into the audio interface, that I might *not* get more than 2 simultaneous tracks.  :confused:

Thanks!

---

### Post by hardcopy on 2010-01-13
you could make do with an 8 channel mixer as long as there are direct outs/inserts for each channel, although inserts are technically a send/return on a single cable so need special cables (and patching) to utilise.

if you wanted a bigger mixer and more freedom to route mixer channels to soundcard channels you would want 8 busses.

by using a mixer you negate the need for specialised input channels on your sound card- the mixer is the pre amp.

something like the M-Audio 1010 seems like it fills your needs, although you can always check the ALSA site if another soundcard catches your eye.

hope that helps.

---

### Post by Th3Professor on 2010-01-13
It looks like I might have to select the mixer first, then the audio interface.

> **hardcopy said:**
> you could make do with an 8 channel mixer as long as there are direct outs/inserts for each channel, although inserts are technically a send/return on a single cable so need special cables (and patching) to utilise.

if you wanted a bigger mixer and more freedom to route mixer channels to soundcard channels you would want 8 busses.

by using a mixer you negate the need for specialised input channels on your sound card- the mixer is the pre amp.

something like the M-Audio 1010 seems like it fills your needs, although you can always check the ALSA site if another soundcard catches your eye.

hope that helps.

The only true 8 bus mixers are 32 channel mixers that range up in the $1500 to $2k range.

The closest thing I could find to that (in a google search) was this:
[http://www.zzounds.com/item--MAC1642VLZIII](http://www.zzounds.com/item--MAC1642VLZIII)
The Mackie 1642 VLZ3 16-channel 4-bus mixer.

It has more strips than I currently need but I could grow into it, especially with XLR/mics.

Some of the basic specs on the 1642 VLZ3:

16 high-headroom line inputs (4 stereo pairs, 8 mono)
4 Aux sends, level, pan, -20dB/Solo and OL/Mute LEDs on each channel
4 stereo Aux returns, 8 Direct outs, 4 stereo Group/Bus outputs
Balanced 1/4 in. inputs and outputs (except inserts)

The confusing bit about those specs deals with the outputs:
8 direct outs <--- mono?
4 stereo group/bus outs <--- stereo? (aka 8 mono?)
and balanced 1/4" outs <--- is this just a general reference to the type (TRS)?

How might I set that up to basically function with "8 busses"?

It appears there are no hi-z features, though that isn't a concern. The electric guitar & bass guitar will be better off mic'd anyway. (Will have to get some more microphones of course.)

There are clearly no digital features in the mixer, which is completely fine, I'm actually avoiding that so I can get an audio interface for the computer that has better chances of being compatible. The MIDI part of the elec.drumset, when not feeding it into the mixer via TRS(1/4"), could connect to a MIDI i/o on the audio interface that I get. The USB/MIDI keyboard can simply stick with USB. That pretty much covers all of it.

So a revised look at the instruments and method of connecting them:
4 XLRs (guitars, basses, etc.)
2 TRS 1/4" (elect.drumset)
1 MIDI I/O (elect.drumset (alternative))
1 USB/MIDI keyboard (into computer's USB)

If I use TRS w/ elec.drumset along with the XLRs, that's 6 outs from the mixer that I need. And only 1 more simultaneous record/playback channel with the USB/MIDI keyboard, which I'm assuming has nothing to do with the mixer's outs, and would require mixing entirely on the computer (and the usb/midi keyboard). Is that right?

Perhaps the question should be:

How might I set up the outs from the mixer so there are enough independent outs leading to the audio interface?

Perhaps?:
4 XLRs = the 4 Busses
and
2 TRS(drums) = 2 of the "8 direct outs"? (Leaving 6 free?)

I must've done the "mixer math" incorrectly. I seem to be "mixing" up things.

The next question is:

Which audio interface would work with that arrangement (with that Mackie 1642 VLZ3 mixer)?

Would the M-Audio Delta 1010 still work with that?

Or would the M-Audio Delta 1010LT work?

(Still wanting to be able to record all of the instruments simultaneously as separate tracks on the computer.)

Thanks!

Edit-
Here's the URL of an image of the back of that mixer-
[http://cachepe.zzounds.com/media/quality,85/brand,zzounds/1642-VLZ3-Rear-037405b39dc83cdd1fde430f5a7563ac.jpg](http://cachepe.zzounds.com/media/quality,85/brand,zzounds/1642-VLZ3-Rear-037405b39dc83cdd1fde430f5a7563ac.jpg)
And the top of the mixer-
[http://cachepe.zzounds.com/media/quality,85/brand,zzounds/1642-VLZ3-Top-e117eb85437daa031bad3e7618cf865a.jpg](http://cachepe.zzounds.com/media/quality,85/brand,zzounds/1642-VLZ3-Top-e117eb85437daa031bad3e7618cf865a.jpg)

Edit2-
Another question:
The M-Audio Delta 1010-LT appears to have the following "ins":
1 MIDI
6 RCA ins
2 Mic/line ins
...and everything is apparently unbalanced...
Meanwhile, the Delta 1010 appears to have these "ins":
1 MIDI
8 bal/unbal 1/4" ins
...apparently offering an all balanced possibility...

The M-Audio Delta 1010  (w/ breakout box) appears to be more appropriate, though it is also nearly $800 (instead of the cheap price for the "cheap" 1010LT).

Is there a less expensive alternative to the Delta 1010 that also offers 8 balanced ins/outs along with MIDI I/O?

And kind of on a different subtopic of this subject-
Would I need to get a "wordclock" device?
How might I use the s/pdif with all of this?

Thank you!

---

### Post by cchhrriiss121212 on 2010-01-13
That mixer looks well suited to what you want. As a cheaper alternative to the delta 1010, you could just get 2 delta 44s which will still offer the same quality.
Most PCs have at least 2 PCI slots so you should be fine installing them, here is I recent thread I saw which explained how to use 2 sound cards with jack: [http://ubuntuforums.org/showthread.php?t=1377954](http://ubuntuforums.org/showthread.php?t=1377954)

---

### Post by hardcopy on 2010-01-13
ok that mackie mixer has a lot of options for recording, lets see if i can give you a clearer picture of how it all works-

the first 8 channels can be hooked up directly to your DAW using the direct outs (post fader) this won't interfere with the signal path of the channels
you could use these channels alone for all your current sound sources just fine (to save you getting mic's for the electric guitars check if the amps you're using have direct injection- this will give a line level signal into the desk)

channels 9&10 can either be used as mono mic channels or stereo/mono line inputs. 11&12 are stereo/mono line inputs. to record these you could hook them up to either the busses or perhaps use effects sends linked up to the soundcard inputs.

delving into the sub-groups tells me that whilst there are only 4 busses, each bus has 2 outputs, this allows the signal to be wired to 2 inputs at the same time, basically so that an 8 track recorder can be used without having to re-patch anything (ie record on channels 1-4, then record on channels 5-8, just make sure you arm the correct channels ;) ) 
sub groups are set up for stereo operation- select the pair you want to send to on the channel, the pan of the channel will direct the signal to either or both (you can then assign the sub group to L&R if you want a mono record channel to be centered in the mix).

to record what you want, i would put mono sources into the first 8 channels and hook the direct outs to the soundcard, and stereo sources i would use in stereo channels to be sure of equal gain, eq and fader levels and record from a sub group.
channels & routing would be something like:
CH1: mic acoustic guitar, direct out to DAWin1
CH2: mic acoustic guitar, direct out to DAWin2
CH3: mic/line electric guitar, direct out to DAWin3
CH4: mic/line BASS, direct out to DAWin4
CH9: line stereo electric drums, set to sub1-2, sub out 1 to DAWin5 & sub out 2 to DAWin6

in the future, with a combination of direct outs, sub groups, and cheeky effects sends usage you could simultaneously record 14 channels (16 if you want to record the main mix too) with the mackie mixer. if you think this is beyond what you will need you could think about getting a lesser mixer.

midi recording of the drums could be useful, but at some point you will still need to record the drums if you want to mixdown the track.

i think to begin with you could make do with the 1010LT (assuming it works in linux), and upgrade to something bigger and better to make use of the possibilities the desk gives at a later date.

wordclock is used for syncing digital signals. if you have something to do the A-D conversion (an old DAT machine for example) you could the spdif as another stereo input on the 1010.

---

### Post by Th3Professor on 2010-01-14
> **cchhrriiss121212 said:**
> That mixer looks well suited to what you want. As a cheaper alternative to the delta 1010, you could just get 2 delta 44s which will still offer the same quality.
Most PCs have at least 2 PCI slots so you should be fine installing them, here is I recent thread I saw which explained how to use 2 sound cards with jack: [http://ubuntuforums.org/showthread.php?t=1377954](http://ubuntuforums.org/showthread.php?t=1377954)

That's a good idea w/ 2 Delta 44s, though it looks like they might have some limitations compared to 1 1010. (Not the 1010LT but the actual 1010.) Thank you for the mention of that though, and the link to the other thread, I'll bookmark that thread.

I'm going to try the Mackie 1642-VLZ3 with the M-Audio Delta 1010 (the 1010, not the 1010lt). Hopefully that set-up will do the trick. And a couple additional microphones to add to the mix.

> **hardcopy said:**
> ok that mackie mixer has a lot of options for recording, lets see if i can give you a clearer picture of how it all works-

the first 8 channels can be hooked up directly to your DAW using the direct outs (post fader) this won't interfere with the signal path of the channels
you could use these channels alone for all your current sound sources just fine (to save you getting mic's for the electric guitars check if the amps you're using have direct injection- this will give a line level signal into the desk)

An amp has "line out" (1 output) in the back along with "effects" ("send" and "receive").

Another amp has "line out" (2 outputs, left and right).

This isn't part of the guitar/bass amps but there's an addition piece of equipment in this set-up, an old 4 channel power amp.

The front of the PA:
4 Channels, balanced inputs (1/4"), each with 4 knobs (level, low, high, reverb)
1 Master (eq with low, mid, high)
1 "Aux. In" input (1/4"),  main level, and reverb return

The back of the PA:
2 jacks (1/4") for speakers
2 jacks (1/4") for effects loop (send and receive)

I'm not really sure how to utilize that power amp with the rest of the equipment. Any ideas?

But as far as the 1st 8 outs on the mixer, that'd be perfect:
Direct Outs 1-8 (of Mackie 1642-VLZ3)
into
Input 1-8 (of M-Audio Delta 1010)

> **hardcopy said:**
> channels 9&10 can either be used as mono mic channels or stereo/mono line inputs. 11&12 are stereo/mono line inputs. to record these you could hook them up to either the busses or perhaps use effects sends linked up to the soundcard inputs.
For the recording setting, would I be maxed out on available inputs in the Delta 1010 (inputs 1-8 ) if I use the Mackie's Direct Outs 1-8?

Or could use the outs on the Delta (outputs 1-8 ) to send signals back to the mixer (where to?), and then feed that signal from the mixer back into the mixer itself via something like "insert" or "aux"? (If adding to the same instruments.)

Basically, I'm wondering how I can utilize the 9-16, inserts, auxs, etc. features of the mixer and the 8 outs of the Delta - in a home studio recording situation. That is, how to use the features beyond the mixer's "8 Direct Outs" with the Delta's 8 inputs.

The Delta has the MIDI I/O, I can hook the drums up to that as an alternative or addition to the TRS (1/4") connection to the Mackie. I wonder how that would work - having the elect. drumset go into both sources at the same time, one as "live" and one as MIDI.

> **hardcopy said:**
> delving into the sub-groups tells me that whilst there are only 4 busses, each bus has 2 outputs, this allows the signal to be wired to 2 inputs at the same time

This part is confusing.

> **hardcopy said:**
> basically so that an 8 track recorder can be used without having to re-patch anything (ie record on channels 1-4, then record on channels 5-8, just make sure you arm the correct channels ;) )

Also confusing. :?

> **hardcopy said:**
> sub groups are set up for stereo operation- select the pair you want to send to on the channel, the pan of the channel will direct the signal to either or both (you can then assign the sub group to L&R if you want a mono record channel to be centered in the mix).

I'll be recording stereo tracks. I figure that'd entail:
1 strip pan left + 1 other strip pan right = 1 instrument (via 2 microphones).

The sub group stuff gets a little confusing.

> **hardcopy said:**
> to record what you want, i would put mono sources into the first 8 channels and hook the direct outs to the soundcard, and stereo sources i would use in stereo channels to be sure of equal gain, eq and fader levels and record from a sub group.
channels & routing would be something like:
CH1: mic acoustic guitar, direct out to DAWin1
CH2: mic acoustic guitar, direct out to DAWin2
CH3: mic/line electric guitar, direct out to DAWin3
CH4: mic/line BASS, direct out to DAWin4
CH9: line stereo electric drums, set to sub1-2, sub out 1 to DAWin5 & sub out 2 to DAWin6

Okay so instead of using all 8 direct outs, basically that's:

XLRs into Mackie strips/channels 1-4 (or 1-2 with "lines" into 3-4)
Lines (1/4" TRSs) into Mackie strip/channel 9 (with "sub1-2" enabled)
...then...
Mackie's direct outs 1-4 into Delta's ins 1-4
Mackie's sub out 1 into Delta's in 5
Mackie's sub out 2 into Delta's in 6

Is that right?

(I know it's pretty much just a rephrasing of what you said but I just want to make sure I understand it.)

> **hardcopy said:**
> in the future, with a combination of direct outs, sub groups, and cheeky effects sends usage you could simultaneously record 14 channels (16 if you want to record the main mix too) with the mackie mixer. if you think this is beyond what you will need you could think about getting a lesser mixer.

For effects (to go into "aux"? or "insert"?) I figure I'll use things like effects rack mount units.

Are there any recommended solid effects units?

If you check out the image of the top of that 1642-XLZ3 mixer, the bottom of the strips have a weird labeling system, from left to right, along with each strip's channel number:

channel 1: "rec 1"
channel 2: "rec 2"
channel 3: "track 1"
channel 4: "track 2"
channel 5: "track 3"
channel 6: "track 4"
channel 7: "track 5"
channel 8: "track 6"
channels 9-10: "track 7"
channels 10-12: "track 8"
channels 13-14: "efx a"
channels 15-16: "efx b"

Any idea what that's all about?

> **hardcopy said:**
> midi recording of the drums could be useful, but at some point you will still need to record the drums if you want to mixdown the track.

Do you mean I'll still need to record a "live" type of recording (via the 1/4" "lines") if I want to mixdown the track?

Or could I still mix the track down if the drumset is performed/recorded into MIDI I/O of the Delta? (Could that signal use an "out" on the Delta into an "in" in the Mackie?)

> **hardcopy said:**
> i think to begin with you could make do with the 1010LT (assuming it works in linux), and upgrade to something bigger and better to make use of the possibilities the desk gives at a later date.

I'm going to give the 1010 (instead of the 1010LT) a try.

Do you or does anyone know if the M-Audio Delta 1010 (*not* the 1010lt) works in Linux?

> **hardcopy said:**
> wordclock is used for syncing digital signals. if you have something to do the A-D conversion (an old DAT machine for example) you could the spdif as another stereo input on the 1010.

No DAT machines. I'm trying to see if there's a way I can utilize the wordclock feature of the Delta 1010. Another digital signal... hmm... not sure.

---

### Post by hardcopy on 2010-01-14
> 
An amp has "line out" (1 output) in the back along with "effects" ("send" and "receive").

Another amp has "line out" (2 outputs, left and right).
yes, these line outs are just what you want to plug into the desk.

> This isn't part of the guitar/bass amps but there's an addition piece of equipment in this set-up, an old 4 channel power amp.

The front of the PA:
4 Channels, balanced inputs (1/4"), each with 4 knobs (level, low, high, reverb)
1 Master (eq with low, mid, high)
1 "Aux. In" input (1/4"),  main level, and reverb return

The back of the PA:
2 jacks (1/4") for speakers
2 jacks (1/4") for effects loop (send and receive)

I'm not really sure how to utilize that power amp with the rest of the equipment. Any ideas?

the efects send outputs would be the ones to use to feed a desk, althoght your amps already can do the job as i've said above.

> But as far as the 1st 8 outs on the mixer, that'd be perfect:
Direct Outs 1-8 (of Mackie 1642-VLZ3)
into
Input 1-8 (of M-Audio Delta 1010)


For the recording setting, would I be maxed out on available inputs in the Delta 1010 (inputs 1-8 ) if I use the Mackie's Direct Outs 1-8?

yes this would max out the 1010 inputs, thats why i suggested a configuration below, sorry for the confusion.

> Or could use the outs on the Delta (outputs 1-8 ) to send signals back to the mixer (where to?), and then feed that signal from the mixer back into the mixer itself via something like "insert" or "aux"? (If adding to the same instruments.)

Basically, I'm wondering how I can utilize the 9-16, inserts, auxs, etc. features of the mixer and the 8 outs of the Delta - in a home studio recording situation. That is, how to use the features beyond the mixer's "8 Direct Outs" with the Delta's 8 inputs.

you could route the 1010 outputs in a way that mirrors the record structure

so in addition to the setup i suggested
DAWout1 to mixer CH5
DAWout2 to mixer CH6
DAWout3 to mixer CH7
DAWout4 to mixer CH8
DAWouts5&6 to mixer stereo CH10

of course you will probably be doing the mix in software, so you could just hook up 2 channels to a stereo mixer channel for monitoring purposes.

> The Delta has the MIDI I/O, I can hook the drums up to that as an alternative or addition to the TRS (1/4") connection to the Mackie. I wonder how that would work - having the elect. drumset go into both sources at the same time, one as "live" and one as MIDI.


yes you could record the midi performance and the live output at the same time, this gives you the flexibility of being able to edit the drummers performance or change the kit being used at a later date, then just record another take of the drums to disk.


> This part is confusing.
ok, what i mean is that sub output 1&5, 2&6, 3&7, 4&8 on the back of the desk carry the same signal, you dont have 8 discreet sub outs, instead you have 4 sub outs, and each sub out can be directly conneted to 2 different places at the same time.



> Also confusing. :?

lets say you had an 8 track hard disk recorder, but only ever need to record 4 tracks at the same time. the mixer configuration would mean that you can have all 8 inputs on the hd recorder hardwired to the sub group outs at all times. you first 'arm' and record channels 1-4, then for the overdubs you 'arm' and record channels 1-5, no re-patching is required


> I'll be recording stereo tracks. I figure that'd entail:
1 strip pan left + 1 other strip pan right = 1 instrument (via 2 microphones).

The sub group stuff gets a little confusing.

mixers are set up for stereo operation, and as such, sub-group routing uses a combination of button selection and pan to determine where a signal goes- to understand it, i think you should ignore the existance of sub outs 5-8 completely. sub outs 1&2 are a pair, so with the 1-2 button selected and a channel panned left it goes to sub 1, panned right it goes to sub 2.


> Okay so instead of using all 8 direct outs, basically that's:

XLRs into Mackie strips/channels 1-4 (or 1-2 with "lines" into 3-4)
Lines (1/4" TRSs) into Mackie strip/channel 9 (with "sub1-2" enabled)
...then...
Mackie's direct outs 1-4 into Delta's ins 1-4
Mackie's sub out 1 into Delta's in 5
Mackie's sub out 2 into Delta's in 6

Is that right?

(I know it's pretty much just a rephrasing of what you said but I just want to make sure I understand it.)

yes you've got it

> For effects (to go into "aux"? or "insert"?) I figure I'll use things like effects rack mount units.

Are there any recommended solid effects units?
inserts and effects sends are basically the same thing but for different purposes:
inserts allow you to take a single channel and rout it to some outboard effects, then insert it back into the channel strip with the effects wet/dry state being set on the effect unit ie adding a flanger to a guitar. inserts are a break in the signal path so must return to the desk for you to hear anything from the channel.
effects sends allow multiple sources to be sent to outboard effects, and then a completely wet signal can be mixed at a level of your choosing when it returns. fx sends do not disrupt the signal path.

I> f you check out the image of the top of that 1642-XLZ3 mixer, the bottom of the strips have a weird labeling system, from left to right, along with each strip's channel number:

channel 1: "rec 1"
channel 2: "rec 2"
channel 3: "track 1"
channel 4: "track 2"
channel 5: "track 3"
channel 6: "track 4"
channel 7: "track 5"
channel 8: "track 6"
channels 9-10: "track 7"
channels 10-12: "track 8"
channels 13-14: "efx a"
channels 15-16: "efx b"

Any idea what that's all about?
i think thats just a nod to conventional mixing practises- ch1&2 as a stereo pair feed from your daw, individual mono/stereo tracks for mixing, and then 13-14&15-16 used as the effects returns- it is common to use channel strips for effects returns instead of the provided return inputs as not only are you then able to set the return level with a fader, you can also eq the returning effects.

> 

Do you mean I'll still need to record a "live" type of recording (via the 1/4" "lines") if I want to mixdown the track?

Or could I still mix the track down if the drumset is performed/recorded into MIDI I/O of the Delta? (Could that signal use an "out" on the Delta into an "in" in the Mackie?)


hopefully i answered this above, i will add that midi contains no sound data at all, it is just used to control midi devices that then create sound from that data

> I'm going to give the 1010 (instead of the 1010LT) a try.

Do you or does anyone know if the M-Audio Delta 1010 (*not* the 1010lt) works in Linux?
the ALSA site says the 1010 is supported by their drivers.

> No DAT machines. I'm trying to see if there's a way I can utilize the wordclock feature of the Delta 1010. Another digital signal... hmm... not sure.

just to clarify: spdif is a digital signal carried over either a phono or optical cable. wordclock is a sync signal sent over bnc that is necessary for proper digital syncing.

i hope thats clearing up the confusion its quite a big topic sound engineering so ask more questions if its not making sense

---

### Post by Th3Professor on 2010-01-14
Thank you for the continued input on this stuff.

I purchased the Mackie 1642-VRZ3 and the M-Audio Delta 1010.

Still need to get a couple more mics. Going in to a local store tomorrow to get a bunch of 1/4" cables to go between the Mackie & Delta devices. The 2 mics I have now are cardioid condenser microphones... I haven't decided yet if the 2 additional mics I get will be like that too or of a different variety. :?

> **hardcopy said:**
> you could route the 1010 outputs in a way that mirrors the record structure

Okay, let's update the paraphrased version of that, and I think I need to revise the "9-10" and "11-12" bit, maybe not, I hope this is right-

1. XLRs into Mackie strips/channels 1-4 (or 1-2 with "lines" into 3-4)
2. Lines (1/4" TRSs) into Mackie strip/channel "9-10" (with "sub1-2" enabled)
3. Mackie's direct outs 1-4 into Delta's ins 1-4
4. Mackie's sub outs 1-2 into Delta's ins 5-6
5. Delta's outs 1-4 into Mackie's strips/channel 5-8
6. Delta's outs 5-6 into Mackie's strip/channel "11-12"

Where would the Mackie's strips/channels 5-8 & "11-12" go out to?

Is that for if I have an external recording device to send those signals to?

Would the Mackie's 5-8 outs be "direct outs" 5-8 and 11-12 outs be "sub outs 3-4" (with "sub3-4" enabled on strip 11-12)?

At one point I considered this:
[http://www.tascam.com/products/ss-r1.html](http://www.tascam.com/products/ss-r1.html)
The Tascam SS-R1. It was highly recommended by an old teacher. It's a bit pricey but I'm sure worth every penny. Anyway, I won't be going that route (not for the time being at least). I considered recording into a device like that first, then editing/etc. in the computer, though I'm just going to do all of it on the computer for now.

Regarding doing the mix in the software, you mentioned that I could hook up 2 channels to a stereo mixer channel for monitoring. Do you mean something like this?:

1. XLRs into Mackie strips/channels 1-4 (or 1-2 with "lines" into 3-4)
 2. Lines (1/4" TRSs) into Mackie strip/channel "9-10" (with "sub1-2" enabled)
 3. Mackie's direct outs 1-4 into Delta's ins 1-4
 4. Mackie's sub outs 1-2 into Delta's ins 5-6
5. Assign Delta's ins 1-6 (via software) to Delta's outs 7-8
6. Delta's outs 7-8 to Mackie's strip/channel "15-16"
7. Mackie's (which output?) to monitor speakers (perhaps enable sub3-4 on 15-16 and use outputs for subs 3-4 for the speakers?)

I'd figure I could use "C-R Outs (L/R)" from the back of the Mackie into the speakers, though maybe I'd have to assign the specific strip "15-16" to it. Not sure.

My hunch is that the software assigning of Delta's ins 1-6 to Delta's outs 7-8 would be fairly easily done in Ardour. (Hopefully.)

Maybe Delta's outs 7-8 should be Delta's outs 1-2 instead? (Unless that'd get mixed up with Delta's ins 1-2.)

Perhaps Mackie's strips/channels 15-16 should be another channel pair like 11-12. My guess is in this case it might not matter.

Perhaps a combination set-up...


1. XLRs into Mackie strips/channels 1-4 (or 1-2 with "lines" into 3-4)
 2. Lines (1/4" TRSs) into Mackie strip/channel "9-10" (with "sub1-2" enabled)
 3. Mackie's direct outs 1-4 into Delta's ins 1-4
 4. Mackie's sub outs 1-2 into Delta's ins 5-6
 5. Delta's outs 1-4 into Mackie's strips/channel 5-8
 6. Delta's outs 5-6 into Mackie's strip/channel "11-12"
7. Assign Delta's ins 1-6 (via software) to Delta's outs 7-8
8. Delta's outs 7-8 to Mackie's strip/channel "15-16"
9. Mackie's (which output?) to monitor speakers (perhaps enable sub3-4 on 15-16 and use outputs for subs 3-4 for the speakers?)

> **hardcopy said:**
> 
yes you could record the midi performance and the live output at the same time, this gives you the flexibility of being able to edit the drummers performance or change the kit being used at a later date, then just record another take of the drums to disk.

Recording elec.drums via 2 mediums simultaneously - MIDI *and* "live" - is a very cool concept. ...to be able to apply the "normal drumset" sounds with the live tracks and mix in various MIDI-unique elements with the MIDI tracks. :)

> **hardcopy said:**
> ok, what i mean is that sub output 1&5, 2&6, 3&7, 4&8 on the back of the desk carry the same signal, you dont have 8 discreet sub outs, instead you have 4 sub outs, and each sub out can be directly conneted to 2 different places at the same time.

I think the whole "sub" context (punny, "subcontext") topic will make sense soon enough. I understand that sub out 1 and sub out 5 have the same signal, and the same for the remaining subs. Is that why one sub out is often assigned to "left" (with a strip panned left) and the other sub out assigned to "right" (with strip panned right)?

The confusing bit there is that the strips on the top of mixer show 3 buttons below the "solo" button:

"1-2"
"3-4"
"L/R"

So if "1-2" can be left with that strip panned left and "3-4" can be right with that strip panned right... then the sub outs would... wait, nevermind, I'm making it more confusing. lol

The "L/R" - my guess is that means that strip will use "both left and right at the same time". :confused: It's like the topic of subs... oh boy you know I think I'm confusing busses with this. Okay, one step at a time and I'll get this. ;) It's intriguing stuff. My guess is that with physically working with the gear, hands-on, I'll get a solid grasp of things.

> **hardcopy said:**
> lets say you had an 8 track hard disk recorder, but only ever need to record 4 tracks at the same time. the mixer configuration would mean that you can have all 8 inputs on the hd recorder hardwired to the sub group outs at all times. you first 'arm' and record channels 1-4, then for the overdubs you 'arm' and record channels 1-5, no re-patching is required

Okay more sub stuff... hmm... for the moment since I'm not using an 8 track recorder, I think I'll put that concept on hold, so as to not too overwhelmed right at the beginning of all of this.

> **hardcopy said:**
> mixers are set up for stereo operation, and as such, sub-group routing uses a combination of button selection and pan to determine where a signal goes- to understand it, i think you should ignore the existance of sub outs 5-8 completely. sub outs 1&2 are a pair, so with the 1-2 button selected and a channel panned left it goes to sub 1, panned right it goes to sub 2.

It feels like I'm right on the edge of understanding that sub group stuff. It's like it's on the tip of my tongue but I can't yet pinpoint an exact and clear understanding. I'm patient (with myself as much as anyone else, lol), I trust it'll all come together soon enough.


> **hardcopy said:**
> inserts and effects sends are basically the same thing but for different purposes

So let's try this-

Inserts = I can use with pre/post fade. Pre fade is raw, no inserted changes. Post fade is with the inserted changes? (That would be controlled via the "pre" buttons and "Aux" knobs?)

There's a very interesting set of controls near the "Aux Master" section of the top of the mixer... Aux Master 1 & 2 with solo 1 & 2, Stereo Returns 1 & 2 (with "to L/R" for each and "to Aux 1" for 1 and "to Aux 2" for 2), and apparently stereo returns 3 & 4 with "Assign Options" for 3 as "main mix" or "to subs" (1-2 or 3-4) 2 buttons, and for 4 as "c-r/phns only" or "returns solo".

You know, I previously had the Mackie 1220i mixer and it didn't have all of these additional features. Wow! :)

Anyway, back to inserts & effects... so the effects-

Effects = similar changes in sounds only not involving pre/post fades, but... hmm wait, if it goes out to other sources that might be via Aux outs on the back of the mixer.

Okay I'm hitting the brakes on this bit just for right now. I'm thinking about too many things at once. lol

It seems like Inserts can be used or not used with "pre" button, allowing the track(s) recorded to be either "dry" (no inserted changes in the sound) or "wet" (with inserted changes to the sound).

It seems like Effects sends signals from board to another external device that provides the effects and then sends the signals back (now with the effects) to the board, yet does not rely on the "pre" button and, perhaps also, is a full-time effect that cannot be removed from the given track(s) (unless removing the effects entirely).

> **hardcopy said:**
> hopefully i answered this above, i will add that midi contains no sound data at all, it is just used to control midi devices that then create sound from that data

Definitely answered, thank you, of course it sparked some more questions but all of this is so damn fascinating! I'm pumped for recording, I just want to make sure I have a good starting point. I actually have some books that deal with recording but they don't deal with the actual setting up/connecting of gear.

Regarding the MIDI and no sound data... I wonder if the Delta 1010 can convert the digital/MIDI messages from the drumset (that goes into the Delta) into analog signals from the Delta's outs to the Mackie's ins.

 > **hardcopy said:**
> just to clarify: spdif is a digital signal carried over either a phono or optical cable. wordclock is a sync signal sent over bnc that is necessary for proper digital syncing.
Okay so wordclock is the signal, not a device, but it can be used between 2 devices that share wordclock I/Os, right?

I'm guessing that I basically don't have to worry about it until I come across some gear that also uses wordclock.

> **hardcopy said:**
> i hope thats clearing up the confusion its quite a big topic sound engineering so ask more questions if its not making sense

It does clear up a lot, and thank you very much for the very helpful input!

I should be getting the Delta 1010 early to middle of next week. Then the new mixer some time late next week or early the week after, a little longer wait on that but that's okay. Time to experiment with the 1010. And time to purchase a couple new microphones (and decide which kind to get to compliment the 2 cardioid condensers).

[IMG]http://i.imdb.com/Photos/CMSIcons/emoticons/basic2/cheers.gif[/IMG]

Edit-
I almost forgot about my USB/MIDI keyboard... lol and it's right here in front of me. ;) Another MIDI option. It'll be interesting working with that combined with the 'live'/analog.

---

### Post by hardcopy on 2010-01-15
"My guess is that with physically working with the gear, hands-on, I'll get a solid grasp of things."

Yes thats my feeling too- you're definately getting a handle on it all, i think if we can clear up the bus confusion most of it will fall into place for you, here goes.....

the buttons "1-2", "3-4" & "L-R" are for assigning where the channel strips signal is sent.

without one of the buttons depressed, the signal is not being sent to any bus.

if you depress the L-R button, the signal is sent to the main mix bus. the pan of the channel strip will then dictate where the sound is placed in the stereo mix.

simple really, im sure you understand this already.

what i think your missing is that the sub groups work in exactly the same way-

by depressing the 1-2 button the signal is sent to what we could call "submix A" (imagine that groups 1&2 are instead labelled "submix A L" & "submix A R" respectively). the pan of the channel strip will then dictate where the sound is placed in the stereo submix. 3-4 can been seen in the same way as submix B.

the reason they aren't labelled as submix A & B is that often you would want sub groups to be interchangable as mono/stereo. to work with mono groups you just use hard panning to prevent the signal from being sent to the wrong bus.

now rather than me explain some examples, can you answer these questions:

1:how do i assign channel 1 to subgroup 2 without hearing channel 1 on subgroup 1?

2:how do i make a stereo submix of channels 2, 3 & 4, with channel 2 panned left, channel 3 centred in the submix, and channel 4 panned right?

put your hand up when you have the answers, then we can go from there :D

---

### Post by Th3Professor on 2010-01-15
> **hardcopy said:**
> i think if we can clear up the bus confusion most of it will fall into place for you, here goes.....

I think I'm alittle mixed up on bus stuff as well as sub stuff.

> **hardcopy said:**
> the buttons "1-2", "3-4" & "L-R" are for assigning where the channel strips signal is sent.

without one of the buttons depressed, the signal is not being sent to any bus.

So only use "1-2", "3-4", and/or "L-R" on a strip if I want to use 1 of the busses. Got it.

> **hardcopy said:**
> if you depress the L-R button, the signal is sent to the main mix bus. the pan of the channel strip will then dictate where the sound is placed in the stereo mix.

So basically, "L-R" = main stereo mix... so the strip with "L-R" sends its signals to both left and right channels of the main mix. If I want it to only go to the main mix L/left channel then pan left and only to R/right then the pan right. The signal will go out from one of the busses.

Hope I'm rephrasing this right. Please let me know if I'm mixing it up.

Let me try it like this, let's see if this is correct or incorrect...

Strip 1, enable "L/R", pan left, the main mix (not a sub) receives left signal only.
Strip 2, enable "L/R", pan right, the main mix (not another sub) receives right signal only.


> **hardcopy said:**
> what i think your missing is that the sub groups work in exactly the same way-

Sub = Bus. Okay. I think. lol

> **hardcopy said:**
> by depressing the 1-2 button the signal is sent to what we could call "submix A" (imagine that groups 1&2 are instead labelled "submix A L" & "submix A R" respectively). the pan of the channel strip will then dictate where the sound is placed in the stereo submix. 3-4 can been seen in the same way as submix B.

That may have confused things a bit. ;) Let me give another look at that...

Strip 1, enable "1-2", pan left, a sub (not the main mix) receives left signal only.
Strip 2, enable "3-4", pan right, another sub (not the main mix) receives right signal only.

> **hardcopy said:**
> the reason they aren't labelled as submix A & B is that often you would want sub groups to be interchangable as mono/stereo. to work with mono groups you just use hard panning to prevent the signal from being sent to the wrong bus.

So it's all about if it's gonna be mono or stereo, then it's about where the signal goes, to either a specific sub mix or to the main mix. Basically that?

> **hardcopy said:**
> now rather than me explain some examples, can you answer these questions:

Oh boy, I hate taking tests. ;) 

> **hardcopy said:**
> 1:how do i assign channel 1 to subgroup 2 without hearing channel 1 on subgroup 1?

okay nothing about panning here, i'm assuming...

strip 1 = enable "3-4", disable "1-2"

> **hardcopy said:**
> 2:how do i make a stereo submix of channels 2, 3 & 4, with channel 2 panned left, channel 3 centred in the submix, and channel 4 panned right?

okay so some panning here and sub stuff, but nothing about main mix so that leaves "L/R" button out of the equation...

strip 2 = enable "1-2", turn "pan" all the way left
strip 3 = enable "1-2" and "3-4", leave "pan" centered
strip 4 = enable "3-4", turn "pan" all the way right

> **hardcopy said:**
> put your hand up when you have the answers, then we can go from there :D

Ferris Bueller.
"Anyone? ...anyone?"

---

### Post by hardcopy on 2010-01-15
ok, i think i see where your going wrong, i just need to find a new way of explaining it so as to not repeat the confusion....

i think what you're missing is that the pan control is always a factor in where the signal is sent by those buttons, you correctly understand how this works when using the main mix (L-R button) but you get confused when L-R is replaced by numbers. im sure you will kick yourself when you get it!

first i'll describe the busses:

L = main mix left
R = main mix right
1 = sub group 1
2 = sub group 2
3 = sub group 3
4 = sub group 4

now i'll describe how the buttons & pan interact

L-R button enabled, pan L = send to left of mix, pan R = send to right of mix, pan centre = send to centre of mix
1-2 button enabled, pan L = send to sub group 1, pan R = send to sub group 2, pan centre = send to sub groups 1 & 2
3-4 button enabled, pan L = send to sub group 3, pan R = send to sub group 4, pan centre = send to sub groups 3 & 4

ok with that in mind re-answer the questions and we'll see if i explained it for you well.

right im off to the pub i'll try to resist posting when i get back drunk!

---

### Post by Th3Professor on 2010-01-15
Okay let's try again. :D

Oh! By the way, my Delta 1010 came in today! :D Woohoo! I installed the PCI card, etc. and the external unit, the actual rack mountable device, is good to go.

Now I just need my new mixer. The irony is I could've used my old mixer with this but I didn't want to spend money on a mixer that had firewire when I couldn't have even used the firewire in it (aka waste of money, at least at present (until that particular mixer becomes compatible)).

So I've hooked up the MIDI cables from the elec.drumset into the MIDI I/O of the Delta. The USB/MIDI keyboard is just using the USB straight into the computer. I wonder if I can still use that along with the MIDI-part of the drumset (both going into a program that supports analog recording too).

There are 8 Ins and 8 Outs on the back of the unit just waiting to be hooked up to my mixer when it arrives. :) There's also the wordclock i/o but I won't be using that until I get something to hook up to it.

I could probably hook up an electric guitar or bass into the TRS jacks on the back of the unit (bypassing a mixer all together). I'll experiment with that.

Okay back to topic...

> 1:how do i assign channel 1 to subgroup 2 without hearing channel 1 on subgroup 1?strip 1 = enable "1-2", turn "pan" all the way right

that's using subgroups 1-2.

i'll assume that question 2, below, is using subgroups 3-4.

> 2:how do i make a stereo submix of channels 2, 3 & 4, with channel 2 panned left, channel 3 centred in the submix, and channel 4 panned right?strip 2 = enable "3-4" and "L/R", turn "pan" all the way left
strip 3 = enable "3-4" and "L/R", leave "pan" in the center
strip 4 = enable "3-4" and "L/R", turn "pan" all the way right

the weird thing w/ that is, strip 3, I'd think that "L/R" could be left disabled if it's going to be centered. However, it looked like it should be enabled to be consistent with the other two strips. :?

---

### Post by Justin Case on 2010-01-16
Do you have your Ubuntu Studio already set up?  
I have a M-Audio Delta 44 card, myself, and found at least 2 versions of Ubuntu Studio, 8.04, and 9.10, failed to fully detect my card.  The inputs were detected, but not the outputs.  Was unable to get it to work.  My easy solution was to install Studio version 9.04, and everything was properly detected.  The M-Audio card sounds fantastic, you will like it. 

Also, I just skipped through the above thread...so I run the risk of redundency here..
Are you using mics?   The preamp out on the amp run through an impedence converter, into the mixer, sounds like crap. 
Sorry if thats been covered...
Gotta go...

---

### Post by Th3Professor on 2010-01-16
> **Justin Case said:**
> Do you have your Ubuntu Studio already set up?  
I have a M-Audio Delta 44 card, myself, and found at least 2 versions of Ubuntu Studio, 8.04, and 9.10, failed to fully detect my card.  The inputs were detected, but not the outputs.  Was unable to get it to work.  My easy solution was to install Studio version 9.04, and everything was properly detected.  The M-Audio card sounds fantastic, you will like it.

I found this how-to on getting the Delta 1010 working in 9.10:
[http://www.milkmachine.org/delta1010.html](http://www.milkmachine.org/delta1010.html)
I didn't know there were any problems with this particular version of Ubuntu Studio (9.10) and the Delta 1010. I haven't tested all of the inputs and outputs yet. If I run into problems I'll try what's suggested on that page but you might consider giving it a try too, if you do let me know how it turns out.

> **Justin Case said:**
> Also, I just skipped through the above thread...so I run the risk of redundency here..
Are you using mics?   The preamp out on the amp run through an impedence converter, into the mixer, sounds like crap. 
Sorry if thats been covered...
Gotta go...

I am using 4 cardioid condensor mics.

I'm not sure I understand what you are staying in the statement:

"The preamp out on the amp run through an impedence converter, into the mixer, sounds like crap."

Could you rephrase that? The sentence appears to be incomplete or a fragment. Confusing.

What preamp, amp, impedance converter, and mixer are you talking about?

The mixer I'm going to be using (still waiting for it to arrive) will be a Mackie 1642-VLZ3, which specializes in sending quality microphone signals. I don't know what you mean about mics "sounding like crap" but I certainly hope that won't be the case with my mics going through my specific mixer, then Delta 1010, and then computer. Note that I have the 1010, not the 1010LT. I don't know how your Delta 44 handles mics. I understand there are similar features between all Delta products, though there is also an approximate $400 difference between the 44 and 1010, so I *really* hope that my mics do *not* end up sounding like crap with this gear!

---

### Post by Th3Professor on 2010-01-18
Update on things... I should be receiving the rest of the new recording gear some time this week. Hopefully things will all come together and work well (aka: will be compatible and fully supported).

---

### Post by robeast on 2010-01-18
Supposedly any M-Audio Deltas made since 2007 have a new architecture that breaks Linux compatibility, so beware!

---

### Post by Th3Professor on 2010-01-18
> **robeast said:**
> Supposedly any M-Audio Deltas made since 2007 have a new architecture that breaks Linux compatibility, so beware!

Do you know if that has anything to do with this?:
[http://www.milkmachine.org/delta1010.html](http://www.milkmachine.org/delta1010.html)

---

### Post by Mike'sHardLinux on 2010-01-18
I am glad you went with the 1010. It has better converters and has them in the breakout box, compared to the 44 and 66, which have the converters on the PCI card, NOT in the breakout box. I have been using a 1010 for years and it works great. You should be able to get some really good recordings.

---

### Post by Th3Professor on 2010-01-19
There have been some reports of "hiss" problems and similar with the 1010, have you had any problems like that? What year did you get your 1010? Which version of Ubuntu & kernel are you using? Some people have said it's only a problem with Ubuntu 9.10, others say that all 1010 units after 2007 have had a conflict with Linux. <shrug> I don't know. I haven't tested mine out yet, I'm waiting for the mixer to arrive then I'll get to testing but hopefully it'll be fine.

---

### Post by Th3Professor on 2010-01-22
Update :) The mixer's in. The patch cables just arrived, now it's time to put this puppy to the test, hopefully everything works out.

Here's what I'll be working with:

Instruments (via mics, line-ins, etc.)
>
Mackie 1642-VLZ3 mixer
>
M-Audio Delta 1010
(MIDI drums > Delta)
>
Computer
(USB/MIDI keyboard/controller > computer)
>
JACK
(and PHASEX (for now at least) for the keyboard)
>
Ardour

-Hook it all up.
-Connect things in JACK.
-Set up Ardour with the set-up.

Hopefully I'll get things right. ;)

EDIT-

I've got my mixer and patch cables now, hooked it up to my new delta 1010. :D I've got levels set on the board, JACK/envy24 is running, and it appears Ardour is picking things up (it also seems to have automatically adjusted JACK's Connections when it loaded). However, I'm getting no playback. :-\ I've only tested my microphones with that gear so far. I have Line Ins on the mixer too, coming from Line Outs on guitar amps, and I have the MIDI drumset hooked up to the MIDI ports on the Delta 1010. I'm not sure how to incorporate the usb/midi keyboard/controller (axiom) and the roland electronic drumset into Ardour (or Rosegarden). The keyboard/controller is USB direct into computer while the drumset is going into the midi of the Delta. (I also have a "main out" from drumset going into the mixer.) Anyway, my *main* concern on that stuff right now is getting playback to work. :confused:

---

### Post by Th3Professor on 2010-01-24
I've got my mixer and patch cables now, hooked it up to my new delta 1010. :grin: I've got levels set on the board, JACK/envy24 is running, and it appears Ardour is picking things up (it also seems to have automatically adjusted JACK's Connections when it loaded). However, I'm getting no playback. :-\ I've only tested my microphones with that gear so far. I have Line Ins on the mixer too, coming from Line Outs on guitar amps, and I have the MIDI drumset hooked up to the MIDI ports on the Delta 1010. I'm not sure how to incorporate the usb/midi keyboard/controller (axiom) and the roland electronic drumset into Ardour (or Rosegarden). The keyboard/controller is USB direct into computer while the drumset is going into the midi of the Delta. (I also have a "main out" from drumset going into the mixer.) Anyway, my *main* concern on that stuff right now is getting playback to work. :confused:

---

### Post by nexus_6 on 2010-02-03
Did you make any progress on your playback issue yet? I'm very interested in this topic, as I'm also looking into buying a Delta 1010.

---

### Post by robeast on 2010-02-04
Did you get a new 1010? I've heard changes to their architecture broke support...would love to know if you got it working!

---

### Post by AutoStatic on 2010-02-05
> **robeast said:**
> I've heard changes to their architecture broke support...I did some digging in the ALSA bugtracking system and as far as I know all 1010's should work: [http://ubuntuforums.org/showpost.php?p=8772770&postcount=43](http://ubuntuforums.org/showpost.php?p=8772770&postcount=43)

---

### Post by niffcreature on 2010-02-06
this thread has been so unrelated to linux!
you all really should know that there is a list of supported firewire audio cards, many of which might have a lot better support than the card you got.
i dunno maybe im missing something completely.

anyway here [http://www.ffado.org/?q=devicesupport/list](http://www.ffado.org/?q=devicesupport/list)

---

### Post by AutoStatic on 2010-02-07
Hello niffcreature, this thread may not be fully Linux releated but it certainly is Multimedia Production related.
And I'm aware of the supported Firewire devices list, I have a Focusrite Firewire device myself. I don't know how it relates to the 1010. The 1010 looks like a real nice card, I'm planning to buy one for a project at work.

---

