---
title: "ardour mix too low"
date: 2010-03-03
forum: Ubuntu Studio
---

### Post by extendedping on 2010-03-03
I am just trying to finish my first song on ardour. I am pretty new to recording and thus am not using any compression or eq cause I don't have a clue. I have hydrogen drums, and myself playing bass and guitar through my tonelab into a firepod. anyway I was ok with the mix I was working on but ardour crashed (as it seems to do often with my pc or settings) and I lost my outputs on my master bus. so when I restored them to system playback 1 and 2 I noticed that the master clip light was reading 5 and was way in the red. the recording did not actually sound bad to me but I have read that is called clipping and will sound bad to those with taste. so I pulled the fader way down on the master bus and listened to the entire track watching the mixer to see for any red on the individual tracks or the master bus. ok so I got everything in under the red on the tracks and on the master bus now. but the thing is when I compare this recorded level after making a wav it is way lower then any mp3s I have on my computer. stuff like the who and the doors not moderen stuff that I hear is compressed and made as loud as possible. so what can I do here? is it normal if all your recorded tracks are under the red for the master bus to be way in the red (I guess it is aggregating the individual signals?)? and is it normal for a home recording that doesn't clip to be way lower then a professional recording? finally, when I see the master way in the red to sound as loud as the mp3's I have of the who and the doors...does that mean that the master bus is clipping and that I need to turn it down? because it didn't really sound overly distorted but again the red on top of the master bus meter was reading 5 (thats 5 over 0) which from my ardour manual seems to be a bad thing. finally, would there be a quick and dirty way for a noob to raise the overall mix without it clipping without totally loosing the dynamics of the recording? 

yea thats like 20 questions I know, if just one or 2 were answered I would be very happy. thanks in advance.

---

### Post by cchhrriiss121212 on 2010-03-04
What you know about this already is on the right track, you will learn more as you record more things. Pop music makes use of compression at many stages in production, from live playing to final mastering, and it is very useful once you know how to use it. It is normal that your recording will sound too quiet if you have not used any compression.
Think of clipping as the audio equivalent of colouring outside the lines on a picture, it is best avoided.

A few tips:

[LIST]
[*]Check your sound levels before you start to record. A clipped recording of a guitar will always be clipped even after you decrease it's volume in the mix. I aim for about -7dB on a rough level average as it leaves room for loud peaks.
[/LIST]

[LIST]
[*]Look at the waveform of what you have recorded to check for clipping. Any peaks that make contact with the top or bottom of the box they are in have clipped, they will sound badly distorted or harsh to your ears.
[*]Once you have something that sounds good in Ardour all the way through you will have what the pros call a final mix which you can export in whatever quality bit/sample rate you like.
[*]You can then compress/edit the final mix to sound louder (this is called mastering). Open up your track in audacity and play around with the compression to see how it sounds. I recommend just using normalization to start with, this will raise the overall sound level without damaging any of what you have recorded.
[/LIST]
Have fun!

---

### Post by extendedping on 2010-03-05
ok thanks for the advice. I saved the low project at 32bit 48000 sample rate as a wav and now open it in the audacity program. I am not really sure how to normalize. I do select all, then I do normalize from the effects window. when I click on audition it plays for a few seconds the beginning of the song pretty loud. but when I hit ok under the effect and play back the song it is no louder then it was, and certainly not what I heard in the audition...so I am making some noob audacity mistake?

---

### Post by cchhrriiss121212 on 2010-03-05
You can only normalize by a certain amount of dB safely, chances are you cannot raise the peaks of your waveform any higher. Post a picture of the track in audacity if you like. 
You can either remix the track in Ardour or compress what you have.

---

