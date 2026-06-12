---
title: "What audio production software is good for beginners?"
date: 2010-02-17
forum: Ubuntu Studio
---

### Post by jsfarney on 2010-02-17
I'm really frustrated because I just want to make some beats and record music, but the ubuntu studio audio programs all seem like they are for programers and not beginners.  Could you please help me know what audio programs are good for a beginning musician to use?

---

### Post by AutoStatic on 2010-02-17
Hello jsfarney, which programs did you try so far?
Maybe a little list of programs that are pretty much self-explanatory will help you a bit:
- Recording/multitracking: Qtractor
- Creating beats: Hydrogen or LMMS
- All-in-one solution (no recording though): LMMS

---

### Post by elliotn on 2010-02-17
Just run Fl studio in Wine

---

### Post by elliotn on 2010-02-17
> **jsfarney said:**
> I'm really frustrated because I just want to make some beats and record music, but the ubuntu studio audio programs all seem like they are for programers and not beginners.  Could you please help me know what audio programs are good for a beginning musician to use?

As for recording, use audacity, its best of em all

---

### Post by Rog-Mahal on 2010-02-17
Gotta second Hydrogen for beats, it's very intuitive and has a ton of downloadable drum kits.

---

### Post by hxcobd on 2010-02-17
Another vote for QTractor here. Awesome program that doesn't get hyped enough.

EnergyXT is another good one.

Also, Renoise, if you're willing to learn how to use trackers.

---

### Post by AutoStatic on 2010-02-18
> **elliotn said:**
> As for recording, use audacity, its best of em allAudacity is a good sound editor and also a nice tool to make simple recordings. But it's less suited for multitracking, just FYI.

---

### Post by AutoStatic on 2010-02-18
> **elliotn said:**
> Just run Fl studio in WineFor a beginner? Well, [good luck]("http://ubuntuforums.org/showthread.php?t=1260057") ;)

---

### Post by cchhrriiss121212 on 2010-02-18
Unfortunately every tool used to make or produce music requires some effort to learn. Keep that in mind when trying things out. I would not recommend a beginner to use any audio programs with wine, there are plenty of alternatives that are native.

I found Ardour to be the best recording program and another vote for Hydrogen as it is very simple and very usable. Zyn is also a great synth which is easy to use with a virtual keyboard.

You could also start having a look at using Jack which is a sound server specifically designed for audio work on Linux. Once I had it running I found it very useful.

---

### Post by jsfarney on 2010-02-18
Hey, thanks for the help.  I got the ubuntu studio audio programs from the repsoitory, but the majority of the stuff in there looks like it is meant for programmers.  I really just want music where I can clip music and loop it and find how many bpm's it is.  And something that can beat match so my drums will match my samples would be great too.  I love open source solutions, so thanks again for the help!

---

### Post by trulan on 2010-02-18
> **jsfarney said:**
> ... the majority of the stuff in there looks like it is meant for programmers.
Well, open source software is made by programmers, often for their own use, so that's kind of a side effect I guess.  The learning curve on some of this stuff is steep but the possibilities are endless.  I don't know much about samples and beats, can't help you much, but hang in there with open source software.  You'll be glad you did.

---

### Post by tekkidd on 2010-02-18
recommend Audacity 

there is also Ardour but thats really advanced 

you can also try using your old windows program in wine

---

### Post by AutoStatic on 2010-02-19
> **jsfarney said:**
> I really just want music where I can clip music and loop it and find how many bpm's it is. And something that can beat match so my drums will match my samples would be great too.Clipping and looping:
- looping can be done with Audacity, not my personal fave though.
- BPM detection: Mixxx can do that, or UltraMixer. Maybe another program, anybody a clue? Audacity maybe?
- there are also dedicated loopers for Linux, like SooperLooper and Kluppe. And the next version of Mixxx will have looping too.

Beat matching, you mean like Traktor does? AFAIK there is no Linux software that does this properly, Mixxx can do it but it's not reliable. Or do you mean something else?

---

### Post by trulan on 2010-02-19
You'll see a lot about Ardour when talking Linux audio.  Ardour is an incredible, excellent program, but it doesn't sound like it would meet your needs.  Ardour really shines at multi-tracking and recording, especially with multiple inputs.  Since that's exactly what I do, Ardour is my main program.  Ardour also is pretty good for non-destructive editing.  You can cut, paste, combine, your audio, while the actual audio file you recorded stays intact.

