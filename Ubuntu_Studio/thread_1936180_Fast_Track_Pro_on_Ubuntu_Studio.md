---
title: "Fast Track Pro on Ubuntu Studio"
date: 2012-03-05
forum: Ubuntu Studio
---

### Post by sirriffsalot on 2012-03-05
Hello!

   I'm an avid guitar-player and would like to start recording a leg up more professionally with the amazing software that Ubuntu Studio and it's packages can provide. But, I think, in order for JACK or the other interfaces to talk to my equipment, I will need some preamp with a USB-plug into my computer for things to add up with Ardour et cetera. I've been searching around the web, but the discussions are always very narrow and detailed, so I wonder if anyone knows whether Fast Track Pro from M-Audio is a viable option?

   Also, I currently, have a Fender Mustang I amplifier, which has a direct USB-plug from the amp to the computer. I wonder, if anyone of similar experience, knows how to record this on Ardour? Thank you very much:)

   --> Leo

---

### Post by sgx on 2012-03-06
Hi, the Mustang usb sound will be in the qjackctl Connect panel,
on the Audio tab, 
System
  Capture_1
  Capture_2

These can be routed anywhere that is available,
Guitarix, Rakarrack, Timemachine etc

(links 4 and 8 at the wiki, explain things)
[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

qjackctl Setup page,

Input Device >
Output Device >   click the  > to see the Mustang, and select it
as input device, select your soundcard or motherboard chip for output device,
and use headphones/speakers on its output connector

The Mustang records fine without any help. You  can also use the
headphone/line combo output, connected to a soundcard line-in.
In that scenario, the amps volume knob is active, not the case
with the usb signal, which is controlled by software.

An editor for all the amp models, fx, and preset storage
is here:

[http://piorekf.org/plug/](http://piorekf.org/plug/)

You need a full synaptic install of QT, as one might get
by installing qjackctl, rosegarden, qsynth, and qtractor,
There are now .deb and .rpm files at the authors download page,
: [http://piorekf.org/plug/download/](http://piorekf.org/plug/download/)

go here for the .deb

[http://debian-multimedia.org/dists/testing/main/binary-i386/package/plug.php](http://debian-multimedia.org/dists/testing/main/binary-i386/package/plug.php)   then

sudo dpkg -i plug_1.0-0.0_i386.deb

[https://bitbucket.org/piorekf/plug/wiki/Home](https://bitbucket.org/piorekf/plug/wiki/Home)  has some
ubuntu details, if it does not work with usb out of the box.
The headphone connector is not effected.

Ardour has lots of configurations to set up, make a project,
insert a track, make sure the Mustang is on it, arm it,
press record and play :popcorn:

There are lots of youtube videos for ardour, part one of 3:

[http://www.youtube.com/watch?v=43ES7p4ejX0&feature=relmfu](http://www.youtube.com/watch?v=43ES7p4ejX0&feature=relmfu)
Cheers

also there is a long thread here, awhile back, about the fast-track pro,
I think newer ubuntu supports it best.

---

### Post by sgx on 2012-03-06
There is an empty Mustang preset available at the Fender website,
that has the cabinet, and all effects turned off, some prefer this
when using specific external fx, not wanting any extra coloration. I just saved a Twin Reverb preset with all the fx off, and neutral gain settings, to be a reasonably clean tone, then build  upon
it with the linux fx available.

---

### Post by sirriffsalot on 2012-03-06
Wow, thorough guide, thanks a lot! Gonna try it later today and get back to you!

---

### Post by sirriffsalot on 2012-03-06
Yes, I've been fiddling around with the additional software that was provided with my purchase, but can you be a tad more precise what you mean by "the linux fx available?":) Recently started trying Ubuntu for the purposes of recording, so please use baby-steps like sgx did :) Cheers!

---

### Post by sirriffsalot on 2012-03-06
Alright, so I've been reading those two links you pointed to, and tried what you said, but already in the beginning there are bumps in the road, probably since the guide is pretty old? Seems like it since the QJackCtl setup is slightly different from the guide's example pictures. Anyway, problems are as follows:

The HowToJACKConfiguration was very helpful, or would have been, if it had worked, haha.:) But perhaps I have skipped ahead a little and missed some important configurations/installs before that makes the HowToJack-link a bit difficult to make add up with the rest. Anyway, all is fine (I'm only gonna have 1.33 msec latency it seems!) until I tick the box saying in Misc "Start Jack audio server on application startup", which is pretty crucial, haha:) There is a series of lines telling me what is wrong when I startup QJackCtl which I will add further down here, but I tried the link's advice at the bottom, which was to "set the appropriate entry (autolaunch) to 0 in the ~/.jackdrc file, qjackctl should work again" even though the problem might not be there. The point is that, in the .jackdrc file, there is no such text whatsoever, all that says is: "/usr/bin/jackd -p 128 -R -P 60 -T -d alsa -n 2 -r 44100 -p 1024 -d hw:0,0". So is there something missing there, something to be removed, or just to leave it as it is?:)

To find out, here is the error message from QJackCtl:) I have done an hour's worth of searching for solutions, but the issues are so specific based on one's situation and hardware that I have not yet found one, however I will keep on looking while I eagerly await response!

Here is the error message:

17:41:00.585 Patchbay deactivated.
17:41:00.593 Statistics reset.
17:41:00.608 ALSA connection change.
17:41:00.623 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
17:41:00.854 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
17:41:00.961 ALSA connection graph change.
17:41:01.147 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: driver "alsa" selected
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Saving settings to "/home/sirriffsalot/.config/jack/conf.xml" ...
Tue Mar  6 17:41:00 2012: Starting jack server...
Tue Mar  6 17:41:00 2012: JACK server starting in realtime mode with priority 10
Tue Mar  6 17:41:00 2012: control device hw:2
Tue Mar  6 17:41:00 2012: control device hw:0
Tue Mar  6 17:41:00 2012: [1m[31mERROR: Failed to acquire device name : Audio2 error : Input/output error[0m
Tue Mar  6 17:41:00 2012: [1m[31mERROR: Audio device hw:2 cannot be acquired, trying to open it anyway...[0m
Tue Mar  6 17:41:00 2012: [1m[31mERROR: Failed to acquire device name : Audio0 error : Input/output error[0m
Tue Mar  6 17:41:00 2012: [1m[31mERROR: Audio device hw:0 cannot be acquired, trying to open it anyway...[0m
Tue Mar  6 17:41:00 2012: creating alsa driver ... hw:0|hw:2|32|2|48000|0|0|nomon|swmeter|-|16bit
Tue Mar  6 17:41:00 2012: control device hw:0
Tue Mar  6 17:41:00 2012: configuring for 48000Hz, period = 32 frames (0.7 ms), buffer = 2 periods
Tue Mar  6 17:41:00 2012: ALSA: final selected sample format for capture: 16bit little-endian
Tue Mar  6 17:41:00 2012: [1m[31mERROR: ALSA: cannot set period size to 32 frames for capture[0m
Tue Mar  6 17:41:00 2012: [1m[31mERROR: ALSA: cannot configure capture channel[0m
Tue Mar  6 17:41:00 2012: [1m[31mERROR: Cannot initialize driver[0m
Tue Mar  6 17:41:00 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
Tue Mar  6 17:41:00 2012: [1m[31mERROR: Failed to open server[0m

Perhaps it makes it easier to type the "dialogue-box" that pops up to inform me of the basic problems? Here it is...

Error - JACK Audio Connection Kit
Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server. 
Please check the messages window for more info.

Sorry for all the text! Immensely appreciate your help:)

--> Leo

Edit: This is my most helpful coincidental event ever, rofl. I forgot to add that when you said that in the JACK Connections preferences in the Audio panel there should be capture_1 and capture_2, there were none. After I finished writing all the above, I tried finding out why Banshee was constantly going idle and non-functional after QJackCtl had kicked in, and I found someone suggesting to someone here [http://ubuntuforums.org/showthread.php?t=1470407](http://ubuntuforums.org/showthread.php?t=1470407) that one should run PulseAudio through JACK. So amazingly enough, when I started JACK again and looked things over, suddenly there was no error message at all and the Audio panel had "PulseAudio Jack Sink [and] System (with capture_1 and capture_2)" on the left, and on the right "PulseAudio Jack Source [and] System (with loads of playback_ lines)". So I suppose this is progress, and I suppose the fact that PulseAudio was not directing to JACK was the reason for all the errors, or? Because all the errors are gone now :-S However, if I start QJackCtl while Banshee is playing, or try to start and play with Banshee later, there is still nothing, so I am going to try to find out how to make them work together by further reading that link. With this working I can continue working with the guide you wrote me, but I am still curious as to whether the PulseAudio connection with JACK Sink not being there was the problem.. Cheers:)

---

### Post by sgx on 2012-03-07
Hi, about usb audio devices, in qjackctl, choose 3 for the
Periods/Buffer setting, very important. Sorry I forgot to mention
that :(

System
Capture_1
Capture_2

there is a little > widget on the left of 'System', click it, and the contents will drop down, revealing Capture_1 and 2, click again to reduce the clutter, or when you know everything you use has stereo input/output

open the qjackctl Setup page, click the  >  widget on the right side of
Input Device   >

The dropdown list should include    hw:1 Mustang Amplifier
(or hw:0 Mustang Amplifier) Select it.

/usr/bin/jackd -P70 -t1000 -dalsa -r44100 -p256 -n3 -D -Chw:1 -Phw:0,0

Use the above line in a terminal, to start jackd.
But change Chw:1 -Phw:0,0 to reflect your qjackctl choices in
the dropdown list of Input/Output devices, Mustang as Input,
and your souncard/chip as output. After running the above command,
the terminal output should end something like this:

ALSA: final selected sample format for capture:
16bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback:
32bit integer little-endian
ALSA: use 3 periods for playback

Now start qjackctl, and it will use the settings from the command, your
Mustang should send its sound to your soundcard outputs. Untick the
option to start jackd automatically, for now.

(Don't use Pulse audio things in your jackd sessions.)

To record, install timemachine (using synaptic) Start it, and in the qjackctl Connect page, Audio tab, select System on the left,
(your Mustang) and timemachine on the right, and press the connect button on this page, (not the one on the main gui) Also connect System on the left, to System on the right, so sound also goes to your soundcard as you record. Press the big green timemachine record button, and it turns orange as it records. Press again, to stop,
use vlc to play the high quality tm.w64 files it creates, import them into audacity to edit, and export them in desired format/bitrate.

Calf plugins fx are excellent, install them, and start them by menu,
or the command  calfjackhost. Open each fx control interface using the edit button on the main Calf gui, and connect them in qjackctl

System(Capture)----to----Calf
Calf---------------to----System(Playback)
Calf---------------to----timemachine

Your guitar is on System(Capture) so if you chose Calf Phaser, the above qjackctl routings would send your 
guitar to the calf phaser, and the output of guitar/phaser to both
your soundcard, and a recording software. The connections duplicate
real-world analog cable connections in most cases.
Cheers

---

### Post by sirriffsalot on 2012-03-08
Well, that cleared up a whole bunch of things, and was real helpful until Audacity was mentioned, haha!:) I was actually wondering why I had read nothing of time machine before in the setup of Ardour, and now I see why. I forgot to mention that I am planning to use Ardour, a bit more professional software which I have looked into in some detail. The command, like everything else you've said apart from Audacity, was the best help ever. I would have sat for ages figuring that out.. It's a shame that people have to hunt as much as they have to since the Ubuntu teams et cetera can't cover all the different variables people put together in their computer and OS et cetera...

Anyway, gonna read on from the guide that UbuntuStudio and Ardour provide, but if you have the answer there too, I will be ever-more grateful! If not, I am still immensely beholden to you, and I am sure a lot of people will find this thread useful!

Cheers mate:)

--> Leo

---

### Post by sgx on 2012-03-09
[http://linux.die.net/man/1/jackd](http://linux.die.net/man/1/jackd)    this manpage itemizes all the
command options for jackd V1, and is handy for reference

[http://tldp.org/](http://tldp.org/)  a trove of links to information about many
linux softwares

[http://www.linuxmanpages.com/](http://www.linuxmanpages.com/)  breaks down many available manpages
based on their type.

Saving $$$ for this:

[http://www.sweetwater.com/store/detail/MustangFLR?utm_source=none&utm_medium=PPC&utm_campaign=none&gclid=CMDstIb72a4CFQFgTAod-iJL0Q](http://www.sweetwater.com/store/detail/MustangFLR?utm_source=none&utm_medium=PPC&utm_campaign=none&gclid=CMDstIb72a4CFQFgTAod-iJL0Q)

:guitar:

---

### Post by sirriffsalot on 2012-03-09
Awesome, cheers mate:) Doing many a favour I am sure, including myself!

--> Leo

---

### Post by sirriffsalot on 2012-03-09
I am curious though, certainly there must be a somewhat easier way of going about starting QJackCtl without having to do that command all of the time? Or is this just for Ubuntu Studio whereby PulseAudio is installed? If so, is removing it an option?

---

### Post by CivilizationII on 2012-03-10
> **LeoTB said:**
> Hello!

   I'm an avid guitar-player and would like to start recording a leg up more professionally with the amazing software that Ubuntu Studio and it's packages can provide. But, I think, in order for JACK or the other interfaces to talk to my equipment, I will need some preamp with a USB-plug into my computer for things to add up with Ardour et cetera. I've been searching around the web, but the discussions are always very narrow and detailed, so I wonder if anyone knows whether Fast Track Pro from M-Audio is a viable option?

   Also, I currently, have a Fender Mustang I amplifier, which has a direct USB-plug from the amp to the computer. I wonder, if anyone of similar experience, knows how to record this on Ardour? Thank you very much:)

   --> Leo


You **don't** need any preamp, just connect you guitar output cable into the microphone input of your sound card (if this one is mini-jack, you need a 'jack converter' --> standard jack to mini-jack, something like 1$). The standard sound chipset of any motherboard delivers some outstanding sound --> cost = 0$. You can even 'naturaly' saturate it (*) by increasing the input volume in alsamixer/pulseaudio, which is a pure marvel with 44khz audio/digital converter, and real heaven with 96Khz or 192Khz one. Any modern motherboard (read less than 3~4 years) have at least a 96Khz converter.

(*) You will never reach heavy saturation by this way, but some sound very similar to tube saturation (so a little bit more than overdrive). Ok, this is not a '59 Bassman, but for 1$ (the jack converter) you can't find anything better, and for 1000$ you can't either :smile:.

Ardour is another marvel for recording, and the mixing capabilities are also outstanding. This software requires a little learning curve, the best is to read the doc. from ardour site, this is something like 1/2 hour to 3 hours, depending on the frequency of your brain ;).

---

### Post by sgx on 2012-03-10
> **LeoTB said:**
> I am curious though, certainly there must be a somewhat easier way of going about starting QJackCtl without having to do that command all of the time? Or is this just for Ubuntu Studio whereby PulseAudio is installed? If so, is removing it an option?
Hi, and hurray for the weekend :popcorn:

when you save the settings from qjackctl, it creates/re-writes the .jackdrc file, and saves the old version as a backup.
So you can easily bring the command and its GUI into agreement. Once you have a working qjackctl setup, then you can opt to have it launch jackd automatically, from the misc tab of the setup page.

Your terminal saves its command history, in the text file .bash_history,
each command is accessed in order, by presssing the up-arrow key,. I edit this periodically,
to cluster commands I use daily, at the top. I also save complex commands I would otherwise forget,
in textfiles I can add back in later, if needed. 

I use different jackd settings for keyboards, drums, Reaper sessions, and sometimes use two input devices, so it is much faster to just tap a key a few times, to launch the desired settings. Using multiple setups means starting qjackctl automatically, is not a good option for me, yet maybe
perfect for others. :)
Cheers

---

### Post by sirriffsalot on 2012-03-10
Hello CivilizationII!

Yea, I knew that was all I needed for a home-studio settings, but I am in need of such a preamp anyway, so I might as well award myself the luxury of even better configuration options and sound at home too!;D

As for the mixing, I'm gonna be going through that tomorrow, I think my brain can handle it within a couple hours unless software complications arise:)

Thanks for your suggestions!

--> Leo

---

### Post by sirriffsalot on 2012-03-12
Great help:) Would you by any chance have a way of running certain commands by keybind commands? Can't work it out, haha:) Also, the command which was very helpful nonetheless, kills my sound outside Ardour and JACK, so when I am done working with Ardour, would there be a way to reset the effects this command has?:)

---

### Post by sgx on 2012-03-12
Ardour and some others may have options to start jackd automatically,
for convenience, but qjackctl still can be run, and jackd shut off using that gui. There is also a command jack_disconnect.

Aqualung is a nice media player that connect to, and uses jackd, if that simplifies things. Handy to quickly overdub a lead guitar, using timemachine to record.
Cheers

---

### Post by sirriffsalot on 2012-03-14
To have some overdub would be handy indeed, but I am running into curious problems with Aqualung already, problems which don't seem to be covered too much on the web:-S If I try to play .mp3-files with it everything's fine, but WMA is no-good. The whole thing crashes and exits as soon as I try to play them... Any ideas?:-S Terminal output is

No output driver specified, probing for a usable driver.
jack_client_new: deprecated
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Probing JACK driver... JACK server not found
Probing PulseAudio driver... OK
VST_PATH not set, defaulting to /home/sirriffsalot/vst:/usr/local/lib/vst:/usr/lib/vst
Aqualung received signal 11 (Segmentation fault).

To help the developers fix the bug causing this crash,
please do the following:

1) configure & make Aqualung with --enable-debug
2) reproduce the crash
3) send the crash report to the developers

Thank you for supporting Aqualung!

Thanks once again for help, really appreciate your saving lots of my time:)

---

### Post by sgx on 2012-03-14
unrestricted-extras

win32codecs-all

gstreamer good bad and ugly

try installing those in synaptic, and make sure raptor is the newest.

[http://www.youtube.com/watch?v=XjzFWE9sstI](http://www.youtube.com/watch?v=XjzFWE9sstI)  ffmpeg wma to mp3 vid

vlc and xmms players have jackd plugins to install, just checked, and
both worked to overdub with timemachine, and an instrument.
Cheers

---

### Post by sirriffsalot on 2012-03-15
Awesome, gonna check it out now, surely some of that, if not all, will work:)

One final thing before another weekend!^^ My speakers are currently a 5.1 surround system, and my ardour session has one master track/bus that has two outputs (master output 1 and 2), that by default have been connected to only the first two of the six "playback_6" options. 

Is there a particular way to connect the master outputs to those different playback input so it comes out the right way...? Now I have simply done it in order, whereby output one goes to 1, output 2 goes to 2, output 1 goes to 3, output 2 goes to 4 et cetera, would this be going about it the wrong way? Is simply one output for the master track/bus and connecting it to all of the different playbacks the way? Thanks again for wonderful help:)

---

### Post by sgx on 2012-03-15
ardour is using ambisonics for surround, article and software links  below
[http://ardour.org/node/2804](http://ardour.org/node/2804)
[http://packages.debian.org/unstable/sound/](http://packages.debian.org/unstable/sound/)

You can install ardour3 beta3 manually. It wont' mess with
other versions that are installed.  [http://ardour.org/node](http://ardour.org/node)

In the meantime,  aplay -l  
and aconnect -o may show some outputs you can use
with ardour panning options.

Keeping a long or steady sound while using various
qjackctl options will be lucky.

alsamixergui can be installed, if its not yet there,
or use envy24control, to make sure any extra channels
are unmuted and loud enough.
The ardour forum may have better info.
Cheers

---