### Post by extendedping on 2010-03-05
thanks I see now in audacity going back and forth crtl z ctrl shift z putting the normalize on and off that the waves do in fact change, just a tiny bit so your assumption is on the mark. I was thrown off because the "audition" feature of normalize like doubled the sound. so I guess I need to learn what some decent but not overly done compression settings would be, then use the normalize to raise the volume a bit. btw, is there any reason do do this in audacity vs doing this on the master bus in ardour itself (or perhaps it can't be done in the master bus).

---

### Post by cchhrriiss121212 on 2010-03-06
The master bus is not really made for mastering, just a general idea of your sound level when recording. You won't get any visual representation of the track on the master bus either.

You can do many more things with audacity as well, increase the bass or remove any noise. It is a very simple and useful tool, so get used to using it as you record stuff. 
It might seem simpler to do everything you want in just one program, but audio production on a Linux system is more of a modular system with lots of different programs all doing specialized things.

---

### Post by extendedping on 2010-03-06
thanks looks like an interesting program, here is one thing I don't get. I opened my .wav file that I exported from ardour in audacity. since I don't really understand eq/compression or any of that stuff (yet) just did a select all (not sure if I had to do that) then selected the compression effect leaving it at its defaults. I do see both the upper and lower soundwaves lines (??left and right of the master bus??) change their shapes. then I do normalize, and only the upper waveform changes size at all. I stared at it doing a do undo again and again and I am sure the bottom wave does not change with normalize. do I somehow have to apply normalize separately for the top and bottom wave forms?  If so I don't know how to do that. my recording had bass panned center, the hydrogen drums center and a left and right guitar so no one side has much more music recorded to it...btw are the steps (as I did an aucacity) compress then limit or limit then compress?

---

### Post by cchhrriiss121212 on 2010-03-06
You don't need to select all as the whole track is selected when you open it up. On the settings for compression there is a check box that says "Normalize to 0dB after compression?". It is checked by default, so if you compress your track you will not need to normalize after. It sounds like one of your channels is slightly louder than the other, which is normal if you recorded 2 separate guitar parts.
This should help you understand compression:
[http://www.humbuckermusic.com/comex.html](http://www.humbuckermusic.com/comex.html)

---

### Post by extendedping on 2010-03-06
thanks I am going to read that. I found this too which talks about normalize vs amplify in audacity,(I only understand that nomalize does not work like normal no pun intended...
[http://wiki.audacityteam.org/index.php?title=Amplify_and_Normalize](http://wiki.audacityteam.org/index.php?title=Amplify_and_Normalize)

---

### Post by extendedping on 2010-03-06
> **cchhrriiss121212 said:**
> You don't need to select all as the whole track is selected when you open it up. On the settings for compression there is a check box that says "Normalize to 0dB after compression?". It is checked by default, so if you compress your track you will not need to normalize after. It sounds like one of your channels is slightly louder than the other, which is normal if you recorded 2 separate guitar parts.
This should help you understand compression:
[http://www.humbuckermusic.com/comex.html](http://www.humbuckermusic.com/comex.html)

under compression (which I left at its defaults threashhold -12db  noise floor -40db ratio 2:1 attack time 0.2 decay time 1.0 there is a box checked that says...."make-up gain for 0db after compressing" and a box that says 
"compress based on peaks" which is unchecked. is the make up gain line the same as the normaize to odb after compression?

---

### Post by extendedping on 2010-03-06
to make it worse, when I use soundkonverter with 320 bitrate to make an mp3 after compressing in audacity, the mp3 is lower then the audacity compressed wav file and lower then the vav I originally put in audacity. oh well. to see how low it is you could check out this link, with my magical repeating hydrogen loop and plodding single note bass playing (at least I am sparing you the vocals for now). the thing is when I did an mp3 from a wav file created by ardour, the mp3 seems close to the wav in loudness. but once I compress the wav in audacity and do an mp3 off that it is distinctly lower sounding :(

plus the mp3 seems to kind of have a sound of stuff getting louder and softer then the compressed .wav file it was created from...:(


sad noob this home recording is hard to learn from scratch :(
[http://soundclick.com/thekidfromperu](http://soundclick.com/thekidfromperu)
crapmix is what I have called it. thing is the other 2 that I did on cubase a few years ago sound a lot more punchy to me (perhaps they are clipping I don't know, I did make sure this recording never turned red on my firepod or in ardour).

---

### Post by Capoeira on 2010-03-07
> **extendedping said:**
> 
sad noob this home recording is hard to learn from scratch :(

you will get there ;-)

> **extendedping said:**
> 
sad noob this home recording is hard to learn from scratch :(
[http://soundclick.com/thekidfromperu](http://soundclick.com/thekidfromperu)
crapmix is what I have called it..

its clipping.

from what i understand from your first post, you bounced the track in ardour while the master went over 0db!?
you can't do that, mix it in ardour again or simply lower the master. never ever go over 0db. don't worry about the loudness till the master-process

---

### Post by extendedping on 2010-03-07
> **Capoeira said:**
> you will get there ;-)



its clipping.

from what i understand from your first post, you bounced the track in ardour while the master went over 0db!?
you can't do that, mix it in ardour again or simply lower the master. never ever go over 0db. don't worry about the loudness till the master-process

no since that post I lowered the master bus slider to -10.2 to ensure that it never went over the 0 level (none of the individual tracks in ardour or the master bus ever made the top of the fader go red).

so I thought (though of course this is basically a learning test track with no vocals and a crummy drum loop) that by putting it into audacity, and doing the compression thing that I was in fact in the mastering phase...the ardour mix that I exported to wav does in fact get a bit "louder" when I compression (using the audacity defaults for compression) but the mp3 I make out of the audacity wav is lower then the original wav that went into audacity. 

does the track actually sound like it is clipping? I don't really know what clipping sounds like (though of course I have heard it). again, I made absolutely sure neither the individual tracks or the master bus clipped in ardour (thus having a low mix and setting my on my quest to up the sound). finally I just read about something called jamin. is that on par with audacity for mastering the master bus track? the strange thing to me is that if I make an mp3 from the first wav file (the one that I made directly from ardour, and then put into aucacity, not the compressed wav that I created in aucacity) that mp3 is (to my ears) the same loudness as the wav. but if I make an mp3 from the second wav (the one created with compression in audacity) using the same settings on soundkonverter, the resulting mp3 sounds lower then the first mp3 (the one created from the ardour exported wav. hmmm 

thanks everyone for bearing with me on this and listening to my crap, probably clipping track...

---

### Post by Capoeira on 2010-03-07
jamin is for mastering audacity is for audioediting.

so, use jamin

read this: [http://www.64studio.com/howto-mastering](http://www.64studio.com/howto-mastering)

---

### Post by extendedping on 2010-03-11
thanks I have not had time to return to the track but will try using jamin when I do.

---

### Post by sgx on 2010-03-11
Keep in mind that if most of the sound level is, low, but there are peaks that prevent boosting volume, you can zoom in on them, and redraw to lower them with the pencil tool, or select the peaks, choose 'amplify' from the effects menu and lower the peak by using a minus 2.0  ( -2.0 ) as a starting point, more ore less according to need. Conversely, you may on occasion have delicate sections between good solid parts, and you can select those, and amplify them so they are clearly heard.

You can also use bassboost, lowpass, and highpass filters in audacity
to change part of, or the overall output, without need to compress things. Lets say one string of a finger-pick phrase or keyboard riff is way to loud, a filter or amplify change, or both, might bring it back
enough to keep it in the mix. 

If the same phrase occurs several times,
you may also be able to cut/paste a better version, assuming the background and foreground of that section have the same ambience, and
that there is no overlapping melody line of a different pitch. When you zoom in to look for cut/paste points, jot down numeric locations, and try to select cut lines where both l/r sound waves are on the line. You can zoom in and redraw the 'joint' with the pencil tool, you'll hear a little 'pop' if the gap is big enough. Lots of undo fiddly editing, but worth it for a song you like, and skills you'll perfect!

Take notes of effects numeric values that work well as you experiment, so you can use them as reference points later.
Cheers

---

### Post by kayosiii on 2010-03-12
While mixing your volume levels SHOULD be a LOT quieter than a commercially produced track particularly anything produced in the last 15 years. Don't be alarmed by this, turn the volume up and concentrate on getting the balance of the mix right. At this point you want to be using compression et al to get the dynamic range of the instruments right rather than optimising for loudness. 

If you want good reference material for what an album should sound elike before it is mastered look here. [http://www.digido.com/honor-roll.er](http://www.digido.com/honor-roll.er) 

There are a few things that may help.
Filtering out low frequencies on tracks that don't require them will allow you to get the track louder than you otherwise would. Use something like jaaa to look at your tracks and see if they are carrying low frequencies that aren't contributing to the mix. a highpass filter is usually used to remove these frequencies.

Speakers can be buzzed by just one frequency being over. When EQing keep in mind that making a frequency seem louder can be done by drop other frequencies as well as by raising that one. 
Again jaaa or japa can be useful to spot problem frequencies. And don't think because it sounds fine on your speakers that you are safe.

Finally you might want to make use of jamin or other mastering tools to really bring your final levels up without doing to much damage.

Good luck

---

