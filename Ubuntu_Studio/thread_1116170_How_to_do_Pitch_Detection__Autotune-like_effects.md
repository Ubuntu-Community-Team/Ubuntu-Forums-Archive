---
title: "How to do Pitch Detection / Autotune-like effects"
date: 2009-04-04
forum: Ubuntu Studio
---

### Post by jeremybubs on 2009-04-04
I have been looking around for a while for an autotune effect (pitch correction, or whatever name you care to call it) for linux.  Unfortunately everything I have found either cost money or wasn't for linux, or required special setup (wine, or other nasty things). All I could find in terms of linux autotune was people also looking for autotune.  However, all the answers were unsatisfactory, either because they required manual pitch recognition (Not so good for the tone-deaf among us), or people confused it with pitch shifting in general. I eventually did find that praat (it's in synaptic), a speech analysis tool, comes surprisingly close to autotune functionality.  It will give you a T-pain like effect, but it requires you to manually place the notes (although it will detect the pitch for you).  I am not very experienced with praat, although this is what I figured out how to do (some of it from the original mailing list post, other I read from the manual or figured out).

Although it's GUI isn't too nice, and it isn't designed for musical manipulation, it gets the job done.

1.  Loading the sound

Start up praat, and go to the window labeled "praat" (rather than the one labeled "praat picture"). You can either record a sound, or load a .wav or .flac file (.ogg is not supported and I don't know about .mp3).  One thing to note is that I got a slight background squeal when recording in praat (maybe just my setup)  so you might want to record another way (Sound Recorder or Audacity).

A) Recording
Click the "new" menu bar at the top, and on the drop-down menu, click "Record Mono Sound..."  (If you have a stereo mic I suppose you could try recording stereo, but I have not idea how that will work with pitch detection.)  A window will come up titled "SoundRecorder".  Try speaking into your microphone and seeing if the volume meter goes up.  You can try changing the Input Source to fix it if it won't record.  In the bottom righthand corner you can give the recording a name.  When you are ready, click "record" and say whatever you want, or sing or whatever, and when you are done, click "stop".  Then click "Save to List & Close" (Or just "Save to List" if you want record multiple sounds.  You can close it when you are done)

B) Loading a file
On the menu bar, click "Read", and from the dropdown menu click "Read from File..."  You can try navigating to the file you want (wav or flac only as far as I can tell), or just type in it's absolute location on the bottom line and click "Ok" (Ex: /home/jeremybubs/Music/Mesinging.wav)

Now, weather you loaded the file, or recorded it, on the main "praat" window, on the left under the "Objects:" label, it should say "1. Sound Mesinging", or whatever, depending on the title of your sound.  You can now test it by clicking the play button on the right (be careful, I haven't figured out a way to stop it, so be prepared to hear the whole recording.).  Now, it is time to start manipulating the pitch.  

2.) Creating a Pitch manipulation object

Select your sound on the left, and on the righthand side, under the "Manipulate" section, click "To Manipulation..."  A little dialog will pop up.  It's ok to just click "OK", but you can change the maximum and minimum pitch if you know the sound is outside that range.  When you click "ok", it will take some time, depending on how long your sound is, to do some processing.  When it is done, is should say "2. Manipulation Mesinging" on the list directly under "1. Sound Mesinging".  Note that pitches and sounds and everything you create in praat are all considered "Objects" and placed in the same list.

3.) Edit the Pitch

Click the "Edit" button on the righthand side.  A window should pop up which shows the sound waves on the top and a (hopefully accurate) graph of the pitch of the sound.  Now, you could try and drag around each one of those pitch points, but there are too many, and you want to get a robotic voice anyway, so you don't need smooth contours.  You will be dealing with only the bottom half now, the pitch countours.  If you left click anywhere, to the left of the graph it will tell you the "pitch" of that hight (anything that height has that pitch.)  and on the right, it will tell you the pitch of the note at that horozontal location (where the vertical line from your cursor intersects the pitch contour.)  You can drag around the points, but you will have to move a lot of them to make an audible difference.  You can also drag to select.  If you have some selected, you can click the "Pitch" menu at the top, and then "Shift Pitch Frequencies" to change the pitch of the selected parts . (you can choose the units to be hertz or semitones, which I think are the same as half-steps in music)  Press tab to start and stop playing from the last place you clicked (it will play the modified pitch)

4.)  Get some auto-tuning!

Click the "Pitch" menu and then click "Stylize pitch (2 st)". Congratz, you have done the first step on your way to autotuning.  Try playing it again (Tab), and if you have good ears, you will hear the flatter sound it has now.  As you can clearly see, the number of pitch points has been drastically reduced.  The other ones are just linearly interpolated between these now.  For example, if one pitch point is higher than the previous one, for all the time in between them, the pitch will slowly be changing between the two pitches.  Usually it does a pretty good job of fitting the sound.

