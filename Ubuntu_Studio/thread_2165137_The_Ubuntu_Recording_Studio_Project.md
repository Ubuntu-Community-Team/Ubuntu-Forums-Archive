---
title: "The Ubuntu Recording Studio Project"
date: 2013-08-03
forum: Ubuntu Studio
---

### Post by pepsifx357 on 2013-08-03
Hey all!

I wanted to share with you guys, a projects that I have been working on for a few years now.  I started using Ubuntu back in 2007, while I was in college.  Back then, I was using Windows with Nuendo for recording editing and mixing in the box.  I started studying Ubuntu, bought some books, and started using it as a DAW when 10.04 came out.  I"ve seen a lot of people use Ubuntu or some other Gnu/Linux distro as a DAW, but I wanted to see if Ubuntu would work for a mid sized professional level studio.  My goal was a setup that would allow you to Track, Edit, Mix, and possibly master a professional sounding album.  Right now, the system is running at 88.2K@24bit@0.7ms with a custom built 3.4.47-rt62 kernel. I've been at this for a while and I'm just now getting to the point where I'm about ready to open for business...at least for testing.  Here are my computer specs along with the studio equipment:

Computer:
AMD FX 8350 Vishera 8 Core
16GB DDR3 RAM
ASUS Sabertooth 990FX
Nvidia GTX 560 ti
RME HDSP MADI

Studio Equipment List:
SSL Alpha MADI AX - Converter
(2) Seventh Circle Audio N72 pre amps
(2) Seventh Circle Audio B16 Compressors
(1) Seventh Circle Audio 2 channel Active DI
Soundcraft Spirit Studio 24
Lexicon MX400
Midiman MidiSport 8x8
DBX 163x/463x
Coleman Audio M3
Yamaha NS-10m Monitors
Dynaudio Acoustics BM15a Monitors
Patchbay
Philips CD recorder

Microphones:
(3) Shure SM-57
(1) Senhheiser 421
(2) Cascade Fathead
(1) Peluso 22 251
(1) AKG C451e
(1) Shure Beta 52
(1) Modified MXL V63M
(1) AKG 119
(1) Shure 55

Here are some dark and fuzzy pics of the control room setup.  The overhead light is out and I'm not a photographer...sorry.


Oh...and the left side cart isn't finished yet.  I still need to stain and poly.  Also, The KRK Monitors are a friend's.
[IMG]http://ubuntuone.com/4lwGdOLiCfiQrz3fkFvUUT[/IMG]

[IMG]http://ubuntuone.com/4ShBd6JlX5cqffN3i9bAwq[/IMG]

[IMG]http://ubuntuone.com/0BzYGSZ7574A4xfqNp8IGC[/IMG]

[IMG]http://ubuntuone.com/6gAV2K4zOUa8olVs7uOymr[/IMG]

---

### Post by cub on 2013-08-04
Cool! Please keep us posted. I had not heard about the Seventh Circle DIY builds before, do you have anything recorded with them? Were they hard to build?
Also, what is your typical setup inside the computer, what DAW do you use and so on?

---

### Post by pepsifx357 on 2013-08-04
> **cub said:**
> Cool! Please keep us posted. I had not heard about the Seventh Circle DIY builds before, do you have anything recorded with them? Were they hard to build?
Also, what is your typical setup inside the computer, what DAW do you use and so on?

Sorry, I should have mentioned the software...DER!

Ubuntu 12.04 - KDE4
Patchage
Ardour 3
Hydrogen
Linux sampler-Jsampler
Was using FL Studio, but now moving away from it entirely.

