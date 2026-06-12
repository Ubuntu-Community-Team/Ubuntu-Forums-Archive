---
title: "HOWTO: Install The Wiinstrument for Linux"
date: 2008-07-21
forum: Ubuntu Studio
---

### Post by motin on 2008-07-21
I find it rather remarkable that there seem to be no tutorial, guide or blogpost whatsoever that explains how to get a fully working The Wiinstrument for Linux going (searching for "wiinstrument" on ubuntuforums.org actually returned 0 search results!), despite the fact that it has been out since September last year... The best documentation out there is [the official release note](http://screenfashion.org/2007/09/the_wiinstrument_02_for_linux.html), where half-complete instructions for compiling and installing the Linux version can be found.

Here is a more complete recipe on how to install the 0.2b717 version for Linux (the current - as of 2008-07-21 - latest release*):

Before we begin, I'll mention that even though the application installs and runs (albeit with stability issues) - I have yet to be able to use the application in any other way than making few and random noises... Hopefully this guide will help more getting at least as far as I did, and together maybe we can solve some of the usability issues... Ok let's get going:

1. Go to the [Sourceforge site]("http://sourceforge.net/projects/wiinstrument/") and download "The_Wiinstrument_0.2b717_source_linux.tar.gz": [http://sourceforge.net/project/platformdownload.php?group_id=190975&sel_platform=4445](http://sourceforge.net/project/platformdownload.php?group_id=190975&sel_platform=4445)

2. Open a terminal, browse to the directory where you downloaded the tar.gz-file and run the following:
```
sudo apt-get install libboost-dev libportmidi-dev libglew1.5-dev zlib1g-dev libcwiid0-dev
tar -xvf The_Wiinstrument_0.2b717_source_linux.tar.gz
wiinstrument/configure
cp wiinstrument/lib/boost/  wiinstrument/src/ -r
cp wiinstrument/lib/Gosu/ wiinstrument/src/ -r
cp wiinstrument/lib/Gosu/gcc/* wiinstrument/src/ 
cp wiinstrument/lib/portmidi/* wiinstrument/src/
cp wiinstrument/lib/glew/* wiinstrument/src/ -r
cp wiinstrument/lib/drums/* wiinstrument/src/
cp wiinstrument/lib/libcwiid/* wiinstrument/src/
cd wiinstrument

```

2. Compile:
```
make
```

3. Install the wiinstrument-package version of libfmod-3.75.so (we are making a backup of the currently installed file if any):
```
sudo cp /usr/lib/libfmod-3.75.so /usr/liblibfmod-3.75.so.org.bak
sudo cp fmodapi/api/libfmod-3.75.so /usr/lib

```

4. Download Wingdings.ttf (from a Windows CD or from somewhere on the net), put it into ~/.fonts and then logout and back in again.

5. Open up a terminal once again, cd into the wiinstrument-directory and run the application from the "src/" subfolder:
```
cd src/
./wiinstrument

```

6. Press 1+2 on your wiimote as instructed (do this even rather quickly after starting the application - even before the application window pops up)

Ok great - now you should be able to wiggle your wiimote (and optionally your nunchuk) and see how the colorful bars react on your movements (see screenshot).

If you have an external MIDI-controller, choose the relevant output port from within The Wiinstrument (Options page -> MIDI Device) and configure the MIDI controller as usual.

If you lack hardware MIDI goodness: Fire up any application that supplies a MIDI output port (Rosegarden, Qsynth with output device set to file, etc) and use that output port instead. 
You should now be getting those Wiimote-generated MIDI events routed into your application of choice!

HOWEVER, since the application is using OSS for sound output, it will hog your current sound output device, making it impossible to start a software synthesizer in parallell! At least for me (with but one sound-card and no external MIDI controller), this means no sound at all... and the purpose of the application is kinda defeated...

Fear not! Here is where jacklaunch comes in. It will route the sound through JACK. 

Install jacklaunch from the repositories:
```
sudo apt-get install libjackasyn0
```

Now fire up JACK as usual then run:
```
jacklaunch ./wiinstrument
```
Instead of only "./wiinstrument"

Press Home on the wiimote to come to the MIDI Drum mode. Be sure to set Qsynth's instrument on Channel 1 to a drumset. Hopefully you will be able to get some drum notes now!

Some issues are evident though:
0. I can't seem to get more than two different sounds going though (one from the wiimote and one from the nunchuk). These can be changed by pressing left or right then B - after that the conjacent MIDI notes will be played instead. If anyone understand how to get more sounds by moving in different ways - please share!

[1. The application tends to crash every second minute or so]("http://sourceforge.net/tracker/?func=browse&group_id=190975&atid=935516") (but can sometimes run 10 minutes or more at once), leaving the following trail in stdout:
```
wiinstrument: ./boost/circular_buffer/details.hpp:285: typename boost::iterator<std::random_access_iterator_tag, typename Traits::value_type, typename Traits::difference_type, typename Traits::pointer, typename Traits::reference>::reference boost::cb_details::iterator<Buff, Traits>::operator*() const [with Buff = boost::circular_buffer<double, std::allocator<double> >, Traits = boost::cb_details::nonconst_traits<std::allocator<double> >]: Assertion `is_valid(m_buff)' failed.
Avbruten (SIGABRT)

```

2. ALSA sequencer buffer overflow messages: When running Qsynth with the options Verbose MIDI events and Dump MIDI router events enabled, these errors crop up frequently:
```
fluidsynth: warning: ALSA sequencer buffer overrun, lost events
fluidsynth: warning: ALSA sequencer buffer overrun, lost events
```
This may be related to the fact that it seems that far from many MIDI events are being received from the Wiinstrument - making it feel rather insensitive and ungracious to work with...

3. There has only been two new releases since early september 2007: the 0.2.b745 bugfix release for Mac OS X (released later that month), and the 0.2.1b version for Windows (released in november 2007)
I have seen no information about any upcoming release plans, and it kinda looks as if the Linux port has been more or less abandoned...

**Quick notes about solutions to the above:**
No. 1 could be solvable by a dedicated hacker... Anyone? (Sorry, but I lack C-skills...)
No. 2 could be able to be avoided by increased the ALSA sequencer buffer - but how is that done?
No. 3: If we together can help solve these issues, then of course I promise to upload and annonce the patched version of The Wiinstrument for Linux 0.2 - helping to solve this point, albeit only for the 0.2.0-release series. 
If anyone (or everyone...) could get in touch (preferably through the [project site]("http://sourceforge.net/projects/wiinstrument/")) with [fuersthoelle]() or [hyp__](http://sourceforge.net/users/hypo__/) from [screenfashion.org]("http://screenfashion.org/") (the  original developers) about these issues then maybe an official release may be available in the future... [Maybe even a Linux port of 0.2.1b?]("http://sourceforge.net/tracker/index.php?func=detail&aid=2023923&group_id=190975&atid=935519")

If anyone is able to help out fixing these issues - please do... and report here your success and failure stories!

Looking forward to hear from you all!

UPDATE 23-jul-2008: Two major / minor issues from before (that the application hogged all of the sound device + there was no jack output) has now been solved by the [successful installation and configuration of oss2jack]("http://ubuntuforums.org/showthread.php?p=5438615#post5438615")! Updated the Howtos accordingly.

UPDATE 10-aug-2008: There is even a simpler alternative than oss2jack! "jacklauncher" is in the repos, does the job well and does not require any kernel module compilation... Updated the howto accordingly. So much for writing [that guide]("http://ubuntuforums.org/showthread.php?p=5438615#post5438615")...

---

### Post by eyecreate on 2008-09-29
I have been trying this to compile but it will not go through the make command. The little bit I read online seems to point to the fact that fmod 3.75 is in 32bit and I can't compile wiiinstrument with a 32bit library on a 64bit application. Is there any 64 bit fmod or a way to change the dependency on fmod to version 4 which is 64 bit?

---

### Post by Stochastic on 2008-09-29
Wow, seems like a lot of work for an app that just simply isn't performance ready just yet.

I was sending my wii through PD via the PD external: [http://mikewoz.com/index.php?page=pd-stuff](http://mikewoz.com/index.php?page=pd-stuff) then creating my own instruments.  I've only had one crash during a performance so far.

---

### Post by motin on 2008-09-29
> **Stochastic said:**
> Wow, seems like a lot of work for an app that just simply isn't performance ready just yet.

I was sending my wii through PD via the PD external: [http://mikewoz.com/index.php?page=pd-stuff](http://mikewoz.com/index.php?page=pd-stuff) then creating my own instruments.  I've only had one crash during a performance so far.

Yeah, unfortunately the only way to determine if it was performance ready or not was to get it running as good as possible :/

PD sounds interesting, would you mind briefing us how you use it in audio production/performing together with the wiimote?

Cheers

---

### Post by Stochastic on 2008-09-30
> **motin said:**
> PD sounds interesting, would you mind briefing us how you use it in audio production/performing together with the wiimote?

Cheers

Well I ran the 1 & 2 buttons and the numchuck upper & lower buttons into a trigger sensor that incremented pitches in a tone row, its inversion, its retrograde, and its inversion retrograde, respectively; these pitches were sent as midi notes to a soundfont in QSynth.  The + and - buttons were used as controls to increment and decrement (respectively) the midi channel # on which the notes were being sent (effectively changing instruments in QSynth).  The numchuck joystick's up-down axis was mapped to midi velocity values and the left-right axis was mapped to the midi duration values (i.e. time before a note-off message was sent).

I then patched the tilt values of the wiimote to the amplitude of an additive synthesis patch I had built (level was a 0 amplitued value, and there was a threshold of about 20 degrees incline before the envelope would open).  The accelleration value was also calculated, where the faster the wiimote moved, the higher the harmonic content and louder the slowly enveloped notes were.  The pitch of these notes were based on the last pitch sent from the midi triggers.

I was working along side a guitarist at this show, and we were attempting to map the output of his guitar through a waveshaper patch I was working on.  I was trying to map the left-right motion of the wiimote to the waveshaper, recording these motions into the waveshaping function only immediately after the pressing of the wiimote's trigger button.  But alas this wasn't production-ready in time for performance, so it was ditched.  (the one performance where this system crashed out on me was when I had this enabled waveshaping feature enabled - I think I just had too many inefficient chunks of code working away at once)

On top of all this, the wiimote was in a laser-gun holder and the laser was drawing virtual graffiti on the room's wall with Graffiti Research Lab's Laser Tag software (running on a different computer).  But that has no real connection to the wiimote and pd - it's just an added coolness factor.

Hopefully this has given you some inspirations for sounds from the wiimote! :D

---

### Post by motin on 2008-10-01
> **Stochastic said:**
> Hopefully this has given you some inspirations for sounds from the wiimote! :D

It sure have! Unfortunately I have NO idea of how you actually made it all work as you are describing... Are you willing to share a recipe for the rest of us on how to accomplish the same thing as you did? It'd be a great start-off to experiment further - maybe we will be able to take the concept further and give something back that you can use for upcoming performances...

---

### Post by julie2008 on 2008-10-01
separate software are provided to install win instrument for Linux.the time duration to install is all low.
___________________________________________________________________
[Sending flowers to chicago](http://www.florist-flowers-roses-delivery.com/illinois/chicago_il.html) [low rate loans](http://www.cheaponline-loans.co.uk/) [vilafranca del penedes](http://www.vilafrancadelpenedes.com) [download ringtones](http://www.myringtoneshub.com/)

---