I also use audacity a bit.  To me, using Audacity is like working with a scissors and scotch tape.  You can slice, dice, etc., (this is called destructive editing) and actually change the raw audio files.  But I'm afraid that's also not really what you are looking for.  It would be great for editing your samples, but not so much for looping them or matching beats.

Maybe it would be good to insert here that the Linux model is not to have one program that does it all, but to use several specific programs, each tailored to the task you want to accomplish.  For instance, you could lay down a beat sequence with Hydrogen, set up a synth sound with zynaddsubfx, drive that with a midi sequence from Qtractor or a live midi keyboard, sing along with it, and record it all into Ardour (or mix it all into one output with Jack Mixer to use in a live concert, if that's your style).  To do all this, you need jackd running in the background, letting you connect everything together.  It sounds complicated, I know, but once you get the hang of connecting things in jack, you'll never look back.  (Patchage is very helpful for this - it gives a good visual image of what is going on behind the scenes).

Sorry for the ramblings - I hope I haven't added to your confusion.  Good luck!

---

### Post by prokoudine on 2010-02-20
> **AutoStatic said:**
> 
- BPM detection: Mixxx can do that, or UltraMixer. Maybe another program, anybody a clue? Audacity maybe?
Audacity sort of has BPM detection, but it's just a Nyquist script that creates labels. Now Smasher and Freecycle do have BPM detection, but those are not composition tools really.

---

### Post by AutoStatic on 2010-02-20
Smasher too? I like that tool, thanks for the tip!

---

### Post by sgx on 2010-02-20
> **jsfarney said:**
> I'm really frustrated because I just want to make some beats and record music, but the ubuntu studio audio programs all seem like they are for programers and not beginners.  Could you please help me know what audio programs are good for a beginning musician to use?
Spend a few days with hydrogen, since it plays samples in patterns, and sequences of patterns that you place on the grid, it is far more than just a great drum machine. There is a kit-making tutorial a few months back, use it to make a 'drumkit', but made  of synth sounds, bass lines, guitar riffs, backing vocals etc, 32 samples are allowed in a kit. Find or make a long sweeping pad in zynaddsubfx for example, record it using audacity, save it as a pattern (though it would be a 'one beat pattern'), and if the sample is four measures long, put the pattern in the first fifth, and 9th and 13th spots etc on the song grid. Record a bassline, and a variant, as separate patterns, one of those would be in every spot on the song grid, A rythm guitar pattern might stretch over two measures, so the main things is, use the tools to your advantage, use your style, and creativity to redefine 'the box'you work in.

It will be important to form a titling system, so over months and years, there will be hooks in titles of projects, names of the elements of projects, and titles of finished tracks. I recently spent 4 hours searching for the project of a song that turned out with the rendered final track having the lead line obscuring nice rythmic elements, and I wanted to redo it, but I couldn't remember the instruments used,
and had failed to rename the project to match the title at the time. So I had to hunt through all the old projects from before taking my own advice.
:)
Cheers

---

### Post by markbuntu on 2010-02-25
I like to use hydrogen, rosegarden-zynaddsubfx and ardour all together and control them with jack transport. It makes it easy for me to change the drums in hydrogen and the midi tracks in rosegarden and the synth sound in zynaddsubfx and then just hit play to hear what it sounds like. The some editing and effects in ardour, which has midi now, yay! Endless fooling around before hitting record.
It helps to have a few monitors so you can watch everything.

I am also in the (long slow constantly distracted from) process of dialing in the korg nanos to these apps. They are very handy toys that take up little space.

Here are some helpful tutorials I found

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

Excellent ardour tutorial here:

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

If you are wondering how to sync applications together through jack. 

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

---

### Post by dvwolfman on 2010-05-29
> **jsfarney said:**
> I'm really frustrated because I just want to make some beats and record music, but the ubuntu studio audio programs all seem like they are for programers and not beginners.  Could you please help me know what audio programs are good for a beginning musician to use?

I recommended Jokosher to a loved one because it can be used without jack, and asks you what setup you want to use for audio when you start up. 
it's easy compared to Ardour2 w/jack

This is good if you are just recording like, a guitar and vocal track, etc...it has some effects too

I believe it is available in add/remove programs