We've figured out a good workflow inside linux.  We think.  I'm using a few virtual desktops here.  Patchage sits on the first desktop and is also open on another computer so we can easily patch what to where without switching desktops.  Linux sampler sits on the second desktop with as many instruments open at one time.  This give us the ability to add any instrument we want when we want it.  Takes up a lot of ram though.  Hydrogen sits on the 3rd desktop and Ardour sits on the 4th and 5th desktops.  Editing Window on the 4th and Mixing on the 5th.  If I'm using Guitarix, it will sit on the 6th desktop along with lingot(tuning).  With all this running, everything gets piped into Ardour 3, including individual drum tracks from hydrogen, and all the Inputs are turned on so everything can play through Ardour while we tweak.  Everything form Ardour gets sent directly out.  Channel 1 to 1 Channel 2 to 2 and so on until the board is full.  Then we mix!
To create a mixdown, the Group Outputs on the board are piped directly back into the system via 1-8 inputs on the sound card.  We just send all the channels through groups 1 and 2 and record the results.  We can record the mixdown with any other program including ardour.  Most of the time I use Audacity to record the mixdown from the Group Outputs, unless I'm creating stems. The connection of Ardour to the ouputs usually look like this:

Kick        -> 1
Snare_bot->2
Snare_top->3
HH          ->4
Tom-1     ->5
Tom-2     ->6
Tom-3     ->7
Cymbols   -> 8-9
Overheads->10-11
Bass        ->12
Guitars-L  ->13
Guitars-R  ->14
Ect.

I've tried to use some different software for storing sessions (LADISH) like Claudia, Cadence ect.  To no avail.  They're just not mature enough yet.

Seventh Circle Audio provides instructions that remind me of those lego kits I used to get when I was a kid.  I know how to solder and take DMM readings...that's about all you need.  It took about 7 hours to build the first N72 and about 4 hours on the second one.  The DI took about 2 hours and the compressors took about 2 to 3 hours a peice.  They have a new system now where you can get a single unit with a small enclosure and you can mount up to 4 of them in an auxillary rack mount.  The compressor is AMAZING!  I can't reccomend this company enough!

Here's a song where the background(clean) guitars were recorded with the N72 and some of the heavy guitars.  Not the best mix, buts it's all I got right now.  Drums are a set of samples I've had for a while, setup in Hydrogen, the bass is Linux Sampler, half of the heavy guitars were recorded with the Seventh Circle Audio DI box -> N72 into Guitarix, the other half is a mesa boogie recorded with a sennheiser 421 -> N72.  The bass is crap...I need better samples or a bass guitar.  Reverb is the Lexicon MX400.  Hope you enjoy!

[http://ubuntuone.com/4LLoToWC1SbIh8NZnJxHaz]("http://ubuntuone.com/4LLoToWC1SbIh8NZnJxHaz")

Here's another one but the guitars used were all run through the DI -> N72 straight into Guitarix.  It's just a little something we were playing around with.  The sequencing was in FL Studio on this one, but like I said, I'm trying to get away from it alltogether.

[http://ubuntuone.com/2L0HHtIORrOCCUfUcNDl50]("http://ubuntuone.com/2L0HHtIORrOCCUfUcNDl50")

---

### Post by tomasisainmdom on 2013-08-12
Really great what you're doing, and a quality sound you're achieving.  Its obvious you've really thought everything through and have put a lot of effort into it.  I'd love to hear more of what you've done.  It would be nice to see a showcase of well produced material coming from linux based studios (even more so from Ubuntu Studio). 

I'm sure you've invested a good amount of money, as hardware isn't cheap, but it looks like you serve as a proof of concept that you can create a quality studio without breaking the bank.

Keep up the good work, good luck with the business, and please keep us updated.

---

### Post by pepsifx357 on 2013-08-12
I appreciate the kind words.  I'm still working on baffles and cabling from the live room to the control room, but she's coming together nicely!

I hope to get some demos together for the studio, so you guys can enjoy my "GNU Sounds."  Awesome! That should be my studios name!  

By the way, me and a friend went through and tested zynaddsubfx.  Wow!  There's a lot of really good quality sounds with that synth.  I'm not sure I need any other synth after hearing the results.  It has soooo many sounds it's rediculous.  Sure beats the heck out of FL Studio's quality.

---