5.)  Tune away!
Now you can drag the points and set up the pitch.  If you look to the sides of the window, it will tell you the exact pitch you have.  Unfortunately, for those with no understanding of music, you can't just automatically make it "sound good"  You have to choose a scale, and make the notes match to it. If you have no idea, just choose the C scale, and make all your notes be non-sharp or flat (CDEFGAB).  You can look of the frequency of notes here [http://en.wikipedia.org/wiki/Piano_key_frequencies](http://en.wikipedia.org/wiki/Piano_key_frequencies)  Now, go through and make everything match the closes note in the scale you chose. (or match a predetermined melody if you are aiming for that.)  Remember, you need two points at the pitch you want, and that will make everything in between be that pitch.  To get the characteristic Autotune Sound (T-Pain like), you make the jumps between notes be sudden.  If you want to zoom in or out for finer detailed editing, click the "View" menu on the top and select the appropriate option.  (Remember, you can press Tab to hear your work at any time.)

6.) Saving

When you are satisfied, select "Publish Resythesis" Under the file menu.  Now, under the main window (you can edit the Manipulation window if you want to) a Third object should have appeared on the list "3. Sound fromManipulationEditor".  Select it and on the top click "Write" and then select "Write To WAV File..."  You can then type in the location you want to save it, or navigate to the correct location.

7.) WOOHOO!!
Now you can load up that sound in whatever audio editor you choose.
Some bonus stuff:  For an alternative resynthesis, before you click "Publish Resynthesis" , under the "Synth" menu on the Manipulation Window, click the last option, "LPC -- Pitch". Now it will be the alternative whenever you play or save the file.  You can always switch back by selecting "sound and pulses" on the same menu directly above it.
There is also a way to copy the exact pitch of one file and apply it to another, I don't feel like figuring it out again, but if you are interested, ask me.
LOOK AROUND.  Seriously, explore praat, it is such a cool program, you can manipulate other things like pulses, etc have it hum the tune of your recording, or just the beats without pitch, or change the gender, as well as have it synthesize its own speech and other crazy stuff I don't understand.

So I guess it is more like "Manualtune", but at least the pitch recognition works correctly.  I hope I didn't write too confusingly (or use to many parenthesis.)  Either way, the effect is cool, and hardly found anything online aware of praat's capabilities, so I thought I would post it here to get people aware of it.  If you have any corrections or questions, or know more about praat than me, please post!

NOTE: This tutorial applies to any operating system that can run praat, not just ubuntu or even linux.

--Jeremybubs

---

### Post by kayosiii on 2009-11-10
[http://web.mit.edu/tbaran/www/autotalent.html](http://web.mit.edu/tbaran/www/autotalent.html)

---

### Post by wrathkeg on 2009-11-10
I second the recommendation of Praat.  I have used it for years for speech analysis, as have many of my colleagues.  It is very widely used in phonetics (the scientific study of speech production and perception). The authors of Praat are actively developing it, and in my experience have always been very responsive to feedback, bug reports etc.  I think they do a really good job of offering genuine cross-platform support.
wrathkeg

---

### Post by Stochastic on 2009-11-11
> **kayosiii said:**
> [http://web.mit.edu/tbaran/www/autotalent.html](http://web.mit.edu/tbaran/www/autotalent.html)

Thanks Kayosii, that looks like a very useful plugin, now I can sing well! :)

(did you smell the sarcasm)
In all seriousness though, I'm glad there is an autotune plugin.  Now time to package it for Ubuntu.

---

### Post by AutoStatic on 2009-11-11
Funny that Praat pops up over here, those are colleagues of mine. I haven't had the need for an autotune plugin, I luckily manage to sing in tune a bit ;)

---

### Post by Madspyman on 2009-11-11
Gsnap is another good one, it's a free vst for pitch correction, and it works in LMMS. [http://www.gvst.co.uk/gsnap.htm]("http://www.gvst.co.uk/gsnap.htm")

---

### Post by Stochastic on 2009-11-11
> **Madspyman said:**
> Gsnap is another good one, it's a free vst for pitch correction, and it works in LMMS. [http://www.gvst.co.uk/gsnap.htm]("http://www.gvst.co.uk/gsnap.htm")

Free as in beer (i.e. costs nothing), not free as in speech (i.e. can't re-distribute it for all of Ubuntu, nor develop upon it, nor fix bugs in it, etc...).

---

### Post by Madspyman on 2009-11-11
Fair enough.

---

### Post by jeremybubs on 2009-12-27
So I've packaged a .deb of autotalent for anyone who wants it here:

[https://launchpad.net/~jeremybubs/+archive/salwenj/](https://launchpad.net/~jeremybubs/+archive/salwenj/)

---

### Post by roberto.tomas on 2011-10-18
:KShow do you nominate a thread for saving for important information?

---