but I encourage you to learn about music software, because there is a high learning curve on ANY OS for all music software. In the old days, you basically had to have a sound engineer present just to make the equiptment work. Was that a bad thing, I don't think so, the computer has taken place of the sound engineer and the computer is but an emulation of the real engineer, some would say a forgery...but there is electronic music which is an artform in and of itself where production and compostion meet and are indistiguishable....

Empower yourself, learn more about it, it is now a do-it yourself industry anyway
Good skill, not good luck
:guitar:

---

### Post by psidrum on 2010-05-29
Fasttracker 2
Impulse Tracker

any "Tracker" programs

once your learn these apps, it will be easy working with other DAW apps

---

### Post by dvwolfman on 2010-05-29
> **psidrum said:**
> Fasttracker 2
Impulse Tracker

any "Tracker" programs

once your learn these apps, it will be easy working with other DAW apps

for dance/electronic music agreed, but that's one approach to those forms, the point is dependent on stylistic needs:guitar:
not invalidating, just saying Hydrogen is a great enviornment to make beats for begginers too...one would not waste one's time with Trackers for sure, just saying that there are options, this is a modular envornment

---

### Post by psidrum on 2010-05-30
> **dvwolfman said:**
> 
not invalidating, just saying Hydrogen is a great enviornment to make beats for begginers too...one would not waste one's time with Trackers for sure, 

he is asking for assistance on whatever software that is out that assist beginners

no one is talking about which software "wins" or "loses" or "superior" or "inferior" to one another

so quit your "inferiority" debate bullshit projection to people and stop trying to create some "competition" with music softwares

---

### Post by dvwolfman on 2010-05-30
> **psidrum said:**
> he is asking for assistance on whatever software that is out that assist beginners

no one is talking about which software "wins" or "loses" or "superior" or "inferior" to one another

so quit your "inferiority" debate bullshit projection to people and stop trying to create some "competition" with music softwares

Ouch, didn't know their was a 'right' way to do things in this case, but I understand you, however educating oneself is important in production, I don't recend that motive as a musician or an ubuntu user, I'm sorry you need harsh language to express yourself, does that usually shut people up? Try it in all caps, I'm walking away, peace :p

---

### Post by geet89 on 2010-05-31
try nuendo with wine.. also i lke adobe audition for multitrack and it has a very intutive interface

---

### Post by psidrum on 2010-05-31
> **dvwolfman said:**
> 
not invalidating, just saying Hydrogen is a great enviornment to make beats for begginers too...one would not waste one's time with Trackers for sure, just saying that there are options, this is a modular envornment

another thing

Ubuntu is an African word meaning 'Humanity to others'

these softwares are created by people who gives themselves to assist people, without the belief of winning/losing/better than/less than

it is not created just so people like you can compare them and bash other softwares in the belief that one software is superior to another

its created so you can express yourself and you dont have to pay for it

so next time, keep your bullshit to yourself, because its not acceptable here

---

### Post by dvwolfman on 2010-05-31
> **psidrum said:**
> another thing

Ubuntu is an African word meaning 'Humanity to others'

these softwares are created by people who gives themselves to assist people, without the belief of winning/losing/better than/less than

it is not created just so people like you can compare them and bash other softwares in the belief that one software is superior to another

its created so you can express yourself and you dont have to pay for it

so next time, keep your bullshit to yourself, because its not acceptable here

walking away...your right btw, but you are contradicting yourself with your tone, satstisfied? Anger-->Hate-->Decadence

---

### Post by dvwolfman on 2010-05-31
> **dvwolfman said:**
> walking away...your right btw, but you are contradicting yourself with your tone, satstisfied? Anger-->Hate-->Decadence
  However, I must correct you, I didn't bash any software it is an issue of them serving different functions, they are different, not better or worse in general, you know that, you've been around the block with the software, let's not even argue, I bet you do a lot of good things, if you are here at all, and are a pretty decent individual, but I made you mad, so you lashed out, I understand that, but don't you dare say I'm bashing the software, I just think which to learn first for what purpose is a matter of taste and choice...lay off, relax, you don't have to win an argument for the sake of winning an argument, rather I do stand somewhat corrected, it is important to get beginners exactly what they need and keep it simple. Fine leave it at that, any more converstation about this farce would result in time better spent on helping things in general. So peace to you, Ubuntu to you. ok? I'll try not to think outloud, wouldn't want to be a thought criminial.

---

### Post by cariboo on 2010-05-31
This thread really doesn't seem to be going anywhere. Closed.

---

