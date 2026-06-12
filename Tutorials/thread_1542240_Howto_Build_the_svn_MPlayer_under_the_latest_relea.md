---
title: "Howto: Build the svn MPlayer under the latest release version of Ubuntu"
date: 2010-07-30
forum: Tutorials
---

### Post by andrew.46 on 2010-07-30
April 29th 2012

Due to the upcoming changes to this guide's old home on these Forums I have, with much regret, moved this guide to my own personal website:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://www.andrews-corner.org/mplayer.html](http://www.andrews-corner.org/mplayer.html)

where I have just now released an updated version for Ubuntu 12.04, Precise Pangolin.

I attach a complete copy of the older guide as *mplayer_guide.gz* in case anybody wishes to make a wiki, blog, web page etc of this guide as it was for Oneiric Ocelot.

Andrew

---

### Post by mc4man on 2010-07-31
> the svn MPlayer requires Version 190.32 (or later) of the NVidia drivers to enable vdpau output. You will need to have these drivers and appropriate vdpau libraries
If your card supports then just install libvdpau-dev to enable vdpau . If unsure go ahead and build with vdpau support and try - no harm done if not supported.
YMMV depending on source material and video adapter, you don't have to use it.

---

### Post by andrew.46 on 2010-07-31
Hi mc4man,

> **mc4man said:**
> If your card supports then just install libvdpau-dev to enable vdpau . If unsure go ahead and build with vdpau support and try - no harm done if not supported.

Thanks for the clarification, I am currently compiling against libvdpau-dev on a system without an appropriate card and if there are no error messages in general usage (that is without using -*vo vdpau -vc ....*) I may very well just add this into the dependencies for the moment. Now to look for a way around the forum's annoying habit of censoring subtitle ./configure options dealing with libass, or more particularly for the options such as '--disable-a s s -internal'...

Any thoughts on the 'single command' approach? From a purist point of view I am not keen on it and there are some dangers with broken commands, but from a point of view of an Ubuntu user not particularly familiar with compiling I think it provides a way into the often arcane world of building from source.

Andrew

---

### Post by Linuxforall on 2010-07-31
Bravo, have been compiling mplayer via your older thread and with additions by mac4man, this one makes it more covenient, thank you andrew.

---

### Post by mc4man on 2010-07-31
> Any thoughts on the 'single command' approach?overall seems ok - I'd break myself after the mplayer config to allow review if desired

> Now to look for a way around the forum's annoying habit of censoring...--disable-*ss-internal

Remember some posts about - no recollection of any way around when in a command ( possibly a mod can edit after the fact? - though seems pretty automatic

---

### Post by andrew.46 on 2010-07-31
Hi Linuxforall,

> **Linuxforall said:**
> Bravo, have been compiling mplayer via your older thread and with additions by mac4man, this one makes it more covenient, thank you andrew.

Still a few small changes to make but the guide itself looks fairly robust and certainly produces a very usable MPlayer on my own system. I considered adding blueray material but I might wait until support for *encrypted* disks is added. Glad the guide has been useful for you :).

All the best,

Andrew

---

### Post by mc4man on 2010-07-31
edit - never mind - A bit confused here - the option is ( --[COLOR="Blue"]enable[/COLOR]-*ss-internal  -(autodetect)
That's as seen in ./configure --help, the configure script shows both options, the autodetect is ?

---

### Post by typos1 on 2010-08-02
Oops, I think I compiled it twice...will that matter?

---

### Post by andrew.46 on 2010-08-02
Hi typos,

> **typos1 said:**
> Oops, I think I compiled it twice...will that matter?

I suspect not :). Remember though that wma lossless still depends on external codecs and this particular codec is not available to 64 bit installations, so playback is problematic on such systems until such time as a native decoder arrives. Under a 32 bit system it is handled as follows:

```

andrew@skamandros~/samples$ mplayer luckynight.wma 
MPlayer SVN-r31847-4.4.4 (C) 2000-2010 MPlayer Team

Playing luckynight.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 title: Lucky Night
 author: Jody Marie Gnant
 copyright: 1995 Sirius Publishing
 comments: 1-minute song sample demonstrating Windows Media lossless audio compression
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
AUDIO: 44100 Hz, 2 ch, s16le, 868.7 kbit/61.55% (ratio: 108583->176400)
**[COLOR="Red"]Selected audio codec: [wma9dmo] afm: dmo (Windows Media Audio 9 DMO)[/COLOR]**
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  63.1 (01:03.0) of 60.5 (01:00.4)  4.3% 


Exiting... (End of file)

```

This sample file [here]("http://samples.mplayerhq.hu/A-codecs/lossless/luckynight.wma"). But you should have no trouble with Real Audio / Real Media and SMPlayer makes it all easy :).

Andrew

---

### Post by typos1 on 2010-08-02
It wont play .ra s-I ve tried updating it-its doing it now...

(I thought you could run 32bit apps on 64bit systems-I did for a while to get iplayer and flash movies working when there was no 64 bit support

Edit-updated and still wont play .ra s

Smplayer wont play the audio opn WM9 videos either-this is something else other people apparently can get ubuntu to do but I ve never been able to get anything to.

---

### Post by ron999 on 2010-08-02
Posted in error.

---

### Post by FakeOutdoorsman on 2010-08-02
A rolling release guide.  That's a good idea.  This is a nice find after being in a small internet-less town for five days.

**Update:** Also...how unfortunate and annoying that the forum censorship is interfering with a legitimate word.

---

### Post by andrew.46 on 2010-08-02
Hi typos,

> **typos1 said:**
> It wont play .ra s-I ve tried updating it-its doing it now...

Now that is odd. Could you try running one of your problem files as follows:

```
mplayer -v *problem_file.ra*
```

and post the terminal output here? I suspect there may be a problem with your sound + MPlayer rather than a problem with MPlayer alone.

> (I thought you could run 32bit apps on 64bit systems-I did for a while to get iplayer and flash movies working when there was no 64 bit support

Apparently this can be done with the svn MPlayer and mc4man has done it I believe, it goes a little beyond the scope of this guide although I am sure mc4man would not mind commenting here? Different compiler flags for starters and a few other differences.

Andrew

---

### Post by typos1 on 2010-08-02
Ok, coded what you said-here is the result:

Using nanosleep() timing
get_path('input.conf') -> '/home/jason/.mplayer/input.conf'
Can't open input config file /home/jason/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
get_path('03.conf') -> '/home/jason/.mplayer/03.conf'

Playing 03.
get_path('sub/') -> '/home/jason/.mplayer/sub/'
File not found: '03'
Failed to open 03.

get_path('-.conf') -> '/home/jason/.mplayer/-.conf'

Playing -.
get_path('sub/') -> '/home/jason/.mplayer/sub/'
Reading from stdin...
[file] File size is -1 bytes
STREAM: [file] -
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)

---

### Post by ron999 on 2010-08-02
> **typos1 said:**
> Ok, coded what you said-here is the result:

Using nanosleep() timing
get_path('input.conf') -> '/home/jason/.mplayer/input.conf'
Can't open input config file /home/jason/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
get_path('03.conf') -> '/home/jason/.mplayer/03.conf'

Playing 03.
get_path('sub/') -> '/home/jason/.mplayer/sub/'
File not found: '03'
Failed to open 03.

get_path('-.conf') -> '/home/jason/.mplayer/-.conf'

Playing -.
get_path('sub/') -> '/home/jason/.mplayer/sub/'
Reading from stdin...
[file] File size is -1 bytes
STREAM: [file] -
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)

What's this supposed to be?
Show the command that you used.

---

### Post by mc4man on 2010-08-02
here was the way I built 32bit on amd_64 - not a walkthru, more just the commands used on livecd.
[http://ubuntuforums.org/showthread.php?p=9338517](http://ubuntuforums.org/showthread.php?p=9338517)

@typos1
did you review comment after mine in your other thread - concerning sound devices?

Andrew - you don't happen to know of a sample file that would 'indicate' if mplayer is using the internal supplied libass vs. an externally installed libass4? I swear it seems mplayer uses the supplied libraries no matter what the config. (with exception of a ldflags in config

(unless I'm misunderstanding the meaning of 'internal' which is clearly possible

---

### Post by andrew.46 on 2010-08-03
Hi mc4man,

> **mc4man said:**
> Andrew - you don't happen to know of a sample file that would 'indicate' if mplayer is using the internal supplied libass vs. an externally installed libass4? I swear it seems mplayer uses the supplied libraries no matter what the config.

It looks like MPlayer has shifted the goalposts at some stage and the release version of libass is no longer enough. I rebuilt with the git version on my Slackware partition and that has succeeded:

```

andrew@skamandros~/Desktop/mplayer$ ./configure \
>   --prefix=/usr \
>   --mandir=/usr/man \
>   --confdir=/etc/mplayer \
>   --codecsdir=/usr/lib/codecs \
>   **[COLOR="Red"]--disable-***-internal[/COLOR]** \
>   --disable-libmpeg2-internal
[.........]
Checking for bitmap font support ... yes 
Checking for freetype >= 2.0.9 ... yes 
Checking for fontconfig ... yes 
**[COLOR="Red"]Checking for SSA/*** support ... yes (external)[/COLOR]**
Checking for fribidi with charsets ... yes 
Checking for ENCA ... yes 
Checking for zlib ... yes 
[....]

```

This reveals:

```

root@skamandros/home/andrew/source/mplayer# ldd /usr/bin/mplayer | grep libass
	libass.so.4 => /usr/lib/libass.so.4 (0xb6f00000)

```

So I shall ask the Forum moderators to see what they can do with the libass configure option and think about incorporating this into the guide. For those keen to get a head start the libass git repository can be accessed with:

git clone --depth=1 git://repo.or.cz/libass.git

and run ./autogen.sh to start things rolling...


Andrew

---

### Post by andrew.46 on 2010-08-03
Hi typos1,

Your terminal output was cut short a little at both ends :). Below is a typical terminal output from MPlayer and a realmedia file, I have highlighted some of the points that mau be problematical on your own file:

```

**[COLOR="Red"]andrew@skamandros~/Desktop$ mplayer -v test.rm [/COLOR]**
MPlayer SVN-r31907-4.4.4 (C) 2000-2010 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 10
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
extended cpuid-level: 8
extended cache-info: 134242368
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2 SSSE3 CMOV
get_path('codecs.conf') -> '/home/andrew/.mplayer/codecs.conf'
Reading /home/andrew/.mplayer/codecs.conf: Can't open '/home/andrew/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --mandir=/usr/man --confdir=/etc/mplayer --codecsdir=/usr/lib/codecs --disable-***-internal --disable-libmpeg2-internal
CommandLine: '-v' 'test.rm'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/andrew/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/andrew/.mplayer/input.conf'
Can't open input config file /home/andrew/.mplayer/input.conf: No such file or directory
Can't open input config file /etc/mplayer/input.conf: No such file or directory
Falling back on default (hardcoded) input config
get_path('test.rm.conf') -> '/home/andrew/.mplayer/test.rm.conf'

Playing test.rm.
get_path('sub/') -> '/home/andrew/.mplayer/sub/'
[file] File size is 292646 bytes
STREAM: [file] test.rm
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: RealMedia format
Checking for YUV4MPEG2
ASF_check: not ASF guid!
[B][COLOR="Red"]Checking for REAL
REAL file format detected.[/COLOR][/B]
real: Header size: 18
real: Header object version: 0
real: File version: 0
Chunk: PROP (504f5250) (size: 0x32, offset: 0x12)
First index chunk offset: 0x0
First data chunk offset: 0x153
Flags (9): [save allowed] 
Chunk: CONT (544e4f43) (size: 0x59, offset: 0x44)
Chunk: MDPR (5250444d) (size: 0xac, offset: 0x9d)
Found new stream (id: 0)
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
==> Found audio stream: 0
[real] Audio stream found, -aid 0
Found audio stream!
version: 5
header size: 78
coded_frame_size: 1400
sub_packet_h: 16
frame_size: 1400
sub_packet_size: 280
samplerate: 44100, channels: 2
audio fourcc: cook (6b6f6f63)
======= WAVE Format =======
Format Tag: 28515 (0x6F63)
Channels: 2
Samplerate: 44100
avg byte/sec: 12058
Block align: 280
bits/sample: 16
cbSize: 16
Unknown extra header dump: [1] [0] [0] [3] [8] [0] [0] [25] [0] [0] [0] [0] [0] [8] [0] [5] 
==========================================================================
### skipping 0 bytes of codec info
Chunk: DATA (41544144) (size: 0x0, offset: 0x149)
Packets in file: 0
Auto-selected RM audio ID = 0
AUDIO:  cook [6B6F6F63]
Clip info:
 title: "ABC Classic FM 1"
 author: "ABC Radio"
 copyright: "Australian Broadcasting Corporation 2005"
get_path('sub/') -> '/home/andrew/.mplayer/sub/'
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
dec_audio: Allocating 192000 + 65536 = 257536 bytes for output buffer.
FFmpeg's libavcodec audio codec
INFO: libavcodec "cook" init OK!
AUDIO: 44100 Hz, 2 ch, s16le, 96.5 kbit/6.84% (ratio: 12058->176400)
**[COLOR="Red"]Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio)[/COLOR]**
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
Trying every known audio driver...
ao2: 44100 Hz  2 chans  s16le
audio_setup: using '/dev/dsp' dsp device
audio_setup: using '/dev/mixer' mixer device
audio_setup: using 'pcm' mixer device
audio_setup: sample format: s16le (requested: s16le)
audio_setup: using 2 channels (requested: 2)
audio_setup: using 44100 Hz samplerate (requested: 44100)
audio_setup: frags:  16/16  (4096 bytes/frag)  free:  65536
**[COLOR="Red"]AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)[/COLOR]**
AO: Description: OSS/ioctl audio output
AO: Author: A'rpi
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
Video: no video
Freeing 0 unused video chunks.
Starting playback...
Increasing filtered audio buffer size from 0 to 65536
A:976482.8 (271:14:42.8) of 24.3 (24.2)  1.1% 
ds_fill_buffer: EOF reached (stream: audio)  
A:976482.8 (271:14:42.8) of 24.3 (24.2)  1.1% 
ds_fill_buffer: EOF reached (stream: audio)  
A:976482.9 (271:14:42.8) of 24.3 (24.2)  1.1% 
EOF code: 1  

Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: ffmpeg
vo: x11 uninit called but X11 not initialized..

Exiting... (End of file)

```

All the best,

Andrew

---

### Post by mc4man on 2010-08-03
> It looks like MPlayer has shifted the goalposts at some stage and the release version of libass is no longer enough
That's what it was, mplayer auto. switched back to internal with the release version avail. in lucid.
It appears if using external libass it must be shared/static,  - just to note most will also have a shared libass in /usr (dependency of gstreamer bad plugin.

---

### Post by typos1 on 2010-08-03
Sorry, I cut the top off the terminal, but not the bottom:

jason@jason-desktop:~$ mplayer -v 01 - Track 1.ra

MPlayer SVN-r31895-4.4.3 (C) 2000-2010 MPlayer Team
CPU vendor name: AuthenticAMD  max cpuid level: 1
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 75, Stepping: 2)
extended cpuid-level: 24
extended cache-info: 33587520
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNowExt: 1 SSE: 1 SSE2: 1 SSSE3: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowExt SSE SSE2 CMOV
get_path('codecs.conf') -> '/home/jason/.mplayer/codecs.conf'
Reading /home/jason/.mplayer/codecs.conf: Can't open '/home/jason/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --confdir=/etc/mplayer --disable-mencoder --disable-x264
CommandLine: '-v' '01' '-' 'Track' '1.ra'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/jason/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/jason/.mplayer/input.conf'
Can't open input config file /home/jason/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
get_path('01.conf') -> '/home/jason/.mplayer/01.conf'

Playing 01.
get_path('sub/') -> '/home/jason/.mplayer/sub/'
File not found: '01'
Failed to open 01.

get_path('-.conf') -> '/home/jason/.mplayer/-.conf'

Playing -.
get_path('sub/') -> '/home/jason/.mplayer/sub/'
Reading from stdin...
[file] File size is -1 bytes
STREAM: [file] -
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)

It seems (I m no expert tho) that it doesnt know where the file is, should there be something in the command to tell it?

---

### Post by andrew.46 on 2010-08-03
Hi typos,

> **typos1 said:**
> Sorry, I cut the top off the terminal, but not the bottom:
```

jason@jason-desktop:~$ mplayer -v 01 - Track 1.ra
```

[...]

It seems (I m no expert tho) that it doesnt know where the file is, should there be something in the command to tell it?

Indeed, you have to give the correct path to the file and also escape the spaces in the filename. If the file is on your Desktop try:

```
 
cd $HOME/Desktop
mplayer -v **[COLOR="Red"]'[/COLOR]**01 - Track 1.ra**[COLOR="Red"]'[/COLOR]**

```

Andrew

---

### Post by andrew.46 on 2010-08-03
Hi mc4man,

> **mc4man said:**
> It appears if using external libass it must be shared/static,  - just to note most will also have a shared libass in /usr (dependency of gstreamer bad plugin.

Hmmmm..... I try to avoid messing with the web of dependencies, something always seems to break :(. I may very well continue with the external libass on my Slackware box for personal experimentation and keep to the internal libass for this guide at the moment. The MPlayer mailing list suggests that some time soon MPlayer will switch to the external library, hopefully as an *svn external* as there will be no dependency issues with Ubuntu.

Andrew

---

### Post by mc4man on 2010-08-04
A few add. on libass - 
the configure option isn't needed here, definitely will fall under auto and go with external if version requirement is met.

As to whether a good idea to add or replace libass - can't say really, don't have a file to test with the rather short list of gstreamer players that would use libass

Using checkinstall (vs. a debian package(s) build

Because the ubuntu package is libass4, there is no package conflict if installed as libass to /usr/local. There would be 2 libass.so.4.0.0, the /usr/local taking preference.

Or if packaged as libass4 (version 0.9.9-1), then it would replace the current libass4 (and also provide the headers ala libass-dev, which couldn't be installed, - a good thing actually) and at the very least satisfy the bad plugin dep.

Either way not a big risk - though would be good to test.

---

### Post by gillza on 2010-08-05
Andrew, 

I compiled the mplayer using this guide (fresh ubuntu) and just noticed that after pausing a video and resuming it stutters for a second or two and only then resumes a normal playback. 

I have audio output driver setup to pulseaudio and video setup to xv. I have ATI x1400 video card with 128 dedicated and 128 shared memory, 2ghz cpu, 2gb ram. It is definitely not resource issue as mplayer used to work fine in previous installations (even in 10.04). Any ideas?

Thank you.

---

### Post by andrew.46 on 2010-08-05
Hi gillza,

> **gillza said:**
> I compiled the mplayer using this guide (fresh ubuntu) and just noticed that after pausing a video and resuming it stutters for a second or two and only then resumes a normal playback. 

I have audio output driver setup to pulseaudio and video setup to xv.

I have just recompiled and unfortunately I cannot duplicate this on my own setup. Could you experiment a little with the sound settings an see if *mplayer -ao alsa filename* or *mplayer -ao oss filename* make any difference? (Where of course you substitute the actual name of your file for *filename*.)

BTW did you find the guide easy to work through or any areas confusing? I am trying a slightly different approach with this iteration of the guide and I am keen to adjust any difficult areas.

Andrew

---

### Post by gillza on 2010-08-06
> **andrew.46 said:**
> Hi gillza,



I have just recompiled and unfortunately I cannot duplicate this on my own setup. Could you experiment a little with the sound settings an see if *mplayer -ao alsa filename* or *mplayer -ao oss filename* make any difference? (Where of course you substitute the actual name of your file for *filename*.)

BTW did you find the guide easy to work through or any areas confusing? I am trying a slightly different approach with this iteration of the guide and I am keen to adjust any difficult areas.

Andrew

Andrew

The guide is super easy (too easy for my taste hehe ) it is all copy paste basically. I have been following your guides for a while now and pretty much know what is going on during each step. The most helpful part of it is the installation of all the dev files. I myself would like to know how you compile this list :) ? 

Regarding the issue: Um.. it is rather strange but now I can't replicate the problem myself. I guess I should have waited longer before jumping to conclusions. All I did was change between xv and xv (0 Radeon textured video) back and forth and now it all works just fine with either of the settings selected..

Thank you for the guide!

---

### Post by andrew.46 on 2010-08-06
Hi gillza,

> **gillza said:**
> The guide is super easy (too easy for my taste hehe ) it is all copy paste basically. I have been following your guides for a while now and pretty much know what is going on during each step. The most helpful part of it is the installation of all the dev files. I myself would like to know how you compile this list :) ? 

I have deliberately made the guide a little easier for those who are new to building software such as MPlayer in the hope that the guide will be more accessible to the average Ubuntu user. Whether or not this proves to the correct course time will tell I guess.

As for the -dev files, there are several techniques used to get this list. I have always started with the build-depends for the typical Ubuntu package. This can now be seen in the MPlayer source code in the newly refurbished debian/control. These need to be screened a little as they are not all relevant to an svn package. Next is the slightly painful process of running ./configure and seeing what is found and not found automagically by MPlayer and then simply adding the required files until MPlayer is happy.

After this some detective work is required and close attention to the MPlayer mailing lists. A classic example of this is the saga of amr playback. This started as closed source / patent encumbered software from an external source that had to be compiled separately. When libopencore-amr first came into being this also had to be compiled from an external source until a little later Medibuntu hosted the files. Finally we have the -dev files conveniently hosted by the Ubuntu repository. Each of these changes had to be catered for in these guides. The leapfrogging of x264 versions and dependency clashes was even worse until I stopped building MEncoder and that particular pain was gone :).

> Regarding the issue: Um.. it is rather strange but now I can't replicate the problem myself. I guess I should have waited longer before jumping to conclusions. All I did was change between xv and xv (0 Radeon textured video) back and forth and now it all works just fine with either of the settings selected..

In that case I take full credit for solving your problem :).

Andrew

---

### Post by mad_max0204 on 2010-08-08
Why is x264 disabled in configure ?
When I play 1080p video I get alot of bugging which I dont get with xbmc.
VDPAU is used in both cases.
Anyone knows what could be the issue ?
When I dont disable x264 I cannot make without errors.

---

### Post by Linuxforall on 2010-08-08
Its usually preferred to compile the latest x264 and use that rather than use the older one in mplayer.

---

### Post by andrew.46 on 2010-08-09
Hi mad_max,

> **mad_max0204 said:**
> Why is x264 disabled in configure ?
When I play 1080p video I get alot of bugging which I dont get with xbmc.

x264 is disabled in the ./configure string as this guide does not build MEncoder, and x264 is not required for h264 playback by MPlayer. It is a small matter though to build x264 and then build MPlayer *as well as *MEncoder..

Andrew

---

### Post by andrew.46 on 2010-08-09
Hi mc4man,

> **mc4man said:**
> As to whether a good idea to add or replace libass - can't say really, don't have a file to test with the rather short list of gstreamer players that would use libass

Looks like the internal libass has pretty much caught up anyway:

```

andrew@skamandros~$ svn log -r r31932 svn://svn.mplayerhq.hu/mplayer/trunk
------------------------------------------------------------------------
r31932 | greg | 2010-08-07 07:13:41 +1000 (Sat, 07 Aug 2010) | 1 line

Import libass 0.9.10
------------------------------------------------------------------------

```

Andrew

---

### Post by Linuxforall on 2010-08-19
I just wanted to add to this already excellent guide. Mencoder is the backbone of many great Linux video utilities. Removing it or not including it means many apps like Acidrip, K9, DeVeDe and more won't work. There is a simple solution to this. Compile x264 following FakeOutdoorsman's excellent guide here at [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Then follow andrew46's instructions to a T, when it comes to configure and install, its there you need to make the necessary changes.

in ./configure, remove the disable x264 and disable mencoder lines

It should look like 

```
./configure --confdir=/etc/mplayer 
```

then do a make, if you have dual core or more add the -jx command with x representing the number of cores. This speeds up the compile.

After that the install code has to be 

```
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
   --pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`" --provides "mplayer,mencoder"
```

mplayer picks up the static ffmpeg and x264 build when its pre-installed and lets mencoder use them.

After this your mencoder will be latest along with mplayer and use latest x264 and ffmpeg. I have tested this on Acidrip, DeVeDe and K9, using latest x264 speeds up conversion greatly as its optimized for your CPU unlike the older one in the repos. Even WinFF works fine once you edit out the 'b' in 'kB' from the presets.

Make sure to lock ffmpeg, x264 and mplayer in synaptic.

andrew, feel free to edit or remove this post if you don't find it pertinent to this thread and thank you again for your excellent guide.

---

### Post by ron999 on 2010-08-20
> **Linuxforall said:**
> 

Make sure to lock ffmpeg, x264 and mplayer in synaptic.


What does this mean?

---

### Post by Linuxforall on 2010-08-20
> **ron999 said:**
> What does this mean?

In synaptic, highlight these packages and then select lock in properties.

---

### Post by ron999 on 2010-08-20
> **Linuxforall said:**
> In synaptic, highlight these packages and then select lock in properties.

I don't see an option to lock in Properties.
Just:-
Common
Dependencies
Installed Files
Versions
Description

---

### Post by mc4man on 2010-08-20
> In synaptic, highlight these packages and then select lock in properties.
There should be no need to do this - mplayer, x264, ect. builds from these guides should be versioned higher than any ubuntu versions.

(the option is seen when highlighting a package - then click on the package tab in synaptic

---

### Post by ron999 on 2010-08-20
> **mc4man said:**
> 
(the option is seen when highlighting a package - then click on the package tab in synaptic

Yes, in 'Package' it shows 'Lock Version'.

---

### Post by andrew.46 on 2010-08-20
Hi Linuxforall,

Thanks for adding in the MEncoder details :). I will admit my enthusiasm for MEncoder died a while back when FakeOutdoorsman's guide introduced me to FFmpeg. It died a little further when I realised that there is little active development of MEncoder and that the program is really only aimed at using the avi container, I realise other containers are possible but not well supported. Having said that I acknowledge that many fine programs use MEncoder as their backend, as you have mentioned.

You might consider adding to your post the vital -dev files for faac and lame which enable transcoding to aac and mp3 respectively. MEncoder can of course be tested for transcoding options as follows:

```

andrew@skamandros~$**[COLOR="Red"] mencoder -ovc help[/COLOR]**
MEncoder SVN-r31983-4.4.4 (C) 2000-2010 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   x264     - H.264 encoding

andrew@skamandros~$ **[COLOR="Red"]mencoder -oac help[/COLOR]**
MEncoder SVN-r31983-4.4.4 (C) 2000-2010 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding (useful for AC3)
   pcm      - uncompressed PCM audio
   mp3lame  - cbr/abr/vbr MP3 using libmp3lame
   lavc     - FFmpeg audio encoder (MP2, AC3, ...)
   faac     - FAAC AAC audio encoder

```

Thanks for your very helpful post!

Andrew

---

### Post by Linuxforall on 2010-08-20
Thanks andrew, can you tell me which other dev files to add specifically.

---

### Post by Linuxforall on 2010-08-20
> **mc4man said:**
> There should be no need to do this - mplayer, x264, ect. builds from these guides should be versioned higher than any ubuntu versions.

(the option is seen when highlighting a package - then click on the package tab in synaptic

The reason to take this safeguard is when you add ppas from other sources, the vlc c.korn ppa has newer ffmpeg which it might try and update, same goes for other ppas.

---

### Post by andrew.46 on 2010-08-20
Hi Linuxforall,

> **Linuxforall said:**
> Thanks andrew, can you tell me which other dev files to add specifically.

These would be libfaac-dev and libmp3lame-dev. I suspect these plus x264 should be enough for a decent MEncoder build but I will admit that I build MEncoder on my *other* distro, where there are no '-dev' files, rather than on Lucid...

All the best,

Andrew

---

### Post by Linuxforall on 2010-08-20
> **andrew.46 said:**
> Hi Linuxforall,



These would be libfaac-dev and libmp3lame-dev. I suspect these plus x264 should be enough for a decent MEncoder build but I will admit that I build MEncoder on my *other* distro, where there are no '-dev' files, rather than on Lucid...

All the best,

Andrew

Andrew,


The first thing I do is install x264 and ffmpeg and part of the requirement is these two dev files that you mention so when I compile mplayer, they are already there.

Are you still using Gentoo btw?

---

### Post by andrew.46 on 2010-08-20
Hi Linuxorall,

> **Linuxforall said:**
> The first thing I do is install x264 and ffmpeg and part of the requirement is these two dev files that you mention so when I compile mplayer, they are already there.

Hence the need when writing guides to start with a 'clean' system :). This becomes a lot easier when using VMs as you can install a complete base system and then save that state.

> Are you still using Gentoo btw?

No, I settled on Slackware as my host desktop a while back with multiple VMs runnng through Virtualbox OSE. I attach a screenshot showing my Lucid VM running, it is not a perfect setup on this little laptop but I am almosd used to the size of the screen now...

Andrew

---

### Post by Linuxforall on 2010-08-20
I will be trying out SLAX soon, hope I can compile x265, ffmpeg and mplayer as easily as I do it on Ubuntu with your instructions.

Rule of thumb for anyone planning to use latest mencoder should be to follow FakeOutdoorsman's guide for compiling latest x264, ffmpeg and libvpx, then follow andrew's guide with my recommendations, all the static libraries are picked up by mencoder. This is why I like K9, it allows me to use mencoder or ffmpeg.

---

### Post by andrew.46 on 2010-08-21
Hi Linuxforall,

> **Linuxforall said:**
> I will be trying out SLAX soon, hope I can compile x265, ffmpeg and mplayer as easily as I do it on Ubuntu with your instructions.

Would you consider ignoring the forks and going straight for Slackware itself? It is a superb compiling environment with absolutely nothing getting in your way...

Andrew

---

### Post by Linuxforall on 2010-08-21
> **andrew.46 said:**
> Hi Linuxforall,



Would you consider ignoring the forks and going straight for Slackware itself? It is a superb compiling environment with absolutely nothing getting in your way...

Andrew

I surely would, was just being lazy but considering I would be building the codecs and mplayer, might as well go for the whole shabang, I still find Slackware to be friendlier than Gentoo. Thanks for the advice Andrew, btw, is there any repository that you would specifically recommend for Slackware?

---

### Post by andrew.46 on 2010-08-21
Hi Linuxforall,

> **Linuxforall said:**
> btw, is there any repository that you would specifically recommend for Slackware?

Slackware does not really have a repository system as such, but the biggest source of quality installation scripts is [slackbuilds.org]("http://slackbuilds.org/"). Some of my work is there if you ever head that way:

[http://slackbuilds.org/repository/13.1/multimedia/mkvtoolnix/](http://slackbuilds.org/repository/13.1/multimedia/mkvtoolnix/)
[http://slackbuilds.org/repository/13.1/libraries/libebml/](http://slackbuilds.org/repository/13.1/libraries/libebml/)
[http://slackbuilds.org/repository/13.1/libraries/libmatroska/](http://slackbuilds.org/repository/13.1/libraries/libmatroska/)
[http://slackbuilds.org/repository/13.1/network/leafnode/](http://slackbuilds.org/repository/13.1/network/leafnode/)

For FFmpeg, MPlayer and vlc-git I use my own slackbuild scripts as for the most part slackware does not follow the bleeding edge...

Andrew

---

### Post by Linuxforall on 2010-08-21
> **andrew.46 said:**
> Hi Linuxforall,



Slackware does not really have a repository system as such, but the biggest source of quality installation scripts is [slackbuilds.org]("http://slackbuilds.org/"). Some of my work is there if you ever head that way:

[http://slackbuilds.org/repository/13.1/multimedia/mkvtoolnix/](http://slackbuilds.org/repository/13.1/multimedia/mkvtoolnix/)
[http://slackbuilds.org/repository/13.1/libraries/libebml/](http://slackbuilds.org/repository/13.1/libraries/libebml/)
[http://slackbuilds.org/repository/13.1/libraries/libmatroska/](http://slackbuilds.org/repository/13.1/libraries/libmatroska/)
[http://slackbuilds.org/repository/13.1/network/leafnode/](http://slackbuilds.org/repository/13.1/network/leafnode/)

For FFmpeg, MPlayer and vlc-git I use my own slackbuild scripts as for the most part slackware does not follow the bleeding edge...

Andrew

Thanks a lot Andrew, maybe I will bother you for the script once I am done installing Slackware if its not too much trouble.

---

### Post by andrew.46 on 2010-08-21
Hi Linuxforall,

> **Linuxforall said:**
> Thanks a lot Andrew, maybe I will bother you for the script once I am done installing Slackware if its not too much trouble.

It would be my pleasure, mind you I would have to make them a little tidier, being for my own consumption they are formatted a little roughly :).

Andrew

---

### Post by Linuxforall on 2010-08-21
> **andrew.46 said:**
> Hi Linuxforall,



It would be my pleasure, mind you I would have to make them a little tidier, being for my own consumption they are formatted a little roughly :).

Andrew

Well at least it will give me an idea where to start with, many thanks again.

---

### Post by ftcbr on 2010-08-25
Hello Linux Folks,

I got this...


Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages

 404  Not Found

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

W: Failed to fetch [http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead. 


What is the consequence?

Needless to say, I am a newbie.

Thanks

---

### Post by andrew.46 on 2010-08-25
Hi ftcbr,

One of the errors is telling you that the Korn PPA is missing in action, presumably you picked up vlc from there? The other error is telling you that the Medibuntu repository seems to be having some stormy weather :). Hopefully Medibuntu will sort itself out soon...

Andrew

---

### Post by Hero of Time on 2010-08-26
Any idea about DVD playback with Mplayer? It's been experimental to say at best with the repo versions. What about the SVN one? I like to have a system that is as slim as possible, so installing Totem would give me half of Gnome that I don't use on Xfce4. VLC is a last resort, but it's not perfect either. I rather stick to Mplayer, even though it hasn't been the best one to play DVDs on either disc or hard drive.

And, comparing this compile to the one in RVM's PPA that needs a bundle of additional packages, does this one require the same, or is it just like the Ubuntu build itself build into the package?

I have to compile Mplayer from source because there is no PPA available with recent builds and one of the anime fansub groups decided to use mkv header compression which is only supported by the latest Mplayer builds.

Great howto either way. Just sucks I run a 64 bit system, don't want to hog it with build packages and can't run 64 bit VMs XD. Guess I have to sacrifice my 64 bit laptop for the compilation :P.

---

### Post by Linuxforall on 2010-08-26
Brandon Snider's cutting edge multimedia ppa has fairly latest mplayer.

DVDs play fine with the compiled mplayer, must make sure that you have libdvdcss installed.

---

### Post by andrew.46 on 2010-08-26
Hi Hero,

> **Hero of Time said:**
> Any idea about DVD playback with Mplayer? It's been experimental to say at best with the repo versions. What about the SVN one?

I have had little trouble with DVD playback with the svn MPlayer but I will admit to seeing some odd effects from time to time with DVD menus :).

> And, comparing this compile to the one in RVM's PPA that needs a bundle of additional packages, does this one require the same, or is it just like the Ubuntu build itself build into the package?

I have not used RVM's MPlayer package or even the Ubuntu repository version I have to admit! I suspect the packages required will be pretty equal amongst all of these versions though.

All the best,

Andrew

---

### Post by andrew.46 on 2010-08-27
I have neglected this guide a little while thrashing away with a vlc guide but I finally have a little time. I have added in compilation of rtmpdump which allows playback of rtmp (Real Time Messaging Protocol) streams. Not all that common but here are a couple of streams to test:

rtmp://video-12.radioradicale.it/store-51/mp4:FL532501.f4v
rtmp://fsapfs.fplive.net/fsap/Videos/foie_gras_uk_high.flv 
rtmp://directv.fcod.llnwd.net/a517/d1/com/lp/testdrive/active_channel-hack.flv 

Compilation will not be required under maverick as rtmpdump will be in the Ubuntu repository.

Andrew

---

### Post by Hero of Time on 2010-08-27
> **andrew.46 said:**
> Hi Hero,
I have had little trouble with DVD playback with the svn MPlayer but I will admit to seeing some odd effects from time to time with DVD menus :).

I have not used RVM's MPlayer package or even the Ubuntu repository version I have to admit! I suspect the packages required will be pretty equal amongst all of these versions though.

All the best,

Andrew
Yes, DVD playback can have a few odd effects, but I was more worried about the actual workings of the menus, especially selecting the audio and subtitle tracks. It didn't always work for me.

As for the package dependencies, I know that the versions between the Ubuntu repo and RVM's PPA differ a year (20090426 vs 20100416), but there is quite a difference in it. RVM needs 62 packages, Ubuntu needs just 48. I haven't noticed any difference in playback capabilities so far. Only that the actual reason I need(ed) to compile the latest Mplayer, fansub using MKV header compression, is no longer an issue. Only have the 'problem' with the font of the subs, it's default instead of their styled one.


@Linuxforall:
I'm gonna check out his PPA. It sounds interesting. Might keep me from compiling Mplayer myself and keep it up to date. If he actually had packages in it XD.

---

### Post by Linuxforall on 2010-08-27
Having used RVM's packages in the past, I can tell you that there was nothing extra drawn in expect for nvidia-vdpau driver.

---

### Post by andrew.46 on 2010-08-27
Another addition: finally remembered to document the removal of totem-mozilla and installation of the gecko-mediaplayer....

Andrew

---

### Post by Hero of Time on 2010-08-28
Andrew, do you know what happens when you run two commands as one with &&? You might want to change the howto to use ; instead, as with &&, the next command will be used no matter if the previous one finished or exited normally. With ;, the second command only gets executed when the first one is done. But then again, maybe it's needed to continue anyway.

Just something I thought about when following the guide.

Oh, just one last thing: the package you get from checkinstall, does it note all the dependencies it might need afterwards in case you build it on one system and install it on another? You don't want to end up with a broken dependency or feature.

---

### Post by mc4man on 2010-08-28
> the package you get from checkinstall, does it note all the dependencies it might need afterwards in case you build it on one system and install it on another

No - if you wished that you'd need to use the --requires option in checkinstall.
While possible, it could be a little time consuming initially, though you could possibly shorten if when possible only requiring a 'base' package.

In other words if package a,b and c were depends but package c depended on a and b then possibly you'd only need to require package c.
(I believe gdebi would handle this properly, can't test on maverick because gdebi is broken
Another way to limit depends would be to statically link where possible - again probably not worth the effort 

Also you'd want to enable 'runtime cpu detection' unless building for same cpu.

If installing to another ubuntu release you may also run into library version issues - overall better to build on machine being used.

---

### Post by Hero of Time on 2010-08-28
I already found out that checkinstall doesn't list the dependencies. Had issues with that in the past when I made packages from source before with that.
Since I have a minimal installation, this compile guide broke Mplayer for me with all the new dependencies it is compiled against. First it was libopenjpeg, removed that one from the compile machine, now it's libmpg123. This is why adding a dependency list in the package is important.

I build Mplayer on the same OS, so there are no version mismatches possible. The only difference is the CPU it's compiled on compared to the one it will run on (Intel P8700 vs AMD FX-60 which will run Mplayer), and it's a virtual machine too.
Really wish there was a better dependency check here, but that would make it a bit harder to keep the guide simple. It appears that checkinstall is only used to put it in your package list for easy removal.

No offence here, the guide is fine for the average Ubuntu user, but those with more knowledge might get some small problems along the way. This whole compiling thing is pretty new to me too though.

---

### Post by andrew.46 on 2010-08-28
Hi Hero,

> **Hero of Time said:**
> Andrew, do you know what happens when you run two commands as one with &&?

It does not actually run 2 commands as one, it runs the first command and then *if* that first command returns an exit status of zero it runs the second command. (Exit status of zero is of course a successful command.) This represents the boolean AND, you will see all the gory details in the bash man pages :).

> Oh, just one last thing: the package you get from checkinstall, does it note all the dependencies it might need afterwards in case you build it on one system and install it on another? You don't want to end up with a broken dependency or feature.

To create a package of that sort checkinstall is not the tool to use, you must invest a little time and effort into creating a formal debian package. I have never really found the motivation to learn debian packaging I'm afraid...

Andrew

---

### Post by Hero of Time on 2010-08-29
> **andrew.46 said:**
> Hi Hero,
It does not actually run 2 commands as one, it runs the first command and then *if* that first command returns an exit status of zero it runs the second command. (Exit status of zero is of course a successful command.) This represents the boolean AND, you will see all the gory details in the bash man pages :).
Ah, yes, now that I read it again, I understand it better. Sorry to have doubted you.

> To create a package of that sort checkinstall is not the tool to use, you must invest a little time and effort into creating a formal debian package. I have never really found the motivation to learn debian packaging I'm afraid...
Same here ;). I've tried it, but some things are quite hard to understand, especially when they use 'easy' examples like 'Hello World'. That doesn't really deal with dependencies. Of course, once you get the hang of it, it will seem a lot easier than you thought it would be. It works now for me, running Mplayer from the terminal helped me getting my dependencies and build packages straight for my own system.

---

### Post by andrew.46 on 2010-08-29
Hi Hero,

> **Hero of Time said:**
> Ah, yes, now that I read it again, I understand it better. Sorry to have doubted you.

I actually prefer the techniques I use for this and my other guides to be doubted and questioned. This way I can review my methods and then build a better and more robust guide...

All the best,

Andrew

---

### Post by Cypress421 on 2010-09-01
Excellent guide! Some questions:

1) Are there any optimizations for 64-bit systems? I noticed a switch to install the 64-bit codecs, but are there any other optimizations?

2) Will these codecs conflict with those installed via Gstreamer for Totem?

3) The mplayer build folder in my home folder needs to be left alone?

4) Is there a command to check which version of mplayer you have?

I also ran the final command again, to see if there any updates and it seems like mplayer did exactly the same thing when I checked the first time, but needed to add my password - this is normal?

Thanks for a great guide!

---

### Post by andrew.46 on 2010-09-02
Hi Cypress,

I am glad this guide has been useful to you :).

> **Cypress421 said:**
> 

1) Are there any optimizations for 64-bit systems? I noticed a switch to install the 64-bit codecs, but are there any other optimizations?

The 64 bit codecs actually compare very poorly to those available to 32 bit systems I'm afraid. But no other optimisations, and in fact specific compile time options will mean the MPlayer developers will not help you with any problems...

> 2) Will these codecs conflict with those installed via Gstreamer for Totem?

No, there will be no conflict.

> 3) The mplayer build folder in my home folder needs to be left alone?

You are best to leave that in place for future updates as well as safe storage of older debs.

> 4) Is there a command to check which version of mplayer you have?

Indeed there is:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer | head -n 1[/COLOR]**
MPlayer SVN-r32037-4.4.4 (C) 2000-2010 MPlayer Team

```

> I also ran the final command again, to see if there any updates and it seems like mplayer did exactly the same thing when I checked the first time, but needed to add my password - this is normal?

This is the checkinstall command asking for your password not the actual 'svn up' procedure which can be done as an ordinary user.

All the best,

Andrew

---

### Post by Cypress421 on 2010-09-02
Thanks, last question, what is the "SVN up" procedure? Is there another command for mplayer updates?

---

### Post by andrew.46 on 2010-09-02
Hi Cypress,

> **Cypress421 said:**
> Thanks, last question, what is the "SVN up" procedure? Is there another command for mplayer updates?

This is the shortened version of the command *svn update*. What you now have on your computer is a copy of the source code for MPlayer that is being constantly added to by MPlayer developers. The command *svn up* simply realigns your local copy with any changes sunsequently made in the remote subversion repository. You will have read-only access to this repository, if you had write access you could also make local changes and upload them to the remote repository.

There is a great deal of manipulation you can do with read-only access. Perhaps you could be one of the few people to read a guide I wrote a while back:

Linux Basics: A gentle introduction to accessing 'svn' repositories
[http://ubuntuforums.org/showthread.php?t=1167578](http://ubuntuforums.org/showthread.php?t=1167578)

which details some easy and not so easy techniques to use when accessing svn repositories. Maybe one day this guide will take off....

Andrew

---

### Post by Cypress421 on 2010-09-02
Ahh, got it. I cd'd into $HOME/mplayer_build/mplayer and then entered svn up, but I get this:

svn: Can't connect to host 'svn.mplayerhq.hu': Connection refused

Doesn't work with sudo either. Ideas? and is this all I need to do to ensure MPlayer is kept updated or do I need to recompile too?

Thanks!

---

### Post by andrew.46 on 2010-09-02
Hi Cypress,

> **Cypress421 said:**
> Ahh, got it. I cd'd into $HOME/mplayer_build/mplayer and then entered svn up, but I get this:

svn: Can't connect to host 'svn.mplayerhq.hu': Connection refused



I have just checked and the subversion repository is working well from here. Try testing your connection as follows:

```

andrew@skamandros~$ **[COLOR="Red"]traceroute svn.mplayerhq.hu[/COLOR]**
traceroute to svn.mplayerhq.hu (213.144.138.186), 30 hops max, 60 byte packets
 1  dsldevice.lan (192.168.1.254)  38.334 ms  37.612 ms  36.890 ms
 2  loopback100.cor13.syd.connect.com.au (210.8.1.242)  17.449 ms  22.606 ms  27.982 ms
 3  * * *
 4  * * *
 5  xe7-0-0-320.sybr4.global-gateway.net.nz (202.50.238.205)  63.542 ms  68.027 ms  83.800 ms
 6  * * *
 7  * * *
 8  * * *
 9  te-7-4.car2.SanJose2.Level3.net (4.59.4.93)  204.582 ms  174.062 ms  173.203 ms
10  ae-3-89.edge1.SanJose3.Level3.net (4.68.18.144)  177.357 ms *  177.548 ms
11  GlobalCrossing-level3-xe.SanJose3.level3.net (4.68.111.162)  182.312 ms  186.762 ms  192.156 ms
12  146.82.32.154 (146.82.32.154)  355.292 ms  359.633 ms  365.104 ms
13  r1gva1.core.init7.net (77.109.128.54)  371.120 ms  374.372 ms  379.885 ms
14  r1zur2.core.init7.net (77.109.128.217)  392.275 ms  397.411 ms  401.246 ms
15  r1zba1.core.init7.net (77.109.128.206)  399.235 ms  404.142 ms  418.387 ms
16  natsuki.mplayerhq.hu (213.144.138.186)  343.859 ms  344.044 ms  348.824 ms

```

I love using traceroute!! Going from my router to Sydney ISP to New Zealand and then the US... Hopefully just a transient problem from your connection.

> and is this all I need to do to ensure MPlayer is kept updated or do I need to recompile too?

Recompile is required as well. If you look at the base of the guide you will see a little copy and paste section that should assist with this.

All the best,

Andrew

---

### Post by Cypress421 on 2010-09-02
Success! It was a Firestarter policy. I split the update command in two - svn update, then the rest. It was updated to the newest r32039, from 38 yesterday. Thanks a lot! Seems like mplayer is really frequented updated. Also, what do I change here:

```
./configure --confdir=/etc/mplayer --disable-mencoder --disable-x264
```

to enable x264? Is it worth updating x264? I have the latest one from git, so should I use it? Many thanks again!

---

### Post by andrew.46 on 2010-09-02
Hi Cypress,

> **Cypress421 said:**
> [...]what do I change here:

```
./configure --confdir=/etc/mplayer --disable-mencoder --disable-x264
```

to enable x264? Is it worth updating x264? I have the latest one from git, so should I use it? Many thanks again!

It does not help MPlayer itself to compile against x264 as *playback* does not depend on this. It is only useful if you wish to build and utilise MEncoder, in which case you will need to omit these option: *--disable-mencoder --disable-x264* and perhaps also add in the -dev files for libmp3lame and faac. Have you built x264 for FFmpeg? I would not personally build MEncoder if you are running the svn FFmpeg but it is up to you :).

Andrew

---

### Post by Cypress421 on 2010-09-02
I built libx264 for FFmpeg, but you are right, don't need Mencoder. 

Also, do you know what are the best options for accerlerating 1080p x264/mkv content with an ATI card, or should I buy Nvidia and compile VPDAU for Mplayer? This SVN looks like it supports VPDAU but AMD or Nvidia x264 acceleration? Specifically a 5570 GPU.

---

### Post by andrew.46 on 2010-09-03
Hi Cypress,

> **Cypress421 said:**
> Also, do you know what are the best options for accerlerating 1080p x264/mkv content with an ATI card, or should I buy Nvidia and compile VPDAU for Mplayer? This SVN looks like it supports VPDAU but AMD or Nvidia x264 acceleration? Specifically a 5570 GPU.

I must say I am a little relieved that I have come across a question I cannot answer :). Unfortunately I do not have access to much more than an Intel 945GM Chipset so my knowledge of such things is minimal to say the least. Hopefully somebody else on this thread can answer?

Andrew

---

### Post by Linuxforall on 2010-09-03
ATI has VAAPI and mplayer picks that up if ATI driver is installed.

---

### Post by Cypress421 on 2010-09-03
> **Linuxforall said:**
> ATI has VAAPI and mplayer picks that up if ATI driver is installed.

Does this work well? If so, I'll purge 7 off my desktop for sure.

---

### Post by Linuxforall on 2010-09-03
> **Cypress421 said:**
> Does this work well? If so, I'll purge 7 off my desktop for sure.

[http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/](http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/)

Instructions for mplayer vaapi and ati here at [http://www.vanstormbroek.nl/blog/?p=26](http://www.vanstormbroek.nl/blog/?p=26)

---

### Post by Cypress421 on 2010-09-03
I'll try these options out first.

---

### Post by mc4man on 2010-09-08
Hey Andrew - if you get a chance - try using mplayer to convert a wmapro to .wav 
The 2 installs here, 32028 and one slightly earlier do something quite odd when using ffwmapro, they  seem to give full bitrate to each channel
(whem forcing dmo all is normal
Ex.  = luckynight.wma using ffwmapro
> General
Complete name                    : /home/doug/1.wav
Format                           : Wave
File size                        : 34.2 MiB
Duration                         : 1mn 33s
Overall bit rate                 : 3 072 Kbps

Audio
Format                           : PCM
Format profile                   : Float
Format settings, Endianness      : Float
Codec ID                         : 3
Codec ID/Hint                    : IEEE 
Duration                         : 1mn 33s
Bit rate mode                    : Constant
Bit rate                         : 3 072 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 48.0 KHz
Resolution                       : 32 bits
Stream size                      : 34.2 MiB (100%)

dmo
> 
General
Complete name                    : /home/doug/2.wav
Format                           : Wave
File size                        : 17.1 MiB
Duration                         : 1mn 33s
Overall bit rate                 : 1 536 Kbps

Audio
ID                               : 0
Format                           : PCM
Codec ID                         : 1
Codec ID/Hint                    : Microsoft
Duration                         : 1mn 33s
Bit rate                         : 1 536 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 48.0 KHz
Resolution                       : 16 bits
Stream size                      : 17.1 MiB (100%)


Time for new builds I guess
(On my desktop had forgotten to uncomment the 6 channel output - the br was over 9000

Edit:
still doing the same w/r32105 (10.10

---

### Post by andrew.46 on 2010-09-08
Hi mc4man,

Interesting. Looks like the pcm is made a little differently by MPlayer, for dmo:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer -ac wmadmo test.wma -ao pcm:file=ac_dmo.wav[/COLOR]**
MPlayer SVN-r32049-4.4.4 (C) 2000-2010 MPlayer Team

Playing test.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 title: 
 author: 
 copyright: 
 comments: 
==========================================================================
Forced audio codec: wmadmo
Opening audio decoder: [dmo] Win32/DMO decoders
AUDIO: 48000 Hz, 2 ch, **[COLOR="Red"]s16le[/COLOR]**, 288.4 kbit/18.78% (ratio: 36054->192000)
Selected audio codec: [wmadmo] afm: dmo (Windows Media Audio DMO)
==========================================================================
[AO PCM] File: ac_dmo.wav (WAVE)
**[COLOR="Red"]PCM: Samplerate: 48000Hz Channels: Stereo Format s16le[/COLOR]**
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
**[COLOR="Red"]AO: [pcm] 48000Hz 2ch s16le (2 bytes per sample)[/COLOR]**
Video: no video
Starting playback...
A:  93.3 (01:33.2) of 93.6 (01:33.5)  1.1% 


Exiting... (End of file)

```

and for ffwmapro:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer -ac ffwmapro test.wma -ao pcm:file=ac_ffwmapro.wav[/COLOR]**
MPlayer SVN-r32049-4.4.4 (C) 2000-2010 MPlayer Team

Playing test.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 title: 
 author: 
 copyright: 
 comments: 
==========================================================================
Forced audio codec: ffwmapro
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, **[COLOR="Red"]floatle[/COLOR]**, 288.4 kbit/9.39% (ratio: 36054->384000)
Selected audio codec: [ffwmapro] afm: ffmpeg (WMA Pro audio (FFmpeg))
==========================================================================
[AO PCM] File: ac_ffwmapro.wav (WAVE)
**[COLOR="Red"]PCM: Samplerate: 48000Hz Channels: Stereo Format floatle[/COLOR]**
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
**[COLOR="Red"]AO: [pcm] 48000Hz 2ch floatle (4 bytes per sample)[/COLOR]**
Video: no video
Starting playback...
A:  94.8 (01:34.8) of 93.6 (01:33.5)  0.4% 


Exiting... (End of file)

```

with the '2 bytes per sample' and '4 bytes per sample' showing the reason for doubled size of the ffwmapro sample:

```

andrew@skamandros~/Desktop$ du ac_ffwmapro.wav ac_dmo.wav 
34980	ac_ffwmapro.wav
17492	ac_dmo.wav

```

But as to the significance of this I am not entirely sure, although the evidence is nicely given by MPlayer :(. The defaults can be overridden of course as follows:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer -ac wmadmo test.wma -af format=floatle -ao pcm:file=ac_dmo.wav[/COLOR]**
MPlayer SVN-r32049-4.4.4 (C) 2000-2010 MPlayer Team

Playing test.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 title: 
 author: 
 copyright: 
 comments: 
==========================================================================
Forced audio codec: wmadmo
Opening audio decoder: [dmo] Win32/DMO decoders
AUDIO: 48000 Hz, 2 ch, **[COLOR="Red"]s16le[/COLOR]**, 288.4 kbit/18.78% (ratio: 36054->192000)
Selected audio codec: [wmadmo] afm: dmo (Windows Media Audio DMO)
==========================================================================
[AO PCM] File: ac_dmo.wav (WAVE)
**[COLOR="Red"]PCM: Samplerate: 48000Hz Channels: Stereo Format floatle[/COLOR]**
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
**[COLOR="Red"]AO: [pcm] 48000Hz 2ch floatle (4 bytes per sample)[/COLOR]**
Video: no video
Starting playback...
A:  93.3 (01:33.2) of 93.6 (01:33.5)  1.2% 


Exiting... (End of file)

```

But I am not sure of the value in doing this...

Andrew

---

### Post by mc4man on 2010-09-08
Where it came up was fooling around w/ a batch mplayer pipe -  wmal to flac. As it was there was a wmap in the folder and flac choked on it.

If ffmpeg was used on the wmap then the result is as expected.

I guess mplayer is defaulting to 4 bits per sample for playback of wmap which also is seen (used) in extraction  Edit: bit of a brain lock there for me - extraction in this case is just a 'clone' of playback.., no presumption that the bitrate or bit depth would would be the 'norm'


(obviously no compelling reason to use mplayer to extact/convert wmap

---

### Post by tock on 2010-09-09
I copy and pasted all the commands.  Install went well.  I can play avi files and all works great.  Now for the dreaded hair pulling MTS files my HD camera creates.  The video plays with lots of horizontal lines (needs de-interlaced?) and I have no audio.  I've been fighting these files with Ubuntu now for weeks.  I've tried converting them to h.264 using fakeoutdoorsmans ffmpeg/h264 guide with not much success.  The only way I've gotten them to play correctly was converting them to non-hd avi :/.
The nvidia card I have is a hd card but from what I"ve read the vdpau drivers only work with the 8000 series cards.  I have a dual core intel with 2 gig of ram and a nvidia 7500 HD card

Thankyou for taking the time to create a guide for us.  Its folks like you that are truly making linux work for the rest of us!

---

### Post by andrew.46 on 2010-09-09
Hi tock,

> **tock said:**
> I copy and pasted all the commands.  Install went well.  I can play avi files and all works great. 

Great news :).

> Now for the dreaded hair pulling MTS files my HD camera creates.  The video plays with lots of horizontal lines (needs de-interlaced?) and I have no audio.  I've been fighting these files with Ubuntu now for weeks.  I've tried converting them to h.264 using fakeoutdoorsmans ffmpeg/h264 guide with not much success.  The only way I've gotten them to play correctly was converting them to non-hd avi :/.

I have not had much to do with mts files but I understand they usually have h264 video and either ac-3 or pcm sound neither of which should cause problems with FFmpeg or MPlayer. Can you post a sample somewhere? Also FakeOutdoorsman is very approachable if there are problems reaizing or transcoding...

> The nvidia card I have is a hd card but from what I"ve read the vdpau drivers only work with the 8000 series cards.  I have a dual core intel with 2 gig of ram and a nvidia 7500 HD card

Don't worry I don't have a video card at all on this underpowered laptop, just an intel chip, and I manage :).

> Thankyou for taking the time to create a guide for us.  Its folks like you that are truly making linux work for the rest of us!

Thanks for your kind words!

Andrew

---

### Post by TOfregato on 2010-09-10
Thank you for this awesome script and guide!

In my complete n00biness i found out that running the make command with a -j5 parameter makes compiling a lot faster on my quadcore machine (and by a lot, I mean really much faster). Maybe you can add this info to your guide to speed things up for people with multicore machines.

Again, thanks for sharing your work!

---

### Post by andrew.46 on 2010-09-10
Hi TOfregato,

> **TOfregato said:**
> Thank you for this awesome script and guide!

It is my pleasure :).

> In my complete n00biness i found out that running the make command with a -j5 parameter makes compiling a lot faster on my quadcore machine (and by a lot, I mean really much faster). Maybe you can add this info to your guide to speed things up for people with multicore machines.

Indeed this is something I do on my own setup and as you have found it speeds up compilation in a big way. I have not added it into this guide in part because it would require a different integer for each computer the guide runs on and in part when compilation fails the error messages are not quite as clean. Nevertheless I suspect I will add a brief message into the body of the guide mentioning the possibilities of adding this option.

Thanks,

Andrew

---

### Post by Linuxforall on 2010-09-12
> **TOfregato said:**
> Thank you for this awesome script and guide!

In my complete n00biness i found out that running the make command with a -j5 parameter makes compiling a lot faster on my quadcore machine (and by a lot, I mean really much faster). Maybe you can add this info to your guide to speed things up for people with multicore machines.

Again, thanks for sharing your work!


For quad it should be j4, for my dual XEON its j8.

---

### Post by tock on 2010-09-12
What I've noticed is that the files play ok when pulled directly from the camera with no editing.  When I edit the file using the software that came with the camera mplayer will no longer play the audio but vlc will.  I've uploaded a [clip]("http://myweb.cableone.net/kedwards2008/").

---

### Post by andrew.46 on 2010-09-13
Hi tock,

> **tock said:**
> What I've noticed is that the files play ok when pulled directly from the camera with no editing.  When I edit the file using the software that came with the camera mplayer will no longer play the audio but vlc will.  I've uploaded a [clip]("http://myweb.cableone.net/kedwards2008/").

Thanks for taking the trouble to upload the file. It certainly plays on the svn MPlayer, including the sound, but indeed it struggles a little on my underpowered setup and even my old eyes can see the interlacing problem.

However the svn FFmpeg did an excellent job transcoding, resizing and deinterlacing the file. I borrowed the syntax from [FakeOutdoorsman's guide]("http://ubuntuforums.org/showthread.php?t=786095"), added in -deinterlace:

```

ffmpeg -i clip.M2TS \
       -acodec libfaac -ab 128k -ac 2 \
       -vf scale=640:-1 -deinterlace \
       -vcodec libx264 -vpre slow -crf 22 \
       -threads 0 UF_train.mp4

```

I am ready for correction on this usage of FFmpeg (deinterlacing) as I have not really dabbled in this area before, although the results look fine. I have placed the 16 meg file here if you are interested:

```

wget http://www.andrews-corner.org/samples/UF_train.mp4

```

but you should easily be able to produce something similar with your files I suspect. And if that man in front of the camera is a relative of yours you should tell him to wear a hat :).

Andrew

---

### Post by FakeOutdoorsman on 2010-09-13
> **andrew.46 said:**
> I am ready for correction on this usage of FFmpeg (deinterlacing) as I have not really dabbled in this area before, although the results look fine.

I suspect that *yadif* will be introduced into FFmpeg soon.  The patch is being tossed around lately in the ffmpeg-devel mailing list.  I am eagerly awaiting this addition because I am currently using it for a work project via MPlayer with a named pipe to FFmpeg.  I use *-deinterlace* in FFmpeg for less important encodes and use the usually slower *yadif* when I have the time or need a more versatile deinterlacer.

---

### Post by andrew.46 on 2010-09-13
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> I suspect that *yadif* will be introduced into FFmpeg soon.  The patch is being tossed around lately in the ffmpeg-devel mailing list.  I am eagerly awaiting this addition because I am currently using it for a work project via MPlayer with a named pipe to FFmpeg.  I use *-deinterlace* in FFmpeg for less important encodes and use the usually slower *yadif* when I have the time or need a more versatile deinterlacer.

Just to display my total ignorance of deinterlacing I had no idea yadif was available to MPlayer let alone how to use it :). However it certainly does a brilliant job with the big mts file posted by tock. Until it all became a little too hard for my feeble laptop the following did a brilliant job:

```

mplayer -vf scale,yadif=1 -xy 640 clip.M2TS

```

but *yadif=3* was too much for my little computer and not first time I am thinking that I am growing out of this little laptop... Thanks again FakeOutdoorsman showing the path :).

Andrew

---

### Post by tock on 2010-09-13
The converted file plays great.  Thank you for your help.  Not sure why the mts file doesn't play the sound(Actually it plays the first scream then stops) on my system but the converted one you created plays perfect.

---

### Post by andrew.46 on 2010-09-14
Hi tock,

> **tock said:**
> The converted file plays great.  Thank you for your help.  Not sure why the mts file doesn't play the sound(Actually it plays the first scream then stops) on my system but the converted one you created plays perfect.

I noticed on my own system that once the errors started appearing: 'Your system is too slow to play this....' the sound would go, so I suspect a system resources problem rather than an MPlayer problem. I seem to remember that you have a copy of the svn FFmpeg so you shuld be able to convert your file to whatever format you want now, my own example was as I mentioned lifted from FakeOutdoorsman's guide and should at least provide a starting point.

All the best,

Andrew

---

### Post by tock on 2010-09-15
Andrew,

Just wanted to say thank you again for the help.  I finally removed mplayer and reinstalled and it started playing. I have the same problem as you with it stalling after a few minutes but at least it finally looks like it should. It amazes me how much processor power it takes to play back videos created from a camcorder that is no bigger then my hand.

---

### Post by Linuxforall on 2010-09-16
tock, the reason is the type of codec used, in your case, it would be better to compile the multi threaded version of mplayer.

---

### Post by andrew.46 on 2010-09-19
I have written and tested the upcoming Maverick version of this guide and good news is that there are few changes and it runs well :). Just waiting for Medibuntu to open up its Maverick Repository and I will publish...

Andrew

---

### Post by Hero of Time on 2010-09-21
So that means that Ubuntu is still shipping an older version of Mplayer, instead of a more recent one? Too bad. I was hoping they would use one of the recent SVN builds and keep that up.

Gonna check which version they include exactly. I also hope that RVM updates his PPA with a newer build too.

---

### Post by andrew.46 on 2010-09-28
An interesting change to the source tree of MPlayer is that now FFmpeg is being utilised as an external svn. Functionally no different to compile but it is an interesting change...

Andrew

---

### Post by andrew.46 on 2010-10-09
Looks like the release of Maverick and the opening of the Medibuntu Maverick Repository should be happening simultaneously in the next 12 hours so I have placed the Maverick information online. Should work well enough but I will retest with a fresh copy of Maverick when I lay hands on one, feel free to point out any glitches...

**Edit:** Medibuntu not on board yet so I have switched the codecs to manual install...

Andrew

---

### Post by digitalkarabao on 2010-10-15
Fresh install of Ubuntu 10.10 and trying to compile mplayer but I am hitting a brickwall after running 'make'. This is what I get:

```
ffmpeg/libavcodec/libavcodec.a(ffv1.o): In function `decode_frame':
ffv1.c:(.text+0x110e): undefined reference to `init_slice_state'
ffmpeg/libavcodec/libavcodec.a(ffv1.o): In function `decode_init':
ffv1.c:(.text.unlikely+0x4b3): undefined reference to `init_slice_contexts'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

Help guys! Thanks.

---

### Post by Marller on 2010-10-15
Could be mplayer itself (svn buggy code). I compiled mplayer on 10.10 (version) at 10.10 (date) without problems. Today i got the same errors as you.

---

### Post by ron999 on 2010-10-15
Yes, me too.
Tried to update today.
Buggy code.:(

```

ffmpeg/libavcodec/libavcodec.a(ffv1.o): In function `decode_frame':
ffv1.c:(.text+0xfb3): undefined reference to `init_slice_state'
ffmpeg/libavcodec/libavcodec.a(ffv1.o): In function `decode_init':
ffv1.c:(.text.unlikely+0x402): undefined reference to `init_slice_contexts'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
ron@ubuntu:~/mplayer$ 

```

---

### Post by sminki on 2010-10-15
> 
```

ffv1.c:(.text.unlikely+0x402): undefined reference to `init_slice_contexts'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

A couple of days ago I checked out Revision: 32483 and it builds fine with these instructions.

Revision: 32493 checked out today fails with the above error, so yes, it's the mplayer repo not the instructions :|

---

### Post by andrew.46 on 2010-10-15
Good news, the following compiled:

```

andrew@skamandros~$ mplayer | head -n 1
MPlayer SVN-r32493-4.3.3 (C) 2000-2010 MPlayer Team

```

But not for sminki? 

**Edit**: I see the confusion on my part, I was using an older gcc. Using Maverick's default gcc build still fails:

```

ffmpeg/libavcodec/libavcodec.a(ffv1.o): In function `decode_frame':
ffv1.c:(.text+0x10cf): undefined reference to `init_slice_state'
ffmpeg/libavcodec/libavcodec.a(ffv1.o): In function `decode_init':
ffv1.c:(.text.unlikely+0x563): undefined reference to `init_slice_contexts'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

I will see if #mplayer might be interested.....

Andrew

---

### Post by andrew.46 on 2010-10-15
A temporary workaround:

```

svn up -r 23802 $HOME/mplayer_build/mplayer/ffmpeg/libavcodec/ffv1.c

```

and compilation will succeed. Hopefully this will be fixed soon, remember *svn up* will overwrite this reversion...

Andrew

---

### Post by mc4man on 2010-10-16
> Hopefully this will be fixed soon
I would think so  - just a bit of a warning becoming a linking error, if your were to enable mencoder/x264 it shouldn't happen

---

### Post by andrew.46 on 2010-10-16
Hi mc4man,

> **mc4man said:**
> I would think so  - just a bit of a warning becoming a linking error, if your were to enable mencoder/x264 it shouldn't happen

Indeed, and this solves the puzzle as to why it compiles on my Slackware computer and not on my wife's 64bit computer: I compile MEncoder on Slackware but not on Ubuntu. Call for help [here]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2010-October/081296.html").

Andrew

---

### Post by Linuxforall on 2010-10-16
> **andrew.46 said:**
> Hi mc4man,



Indeed, and this solves the puzzle as to why it compiles on my Slackware computer and not on my wife's 64bit computer: I compile MEncoder on Slackware but not on Ubuntu. Call for help [here]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2010-October/081296.html").

Andrew

I always compile with mencoder so it never ever fails here, I do compile x264 and ffmpeg first.

---

### Post by andrew.46 on 2010-10-16
Hi Linuxforall,

> **Linuxforall said:**
> I always compile with mencoder so it never ever fails here, I do compile x264 and ffmpeg first.

This guide used to compile MEncoder and x264 before but I will admit that I tired of wrestling with the nest of dependencies created by the dependency tracking scheme, a cleaner option was to compile MPlayer alone. Then there was the issue of lack of development of MEncoder, its use of avi as its native container, lack of time on my part and a few other reasons...

Andrew

---

### Post by Linuxforall on 2010-10-16
As I mentioned before almost any and every DVD conversion program in Linux depends on mencoder, be it K9 in KDE or Acidrip in Gnome or more so I got no choice here. Your guide with just the minor ommision in ./configure and an addition in checkinstall works out mighty fine. :)

---

### Post by mc4man on 2010-10-17
fixed now for those not wishing mencoder
> $ mplayer
MPlayer SVN-r32494-4.5.1 (C) 2000-2010 MPlayer Team

> r25511 | michael | 2010-10-16 17:31:16 -0400 (Sat, 16 Oct 2010) | 1 line

Move shared functions out of CONFIG_FFV1_ENCODER ifdef


---

### Post by andrew.46 on 2010-10-20
Hi Linuxforall,

> **Linuxforall said:**
> As I mentioned before almost any and every DVD conversion program in Linux depends on mencoder, be it K9 in KDE or Acidrip in Gnome or more so I got no choice here. Your guide with just the minor ommision in ./configure and an addition in checkinstall works out mighty fine. :)

I have just come back from a brief holiday and I see all is fixed :). I shall give a bit of though to adding MEncoder back in, as you mention it requires some trivial additions to the guide.....

Andrew

---

### Post by mips on 2010-10-20
If I start a movie with SMPlayer I have high CPU usage, however if I start mplayer from the command line with **mplayer -vo vdpau -vc ffh264vdpau moviename.mkv** I have very low cpu usage.

I followed the first post in this thread to the letter. What's wrong?

Using Ubuntu 10.10.

---

### Post by typos1 on 2010-10-20
Mine wont play anything-I get "mplayer has finished unexpecteddly exit code 127" and the following log:

p, li { white-space: pre-wrap; } mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao alsa -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 79692123 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/jason/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -aid 0 -subpos 100 -volume 0 -nocache -ss 5 -osdlevel 0 -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/jason/Desktop/1.wav
 
 mplayer: error while loading shared libraries: libdirectfb-1.2.so.0: cannot open shared object file: No such file or directory
 

It doesnt play anything, I always get this error.

---

### Post by andrew.46 on 2010-10-20
Hi mips,

> **mips said:**
> If I start a movie with SMPlayer I have high CPU usage, however if I start mplayer from the command line with **mplayer -vo vdpau -vc ffh264vdpau moviename.mkv** I have very low cpu usage.

I suspect you need to manually adjust your video output in SMPlayer from:

Options --> Preferences --> General --> Video --> Output Driver

Andrew

**Edit: **Answered much better in Great Blue Heron's post below :).

---

### Post by Great Blue Heron on 2010-10-20
[QUOTE=mips]If I start a movie with SMPlayer I have high CPU usage, however if I start mplayer from the command line with mplayer -vo vdpau -vc ffh264vdpau moviename.mkv I have very low cpu usage.

I followed the first post in this thread to the letter. What's wrong?

Using Ubuntu 10.10.[/QUOTE]

Mips,

To enable VDPAU in SMplayer you must do two things. I have attached screenshots as an aid in setting the correct options.

1) Select VDPAU as the output driver. 
     Go to:* Preferences => General => Video => Output Driver = VDPAU*

2) Include the video codec options for VDPAU.
     Go to:[I] Preferences => Advanced => Options for MPlayer => Options 
        [/I]Write this line string in Options:[I]
        -vc ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau,[/I]

         Note: It is important to include the comma after the last video codec entry. The comma at the end tells mplayer to search for a suitable codec if one of the previous is not compatible.

Now go watch some movies. :popcorn:

---

### Post by andrew.46 on 2010-10-20
Hi typos,

> **typos1 said:**
> mplayer: error while loading shared libraries: libdirectfb-1.2.so.0: cannot open shared object file: No such file or directory

Perhaps a shared library has moved since you compiled MPlayer? You can either try reinstalling this library:

```
sudo apt-get install libdirectfb-dev libdirectfb-extra
```

and see if MPlayer is happy with that or simply follow the steps given in 'Updating MPlayer...' and compile MPlayer *without* this shared library.

Andrew

---

### Post by mips on 2010-10-21
> **andrew.46 said:**
> Hi mips,



I suspect you need to manually adjust your video output in SMPlayer from:

Options --> Preferences --> General --> Video --> Output Driver

Andrew

**Edit: **Answered much better in Great Blue Heron's post below :).

> **Great Blue Heron said:**
> Mips,

To enable VDPAU in SMplayer you must do two things. I have attached screenshots as an aid in setting the correct options.

1) Select VDPAU as the output driver. 
     Go to:* Preferences => General => Video => Output Driver = VDPAU*

2) Include the video codec options for VDPAU.
     Go to:[I] Preferences => Advanced => Options for MPlayer => Options 
        [/I]Write this line string in Options:[I]
        -vc ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau,[/I]

         Note: It is important to include the comma after the last video codec entry. The comma at the end tells mplayer to search for a suitable codec if one of the previous is not compatible.

Now go watch some movies. :popcorn:


Thanks guys, much appreciated. Working 100% now ;)

---

### Post by andrew.46 on 2010-10-22
Hi,

Has anybody managed to get the new 'capture' option working with MPlayer? Revision here:

```

------------------------------------------------------------------------
r32524 | diego | 2010-10-22 05:19:30 +1100 (Fri, 22 Oct 2010) | 5 lines

Implement a basic capture feature, available through -capture.
If a specified key is pressed during playback, the current stream is
captured to a file, similar to what -dumpstream achieves.
patch by Pásztor Szilárd, don tricon hu

```

Andrew

**Edit:** Looks like it was temporarily broken :). Anybody keen to test the new functionality could try the following:

```

mplayer -capture -dumpfile test.mp3 \
        -playlist 'http://www.abc.net.au/streaming/classic/classicfm.m3u'

```

The default capture key is 'c', I have not tested it extensively but this basic usage works well!

---

### Post by typos1 on 2010-10-23
Andrew.46-is "updating mplayer" a thread?

---

### Post by andrew.46 on 2010-10-23
Hi typos,

> **typos1 said:**
> Andrew.46-is "updating mplayer" a thread?

No, this is the heading of a section of the guide you have followed :). It basically involves updating the MPlayer source files and recompiling as follows with this single command:

```

cd $HOME/mplayer_build/mplayer && \
svn up && \
./configure --confdir=/etc/mplayer --disable-mencoder --disable-x264 \
            --codecsdir=/usr/local/lib/codecs && \
make && \
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/mplayer_build" \
   --pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "2:1.0~svn$(LC_ALL=C svn info 2> /dev/null | \
     grep Revision | cut -d' ' -f2)" && \
make distclean

```

Andrew

---

### Post by typos1 on 2010-10-23
Great, thanks-all working now!

---

### Post by andrew.46 on 2010-10-23
Hi typos,

> **typos1 said:**
> Great, thanks-all working now!

Good news :). Probably worthwhile to update every week or so and as a safeguard keeping hold of one or two of the old .deb files in case compilation is broken. But this is up to you, I suspect many grab a single copy and leave it at that but it is more fun keeping up with development!

Andrew

---

### Post by Segofam on 2010-10-23
> **andrew.46 said:**
> Hi typos,



No, this is the heading of a section of the guide you have followed :). It basically involves updating the MPlayer source files and recompiling as follows with this single command:

```

cd $HOME/mplayer_build/mplayer && \
svn up && \
./configure --confdir=/etc/mplayer --disable-mencoder --disable-x264 \
            --codecsdir=/usr/local/lib/codecs && \
make && \
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/mplayer_build" \
   --pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "2:1.0~svn$(LC_ALL=C svn info 2> /dev/null | \
     grep Revision | cut -d' ' -f2)" && \
make distclean

```Andrew

How do you know where a line ends to hit return, and then when to enter the next line/string/command?
Sincerely,
Scott

---

### Post by andrew.46 on 2010-10-23
Hi Scott,

> **Segofam said:**
> How do you know where a line ends to hit return, and then when to enter the next line/string/command?

The good news is that that entire code block is a single command, which means that you can copy the whole thing, paste it into a terminal window and press return once. There are a few shortcomings to doing it this way but I have done this deliberately to make life a little easier for those who are perhaps not used to navigating the terminal, compiling source code and the like. Hopefully I have succeeded in this aim?

Andrew

---

### Post by andrew.46 on 2010-10-25
Hi Linuxforall,

> **Linuxforall said:**
> As I mentioned before almost any and every DVD conversion program in Linux depends on mencoder, be it K9 in KDE or Acidrip in Gnome or more so I got no choice here. 

You might be interested to have a look at a very *manual* approach to DVD ripping and transcoding that I have published here just the other day:

FFmpeg and 'Fist of Fury'
[http://www.andrews-corner.org/fist.html](http://www.andrews-corner.org/fist.html)

Not for everybody I guess but it guarantees a good result every time, very different to Acidrip and friends though...

Andrew

---

### Post by Linuxforall on 2010-10-25
Really good, thank you again Andrew.


> **andrew.46 said:**
> Hi Linuxforall,



You might be interested to have a look at a very *manual* approach to DVD ripping and transcoding that I have published here just the other day:

FFmpeg and 'Fist of Fury'
[http://www.andrews-corner.org/fist.html](http://www.andrews-corner.org/fist.html)

Not for everybody I guess but it guarantees a good result every time, very different to Acidrip and friends though...

Andrew

---

### Post by andrew.46 on 2010-10-27
An alternative to this guide has appeared which may very well mean that building the svn from source in the manner I have described is less and less relevant to the Ubuntu way of doing things. I speak of a new PPA:

Packages in “MPlayer Daily Builds”
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

Very interesting times :).

Andrew

---

### Post by Linuxforall on 2010-10-27
> **andrew.46 said:**
> An alternative to this guide has appeared which may very well mean that building the svn from source in the manner I have described is less and less relevant to the Ubuntu way of doing things. I speak of a new PPA:

Packages in “MPlayer Daily Builds”
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

Very interesting times :).

Andrew


Your compilation guide is still relevant in every sense. PPAs however convenient may not be for all. This ppa is daily build and that means a new mplayer every now and then, in my case, I update monthly, also notice it has a x264, I compile my own using FO's guide so your guide is still every bit needed.

---

### Post by mc4man on 2010-10-27
> a new PPA:

It seems to be a fairly well enabled build, not everything, but probably what many would need.

For comparison here's the build-deps (the blue is an interesting 'oddity' - does not become an install dep
> Build-Depends: debhelper (>= 7),
               docbook-xml,
               docbook-xsl,
               ladspa-sdk,
               libenca-dev,
               libaa1-dev,
               libasound2-dev [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386],
               libaudio-dev,
               libcaca-dev,
               libcdparanoia-dev | libcdparanoia0-dev,
               libdirectfb-dev,
               libdts-dev,
               libesd0-dev,
               libfaad-dev,
               libfontconfig1-dev,
               libfreetype6-dev,
               libfribidi-dev,
               libgif-dev,
               libgl1-mesa-dev,
               libgtk2.0-dev,
               libjack-dev,
               libjpeg62-dev,
               liblircclient-dev,
               liblivemedia-dev,
               liblzo2-dev,
               libmp3lame-dev,
               libmpcdec-dev,
               libncurses5-dev,
               libopenal-dev,
               libpng12-dev | libpng-dev,
               libpulse-dev,
               libschroedinger-dev,
               libsdl1.2-dev | libsdl1.1-dev,
               libsmbclient-dev,
               libspeex-dev,
               libsvga1-dev [i386 amd64],
               [COLOR="Blue"]libswscale-dev[/COLOR],
               libtheora-dev (>= 1.0~beta1),
               libvorbis-dev,
               libvorbisidec-dev,
               libx11-dev,
               libx264-dev (>= 2:0.99),
               libxext-dev,
               libxinerama-dev,
               libxv-dev,
               libxvidcore-dev,
               libxvmc-dev,
               libxxf86dga-dev,
               libxxf86vm-dev,
               libvdpau-dev [i386 amd64],
               pkg-config,
               vstream-client-dev,
               x11proto-core-dev,
               xsltproc,
               yasm [i386 amd64],
               zlib1g-dev
The configure - 
> CONFIGURE_FLAGS = \
	--prefix=/usr \
	--confdir=/etc/mplayer \
	--enable-xvmc \
	--enable-menu \
	--disable-arts \
	--enable-largefiles \
	--language=all \
Don't know why the --enable-menu or the xvmc
The internal libdvdcss is disabled and uses runtime cpu. 

How often it updates to early to say - if it becomes an auto-build then I'd expect quite often

---

### Post by andrew.46 on 2010-10-28
Hi mc4man,

> **mc4man said:**
> How often it updates to early to say - if it becomes an auto-build then I'd expect quite often

Indeed, [debate continues]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2010-October/081354.html") as to the frequency.

Andrew

---

### Post by mc4man on 2010-10-28
> as to the frequency
With the first auto (build-bot) build later tonight, then the next update would give some indication there.

I'd also think the maintainer (R.T.), unlike w/ the ubuntu builds, would be more likely to consider any changes if there was a good reason for such.

---

### Post by Kamek437 on 2010-10-29
Ok I just followed this guide and I'm having a bit of a problem. I have two videos that mplayer can't play, but it seems ffplay can. Some info:

```

uname -a
Linux SpellBook 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

MPlayer SVN-r32566-4.4.5 (C) 2000-2010 MPlayer Team

FFmpeg version SVN-r25603, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct 29 2010 14:54:27 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab

Geforce 7600 Go (No VDPAU):(

```

Video 1: I get no video or audio (Exit Code 1 in SMPlayer) but Totem works

```

VCodec: WMV9 10fps 1024x768 2742kbps
ACodec: WMA V8 166kps
Mplayer Log:
mplayer -noquiet -nofs -nomouseinput -lavdopts threads=2 -sub-fuzziness 1 -identify -slave -vo xv:adaptor=0 -ao alsa -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 79692123 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/kamek/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -volume 100 -nocache -osdlevel 0 -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/kamek/Videos/DynamicXmlWithCSharp4_2MB_ch9.wmv

MPlayer SVN-r32566-4.4.5 (C) 2000-2010 MPlayer Team
Terminal type `unknown' is not defined.

Playing /home/kamek/Videos/DynamicXmlWithCSharp4_2MB_ch9.wmv.
ASF file format detected.
ID_AUDIO_ID=1
[asfheader] Audio stream found, -aid 1
ID_VIDEO_ID=2
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  1024x768  24bpp  1000.000 fps  928.0 kbps (113.3 kbyte/s)
Clip info:
 title: 
ID_CLIP_INFO_NAME0=title
ID_CLIP_INFO_VALUE0=
 author: 
ID_CLIP_INFO_NAME1=author
ID_CLIP_INFO_VALUE1=
 copyright: 
ID_CLIP_INFO_NAME2=copyright
ID_CLIP_INFO_VALUE2=
 comments: 
ID_CLIP_INFO_NAME3=comments
ID_CLIP_INFO_VALUE3=
ID_CLIP_INFO_N=4
ID_FILENAME=/home/kamek/Videos/DynamicXmlWithCSharp4_2MB_ch9.wmv
ID_DEMUXER=asf
ID_VIDEO_FORMAT=WMV3
ID_VIDEO_BITRATE=928000
ID_VIDEO_WIDTH=1024
ID_VIDEO_HEIGHT=768
ID_VIDEO_FPS=1000.000
ID_VIDEO_ASPECT=1.3333
ID_AUDIO_FORMAT=353
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_START_TIME=3.00
ID_LENGTH=868.90
ID_SEEKABLE=1
ID_CHAPTERS=0
Opening video filter: [*** auto=1]
[***] auto-open
Opening video filter: [screenshot]
==========================================================================
Opening video decoder: [dmo] DMO video codecs


MPlayer interrupted by signal 11 in module: init_video_codec
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
ID_SIGNAL=11
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

Video 2: I get audio only Totem won't play either

```

VCodec: SMC 640x480 5kbps
ACodec: MP3 32kbps
Mplayer Log:
mplayer -noquiet -nofs -nomouseinput -lavdopts threads=2 -sub-fuzziness 1 -identify -slave -vo xv:adaptor=0 -ao alsa -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 79692123 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/kamek/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -volume 100 -nocache -osdlevel 0 -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/kamek/Videos/0101 - About this Course.mov

MPlayer SVN-r32566-4.4.5 (C) 2000-2010 MPlayer Team
Terminal type `unknown' is not defined.

Playing /home/kamek/Videos/0101 - About this Course.mov.
libavformat file format detected.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x9aca960] max_analyze_duration reached
ID_VIDEO_ID=0
[lavf] stream 0: video (smc), -vid 0
ID_AUDIO_ID=0
ID_AID_0_LANG=eng
[lavf] stream 1: audio (mp3), -aid 0, -alang eng
VIDEO:  [smc ]  640x480  8bpp  1.000 fps    5.1 kbps ( 0.6 kbyte/s)
Clip info:
 title: VTC Online University
ID_CLIP_INFO_NAME0=title
ID_CLIP_INFO_VALUE0=VTC Online University
 title-eng: VTC Online University
ID_CLIP_INFO_NAME1=title-eng
ID_CLIP_INFO_VALUE1=VTC Online University
 artist: Virtual Training Company
ID_CLIP_INFO_NAME2=artist
ID_CLIP_INFO_VALUE2=Virtual Training Company
 artist-eng: Virtual Training Company
ID_CLIP_INFO_NAME3=artist-eng
ID_CLIP_INFO_VALUE3=Virtual Training Company
 copyright: 1996-2004
ID_CLIP_INFO_NAME4=copyright
ID_CLIP_INFO_VALUE4=1996-2004
 copyright-eng: 1996-2004
ID_CLIP_INFO_NAME5=copyright-eng
ID_CLIP_INFO_VALUE5=1996-2004
ID_CLIP_INFO_N=6
ID_FILENAME=/home/kamek/Videos/0101 - About this Course.mov
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=smc 
ID_VIDEO_BITRATE=5056
ID_VIDEO_WIDTH=640
ID_VIDEO_HEIGHT=480
ID_VIDEO_FPS=1.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=ms
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=22050
ID_AUDIO_NCH=1
ID_START_TIME=0.00
ID_LENGTH=533.81
ID_SEEKABLE=1
ID_CHAPTERS=0
Opening video filter: [*** auto=1]
[***] auto-open
Opening video filter: [screenshot]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffsmc] vfm: ffmpeg (Apple Graphics (SMC) codec)
==========================================================================
ID_VIDEO_CODEC=ffsmc
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4000->88200)
ID_AUDIO_BITRATE=32000
ID_AUDIO_RATE=22050
ID_AUDIO_NCH=2
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[equalizer] Limiting the number of filters to 9 due to low sample rate.
[equalizer] Limiting the number of filters to 9 due to low sample rate.
[equalizer] Limiting the number of filters to 9 due to low sample rate.
AO: [alsa] 22050Hz 2ch floatle (4 bytes per sample)
[equalizer] Limiting the number of filters to 9 due to low sample rate.
[equalizer] Limiting the number of filters to 9 due to low sample rate.
ID_AUDIO_CODEC=mp3
[Mixer] No hardware mixing, inserting volume filter.
[equalizer] Limiting the number of filters to 9 due to low sample rate.
[equalizer] Limiting the number of filters to 9 due to low sample rate.
Starting playback...
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x8a84a60]BICUBIC scaler, from pal8 to yuv420p using MMX2
VO: [xv] 640x480 => 640x480 Planar YV12 

ID_VIDEO_TRACK=0

ID_AUDIO_TRACK=1

```

Now for ffplay's output

Video 2:

```

FFplay version SVN-r25603, Copyright (c) 2003-2010 the FFmpeg developers
  built on Oct 29 2010 14:54:27 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.32. 3 / 50.32. 3
  libavcore      0. 9. 1 /  0. 9. 1
  libavcodec    52.93. 0 / 52.93. 0
  libavformat   52.84. 0 / 52.84. 0
  libavdevice   52. 2. 2 / 52. 2. 2
  libavfilter    1.53. 0 /  1.53. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x96e2080] max_analyze_duration reached
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '0101 - About this Course.mov':
  Metadata:
    title           : VTC Online University
    title-eng       : VTC Online University
    artist          : Virtual Training Company
    artist-eng      : Virtual Training Company
    copyright       : 1996-2004
    copyright-eng   : 1996-2004
  Duration: 00:08:53.81, start: 0.000000, bitrate: 37 kb/s
    Stream #0.0(eng): Video: smc, pal8, 640x480, 5 kb/s, 1 fps, 1 tbr, 600 tbn, 600 tbc
    Stream #0.1(eng): Audio: mp3, 22050 Hz, 1 channels, s16
[ffsink @ 0x96eccd0] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x978e5b0] w:640 h:480 fmt:pal8 -> w:640 h:480 fmt:yuv420p flags:0x4
  17.07 A-V:  0.066 s:0.0 aq=  320KB vq=   22KB sq=    0B f=0/0   f=0/0

```

Video 1:

```

FFplay version SVN-r25603, Copyright (c) 2003-2010 the FFmpeg developers
  built on Oct 29 2010 14:54:27 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.32. 3 / 50.32. 3
  libavcore      0. 9. 1 /  0. 9. 1
  libavcodec    52.93. 0 / 52.93. 0
  libavformat   52.84. 0 / 52.84. 0
  libavdevice   52. 2. 2 / 52. 2. 2
  libavfilter    1.53. 0 /  1.53. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[wmv3 @ 0x992c2d0] Extra data: 8 bits left, value: 0
Input #0, asf, from 'DynamicXmlWithCSharp4_2MB_ch9.wmv':
  Metadata:
    WMFSDKVersion   : 11.0.6001.7001
    WMFSDKNeeded    : 0.0.0.0000
    IsVBR           : 1
    VBR Peak        : 272
    Buffer Average  : 579
    album           : 
    track           : 
    WM/PromotionURL : 
    WM/AlbumCoverURL: 
    genre           : 
    WM/Year         : 
    WM/GenreID      : 
    composer        : 
    WM/Lyrics       : 
    WM/ToolName     : 
    WM/ToolVersion  : 
    album_artist    : 
    WM/AuthorURL    : 
    WM/AudioFileURL : 
    WM/ParentalRating: 
    WM/BeatsPerMinute: 
    WM/InitialKey   : 
    WM/Mood         : 
    WM/DVDID        : 
    WM/UniqueFileIdentifier: 
    WM/ModifiedBy   : 
    WM/RadioStationName: 
    WM/RadioStationOwner: 
    WM/PlaylistDelay: 
    WM/Codec        : 
    WM/DRM          : 
    WM/ISRC         : 
    WM/Provider     : 
    WM/ProviderRating: 
    WM/ProviderStyle: 
    WM/ContentDistributor: 
    WM/SubscriptionContentID: 
    title           : 
    artist          : 
    copyright       : 
    comment         : 
  Duration: 00:14:28.90, start: 3.000000, bitrate: 785 kb/s
    Stream #0.0: Audio: wmav2, 44100 Hz, 2 channels, s16, 96 kb/s
    Stream #0.1: Video: wmv3, yuv420p, 1024x768, 928 kb/s, PAR 1:1 DAR 4:3, 10 tbr, 1k tbn, 1k tbc
[wmv3 @ 0x992c2d0] Extra data: 8 bits left, value: 0
   7.39 A-V: -0.019 s:0.0 aq=  322KB vq= 1849KB sq=    0B f=0/0    =0/0

```

Both play fine with ffplay <filename>. What's going on here?:confused:

Update, got video 2 to play in smplayer. It looks like it was using the wrong demuxer (lavfpref) I changed it to mov and it works ok. The other one I can't get anything but ffplay to play for some reason. Isn't mplayer supposed to use ffmpeg?

Update, Sorry guys I figured it out. -vo gl did the trick on the first file. I think the windows codecs don't like to run in -vo xv. Maybe it's compiz I'm not sure. Can someone point me to some info on this? I'm curious as to why mplayer chose lavfpref over mov and how I can sort that out.

---

### Post by andrew.46 on 2010-10-30
Hi Kamek,

Are you able to post these 2 files somewhere so I can have a look? BTW your post would be a little easier to follow if you use the code tags :).

```
Like this! 
```

Andrew

---

### Post by Kamek437 on 2010-10-30
Oh ok post edited, should be better now. Video 1 is available [here.]("http://mschnlnine.vo.llnwd.net/d1/ch9/7/8/7/4/5/4/DynamicXmlWithCSharp4_2MB_ch9.wmv")
Video 2 is available [here.]("http://cid-621420ed80884f80.office.live.com/self.aspx/Public/Video2.tar.bz2")
Thanks for your help Andrew.
In your experience what's the best video out in mplayer if your running compiz and don't have vdpau?
Also do you think you could modify this guide for mplayer-mt and ffmpeg-mt? 
Or are those not needed anymore, because with my 1080P test source it seemed to be hitting both cores just fine.

---

### Post by mc4man on 2010-10-30
I guess different setups, ubuntu release act a bit differently with those files.
Video 1 (wmv) I believe is simply a dmo error, if w32codecs is present then mplayer defaults to dmo and on that video, crashes

mplayer -vc ffwmv3 DynamicXmlWithCSharp4_2MB_ch9.wmv plays it fine (on any setup here.

The other (smc) is quite curious
On a karmic install everything but mplayer and vlc play fine, inc. totem

On an abandoned lucid (not updated), only xine based players work (& ffplay

On maverick nothing plays except a totem-xine install I've kept alive & ffplay.

vlc complains
main subpicture error: blending YUVA to RGBP failed
mplayer blackscreens

(nvidia in use here

---

### Post by Kamek437 on 2010-10-30
@mc4man What vo are you using?
Like I said it looks like it was -vo nv that was making it crash for some reason. I switched to gl and the wmv plays fine. The other one apparently doesn't like the lavfpref demuxer that mplayer choses, it wants the mov demuxer. What I need to know is which -vo is best for compiz as I get some tearing and poor performance in HD fullscreen stuff with gl. I have both vsync's on in nvidia-settings and compiz on with minimal effects.

---

### Post by mc4man on 2010-10-30
> What vo are you using?
On my laptop (core2duo nvidia 8400 ) I use xv and for h264 & VC1 vdpau - the 8400 has minimal vdpau support

On a desktop (p4 nvidia 7800 OC) I use xv  - obviously here true HD material w/ high bitrate isn't playable 

Overall haven't ever had video tearing in either setup, though a little has creep in rarely on the p4 on maverick w/ the 260.XX drivers. (the best drivers for my 7800 where 195 or less.

As far as compiz I disable most everything but the cube and viewpoint switcher, enable vsync, disable the redirect fullscreen windows, disable workarounds, enable video playback
You haven't posted your hardware/ubuntu release though I'd use xv if possible 

As far as that wmv - it appears either way will work, make mplayer use ffwmv3 instead of dmo or switch to gl.
(I usually have vfm=ffmpeg in mplayer/config so dmo is rarely used

---

### Post by Kamek437 on 2010-10-30
Awesome, vfm=ffmpeg is exactly what I was looking for. Everything seems to work now in -vo nv with less tearing. The mov still needs -demuxer mov instead of lavfpref but I can live with that.

---

### Post by Kamek437 on 2010-10-30
Should I have vsync on in nvidia settings and compiz? What's the preffered method for that?

---

### Post by andrew.46 on 2010-10-30
Hi Kamek,

> **Kamek437 said:**
> Awesome, vfm=ffmpeg is exactly what I was looking for. Everything seems to work now in -vo nv with less tearing. The mov still needs -demuxer mov instead of lavfpref but I can live with that.

There seems to be a little demuxer trouble with '0101 - About this Course.mov' and as you have found it requires *-demuxer mov* to play properly. It might be a little over the top but you could always add the following to your $HOME/.mplayer/config:

```

[extension.mov]
profile-desc="profile for .mov files"
demuxer=mov

```

and this will spare some scrambling around with the commandline :). BTW you can see all your available demuxers by running:

```
mplayer -demuxer help
```

As for FFmpeg-mt and friends I decided a while back to concentrate on the standard svn MPlayer in part for the completely selfish reason that this is what I am running on my own computer :). Compiz too I am afraid I have no experience with, but I am sure there are others reading this thread who use it.

Andrew

---

### Post by mc4man on 2010-10-30
> Should I have vsync on in nvidia settings and compiz? 
I think so..
On maverick have tried 4 combo's
nouveau, no 3d, metacity
nouveau, 3d
nvidia, metacity
nvidia, compiz

At least here nvidia, compiz wins out, bigtime on a large lcd, closer on the laptop.
So w/ nvidia, compiz I've always enabled vsync where ever I can find.
(direct opposite of when I use to use XP, then always disabled where ever

Side note - for vlc and that .mov
 vlc --demux avformat

---

### Post by Kamek437 on 2010-10-30
Awesome, thanks guys every thing's working nicely now. Now I'm off to compile ffmpeg-mt from svn and do some encoding benchmarks.

---

### Post by mIXpRo on 2010-11-07
hii, 
i've tried to install mplayer before but i couldn't and i guess i left some unfinished work ,
cause when i try the command  
> sudo apt-get -y install smplayer smplayer-themes qt4-qtconfig

i get this 
> 
After this operation, 18.5MB of additional disk space will be used.
(Reading database ... 227849 files and directories currently installed.)
[COLOR=Red]Unpacking mplayer (from .../mplayer_2%3a1.0~rc4~try1.dsfg1-1ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/mplayer_2%3a1.0~rc4~try1.dsfg1-1ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/share/man/cs/man1/mplayer.1.gz', which is also in package[/COLOR] mplayer-common 1.0-1.119
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package smplayer.
Unpacking smplayer (from .../smplayer_0.6.9-1_i386.deb) ...
Selecting previously deselected package smplayer-themes.
Unpacking smplayer-themes (from .../smplayer-themes_0.1.20+dfsg-1_all.deb) ...
Selecting previously deselected package smplayer-translations.
Unpacking smplayer-translations (from .../smplayer-translations_0.6.9-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for python-support ...
[COLOR=Red]Errors were encountered while processing:
 /var/cache/apt/archives/mplayer_2%3a1.0~rc4~try1.dsfg1-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

and i have tried 
>  sudo apt-get install -f  but didn't help 

any suggestions ?


thnx

---

### Post by mc4man on 2010-11-08
> mplayer-common 1.0-1.119
Get rid of that, where did you get it from? (an rpm package?

---

### Post by mIXpRo on 2010-11-08
thnx it helped ,

i want to watch mms://XXXXX.wmv and i can use the :Streaming Protocol : **RTSP** 			
In: UDP on port 5005 			
Out: UDP on port 5004 			
In/Out : **TCP on port 554**


i tried with smplayer open->url mms://XXXXX.wmv it crashes and this is the log :
>  p, li { white-space: pre-wrap; } /usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao pulse -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 85983582 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/mixpro/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -volume 50 -cache 1000 -osdlevel 0 -prefer-ipv4 -vf-add screenshot -slices -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 mms://video9.technion.ac.il/Courses/Hozek1/Hozek1-9.wmv
  MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
 Terminal type `unknown' is not defined.
  Playing mms://video9.technion.ac.il/Courses/Hozek1/Hozek1-9.wmv.
 STREAM_ASF, URL: mms://video9.technion.ac.il/Courses/Hozek1/Hozek1-9.wmv
 Resolving video9.technion.ac.il for AF_INET...
 Connecting to server video9.technion.ac.il[132.68.1.27]: 1755...
 Resolving video9.technion.ac.il for AF_INET6...
 Couldn't resolve name for AF_INET6: video9.technion.ac.il
 Resolving video9.technion.ac.il for AF_INET...
 Connecting to server video9.technion.ac.il[132.68.1.27]: 80...


---

### Post by andrew.46 on 2010-11-08
A big day for MPlayer as the default for aac has been changed:

```

andrew@skamandros~/music/ftgws$ mplayer Revelation_21.m4a 
MPlayer SVN-r32605-4.3.3 (C) 2000-2010 MPlayer Team

Playing Revelation_21.m4a.
libavformat file format detected.
[lavf] stream 0: audio (aac), -aid 0, -alang und
Clip info:
 major_brand: M4A 
 minor_version: 512
 compatible_brands: isomiso2
 title: A New Heaven
 artist: Lesley Garrett
 composer: Tolga Kashif
 album: Lesley Garrett - The Singer
 date: 2005
 encoder: Lavf52.84.0
 genre: Classical
 track: 1
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 152.0 kbit/10.77% (ratio: 18999->176400)
**[COLOR="Red"]Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))[/COLOR]**
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A: 364.8 (06:04.8) of 365.2 (06:05.1)  0.5% 


Exiting... (End of file)

```

Should not be long until libfaad2 is removed from the source tree...

Andrew

---

### Post by andrew.46 on 2010-11-08
Hi mixpro,

> **mIXpRo said:**
> 

```

MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team

```


Something has gone a little awry, you are not using the svn MPlayer :).

Andrew

---

### Post by mIXpRo on 2010-11-08
when i try to compile svn 
> cd $HOME/mplayer_build && \
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer && \
cd mplayer && \
./configure --confdir=/etc/mplayer --disable-mencoder --disable-x264 \
            --codecsdir=/usr/local/lib/codecs && \
make && \
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/mplayer_build" \
   --pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "2:1.0~svn$(LC_ALL=C svn info 2> /dev/null | \
     grep Revision | cut -d' ' -f2)" && \
make distclean

i get :

> svn: Working copy 'mplayer' locked
svn: run 'svn cleanup' to remove locks (type 'svn help cleanup' for details)

---

### Post by andrew.46 on 2010-11-08
Hi mixpro,

Try:

```
cd $HOME/mplayer_build/mplayer && svn cleanup .
```

The final dot needs to be there, then run the *update* command:

```

cd $HOME/mplayer_build/mplayer && \
svn up && \
./configure --confdir=/etc/mplayer --disable-mencoder --disable-x264 \
            --codecsdir=/usr/local/lib/codecs && \
make && \
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/mplayer_build" \
   --pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "2:1.0~svn$(LC_ALL=C svn info 2> /dev/null | \
     grep Revision | cut -d' ' -f2)" && \
make distclean

```

Hopefully all will go ahead then.

Andrew

---

### Post by mIXpRo on 2010-11-08
does it suppose to stop like this :
> 
A    debian/mplayer-doc.doc-base.de
A    debian/control
A    debian/mplayer-gui.mime
A    debian/clean
A    debian/mplayer-dbg.links
A    debian/compat
A    debian/mplayer.examples
A    debian/mplayer-doc.doc-base.en
A    debian/rules


 
cause now nothing happens .

---

### Post by mIXpRo on 2010-11-08
suppose it is installed and all went fine ,
what is the command line for streaming mms://XXXXXX.wmv video 
and if it hard with mms protocol these videos can be played with rtsp protocol on

In: UDP on port 5005             
Out: UDP on port 5004             
In/Out : [B]TCP on port 554

[/B]cause i've managed to run these videos with vlc but i had to change the url from mms://XXXXXX.wmv to rtsp://XXXXXX.wmv .

the problem is : i want to be able to speed up the video means play it i.e in 1.x speed 
and this i can't do with vlc .

---

### Post by andrew.46 on 2010-11-08
Hi mIXpRo,

Mind you I cannot actually play [that stream]("mms://video9.technion.ac.il/Courses/Hozek1/Hozek1-9.wmv") on Linux or Windows 7, have you been able to open it?

Andrew

---

### Post by mIXpRo on 2010-11-08
no you can't access that video , it runs only on the technion's (institute of technology of israel ) server  i'm a student there and these are a lectures videos . 
i can play them only with windows media player , but since i "converted" from windows to linux i haven't been able to do so .

except as i mentioned before with vlc , but the problem with this is that i can't play it with the speed i want i.e 1.x playback speed .

---

### Post by andrew.46 on 2010-11-08
Hi mIXpRo,

Difficult to test it then :). In the short term have you considered running Windows in Virtualbox? I attach a screenshot to demonstrate the possibilities...

Andrew

---

### Post by mIXpRo on 2010-11-08
ya that's what i'm doing now , but it's a lot of pressure on the cpu of my laptop , plus it's upsetting to wait the boot time whenever you want to watch a lecture , plus i really hate windows and i want to be able to do everything with my ubuntu .

---

### Post by mc4man on 2010-11-08
> i can't play it with the speed i want i.e 1.x playback speed .
Well the ] key will increase by .1x per touch, [ decrease by .1x, there maybe be other values avail/settable , look in vlc -H
(don't believe you can go finer than 1/10x

Your svn up looked a bit odd - were you updating a svn checkout ala this thread or updating another source that happened to  have a .svn folder

(Andrew - what, if you know, are the various prefixes in a svn up, figure U to be updated, but  A, D ect.

---

### Post by andrew.46 on 2010-11-09
Hi mc4man,

> **mc4man said:**
> Andrew - what, if you know, are the various prefixes in a svn up, figure U to be updated, but  A, D ect.

'A' is the magic one that usually has me scrabbling for the changelogs :). The characters are:

```
    A  Added
    D  Deleted
    U  Updated
    C  Conflict
    G  Merged
    E  Existed
```

A few more details about these codes are included with *svn help update*.

Andrew

---

### Post by s3v3nsins on 2010-11-10
I tried to compile the latest svn release with lirc support.
When i compiled mplayer, it showed

> 
Checking for lirc ... no 
Checking for lircc ... no 


On inspecting the config.log file I get this

> 
============ Checking for lircc ============

#include <lirc/lircc.h>
int main(void) { return 0; }

cc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99  -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--2503/tmp.c -Ilibdvdread4 -I. -Iffmpeg  -D_REENTRANT -I/usr/include/directfb -I/usr/include/     -D_REENTRANT    -I/usr/include/freetype2    -I/usr/include/schroedinger-1.0 -I/usr/include/orc-0.4   -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12    -Wl,-z,noexecstack  -ffast-math   -lncurses -lsmbclient -lpng -lz -ljpeg -lopenjpeg -lungif -lasound -ldl -lpthread -lcdda_interface -lcdda_paranoia -lfreetype -lz -lfontconfig  -lfribidi -lenca -lz -llzo2 -lspeex -lgsm -ltheora -logg   -lmpg123 -ldca -lopencore-amrnb -lopencore-amrwb -lxvidcore -lm -lschroedinger-1.0 -lpthread -lm -lorc-0.4   -lvstream-client -lpthread -ldl -rdynamic  -ldirectfb  -lXext -lX11 -lpthread -lXv -lvdpau -lXinerama -lXxf86vm -lXxf86dga -laa -L/usr/lib -lcaca -lvga -lSDL -lesd   -laudio -lXt -lpulse   -ljack -lopenal -pthread -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lm -lcairo -lpng12 -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0   -lglib-2.0    -o /tmp/mplayer-configure--2503/tmp -llircc
/tmp/mplayer-configure--2503/tmp.c:1: [COLOR="Red"]fatal error: lirc/lircc.h: No such file or directory[/COLOR]
compilation terminated.


Result is: no 


Any ideas as to how I can enable the LIRC support ?

---

### Post by andrew.46 on 2010-11-10
Hi s3v3nsins,

The best way to do this is to add the required -dev file:

```
sudo apt-get install liblircclient-dev
```

and then simply run the ./configure that I have given in the guide, MPlayer should automagically pick up the library and install support. I suspect that you have used the option *--enable-lirc*?

Andrew

---

### Post by s3v3nsins on 2010-11-10
> **andrew.46 said:**
> 

The best way to do this is to add the required -dev file:

```
sudo apt-get install liblircclient-dev
```


Hi Andrew,
Thanks for the pointer, it worked like a charm.
I knew i had to install some dev package but was not sure which one to install.

> **andrew.46 said:**
> 
I suspect that you have used the option *--enable-lirc*?


Yes I had used it, and during make it failed looking for the same file.

---

### Post by andrew.46 on 2010-11-10
Hi s3v3nsins,

> **s3v3nsins said:**
> Thanks for the pointer, it worked like a charm.
I knew i had to install some dev package but was not sure which one to install.

Great news :). I usually don't compile against this library and I am afraid that I know nothing about setting up such a remote control, I would be curious to hear how you go setting your device with MPlayer?

Andrew

---

### Post by s3v3nsins on 2010-11-12
> **andrew.46 said:**
> Hi s3v3nsins,



Great news :). I usually don't compile against this library and I am afraid that I know nothing about setting up such a remote control, I would be curious to hear how you go setting your device with MPlayer?

Andrew

Just give me a day or two to configure the entire thing and I would put in the details.

---

### Post by DrewT on 2010-11-19
Going all the way back to page 1, there are two potential traps for novices like me who are ambitious enough to tackle this, but who already have codecs installed and are not familiar enough with the command line to follow a couple of the variant instructions correctly. 

(1) If you skip the Codecs step (because you already have w32codecs or w64codecs installed), the remaining steps will fail because they won't find the directory that is created at the beginning of the skipped step. Therefore, you must run the first line of that step even if you skip the rest of it:

```
mkdir $HOME/mplayer_build && cd $HOME/mplayer_build

```

(2) In the Compiling mplayer step, if you omit the line beginning "--codecsdir," you must add two ampersands before the backslash at the end of the preceding line; otherwise the compile will stop there. So the line ahead of the omitted line should now look like this:

```
./configure --confdir=/etc/mplayer --disable-mencoder --disable-x264 && \

```

With those tweaks it seemed to work perfectly. Thanks andrew.46!

---

### Post by andrew.46 on 2010-11-19
Hi Drew,

Thanks for pointing that out. I have adjusted the codecs installation so this error will not occur and taken the opportunity to add in another codec that does not feature in the *[I]standard*[/I] codec collection. I hope in the meantime you are enjoying your fresh new cutting edge version of MPlayer :).

Andrew

---

### Post by andrew.46 on 2010-11-27
This guide may very well have a new permanent home soon, I have written it up on my personal website:

How to build the svn MPlayer under Maverick Meerkat
[http://www.andrews-corner.org/mplayer.html](http://www.andrews-corner.org/mplayer.html)

where I will be shifting a few more of my more useful guides over the next few weeks.

Andrew

---

### Post by mc4man on 2010-11-28
> where I will be shifting a few more of my ...
Well then that should prove a very decent site to provide a link to when called for - will keep in mind.

I've come to the conclusion that if i'm going to keep ubuntu on my main media machine that I had to switch the audio to digital out (fairly good 5.1 system).
 While it now has no issue's using pulse for ac3 and dts (pulse set to 5.1 digital output), for stereo streams am not too keen on pulse as configured. (could switch pulse back and forth from 5.1 digital to stereo digital but better to let sleeping dogs lie.

Anyway 2 players seem to have the ability to bypass pulse properly for stereo dig. out - mplayer and audacious. This may lead to a number of mplayer commands depending on the source material. Rather than keep track of or create a bunch of mplayer.desktops was thinking of trying to do thru profiles.

Haven't had a chance to experiment yet, was wondering if profiles added to the conf are 'inactive' unless called by command and can they be ganged together?

---

### Post by SoulSmasher on 2010-12-04
what can I say.. Thanks for the tutorial

---

### Post by andrew.46 on 2010-12-04
Hi SoulSmasher,

Glad to hear it has worked for you :).

Andrew

---

### Post by gillza on 2010-12-28
Andrew.

I have just tried to install mplayer (after not a very successful install of VLC, posted a question in your vlc thread) on a fresh 10.10

when I get to compiling the mplayer itself i get the following: 

```
ffmpeg/libavformat/libavformat.a(avidec.o): In function `avi_read_header':
avidec.c:(.text+0x2888): undefined reference to `ff_get_bmp_header'
ffmpeg/libavformat/libavformat.a(wtv.o): In function `parse_videoinfoheader2':
wtv.c:(.text+0xbe): undefined reference to `ff_get_bmp_header'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

Any ideas on how to solve this? 

P.S. I also encountered the same error when tried to compile mplayer under 10.04 following your guide. I know it might sound dumb but i feel like the installation of VLC had something to do with it.

---

### Post by FakeOutdoorsman on 2010-12-28
I too am getting a similar error on Arch Linux x86_64:
```
ffmpeg/libavformat/libavformat.a(avidec.o): In function `avi_read_header':
avidec.c:(.text+0x1b50): undefined reference to `ff_get_bmp_header'
ffmpeg/libavformat/libavformat.a(wtv.o): In function `parse_media_type':
wtv.c:(.text+0x84a): undefined reference to `ff_get_bmp_header'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
```
I plan on waiting a few days until the MPlayer devs fix it and until then I'll use the repo MPlayer.

---

### Post by gillza on 2010-12-28
Ok I just tried installing it on a different computer and got the same error. No other video player is installed here.



```
ffmpeg/libavformat/libavformat.a(avidec.o): In function `avi_read_header':
avidec.c:(.text+0x2888): undefined reference to `ff_get_bmp_header'
ffmpeg/libavformat/libavformat.a(wtv.o): In function `parse_videoinfoheader2':
wtv.c:(.text+0xbe): undefined reference to `ff_get_bmp_header'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

---

### Post by andrew.46 on 2010-12-29
Hmmm.... I will admit that I do not have any Ubuntu distros installed at the moment, so I guess I have a bit of a nerve posting on the Ubuntu Forums :). However I have the same error under Slackware 13.0:

```

ffmpeg/libavformat/libavformat.a(avidec.o): In function `avi_read_header':
avidec.c:(.text+0x3d25): undefined reference to `ff_get_bmp_header'
ffmpeg/libavformat/libavformat.a(wtv.o): In function `parse_videoinfoheader2':
wtv.c:(.text+0xbe): undefined reference to `ff_get_bmp_header'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

a workaround is to backtrack the FFmpeg version being used and this has worked well on my system. Something like the following:

```

cd $HOME/mplayer_build/mplayer/ffmpeg && \
svn up -r '{'2010-12-20'}' && cd libswscale && \
svn up -r '{'2010-12-20'}' && cd $HOME/mplayer_build/mplayer && \
./configure --confdir=/etc/mplayer --disable-mencoder --disable-x264 \
            --codecsdir=/usr/local/lib/codecs && \
make && \
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/mplayer_build" \
   --pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "2:1.0~svn$(LC_ALL=C svn info 2> /dev/null | \
     grep Revision | cut -d' ' -f2)" && \
make distclean

```

Andrew

---

### Post by mc4man on 2010-12-29
> Ok I just tried installing it on a different computer and got the same error.
You'll need to wait it out, try later or tomorrow

On a side note:
The rvm smplayer ppa, due to time constraints, ect. is a bit old. If one wanted to ck. or use the latest smplayer in ubuntu this should still work fine. (maybe there's other ppa's, don't know

Fill the build-deps if any
sudo apt-get build-dep smplayer

Then create a build folder, cd to it and 
```
svn co https://smplayer.svn.sourceforge.net/svnroot/smplayer/smplayer/trunk smplayer

```
Then simply
```
cd smplayer && ./create_deb.sh
```
(tested on 11.04

---

### Post by pedja_portugalac on 2010-12-29
> **andrew.46 said:**
> Hmmm.... I will admit that I do not have any Ubuntu distros installed at the moment, so I guess I have a bit of a nerve posting on the Ubuntu Forums :). However I have the same error under Slackware 13.0:

```

ffmpeg/libavformat/libavformat.a(avidec.o): In function `avi_read_header':
avidec.c:(.text+0x3d25): undefined reference to `ff_get_bmp_header'
ffmpeg/libavformat/libavformat.a(wtv.o): In function `parse_videoinfoheader2':
wtv.c:(.text+0xbe): undefined reference to `ff_get_bmp_header'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

a workaround is to backtrack the FFmpeg version being used and this has worked well on my system. Something like the following:

```

cd $HOME/mplayer_build/mplayer/ffmpeg && \
svn up -r '{'2010-12-20'}' && cd libswscale && \
svn up -r '{'2010-12-20'}' && cd $HOME/mplayer_build/mplayer && \
./configure --confdir=/etc/mplayer --disable-mencoder --disable-x264 \
            --codecsdir=/usr/local/lib/codecs && \
make && \
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/mplayer_build" \
   --pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "2:1.0~svn$(LC_ALL=C svn info 2> /dev/null | \
     grep Revision | cut -d' ' -f2)" && \
make distclean

```

Andrew

It solve compiling problem. Thank you Andrew. Two days ago I've compiled without backtracking FFmpeg version but tonight it just don't work. Anyway backtracking FFmpeg version solved the problem. Thanks again and wish you Very, Very Happy New Year Friend. ):P

---

### Post by andrew.46 on 2010-12-30
Hi pedja,

> **pedja_portugalac said:**
> It solve compiling problem. Thank you Andrew. Two days ago I've compiled without backtracking FFmpeg version but tonight it just don't work. Anyway backtracking FFmpeg version solved the problem. Thanks again and wish you Very, Very Happy New Year Friend. ):P

Glad to hear this has worked :). I am reluctant to query the MPlayer developers as I suspect most are enjoying their holidays..... And of course all the best to you for the New Year !!!

Andrew

---

### Post by HaboMaster on 2010-12-30
Thank you for the excellent guide. I tried this last night but it wouldn't compile. This morning it was the same, but I just noticed they updated two files so I tried to compile again and it ran without problems.

---

### Post by mc4man on 2010-12-30
> they updated two files so I tried to compile again and it ran without problems.
Sometimes an update to mplayer resolves, other times it's one to the checked out ffmpeg lib's in the mplayer source.

You can access the changes to mplayer,or by cd'ing to the ffmpeg folder it's changes with (blue is adjustable
svn log --limit [COLOR="Blue"]10[/COLOR]

One of andrew's excellent 'starter' guides
[http://ubuntuforums.org/showthread.php?t=1167578&page=2](http://ubuntuforums.org/showthread.php?t=1167578&page=2)

---

### Post by andrew.46 on 2010-12-30
Looks like the lights are still on at MPlayer so I have mentioned the compilation failure on [the mailing list]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2010-December/081749.html"). Hopefully some resolution soon...

Andrew

---

### Post by andrew.46 on 2011-01-01
Good news, the [FFmpeg change]("http://git.ffmpeg.org/?p=ffmpeg;a=commit;h=92b76b9773228bc9565ab13e6ccc7d99873b330c") has been incorporated into the MPlayer tree and compilation should now succeed :).

Andrew

---

### Post by andrew.46 on 2011-01-22
Looks like at least temporarily MPlayer will not be drawing in the FFmpeg tree due to some changes at the FFmpeg end. Some interesting changes ahead...

---

### Post by Jive Turkey on 2011-01-30
> **andrew.46 said:**
> Hi Cypress,



It does not help MPlayer itself to compile against x264 as *playback* does not depend on this. It is only useful if you wish to build and utilise MEncoder, in which case you will need to omit these option: *--disable-mencoder --disable-x264* and perhaps also add in the -dev files for libmp3lame and faac. Have you built x264 for FFmpeg? I would not personally build MEncoder if you are running the svn FFmpeg but it is up to you :).

Andrew

Thanks for the awesome guide (with each release of ubuntu)!
I do plan to use mencoder a bit here and there. I'm curious what your rationale for avoiding the SVN builds for mencoder/ffmpeg is.

---

### Post by andrew.46 on 2011-01-31
> **Jive Turkey said:**
> I do plan to use mencoder a bit here and there. I'm curious what your rationale for avoiding the SVN builds for mencoder/ffmpeg is.

MEncoder is not really maintained any more, it has not been for quite some time, and in my experience far better results can be had with either x264 alone or FFmpeg + x264. Have I given the impression that I avoid the git FFmpeg? I am actually a huge fan...

BTW I have added a git client into the guide so FFmpeg can be downloaded with the new arrangements, plus removed libmpcdec as support for this has been dropped.

---

### Post by andrew.46 on 2011-02-05
New codec pack has been released for 32bit users, I have added in details on the guide. Quite a bit bigger than the old one, looks like downloading these manually rather than depending on Medibuntu has finally paid off :).

---

### Post by MrGrumpyArse on 2011-02-07
Hi, firstly a big thank you for this and previous guides.

However I have Just completed the installation of mplayer/smplayer from this guide (albeit on Lucid 64 bit) with the addition of mencoder (as I use devede occasionally) following the info kindly added by Linuxforall on page 4, after first completing FakeOutdoorsman's guide for FFmpeg / X264 . 

Everything appears fine on the mplayer/smplayer side of things, but I now find when I try to create a dvd using DeVeDe (and presumably mencoder) that the .iso image created has no sound when played back on my pc or indeed if the preview option is used within DeVeDe prior to creating the .iso .    

Has anyone else had this problem or could anyone possibly suggest a cure?

I ran a command I found earlier in this guide in case the output is relevant.
```
mark@mdsubuntulucid:~$ mencoder -ovc help
MEncoder SVN-r32867-4.4.3 (C) 2000-2011 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   xvid     - XviD encoding
   x264     - H.264 encoding

mark@mdsubuntulucid:~$ mencoder -oac help
MEncoder SVN-r32867-4.4.3 (C) 2000-2011 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding (useful for AC3)
   pcm      - uncompressed PCM audio
   mp3lame  - cbr/abr/vbr MP3 using libmp3lame
   lavc     - FFmpeg audio encoder (MP2, AC3, ...)
   faac     - FAAC AAC audio encoder

```

MPlayer SVN-r32867-4.4.3 

Thanks in advance for any advice 

MrGrumpyArse

---

### Post by MrGrumpyArse on 2011-02-07
A little bit more info,

It appears if I try to convert a file which already has ac3 audio with DeVeDe, and I select the relevant box within DeVeDe to say the audio doesn't need to be re-encoded then the resulting  .iso is created complete with audio.

Below is the "adjusted code" I used when compiling mplayer, maybe I made a mistake here?

```
cd $HOME/mplayer_build && \
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer && \
cd mplayer && \
./configure --confdir=/etc/mplayer \
--codecsdir=/usr/local/lib/codecs && \
make -j4 && \
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
   --pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`" --provides "mplayer,mencoder"
make distclean
``` 

I have removed mplayer and repeated the tutorial (to the best of my limited ability) and have the same result...

Interestingly when I look in synaptic it shows mplayer but not mencoder?

 

Cheers

MrGrumpyArse

---

### Post by andrew.46 on 2011-02-08
Hi Grumpy,

Cannot help with this one I'm afraid, I have really looked at DeVeDe, apologies :(.

Andrew

---

### Post by mc4man on 2011-02-12
A bit of disappointment here w/ mplayer performance on 11.04 on the limited hardware sample available here
(whether this is hardware related or not obviously can't tell yet, though many times in linux it is all about the hardware.

Anyway, at least here, mplayer has developed video tearing while using ubuntu's version of compiz-0.9.X (0.9.2.1+glibmainloop
When switching to metacity there is no tearing at all, both machines are also fine in 10.10 w/ compiz-0.8.X

I'm fairly sure earlier versions of the glibmainloop compiz were fine, not so now.

If anyone can suggest a distro currently using compiz-0.9.X that I could do a quick, easy install of I'd like to do a compare. (if it booted from grub2 that would be good though not necessary

---

### Post by andrew.46 on 2011-02-13
> **mc4man said:**
> A bit of disappointment here w/ mplayer performance on 11.04 on the limited hardware sample available here

This is with the svn MPlayer? I can be little help I am afraid, I run on VMs and I am waiting for the beta of 11.04 :(.

---

### Post by mc4man on 2011-02-14
As it turned out the issue w/ mplayer was with the nouveau 3d drivers. Atm in natty if one wanted to test fully up to date then nouveau is the only way with nvidia.
When using only the 2d nouveau mplayer is ok, enabling 3d causes the tearing.
At the end of the day have no intention of ever using nouveau any way, find it hard to trust reverse engineered drivers for a key piece of hardware, particularly on a laptop where a video adapter replacement is not a trivial matter.

---

### Post by jwcalla on 2011-02-16
Does anyone have any good news with regard to merging the MKV ordered chapters and multithreaded decoding support into the main FFmpeg branch?  As it is now we're kind of left with separate development branches and have to compile mplayer on our own here rather than hooking into something amazing like Synaptic to get our updates automatically.

Just look at how much love CCCP gets from Windows users.  Doesn't FFmpeg want to be loved? :-k

---

### Post by andrew.46 on 2011-02-17
I believe that with the rise of PPAs such guides as this are approaching dodo status for the Ubuntu Forums. Always possible to build your own MPlayer in this way, and I will personally continue to do so, but the advent of PPA's such as this one:

Packages in &#8220;MPlayer Daily Builds&#8221;
[https://launchpad.net/~motumedia/+archive/mplayer-daily/+packages](https://launchpad.net/~motumedia/+archive/mplayer-daily/+packages)

put together by one of the MPlayer developers show the way that most Ubuntu users will go. Details are given on the MPlayer site:

> 
As a special service for Ubuntu users, the mplayer project now provides packages for various versions of Ubuntu. The packages are built twice a week from SVN trunk and run independently of your system libraries. 


Thanks for the great time on the Forums with building MPlayer for so many releases of Ubuntu over the last few years, I have enjoyed it immensely and learned a huge amount in the process.

All the best,

Andrew

---

### Post by stupid_for_a_file on 2011-02-27
dear all,

i have followed the instructions, and i would like to thank for the effort, as i got vdpau working on my thinkpad with nvidia gpu.

then i faced another problem i could not solve so far: it looks like for me this setup "hardcodes" he vdpau output, and i get flickering full-screen playback of normal low-res divx and mpeg playback.

when i change the output to xv in smplayer, all works fine for those videos. i also tried to supply the -vo xv argument just for these file types, but it says "error parsing...", i guess because the same option is already there by smplayer itself.

this is a stock maverick install, with the nvidia driver simply activated.

please let me know, if there is anything i can do to use smplayer for both worlds. thanks in advance.

---

### Post by mc4man on 2011-02-27
> is there is anything i can do to use smplayer for both worlds.
Not exactly sure, don't use smplayer much. Maybe you could make use of a profile.
For example here _all_ the .avi's I have are better w/ xv than vdpau. So in that case I can use a simple extension profile for mplayer in ~/.mplayer/config 
Ex.
```
[extension.avi]
profile-desc="profile for .avi files"
vo=xv

```
gnome-mplayer (which is basically a profile itself), will also use that profile automatically, smplayer it appears won't

So maybe put a profile that suits/works for you at the end of ~/.config/smplayer/smplayer.ini and see what happens
As a test put the above profile in there, smplayer now does use xv for .avi's and vdpau for the rest (vdpau is set as default in smplayer's options

Maybe a better way, as mentioned not proficient at all with smplayer

---

### Post by typos1 on 2011-03-22
I recently un-installed smplayer, as it would not play video-the video window was a clear window that you could see right through. To re-install it what do I code exactly to get the most up to date version ? Should I just go through this thread and code every code thats been suggested ?

---

### Post by andrew.46 on 2011-03-23
> **typos1 said:**
> I recently un-installed smplayer, as it would not play video-the video window was a clear window that you could see right through. To re-install it what do I code exactly to get the most up to date version ? Should I just go through this thread and code every code thats been suggested ?

This guide is in truth more aimed at MPlayer than SMPlayer I will have to admit :). But certainly to get the most recent *MPlayer* you will need to follow all the steps of the guide itself, SMPlayer for the purposes of Maverick Meerkat is drawn from the Ubuntu Repository.

Andrew

---

### Post by typos1 on 2011-03-23
Well, I installed it when you started this thread and used the sm player gui cos you recommended it, a few days ago smplayer stopped displaying video (theres just an empty window where the video should be, you can see through it to the desktop or other apps) and it ll play audio but whenever its started its switched to a very low level in pulse audio volume control.

I ve reinstalled it using the beginning of this thread but the problem is still there.

Any ideas why it could be happening?

And should I go through the whole thread and follow every code that has been suggested since it started to make sure its all up to date, I ve used smplayer since the thread started (and removed all other media players), its been great (til now), but I havent read or coded anything thats been posted since I first installed it-could this be the prob?

I thought SMplayer was just a front end and still used ther same repos and basic programme as mplayer ?

Thanks

Edit-just read a few threads up about daily mplayer builds, if I do it this way will I still be able to play all of the formats that I could when I used your build ?

---

### Post by beew on 2011-03-23
> **andrew.46 said:**
> I believe that with the rise of PPAs such guides as this are approaching dodo status for the Ubuntu Forums. Always possible to build your own MPlayer in this way, and I will personally continue to do so, but the advent of PPA's such as this one:

Packages in “MPlayer Daily Builds”
[https://launchpad.net/~motumedia/+archive/mplayer-daily/+packages]("https://launchpad.net/%7Emotumedia/+archive/mplayer-daily/+packages")

put together by one of the MPlayer developers show the way that most Ubuntu users will go. Details are given on the MPlayer site:


Hi, is this version of mplayer multithreaded?

Well with ppas we don't have to build mplayer ourselves, but it is still fun to and it is a good learning process. Thanks for the guide. I have bookmarked it and will work on it once I have the time.

Cheers.

---

### Post by andrew.46 on 2011-03-23
> **beew said:**
> Hi, is this version of mplayer multithreaded?

Well, FFmpeg-mt has been [merged into the videolan FFmpeg code]("http://ffmpeg.org/pipermail/ffmpeg-devel/2011-March/109906.html") and subsequently passed into MPlayer so I guess so :). I have not experimented much with it yet, I guess the magic commandline should be:

```
mplayer -lavdopts threads=N <filename>
```

where N is the number of threads and <filename> of course is the actual filename. I would be interested to hear from FFmpeg-mt fans on results found or not found in MPlayer?


> Well with ppas we don't have to build mplayer ourselves, but it is still fun to and it is a good learning process. Thanks for the guide. I have bookmarked it and will work on it once I have the time.

I am not so keen on PPAs I will have to admit but I know that this personal prejudice of mine is contrary to the direction that Ubuntu is going :(.

Andrew

---

### Post by andrew.46 on 2011-03-23
> **typos1 said:**
> Well, I installed it when you started this thread and used the sm player gui cos you recommended it, a few days ago smplayer stopped displaying video (theres just an empty window where the video should be, you can see through it to the desktop or other apps) and it ll play audio but whenever its started its switched to a very low level in pulse audio volume control.

I ve reinstalled it using the beginning of this thread but the problem is still there.

Any ideas why it could be happening?

Possibly this might not be an actual MPlayer / SMPlayer problem, I would suggest experimenting with both the video out and audio out settings.


> And should I go through the whole thread and follow every code that has been suggested since it started to make sure its all up to date, I ve used smplayer since the thread started (and removed all other media players), its been great (til now), but I havent read or coded anything thats been posted since I first installed it-could this be the prob?

This should not be really necessary, I tend to absorb the better suggestions into the guide itself.


> Edit-just read a few threads up about daily mplayer builds, if I do it this way will I still be able to play all of the formats that I could when I used your build ?

I have not used this PPA myself but the man who put it together is both an MPLayer developer and I believe a debian packager, plus from his posts seems like one of the good guys :). If I used PPAs at all I would probably give this one a go...

Andrew

---

### Post by typos1 on 2011-03-23
Thanks but I dont know what you mean by video/audio out settings-where are they? What are they?

I ve added those repositories to software sources in a terminal, but it says smplayer is already the latest version and it still doesnt work !

---

### Post by andrew.46 on 2011-03-23
> **typos1 said:**
> Thanks but I dont know what you mean by video/audio out settings-where are they? 

For SMPlayer these settings can be found from *Options --> Preferences --> General --> Video --> Output Driver* and *Options --> Preferences --> General --> Audio --> Output Driver*. I have added a couple of screenshots to demonstrate.

---

### Post by typos1 on 2011-03-23
Lol, I see-thought they were some settings in ubuntu I didnt know about !

Checked-video is set to xv and audio is set to pulse, so I know audio is set right, still cant get video to work, its very strange that it suddenly ahppened after 6 months, I did uninstall xine, wondered whether m/smplayer uses something from that, but reinstalled it and still nothing.

---

### Post by andrew.46 on 2011-03-23
> **typos1 said:**
> Checked-video is set to xv and audio is set to pulse, so I know audio is set right, still cant get video to work..

Perhaps experiment a little with the video setting, X11 is a safe choice for example.

Andrew

---

### Post by typos1 on 2011-03-23
Right, well I ve tried them all, they either give the same results-ie a blank window, no window at all like its playing music, or fullscreen opaque video (can see video AND behind smplayer) or it freezes and doesnt respond, except x11slow (the only x11 I ve got) which plays, but with slow video that doesnt keep up with the dialogue.

---

### Post by beew on 2011-03-24
> **andrew.46 said:**
> Well, FFmpeg-mt has been [merged into the videolan FFmpeg code]("http://ffmpeg.org/pipermail/ffmpeg-devel/2011-March/109906.html") and subsequently passed into MPlayer so I guess so :). 

Wow, seems it has happened only 2 days ago. Does it mean that medial players that use ffmpeg such as VLC are all going to be multithreaded now?

---

### Post by andrew.46 on 2011-03-24
> **typos1 said:**
> Right, well I ve tried them all, they either give the same results...

Have you tried playing your files from the commandline as follows:

```
mplayer -v *[COLOR="Red"]my_file[/COLOR]*
```

with my_file changed to reflect the actual filename. Could you post the full terminal output here? If there are no clues here I am afraid I am not entirely sure what the problem is :(.

Andrew

---

### Post by typos1 on 2011-03-24
This is the output-did I do it right or should I have specified a path to the file ?

jason@jason-desktop:~$ mplayer -v sea horses.flv
MPlayer SVN-r33094-4.4.5 (C) 2000-2011 MPlayer Team
CPU vendor name: AuthenticAMD  max cpuid level: 1
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 75, Stepping: 2)
extended cpuid-level: 24
extended cache-info: 33587520
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNowExt: 1 SSE: 1 SSE2: 1 SSSE3: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowExt SSE SSE2 CMOV
get_path('codecs.conf') -> '/home/jason/.mplayer/codecs.conf'
Reading /home/jason/.mplayer/codecs.conf: Can't open '/home/jason/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/jason/.mplayer/fonts'
Configuration: --confdir=/etc/mplayer --disable-mencoder --disable-x264 --codecsdir=/usr/local/lib/codecs
CommandLine: '-v' 'sea' 'horses.flv'
Using nanosleep() timing
get_path('input.conf') -> '/home/jason/.mplayer/input.conf'
Can't open input config file /home/jason/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
get_path('sea.conf') -> '/home/jason/.mplayer/sea.conf'

Playing sea.
get_path('sub/') -> '/home/jason/.mplayer/sub/'
File not found: 'sea'
Failed to open sea.

get_path('horses.flv.conf') -> '/home/jason/.mplayer/horses.flv.conf'

Playing horses.flv.
get_path('sub/') -> '/home/jason/.mplayer/sub/'
File not found: 'horses.flv'
Failed to open horses.flv.

vo: x11 uninit called but X11 not initialized..

Exiting... (End of file)
jason@jason-desktop:~$

---

### Post by andrew.46 on 2011-03-24
> **typos1 said:**
> This is the output-did I do it right or should I have specified a path to the file ?

```
jason@jason-desktop:~$ mplayer -v sea horses.flv
```



Yes you will need the correct path and also enclose the filename **[COLOR="Red"]'[/COLOR]**sea horses.flv**[COLOR="Red"]'[/COLOR]** as you have a space in there.

Andrew

---

### Post by typos1 on 2011-03-24
Ok, is this right ? It seems to be saying it hasnt got the codecs.

jason@jason-desktop:~$ jason@jason-desktop:~$ mplayer -v jason/Desktop/"sea horses.flv"
jason@jason-desktop:~$: command not found
jason@jason-desktop:~$ mplayer -v /jason/Desktop/'sea horses.flv'
MPlayer SVN-r33094-4.4.5 (C) 2000-2011 MPlayer Team
CPU vendor name: AuthenticAMD  max cpuid level: 1
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 75, Stepping: 2)
extended cpuid-level: 24
extended cache-info: 33587520
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNowExt: 1 SSE: 1 SSE2: 1 SSSE3: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowExt SSE SSE2 CMOV
get_path('codecs.conf') -> '/home/jason/.mplayer/codecs.conf'
Reading /home/jason/.mplayer/codecs.conf: Can't open '/home/jason/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/jason/.mplayer/fonts'
Configuration: --confdir=/etc/mplayer --disable-mencoder --disable-x264 --codecsdir=/usr/local/lib/codecs
CommandLine: '-v' '/jason/Desktop/sea horses.flv'
Using nanosleep() timing
get_path('input.conf') -> '/home/jason/.mplayer/input.conf'
Can't open input config file /home/jason/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
get_path('sea horses.flv.conf') -> '/home/jason/.mplayer/sea horses.flv.conf'

Playing /jason/Desktop/sea horses.flv.
get_path('sub/') -> '/home/jason/.mplayer/sub/'
File not found: '/jason/Desktop/sea horses.flv'
Failed to open /jason/Desktop/sea horses.flv.

vo: x11 uninit called but X11 not initialized..

Exiting... (End of file)
jason@jason-desktop:~$

---

### Post by andrew.46 on 2011-03-24
> **typos1 said:**
> Ok, is this right ? It seems to be saying it hasnt got the codecs.
```

jason@jason-desktop:~$ jason@jason-desktop:~$ mplayer -v jason/Desktop/"sea horses.flv"
jason@jason-desktop:~$: command not found
```


Almost :). If your file is on the Desktop this command should open it:

```
mplayer -v "$HOME/Desktop/sea horses.flv"
```

Andrew

---

### Post by andrew.46 on 2011-03-24
> **beew said:**
> Wow, seems it has happened only 2 days ago. Does it mean that medial players that use ffmpeg such as VLC are all going to be multithreaded now?

Interesting question and I confess I am not sure :). I have built both vlc [1.1.8 and vlc-git]("http://ubuntuforums.org/showpost.php?p=10595365&postcount=258") from source against the newest FFmpeg and I am at a bit of a loss as to how one can demonstrate FFmpeg-mt in action. (The linked guide actually compiles against an older FFmpeg but in this case I built against the newest system FFmpeg).

---

### Post by typos1 on 2011-03-24
Ah, right, thank:

jason@jason-desktop:~$ mplayer -v "$HOME/Desktop/sea horses.flv"
MPlayer SVN-r33094-4.4.5 (C) 2000-2011 MPlayer Team
CPU vendor name: AuthenticAMD  max cpuid level: 1
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 75, Stepping: 2)
extended cpuid-level: 24
extended cache-info: 33587520
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNowExt: 1 SSE: 1 SSE2: 1 SSSE3: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowExt SSE SSE2 CMOV
get_path('codecs.conf') -> '/home/jason/.mplayer/codecs.conf'
Reading /home/jason/.mplayer/codecs.conf: Can't open '/home/jason/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/jason/.mplayer/fonts'
Configuration: --confdir=/etc/mplayer --disable-mencoder --disable-x264 --codecsdir=/usr/local/lib/codecs
CommandLine: '-v' '/home/jason/Desktop/sea horses.flv'
Using nanosleep() timing
get_path('input.conf') -> '/home/jason/.mplayer/input.conf'
Can't open input config file /home/jason/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
get_path('sea horses.flv.conf') -> '/home/jason/.mplayer/sea horses.flv.conf'

Playing /home/jason/Desktop/sea horses.flv.
get_path('sub/') -> '/home/jason/.mplayer/sub/'
File not found: '/home/jason/Desktop/sea horses.flv'
Failed to open /home/jason/Desktop/sea horses.flv.

vo: x11 uninit called but X11 not initialized..

Exiting... (End of file)
jason@jason-desktop:~$

---

### Post by andrew.46 on 2011-03-24
Hmmm....

```
File not found: '/home/jason/Desktop/sea horses.flv'
```

This file not on your Desktop? Perhaps try the following:

```
find $HOME -iname 'sea horses.flv'
```

or so we can find any sample to test:

```
find $HOME -iname '*.flv'
```


Andrew

---

### Post by typos1 on 2011-03-24
Soz, I moved it earlier and forgot ! doh !

You still want the output- its quite long? 

It plays but at v low res and controls are not visible even with left or right click

---

### Post by andrew.46 on 2011-03-24
> **typos1 said:**
> You still want the output- its quite long? 

Sure, it does not eat up my disk space :).

> It plays but at v low res and controls are not visible even with left or right click

Basic controls can be seen by running mplayer with no options:


```

andrew@skamandros~$ mplayer
MPlayer SVN-r33097-4.5.2 (C) 2000-2011 MPlayer Team
Usage:   mplayer [options] [url|path/]filename

Basic options: (complete list in the man page)
 -vo <drv>        select video output driver ('-vo help' for a list)
 -ao <drv>        select audio output driver ('-ao help' for a list)
 vcd://<trackno>  play (S)VCD (Super Video CD) track (raw device, no mount)
 dvd://<titleno>  play DVD title from device instead of plain file
 -alang/-slang    select DVD audio/subtitle language (by 2-char country code)
 -ss <position>   seek to given (seconds or hh:mm:ss) position
 -nosound         do not play sound
 -fs              fullscreen playback (or -vm, -zoom, details in the man page)
 -x <x> -y <y>    set display resolution (for use with -vm or -zoom)
 -sub <file>      specify subtitle file to use (also see -subfps, -subdelay)
 -playlist <file> specify playlist file
 -vid x -aid y    select video (x) and audio (y) stream to play
 -fps x -srate y  change video (x fps) and audio (y Hz) rate
 -pp <quality>    enable postprocessing filter (details in the man page)
 -framedrop       enable frame dropping (for slow machines)

Basic keys: (complete list in the man page, also check input.conf)
 <-  or  ->       seek backward/forward 10 seconds
 down or up       seek backward/forward  1 minute
 pgdown or pgup   seek backward/forward 10 minutes
 < or >           step backward/forward in playlist
 p or SPACE       pause movie (press any key to continue)
 q or ESC         stop playing and quit program
 + or -           adjust audio delay by +/- 0.1 second
 o                cycle OSD mode:  none / seekbar / seekbar + timer
 * or /           increase or decrease PCM volume
 x or z           adjust subtitle delay by +/- 0.1 second
 r or t           adjust subtitle position up/down, also see -vf expand

 * * * SEE THE MAN PAGE FOR DETAILS, FURTHER (ADVANCED) OPTIONS AND KEYS * * *

```

Andrew

---

### Post by typos1 on 2011-03-24
Ok:

jason@jason-desktop:~$ mplayer -v "$HOME/Desktop/sea horses.flv"
MPlayer SVN-r33094-4.4.5 (C) 2000-2011 MPlayer Team
CPU vendor name: AuthenticAMD  max cpuid level: 1
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 75, Stepping: 2)
extended cpuid-level: 24
extended cache-info: 33587520
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNowExt: 1 SSE: 1 SSE2: 1 SSSE3: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowExt SSE SSE2 CMOV
get_path('codecs.conf') -> '/home/jason/.mplayer/codecs.conf'
Reading /home/jason/.mplayer/codecs.conf: Can't open '/home/jason/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/jason/.mplayer/fonts'
Configuration: --confdir=/etc/mplayer --disable-mencoder --disable-x264 --codecsdir=/usr/local/lib/codecs
CommandLine: '-v' '/home/jason/Desktop/sea horses.flv'
Using nanosleep() timing
get_path('input.conf') -> '/home/jason/.mplayer/input.conf'
Can't open input config file /home/jason/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
get_path('sea horses.flv.conf') -> '/home/jason/.mplayer/sea horses.flv.conf'

Playing /home/jason/Desktop/sea horses.flv.
get_path('sub/') -> '/home/jason/.mplayer/sub/'
[file] File size is 18077184 bytes
STREAM: [file] /home/jason/Desktop/sea horses.flv
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: FLV format
libavformat file format detected.
[flv @ 0x35db260] Estimating duration from bitrate, this may be inaccurate
==> Found video stream: 0
======= VIDEO Format ======
  biSize 40
  biWidth 320
  biHeight 240
  biPlanes 0
  biBitCount 0
  biCompression 827739206='FLV1'
  biSizeImage 0
===========================
[lavf] stream 0: video (flv), -vid 0
==> Found audio stream: 1
======= WAVE Format =======
Format Tag: 85 (0x55)
Channels: 1
Samplerate: 22050
avg byte/sec: 8231
Block align: 1
bits/sample: 16
cbSize: 0
==========================================================================
[lavf] stream 1: audio (mp3), -aid 0
LAVF: 1 audio and 1 video streams found
LAVF: build 3434240
VIDEO:  [FLV1]  320x240  0bpp  12.000 fps  247.6 kbps (30.2 kbyte/s)
[V] filefmt:44  fourcc:0x31564C46  size:320x240  fps:12.000  ftime:=0.0833
Clip info:
 duration: 463
 starttime: 0
 totalduration: 463
 width: 320
 height: 240
 videodatarate: 242
 audiodatarate: 64
 totaldatarate: 312
 framerate: 12
 bytelength: 18077184
 canseekontime: true
 sourcedata: B4A7D0483HH
 purl: 
 pmsg: 
Load subtitles in /home/jason/Desktop/
get_path('sub/') -> '/home/jason/.mplayer/sub/'
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1680x1050 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
INFO: libavcodec init OK!
Selected video codec: [ffflv] vfm: ffmpeg (FFmpeg Flash video)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
dec_audio: Allocating 4608 + 65536 = 70144 bytes for output buffer.
mp3lib: using SSE optimized decore!
MP3lib: init layer2&3 finished, tables done
MPEG 2.0, Layer III, 22050 Hz 64 kbit Single-Channel, BPF: 208
Channels: 1, copyright: No, original: Yes, CRC: No, emphasis: 0
AUDIO: 22050 Hz, 2 ch, s16le, 64.0 kbit/9.07% (ratio: 8000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Building audio filter chain for 22050Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 22050Hz/2ch/s16le
[dummy] Was reinitialized: 22050Hz/2ch/s16le
Trying preferred audio driver 'pulse', options '[none]'
AO: [pulse] 22050Hz 2ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 22050Hz/2ch/s16le -> 22050Hz/2ch/s16le...
[dummy] Was reinitialized: 22050Hz/2ch/s16le
[dummy] Was reinitialized: 22050Hz/2ch/s16le
Starting playback...
Increasing filtered audio buffer size from 0 to 24064
[ffmpeg] aspect_ratio: 0.000000
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO Config (320x240->320x240,flags=0,'MPlayer',0x32315659)
VO: [vdpau] 320x240 => 320x240 Planar YV12 
VO: Description: VDPAU with X11
VO: Author: Rajib Mahapatra <rmahapatra@nvidia.com> and others
[vdpau] Updating CSC matrix for BT.601
*** [vo] Allocating mp_image_t, 320x240x12bpp YUV planar, 115200 bytes
Unicode font: 5103 glyphs.
Unicode font: 5103 glyphs.
A:   0.2 V:   0.0 A-V:  0.245 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 
Increasing filtered audio buffer size from 24064 to 24096
*** [vo] Allocating mp_image_t, 320x240x12bpp YUV planar, 115200 bytes
A:   4.7 V:   4.8 A-V: -0.001 ct: -0.000   0/  0  4%  3%  0.3% 1 0 
No bind found for key 'MOUSE_BTN2'.                         
A:   7.4 V:   7.4 A-V:  0.000 ct: -0.000   0/  0  3%  2%  0.3% 1 0 
No bind found for key 'MOUSE_BTN2'.                         
A:  17.6 V:  17.6 A-V: -0.000 ct:  0.000   0/  0  1%  1%  0.3% 1 0 
No bind found for key 'MOUSE_BTN0'.-MOUSE_BTN0_DBL                         
A:  17.7 V:  17.8 A-V: -0.000 ct:  0.000   0/  0  1%  1%  0.3% 1 0 
No bind found for key 'MOUSE_BTN0_DBL'.                         
A:  19.2 V:  19.2 A-V: -0.000 ct: -0.000   0/  0  1%  1%  0.4% 1 0 
No bind found for key 'MOUSE_BTN2'.                         
A:  20.0 V:  20.0 A-V:  0.000 ct:  0.000   0/  0  1%  1%  0.4% 1 0 
No bind found for key 'MOUSE_BTN2'.                         
A:  44.5 V:  44.5 A-V:  0.028 ct:  0.002   0/  0  1%  1%  0.4% 1 0 
Unicode font: 5103 glyphs.
Unicode font: 5103 glyphs.
A:  47.3 V:  47.3 A-V: -0.001 ct:  0.001   0/  0  1%  1%  0.4% 1 0 
Unicode font: 5103 glyphs.
Unicode font: 5103 glyphs.
A:  49.3 V:  49.3 A-V: -0.000 ct:  0.000   0/  0  1%  1%  0.4% 1 0 
No bind found for key 'MOUSE_BTN2'.                         
A: 463.1 V: 463.1 A-V:  0.001 ct:  0.000   0/  0  1%  1%  0.4% 1 0 
ds_fill_buffer: EOF reached (stream: audio)  
A: 463.2 V: 463.2 A-V:  0.000 ct:  0.000   0/  0  1%  1%  0.4% 1 0 
ds_fill_buffer: EOF reached (stream: audio)  
A: 463.3 V: 463.2 A-V:  0.000 ct:  0.000   0/  0  1%  1%  0.4% 1 0 
ds_fill_buffer: EOF reached (stream: audio)  
ds_fill_buffer: EOF reached (stream: video)  
A: 463.3 V: 463.2 A-V:  0.001 ct:  0.000   0/  0  1%  1%  0.4% 1 0 
EOF code: 1  

Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: mp3lib
Uninit video: ffmpeg
vo: uninit ...

Exiting... (End of file)
jason@jason-desktop:~$ 

Accessing controls in a terminal isnt very practical though!

---

### Post by andrew.46 on 2011-03-24
Hmmmm.... what happens when you run:

```
mplayer -vo xv -fs "$HOME/Desktop/sea horses.flv"
```

Andrew

---

### Post by mc4man on 2011-03-24
Don't know if it's anything to do w/ the previous, more in general
If ones setup is vdpau capable then mplayer will always default to a vo of vdpau
So that's something to take into consideration depending on if and when you want a vo of vdpau to be used or not
( here I leave a vo of vdpau enabled w/ an appropriate vc list in ~/,mplayer/config but set up some profiles based on .ext to use a vo of xv instead where xv is  better suited

( while I've paid no mind to the whole ffmpeg vx libav deal it looks like ubuntu will be using libav for the time being

---

### Post by typos1 on 2011-03-25
> **andrew.46 said:**
> Hmmmm.... what happens when you run:

```
mplayer -vo xv -fs "$HOME/Desktop/sea horses.flv"
```Andrew
 
This:

jason@jason-desktop:~$ mplayer -vo xv -fs "$HOME/Desktop/sea horses.flv"
MPlayer SVN-r33094-4.4.5 (C) 2000-2011 MPlayer Team

Playing /home/jason/Desktop/sea horses.flv.
libavformat file format detected.
[flv @ 0x26db360] Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: video (flv), -vid 0
[lavf] stream 1: audio (mp3), -aid 0
VIDEO:  [FLV1]  320x240  0bpp  12.000 fps  247.6 kbps (30.2 kbyte/s)
Clip info:
 duration: 463
 starttime: 0
 totalduration: 463
 width: 320
 height: 240
 videodatarate: 242
 audiodatarate: 64
 totaldatarate: 312
 framerate: 12
 bytelength: 18077184
 canseekontime: true
 sourcedata: B4A7D0483HH
 purl: 
 pmsg: 
Load subtitles in /home/jason/Desktop/
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffflv] vfm: ffmpeg (FFmpeg Flash video)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 64.0 kbit/9.07% (ratio: 8000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 22050Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 320x240 => 320x240 Planar YV12  [fs]
A: 463.3 V: 463.2 A-V:  0.001 ct:  0.000   0/  0  0%  0%  0.3% 1 0 


Exiting... (End of file)
jason@jason-desktop:~$ 

The volume is a lot louder than I can get it any other way, playing it via a terminal

---

### Post by andrew.46 on 2011-03-27
And this showed the video satisfactorily, with full screen?

---

### Post by andrew.46 on 2011-03-27
> **mc4man said:**
> ( while I've paid no mind to the whole ffmpeg vx libav deal it looks like ubuntu will be using libav for the time being

I have settled on FFmpeg itself, from videolan, as it looks like they will be developing their own source and cherry-picking the best of the libav work. Not sure if the libav people are following the same strategy though...

---

### Post by typos1 on 2011-03-27
> **andrew.46 said:**
> And this showed the video satisfactorily, with full screen?

Not really-it is fullscreen but the res is very low and the mouse doesnt do anything the only way to stop it is to hit esc. It does play other stuff better, but when there should be black bars on the screen there arent an you can see the desktop behind, plus it plays hd stuff jerkily missing frames. Its all very strange, esp since I un installed and re installed it, plus added daily builds to my repository.

---

### Post by andrew.46 on 2011-04-13
Loks like the MPlayer developers have [raised the bar]("http://git.mplayerhq.hu/?p=mplayer;a=commit;h=7f1729db858668ff8823f77924267abe17d64174") with libvpx, requiring 0.9.6 now. It might be just as well to go with the FFmpeg decoder:

```

andrew@skamandros~$ mplayer -vc help | grep -i vp8

**[COLOR="Red"]ffvp8       ffmpeg    working   FFmpeg VP8  [vp8][/COLOR]**
fflibvpx    ffmpeg    working   FFmpeg wrapper for libvpx/VP8  [libvpx]

```

Those keen to still use external library may have to compile the so-called [Bali release]("http://webm.googlecode.com/files/libvpx-v0.9.6.tar.bz2")...

---

### Post by andrew.46 on 2011-05-08
I am applying for Ubuntu Membership (again!) based on my work in these Forums and as part of this process I am asking for testimonials from those who know and are happy with my work, and perhaps have benefited from my guides or my assistance on the Forums. I am not entirely comfortable with making this request, I prefer to remain in the background to tell the truth, but this is the way the process runs.

So, if you would like to make a testimonial in support of my application for Ubuntu Membership simple write a couple of words in this thread:

Application for Ubuntu Membership: andrew.46
[http://ubuntuforums.org/showthread.php?t=1750777](http://ubuntuforums.org/showthread.php?t=1750777)

And I thank you for your trouble! I am posting the same message in both MPlayer and vlc guides that I run, this seems to be where my current focus is so hopefully this is not too much like spam :).

Thanks for your trouble,

Andrew

---

### Post by andrew.46 on 2011-05-27
I have added in a section detailing how to compile and install the latest version of UMPlayer. Love to hear if anybody finds this useful, likes or dislikes UMPlayer itself, and any thoughts on the build process I have come up with. I am fairly impressed with the built-in youtube viewer but the general interface is also quite nice...

---

### Post by mc4man on 2011-05-28
> **andrew.46 said:**
> I have added in a section detailing how to compile and install the latest version of UMPlayer. Love to hear if anybody finds this useful, likes or dislikes UMPlayer itself, and any thoughts on the build process I have come up with. I am fairly impressed with the built-in youtube viewer but the general interface is also quite nice...

Had some issues w/ the makefile and umplayer itself on a beta 2 install so am doing on a fairly fresh 11/05 install -- release+ updates (race on D&D into umplayer window)

It builds fine w/ your instructions though there is this very odd occurrence, though it doesn't happen all the time (did 4 builds from scratch, happened 3 out of 4

The svn source has a file "umplayer.spec". If checkinstall picks up on it then the .deb creation fails as seen below - check out the various blue

```
dpkg-deb: error: parsing file '/var/tmp/tmp.NZUmslkIkG/package/DEBIAN/control' near line 7 package 'umplayer':
 error in Version string '0-            1': version string has embedded spaces
/var/tmp/tmp.NZUmslkIkG/dpkgbuild.log (END) 

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package version "		1.0" is not a
*** Warning: debian policy compliant one. Please specify an alternate one

This package will be built according to these values: 

0 -  Maintainer: [ root@doug-XPS-M1330 ]
1 -  [COLOR="Blue"]Summary:[/COLOR] [ 		Complete Frontend for MPlayer ]
2 -  [COLOR="Blue"]Name:[/COLOR]    [ 			umplayer ]
3 -  Version: [ 0 ]
4 -  [COLOR="Blue"]Release:[/COLOR] [ 		1 ]
5 -  License: [ GPL ]
6 -  [COLOR="Blue"]Group:[/COLOR]   [ 			Productivity/Multimedia/Video/Players ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ umplayer ]
9 -  Alternate source location: [  ]
10 - [COLOR="Blue"]Requires:[/COLOR] [ 		mplayer xdg-utils
licenses ]
11 - [COLOR="Blue"]Provides:[/COLOR] [ 		umplayer-beta = %{version}-%{release} ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

```
On the other hand if checkinstall 'misses' the file (or one removes before checkinstall then all is fine
```
*** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@doug-XPS-M1330 ]
1 -  [COLOR="Blue"]Summary:[/COLOR] [ Package created with checkinstall 1.6.2 ]
2 -  [COLOR="Blue"]Name[/COLOR]:    [ umplayer ]
3 -  [COLOR="Blue"]Version[/COLOR]: [ 1:0~r163 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  [COLOR="Blue"]Group:[/COLOR]   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ umplayer ]
9 -  Alternate source location: [  ]
10 - [COLOR="Blue"]Requires[/COLOR]: [  ]
11 - [COLOR="Blue"]Provides[/COLOR]: [ umplayer ]
12 - Conflicts: [  ]
13 - Replaces: [  ]
```


very odd, maybe yet again another local 11.04 issue which natty is quite prone to.

---

### Post by andrew.46 on 2011-05-28
Thanks for looking at that mc4man :). Indeed I can confirm this problem which I saw briefly when I first started working with UMPlayer, oddly enough either checkinstall or make clean deletes the offending file after package failure so initially I only saw the error once. Reproducible all the time with *clean* source though.

I have bypassed the problem with some slippery *if* work, I believe spec files are intended for rpms so no use here but I reinstate the file at the end to keep the source clean. 

Thanks!

---

### Post by mc4man on 2011-05-28
Was having some significant issues with umplayer playing local files, at the time using the mplayer daily ppa package.
Using the ubuntu default packages worked fine, so went ahead a built a new mplayer as per this thread - same issues as with the ppa

Turns out there is a cache default for local files (2000), setting to 0 fixed the problems, just thought I'd mention if same arises for others
(symptoms would be the gui  becoming unresponsive, cache % shown at bottom, cpu use @ 100% either overall or per 1 core/thread, video or audio track would play anything, ect.

---

### Post by andrew.46 on 2011-05-29
> **mc4man said:**
> Turns out there is a cache default for local files (2000), setting to 0 fixed the problems, just thought I'd mention if same arises for others (symptoms would be the gui  becoming unresponsive, cache % shown at bottom, cpu use @ 100% either overall or per 1 core/thread, video or audio track would play anything, ect.

This is a change from the SMPlayer source and I have returned the old setting of 0 with a little sed work. I must say that this is turning out to be more of a task than I had anticipated, thanks yet again for looking at this!

---

### Post by mc4man on 2011-05-29
sorta well off the beaten path - 
personally have a lot of fun with the unity launcher and custom icon, quicklists, launcher icon menus ect.

An interesting thing for mplayer is to create a D&D launcher icon - the launcher will expose an icon(s) when dragging a file on to based on mimetype. (I have 2 - one as below, one for -playlists with heavily reduced MimeType= line

So a very basic .desktop for mplayer would be like this, (didn't cull the mimetypes, just used the kitchen sink, icon can be whatever (normally full path), choose the first one I saw (though do like green apples
This can be expanded upon - myself generally use mplayers conf for parameters

```
gedit ~/.local/share/applications/mplayer1.desktop
```

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Exec=mplayer %f
Name=Mplayer
Icon=apple-green
MimeType=video/dv;video/mpeg;video/x-mpeg;video/msvideo;video/quicktime;video/x-anim;video/x-avi;video/x-ms-asf;video/x-ms-wmv;video/x-msvideo;video/x-nsv;video/x-flc;video/x-fli;video/x-flv;video/vnd.rn-realvideo;video/mp4;video/mp4v-es;video/mp2t;application/ogg;application/x-ogg;application/x-matroska;audio/x-mp3;audio/x-mpeg;audio/mpeg;audio/x-wav;audio/x-m4a;audio/x-ms-asf;audio/x-ms-asx;audio/x-ms-wax;application/vnd.rn-realmedia;audio/x-real-audio;audio/x-pn-realaudio;application/x-flac;audio/x-flac;application/x-shockwave-flash;misc/ultravox;audio/vnd.rn-realaudio;audio/x-pn-aiff;audio/x-pn-au;audio/x-pn-wav;audio/x-pn-windows-acm;image/vnd.rn-realpix;audio/x-pn-realaudio-plugin;application/x-extension-mp4;audio/mp4;
```

After creating then browse to ~/.local/share/applications and drag the mplayer1.desktop on to launcher
Then any file you want to play just drag on launcher, Mplayer will light up ect.
(myself generally keep all gui media apps in a Multimedia launcher icon as a quicklist menu so Mplayer will be the only icon to light up

Edit: as an Ex. of playlist D&D launcher icon  - This time %U allows the launcher icon to control as far as min. the terminal  to or quit altogether (screen

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Exec=mplayer -playlist %U
Name=Mplayer List
Icon=apple-red
MimeType=audio/x-mpegurl;audio/x-scpls;
```

---

### Post by amadis2009 on 2011-06-10
Can anyone point me to a way to undo this or downgrade to a previous version? This upgrade had unfortunately made SMPlayer unusable for me. I can get videos to play in the gui version of Mplayer (though cpu is at 60%), but with SMPlayer cpu goes to 100% and I get MPlayer zombie processes.

---

### Post by typos1 on 2011-06-10
Tell me about it!-I ve been getting cpu readings like that from smplayer and mplayer for the last 5months !

---

### Post by andrew.46 on 2011-06-11
> **amadis2009 said:**
> Can anyone point me to a way to undo this or downgrade to a previous version?

You can remove this version of MPlayer easily enough from Synaptic, just search for mplayer. If you then install MPlayer (from Synaptic or from the commandline with *apt-get install*) you will receive the stock Natty MPlayer: 2:1.0~rc4.dfsg1-1ubuntu3 which is based on the latest release version.

> **amadis2009 said:**
> This upgrade had unfortunately made SMPlayer unusable for me. I can get videos to play in the gui version of Mplayer (though cpu is at 60%), but with SMPlayer cpu goes to 100% and I get MPlayer zombie processes.

I cannot reproduce this on my system but perhaps have a look and see if it is a Pulse Audio problem, try running with alsa for example:
```

mplayer -ao alsa *my_file*
```

obviously substituting 'my_file' for the correct path and name of your own file. BTW this guide does not build the default gui for MPlayer, where did you get this from? If purely from this guide you should see the following:

```

andrew@Corinth:~$ **[COLOR="Red"]mplayer | head -n 1[/COLOR]**
MPlayer SVN-r33577-4.5.2 (C) 2000-2011 MPlayer Team

```

---

### Post by amadis2009 on 2011-06-11
Thanks Andrew, but after constant fiddling I finally got it to work without having to uninstall. Firstly, I had problems updating my ATI driver to Catalyst 11.4 when I'd upgraded to Natty. The combination of Unity, Emerald (which I use), and the  new driver made for some screwy unusable settings. I'm not currently using Unity. But I tried upgrading the ATI driver again witout Unity and this time it worked (I might try reinstalling Unity later). After that upgrade, avi files played normally on SMPlayer with no high CPU usage, but mkv files had no video and froze the program eventually. I'd had problems with mkv files about a year ago and adding 

[extension.mkv]
demuxer=mkv

to my mplayer config file had fixed the problem. I went back and tried removing that. Suddenly I had video again, but the CPU was still at 100% and SMPlayer froze after about 30 seconds. I had seen on another thread that changing the cache settings under SMPlayers performance settings could help. I had changed the cache setting for local files to 0 before and that had helped a little with the avi files before, but not enough so I changed it back to the default. I went back and set it to 0 again, and now with the demuxer setting removed from my mplayer config file playback is noraml again!!! CPU usage for SMPlayer is at 0 and for MPlayer at 30. \o/

ETA: Also, I can now play all those mkv files that I had trouble with because of the new mkvmerge header compression issue, without having to remux them thanks to this updated build of MPLayer.

Hope this helps anyone else with similar problems.

---

### Post by amadis2009 on 2011-06-11
Also, yes Andrew, I did have to switch to Alsa. Pulse audio works, but alsa sounds much better.

As for the gui, I installed it from Synaptic. I wanted to see if it was a problem with mplayer or Smplayer. Turns out it was both. Well, my settings for both.

---

### Post by beew on 2011-06-11
> **mc4man said:**
> Was having some significant issues with umplayer playing local files, at the time using the mplayer daily ppa package.
Using the ubuntu default packages worked fine, so went ahead a built a new mplayer as per this thread - same issues as with the ppa

Turns out there is a cache default for local files (2000), setting to 0 fixed the problems, just thought I'd mention if same arises for others
(symptoms would be the gui  becoming unresponsive, cache % shown at bottom, cpu use @ 100% either overall or per 1 core/thread, video or audio track would play anything, ect.

I found that the mplayer daily build is broken for vdpau as well. I have started a thread as a question. I don't know if this is only the latest build or it is a persistent problem.

[http://ubuntuforums.org/showthread.php?t=1778720](http://ubuntuforums.org/showthread.php?t=1778720)

I use the build from ripps' ppa, which is up to date and works perfectly, haven't experienced any problem with Umplayer either. I think that ppa should get more publicity over the MOTU one.

Interesting thread, definitely would want to try it out.

---

### Post by andrew.46 on 2011-06-11
> **beew said:**
> I use the build from ripps' ppa, which is up to date and works perfectly, haven't experienced any problem with Umplayer either. I think that ppa should get more publicity over the MOTU one.

I will admit that I have suggested the MOTU PPA:

MOTU Media Team
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

mostly because it is endorsed on the MPlayer website and was setup by one of the MPlayer developers. At heart though I am not all that keen on PPAs in general as I believe with a little time and effort the package you build yourself will always be more suitable, and certainly more flexible, on your own setup. But I certainly acknowledge that many are perfectly happy with PPAs and I am following the MPlayer PPA debate with some interest :).

---

### Post by beew on 2011-06-11
> **andrew.46 said:**
> I will admit that I have suggested the MOTU PPA:

MOTU Media Team
[https://launchpad.net/~motumedia/+archive/mplayer-daily]("https://launchpad.net/%7Emotumedia/+archive/mplayer-daily")

mostly because it is endorsed on the MPlayer website and was setup by one of the MPlayer developers. At heart though I am not all that keen on PPAs in general as I believe with a little time and effort the package you build yourself will always be more suitable, and certainly more flexible, on your own setup. But I certainly acknowledge that many are perfectly happy with PPAs and I am following the MPlayer PPA debate with some interest :).

Sure, if you know how to do it it would be a lot more fun to build it yourself, but for many people they just need to get a good player so they can use their machine and learning how to build the player can take too much time and effort. I would like to do it once I have the time. But right now I would like to learn a bit more about how to use it effectively and the different libraries first. :)

So do you know if the MOTU version is only broken for vdpau in its latest build or it just doesn't support it? I find ripps' build works better in general even on machines without vdpau  (I don't use coreavc)

---

### Post by andrew.46 on 2011-06-11
> **beew said:**
> Sure, if you know how to do it it would be a lot more fun to build it yourself, but for many people they just need to get a good player so they can use their machine and learning how to build the player can take too much time and effort. I would like to do it once I have the time. But right now I would like to learn a bit more about how to use it effectively and the different libraries first. :)

Well, I guess that is what this guide is intended to do :). I have broken it down a lot so there are only 6 code boxes to copy and paste to produce a decent, fully featured MPlayer build with another code box to update. Even so I realise that this is not for everybody and that is where the PPAs come in...

> **beew said:**
> So do you know if the MOTU version is only broken for vdpau in its latest build or it just doesn't support it? I find ripps' build works better in general even on machines without vdpau  (I don't use coreavc)

My dark secret is that my hardware is very limited, I have a Latitude D520 laptop = intel graphics, and have never used vdpau. Hopefully others on this thread can test the PPA and see what the issue is.

---

### Post by typos1 on 2011-06-11
I think he meant knowing what codes to write for what you want-its easy enough to copy and paste once someone has written it !

---

### Post by andrew.46 on 2011-06-12
> **typos1 said:**
> I think he meant knowing what codes to write for what you want-its easy enough to copy and paste once someone has written it !

True enough, I hope this guide is not so comprehensively written that it does not encourage some experimentation and change. It was always my aim to provide a platform from which people could explore MPlayer a little more easily than simply starting with a blank slate.

---

### Post by mc4man on 2011-06-16
As far as umplayer and local cache - 
I guess it's not an issue for some, at least here it does create huge issues

Anyway - the new src has gone and  upped the cache, this makes the build script fail to lower
```

        threads = QThread::idealThreadCount();
        if(threads < 1) threads = 1;
        cache_for_files = 8192;
        cache_for_streams_seekable = 2000;

```

Small thing - myself don't like global menu in most multimedia players - as far as vlc and or umplayer if desired the menu can be returned by either removing appmenu-qt or editing the Exec= line in either the apps .desktop or in a quicklist entry
Ex. umplayer's 
```
Exec=env QT_X11_NO_NATIVE_MENUBAR=1 umplayer %f

```

---

### Post by andrew.46 on 2011-06-16
> **mc4man said:**
> As far as umplayer and local cache - 
I guess it's not an issue for some, at least here it does create huge issues

Anyway - the new src has gone and  upped the cache, this makes the build script fail to lower

Thanks again mc4man, I have adjusted the number. Should pull out the sed book and work out how to match all numerics rather than specific ones, this will be a job for the weekend I suspect...

---

### Post by beew on 2011-06-17
> **andrew.46 said:**
> Well, I guess that is what this guide is intended to do :). I have broken it down a lot so there are only 6 code boxes to copy and paste to produce a decent, fully featured MPlayer build with another code box to update. Even so I realise that this is not for everybody and that is where the PPAs come in...



My dark secret is that my hardware is very limited, I have a Latitude D520 laptop = intel graphics, and have never used vdpau. Hopefully others on this thread can test the PPA and see what the issue is.

I just found out from Ripps that the mplayer in his ppa is actually mplayer2, that's why it works much better than other versions found in Ubuntu (including the MOTU ppa)

[http://ubuntuforums.org/showthread.php?p=10948598#post10948598](http://ubuntuforums.org/showthread.php?p=10948598#post10948598)

Is it easy to adapt your guide to build mplayer2 instead of mplayer? Thanks.

---

### Post by mc4man on 2011-06-17
> Is it easy to adapt your guide to build mplayer2 instead of mplayer? Thanks. 
Could be worth some consideration - though you could continue to use ripps ppa or build the mplayer2 source youself
some basic diff's page
[http://www.mplayer2.org/comparison.html](http://www.mplayer2.org/comparison.html)

Did notice that _[U][debian experimental]("http://packages.debian.org/experimental/mplayer2")_[/U] is doing an mplayer2 build now, didn't look to uncover their config.

Went ahead and dl'ed and installed it on 11.10 just to see if it would install and run which it does, could be what's used down the road in ubuntu

---

### Post by andrew.46 on 2011-06-17
> **beew said:**
> Is it easy to adapt your guide to build mplayer2 instead of mplayer? Thanks.

I am afraid that I have never looked at the MPlayer2 build system but my quick look seems to indicate that it is certainly a little different to build. Could be a place for somebody to write and maintain a guide for building MPlayer2? Feel free to plunder my own guide if you are interested...

---

### Post by beew on 2011-06-17
> **andrew.46 said:**
> I am afraid that I have never looked at the MPlayer2 build system but my quick look seems to indicate that it is certainly a little different to build. Could be a place for somebody to write and maintain a guide for building MPlayer2? Feel free to plunder my own guide if you are interested...

I am definitely interested but I don't know how, so I am looking for a guide and some instructions. And as typos1 said, I would also want some understanding other than just copying codes. I need a place to start.

---

### Post by andrew.46 on 2011-06-17
> **beew said:**
> I am definitely interested but I don't know how, so I am looking for a guide and some instructions. And as typos1 said, I would also want some understanding other than just copying codes. I need a place to start.

Well I guess if you were interested in the release version of mplayer2 you could first download and install all the dependencies and build tools suggested in my guide. Then download the mplayer2 code, decompress it and change to the appropriate directory:

```

$ wget http://ftp.mplayer2.org/pub/release/mplayer2-build-2.0.tar.bz2
$ tar xjvf mplayer2-build-2.0.tar.bz2
$ cd mplayer2-build-2.0

```

and then simply run:

```
$ make
```

There are many other options carefully described in the README file, including the method of loading the libraries and mplayer2 from git which I have not explored. From here you simply either run *make install* or perhaps use checkinstall to make a package or even backtrack a little and look at the /debian section to build a formal debian package.

It builds well enough on my system:

```

andrew@skamandros~/Desktop/mplayer2-build-2.0/mplayer$ ./mplayer | head -n 1
MPlayer2 2.0 (C) 2000-2011 MPlayer Team

```

but I have not looked into it too much further. Hopefully this gives you a starting point?

---

### Post by beew on 2011-06-17
Thanks andrew. Will try it out.

---

### Post by andrew.46 on 2011-06-17
> **beew said:**
> Thanks andrew. Will try it out.

I would be interested to hear how you get on. Had another quick look and it appears you will have to already have the development libraries for libdvdread and libdvdcss installed as these are not in the mplayer source tree. Bound to be a few more 'gotchas' in there as well :).

---

### Post by beew on 2011-06-18
It seems that I do have a performance problem with Umplayer for high definition clips (1080p) and full screen iif I use it with normal mplayer instead of mplayer2 from ripps' repository.  Smplayer on the other hand does fine.

I didn't realize that because I have been using ripps' mpayer2 shortly after I started using Ubuntu (~one year ago) I always assume that it is just an awesome mplayer build. :)  Umplayer truly rocks with mplayer2.

Now that I am testing the normal build and even mplayer-mt from [https://launchpad.net/~longinus00/+archive/mplayer-mt]("https://launchpad.net/%7Elonginus00/+archive/mplayer-mt") suck by comparison. I would like to see mplayer2 becoming the default 'mplayer' in Ubuntu repositories, that would cut down a lot of people on the forum complaining about video playback. :)

The only catch at this point is that the pausing in gnome-mplayer is kind of broken with mplayer2 so for something like streaming divx videos it is a lot better to use mplayer than mplayer2. It is going to be fixed according to mplayer2's FAQ.

---

### Post by beew on 2011-06-18
> **andrew.46 said:**
> I would be interested to hear how you get on. Had another quick look and it appears you will have to already have the development libraries for libdvdread and libdvdcss installed as these are not in the mplayer source tree. Bound to be a few more 'gotchas' in there as well :).

I would need to do some research and reading first. I am sure I will come back to ask for help. Still haven't gotten around to build ffmpeg. :)

---

### Post by mad_max0204 on 2011-06-19
I install mplayer and smplayer for years like this with no problems.
Last month i switched from ubuntu to xubuntu. Dont ask me why its not for this thread.
So, I installed everything to build mplayer and it went fine. Nvidia drivers installed (last release drivers) and installed smplayer.
When I tried to play x264 video in 1080p resolution it played without video in smplayer. Just sound. Then I ran mplayer from command line and I reveiced this errors:

```

libavformat file format detected.
[matroska,webm @ 0x3497ef0] max_analyze_duration 5000000 reached at 5024000
[matroska,webm @ 0x3497ef0] Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: video (h264), -vid 0, The Eagle (2011)
[lavf] stream 1: audio (ac3), -aid 0, -alang eng, AC3 5.1 @ 640 Kbps
[lavf] stream 2: audio (aac), -aid 1, -alang eng, Commentary 1
[lavf] stream 3: audio (aac), -aid 2, -alang eng, Commentary 2
[lavf] stream 4: subtitle (pgssub), -sid 0, -slang eng
VIDEO:  [H264]  1920x816  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in ./
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.

```

Any help is appreciated.

Thanks

---

### Post by mad_max0204 on 2011-06-19
Wow ignore this I solved it with

ln -s /usr/lib/vdpau/libvdpau_nvidia.so.1 /usr/lib/libvdpau_nvidia.so

---

### Post by beew on 2011-06-22
Hi, Andrew,

I have succeeded in building mplayer2! I downloaded the dev files using the second step of your guide then  followrf the very simple instructions here (I already have the codecs installed system wide from medibuntu)
[http://forum.doom9.org/showthread.php?t=160354](http://forum.doom9.org/showthread.php?t=160354)

```
$ sudo apt-get build-dep mplayer 
$ sudo apt-get install build-essential subversion gitcore yasm autoconf libtool 
$ git clone git://git.mplayer2.org/mplayer2-build.git 
$ cd mplayer2-build && ./enable-mt && ./init 
$ echo --prefix=$HOME >> ./mplayer_options 
$ make -j4 
$ make install 
$ mv $HOME/bin/mplayer $HOME/bin/mplayer2
```I have to say I don't quite understand the "echo" and the "make -j4" lines. I would appreciate it if you can explain that to me. Since the package seems to be quite self contained (it comes with its own ffmpeg) probably it wasn't necessary to download all the packages from the second step of your guide, I will try without that and see what happens.

mplayer2 is really in almost every way vastly superior to mplayer. I didn't know that because I was always using ripps' ppa and thought that it is just a better build of mplayer. But after finding out about mplayer2 I have gone back to reinstall mplayer to see the difference and man is that huge! I have been used to very smooth playback of 720p on my laptop and that include some videos that has a lost of fast motion even with just the nouveau driver (with no vdpau)  But once switched to mplayer most of them are unwatchable. I think mplayer2, instead of mplayer, should be the default "mplayer" package. Performance wise there is no comparison.

There is but one problem. Mplayer2 doesn't work well in streaming videos online because the pausing function in gnome mplayer doesn't work with mplayer2. I read that the reason is that mplayer has some bugs in pausing and gnome-mplayer has patches to handle them. But these bugs were actually fixed in mplayer2 so the patches become a problem if gnome-mplayer use mplayer2 as a backend. This problem will be fixed in future releases of gnome-mplayer but in the mean time if you want to watch video streaming online mplayer is the way to go.

The  best part now is that the building process above creates a mplayer2 executable in /home/username/bin , so now I can have both mplayer2 and the ordinary  mplayer in the same sysyem.  I use mplayer2 with umplayer to watch local video files (it has an option to choose the mplayer backend) and ordinary mplayer with gecko-mediaplayer for streaming, so this is the best of both worlds until the gnome-mplayer has fixed its pausing problem with mplayer2. Umplayer is almost unusable with ordinary mplayer for high definition videos, but it is smooth as butter with mplayer2.

---

### Post by andrew.46 on 2011-06-22
> **beew said:**
> I have succeeded in building mplayer2! I downloaded the dev files using the second step of your guide then  followrf the very simple instructions here (I already have the codecs installed system wide from medibuntu)
[http://forum.doom9.org/showthread.php?t=160354](http://forum.doom9.org/showthread.php?t=160354)
[...]
I have to say I don't quite understand the "echo" and the "make -j4" lines. I would appreciate it if you can explain that to me. Since the package seems to be quite self contained (it comes with its own ffmpeg) probably it wasn't necessary to download all the packages from the second step of your guide, I will try without that and see what happens.

Good on you :). Sounds look you have not only got the basics down but you have started to explore further, so soon enough you will have assembled considerable expertise in building and using MPlayer2. I seriously would love to see you write it all up in the Tutorial and Tips section of these Forums and I encourage you again to pillage my guide for whatever you need with no acknowledgement required.

The echo line:

```
$ echo --prefix=$HOME >> ./mplayer_options 
```

is simply designed to *append* the '--prefix=$HOME' option to the file ./mplayer_options which is Uoti's method of creating configuration options for MPLayer.

The make -j4 option controls how many jobs can run simultaneously and is designed to speed up compilation. The gruesome details can be found in the make man pages under *--jobs* and if you are interested you can see the effects by running *with* that option and *without* prefixing the command with the *time* command. Depends how badly you want to spend lots of time mucking around with your computer I guess :).

---

### Post by beew on 2011-06-22
> **andrew.46 said:**
> Good on you :). Sounds look you have not only got the basics down but you have started to explore further, so soon enough you will have assembled considerable expertise in building and using MPlayer2. I seriously would love to see you write it all up in the Tutorial and Tips section of these Forums and I encourage you again to pillage my guide for whatever you need with no acknowledgement required.
.


Actually it was just cut and paste. I wouldn't know where to start without the instructions from doom9 (mplayer2's web site has no instruction, presumably all Linux users know how to build from source. :)) 

I would have to know a lot more before I can write my own tutorial, I wouldn't feel comfortable until I get to the point where I can figure out how to compile on my own (at least for similar software) like you did. :)  Your guides (along with the VLC one) will be of great help. Aside from the syntax of the codes I have no idea what dependencies are required. Look at the long list of developmental libraries you have on step 2 of this tutorial, I have no idea what they are and why they are needed. 

The reason why I am always hesitant to build from source is that I have  little understanding of the process (what dependencies are required,  which library does what etc) While cut and paste from forum posts such as doom9's   accomplishes the job it doesn't enhance my understanding very much.Is there a place where I can get an overview of the process and what these libraries do?

---

### Post by andrew.46 on 2011-06-22
A lot of experience in this area can only come by compiling and recompiling with different options, building different packages etc etc. Ubuntu makes this a little difficult as the software sources are split up into many different packages and a base install of any version of Ubuntu is not a great software building base. 

The so-called 'development files' for my MPlayer guide were put together various ways. I started with the development files used in the Ubuntu package and then observed what was missing when running ./configure on the MPlayer source code. Monitoring the MPlayer mailing lists allows the addition of newer dev files and the occasional extra compiled packages as new functionality is added to the source. A valuable source is this thread where people will post wish lists for additional functionality or complaints that repository versions are too old.

But don't expect to be on top of the whole area when writing things like guides, I usually learn as I go and never present myself as an authority, just another user trying to learn...

---

### Post by beew on 2011-06-22
Hi, Andrew,

Thanks for the explanation. I guess it is going to take a lot of trial and error.

I have a question and would appreciate your advise. My current setup turns out to be pretty sweet, use Umplayer with the self compiled version of mplayer2 to view local files and use "normal" mplayer for streaming (usually they are not so demanding on decoding) until the conflict between mplayer2 and gnome mplayer re pausing is fixed (at least that is when I don't use the Nvidia proprietary driver. The normal mplayer build from MOTU apparently doesn't even work with vdpau) 

There is only one little glitch. I just found out that my compiled version of Mplayer2 doesn't play dvds because it was compiled without libdvd support according to the error message, whereas the version of mplayer2 from Ripps' PPA works just fine. I am wondering if there is a simple way to add libdvd support in the compiling?

This is not a big issue, I mostly rip my DVDs anyway and I can always use VLC or change Umplayer's backend on the fly. But it would be educational to know how to add such support.

Thanks.

---

### Post by andrew.46 on 2011-06-22
> **beew said:**
>  There is only one little glitch. I just found out that my compiled version of Mplayer2 doesn't play dvds because it was compiled without libdvd support according to the error message, whereas the version of mplayer2 from Ripps' PPA works just fine. I am wondering if there is a simple way to add libdvd support in the compiling?

Uoti has removed the internal dvdread, libdvdcss and libdvdnav libraries. (You may have noticed that MEncoder and GMPlayer are gone as well.) I am not at my Ubuntu computer at the moment but dvd support should be automagically compiled in with the presence of libdvdcss. On this (non-Ubuntu) setup it works well enough:

```

andrew@skamandros~/Desktop/mplayer2-build-2.0/mplayer$ [B][COLOR="Red"]./mplayer dvd://
MPlayer2 2.0 (C) 2000-2011 MPlayer Team[/COLOR][/B]

Playing dvd://.
**[COLOR="Red"]libdvdread: Using libdvdcss version 1.2.10 for DVD access[/COLOR]**
There are 11 titles on this DVD.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000c1830
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000c1afb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000ca62f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002df852
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002e28f9
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 1
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: en aid: 129.
number of audio channels on disk: 2.
subtitle ( sid ): 0 language: hr
subtitle ( sid ): 1 language: cs
subtitle ( sid ): 2 language: da
subtitle ( sid ): 3 language: en
subtitle ( sid ): 4 language: fi
subtitle ( sid ): 5 language: iw
subtitle ( sid ): 6 language: hu
subtitle ( sid ): 7 language: is
subtitle ( sid ): 8 language: no
subtitle ( sid ): 9 language: pl
subtitle ( sid ): 10 language: pt
subtitle ( sid ): 11 language: sv
subtitle ( sid ): 12 language: tr
subtitle ( sid ): 13 language: en
number of subtitles on disk: 14

Detected file format: MPEG-PS
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  7500.0 kbps (937.5 kbyte/s)
[***] auto-open
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 2 threads if supported.
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
**[COLOR="Red"]Starting playback...[/COLOR]**

```

So I have not tested this on Natty but perhaps the following will be enough:

```

sudo apt-get install libdvdread4 libdvdnav-dev libdvdread-dev && \
sudo /usr/share/doc/libdvdread4/install-css.sh

```

and then recompile. MPlayer2 certainly compiles a lot faster than MPlayer :).

---

### Post by andrew.46 on 2011-06-24
Mind you I have built the 'development' version of MPlayer2 and I am starting to warm to it a little..... perhaps it has a place in this guide after all. If some are interested in building this the following *builds* but does not *install* to the system:

```

cd $HOME/mplayer_build && \
git clone git://git.mplayer2.org/mplayer2-build.git && \
cd mplayer2-build && \
./init --shallow && make

```

This builds the mplayer executable in $HOME/mplayer_build/mplayer2-build/mplayer and should show as:

```

andrew@skamandros~/Desktop/mplayer2-build/mplayer$ **[COLOR="Red"]./mplayer | head -n1[/COLOR]**
MPlayer2 2.0-134-g84d8671 (C) 2000-2011 MPlayer Team

```

Very interesting times ahead, I shall look at the checkinstall syntax over the next few days...

---

### Post by beew on 2011-06-24
Hi, Andrew,

I am trying to build mplayer2 again in another Ubuntu installation (Maverick) this time it fails the first step
 > sudo apt-get build-dep mplayer 
[sudo] password for bee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'mplayer2-build' as source package instead of 'mplayer'
E: Unable to find a source package for mplayer2-build

What is wrong?

[B]EDITED: Strange I just build mplayer2 in Natty again successfully but get this error whenever I try in Maverick.  The executable bult in Natty runs without problem in Maverick though (for one Natty install but not the other, see below)
[/B] 
I have built  mplayer2 in two Natty installations (Na and Nb, say). The one compiled in Na is portable, I cut and paste the bin folder (which contains the mplayer2 executable) into Maverick, Nb and yet another Natty (Nc) and mplayer2 works in all, but the version created in Nb works only on Nb. Why is the difference?

I have added the dvd support libraries when compiling mplayer2 in Natty b and it works, thanks.

P.S. Do you find mplayer2 a lot better than mplayer? I have found out that if I install mplayer not from the MOTU ppa but from the mplayer-mt ppa then it does support vdpau and with vdpau its performance is on par with mplayer2, but without vdpau it is massively inferior.

---

### Post by beew on 2011-06-24
Hmm.. Just recompiled mplayer2 in Natty a (Na from last post) and copy the mplayer2 executable to Maverick and it no longer works, as in can't play any file (it works before when there was no dvd support). Maybe the lack of transferability is the result of some dvd -dev libraries have different versions in Maverick and Natty?
(**Edited :Opps, sorry please disregard this, I have somehow copied the bin folder into the wrong place. Now it works and with dvd support too. But I still don't understand why mplayer2 from Nb did not transfer**)

On another note it turns out that mplayer-mt (from this ppa [https://launchpad.net/~longinus00/+archive/mplayer-mt]("https://launchpad.net/%7Elonginus00/+archive/mplayer-mt")) performs well with or without vdpau, the poor performance when vdpau is not available appears to be some problem with umplayer (which works awesomely with mplayer2), switch to smplayer and it works fine (whereas MOTU doesn't work well regardless of gui front end) so it seems that there are many factors at play here and the nouveau driver may have something to do with it too. You probably won't notice that kind of things because you play videos with the command lines. :)

---

### Post by beew on 2011-06-24
A question, how do you know when to update if you install from source? When updating do I have to rerun the whole thing?

---

### Post by Bachstelze on 2011-06-24
When you run svn update, it will either tell you that your source code is up-to-date, in which case you do not need to do anything, or update your source tree, in which case you will need to recompile it in order to gat a binary that incorporates the changes.

---

### Post by andrew.46 on 2011-06-24
> **beew said:**
> A question, how do you know when to update if you install from source? When updating do I have to rerun the whole thing?

Mind you if you are referring to the *development* version of MPlayer2 (which I demonstrated [a few posts ago]("http://ubuntuforums.org/showpost.php?p=10975723&postcount=262")) Uoti has scripted the process so you would change to $HOME/mplayer_build/mplayer2-build and then run:
```

$ ./clean
$ ./update
$ make

```

It might not be such a good idea to use the *build-dep* command for MPlayer2 btw, it drags in a lot of extraneous files that are not needed. I note in particular that MPlayer2 downloads and links statically its own version of FFmpeg...

---

### Post by ron999 on 2011-06-24
> **andrew.46 said:**
> I note in particular that MPlayer2 downloads and links statically its own version of FFmpeg...

Hi Andrew
There is an option to just download mplayer2 'Player only'... 'to use system libraries for all dependencies'
Here:- [http://www.mplayer2.org/]("http://www.mplayer2.org/")

How would you go about changing these commands to link to a git ffmpeg already installed?

```
cd $HOME/mplayer_build && \
git clone git://git.mplayer2.org/mplayer2-build.git && \
cd mplayer2-build && \
./init --shallow && make 
```

(By the way, those commands work OK with Karmic)

---

### Post by beew on 2011-06-24
> **andrew.46 said:**
> Mind you if you are referring to the *development* version of MPlayer2 (which I demonstrated [a few posts ago]("http://ubuntuforums.org/showpost.php?p=10975723&postcount=262")) Uoti has scripted the process so you would change to $HOME/mplayer_build/mplayer2-build and then run:
```

$ ./clean
$ ./update
$ ./make




```

Thanks, that is exactly what I need to know. But how about software you build in general?

> It might not be such a good idea to use the *build-dep* command for MPlayer2 btw, it drags in a lot of extraneous files that are not needed. I note in particular that MPlayer2 downloads and links statically its own version of FFmpeg...I think the idea is that the system ffmpeg is single threaded but the statically linked version is multi-threaded. If you have a single core machine it wouldn't make a difference but if you have a multi core machine there will be a great improvement, that probably explains why stock mplayer from Ubuntu and mplayer from the MOTU ppa perform so poorly comparing to mplayer2 and mplayer-mt in my experience. So  I would prefer to use the statically linked version.(Ripps' ppa version is also statically linked to its own ffmpeg and that was the reason he gave) 

But still I don't understand why build-dep runs in Natty but not Mav, see the error in my post #264. Allso why is it that mplayer2 compiled in one Natty install can be just copied to other Ubuntu installs and works but not mplayer2 compiled in the other Natty? Thanks again.

---

### Post by mc4man on 2011-06-25
> **ron999 said:**
> Hi Andrew
There is an option to just download mplayer2 'Player only'... 'to use system libraries for all dependencies'
Here:- [http://www.mplayer2.org/]("http://www.mplayer2.org/")

How would you go about changing these commands to link to a git ffmpeg already installed?

```
cd $HOME/mplayer_build && \
git clone git://git.mplayer2.org/mplayer2-build.git && \
cd mplayer2-build && \
./init --shallow && make 
```

(By the way, those commands work OK with Karmic)

cd to the mplayer dir., run ./configure and ck. the result. If good then run a make, ect.
If not then take care of and  again run a ./configure, make, ect.
(your main concern may be liba-ss support

---

### Post by ron999 on 2011-06-25
> **mc4man said:**
> cd to the mplayer dir., run ./configure and ck. the result. If good then run a make, ect.
If not then take care of and  again run a ./configure, make, ect.
(your main concern may be liba-ss support

```
mkdir $HOME/mplayer_build && cd $HOME/mplayer_build && \
git clone git://git.mplayer2.org/mplayer2.git && \
cd mplayer2 && \
./configure
```

Thanks mc4man
It went through ./configure OK, but gives errors when I run 'make'.

EDIT
Probably some Karmic packages are not good enough.

---

### Post by mc4man on 2011-06-25
> **ron999 said:**
> ```


EDIT
Probably some Karmic packages are not good enough.

It's the libass version, either you'd build and install the current one or just add to your - 
[CODE]./configure --disable-***
```
(Where *** is the word we never can use here

---

### Post by ron999 on 2011-06-25
> **mc4man said:**
> It's the libass version... or just add to your - 
```
./configure --disable-***
```


Hi mc4man
Using ./configure --disable-a** fixed the problem.

But mplayer2 won't compile against my FFmpeg:-
ffmpeg version N-30971-g4b87a08, built on Jun 23 2011 12:30:48 with gcc 4.4.1

Gives error:- [B]collect2: ld returned 1 exit status
[/B]
Maybe I'll try again next time I rebuild FFmpeg.

---

### Post by mc4man on 2011-06-25
> **ron999 said:**
> .....
But mplayer2 won't compile against my FFmpeg:-

I'm on the road w/ just a laptop that has 11.10, but did try both building using the system ffmpeg libs (4.0.7, libav source) and just using the built-in scripts to statically link

Both worked fine - I'd be inclined to just use default method and statically link - it's a fast build and unless you had a specific reason to want to use your ffmpeg build nothing to be gained

---

### Post by andrew.46 on 2011-06-25
Interestingly enough in my 'other' linux world there is some interest in MPlayer2 by the gent who created the buildscript for MPlayer that is now part of Slackware. It would be very interesting if MPlayer2 made it into the distro, it is much less controversial to package, much easier to build and as an added benefit a lot of old software has been trimmed from it. Interesting times indeed :).

---

### Post by beew on 2011-06-29
> **andrew.46 said:**
> Mind you if you are referring to the *development* version of MPlayer2 (which I demonstrated [a few posts ago]("http://ubuntuforums.org/showpost.php?p=10975723&postcount=262")) Uoti has scripted the process so you would change to $HOME/mplayer_build/mplayer2-build and then run:
```

$ ./clean
$ ./update
$ ./make

```...


Hi,

Just tried my first update, the first 2 commands work (remove and replace a bunch of stuffs) but the third (./make)gave me "no such file or directory" Do you have any idea? thanks.

On another note, a few weeks ago you and mc4man were building umplayer. I remember there was a problem with playing local files fullscreen. I install Umplayer from PPA and have been using Ripps mplayer which is actually mplayer2 so I didn't notice any issue. But I experienced that as well if I switched the mplayer backend to the MOTU build of mplayer,--I think this was the one you tested with,-- or Daneil Lee's mplayer-mt ([https://launchpad.net/~longinus00/+archive/mplayer-mt]("https://launchpad.net/%7Elonginus00/+archive/mplayer-mt")) Umplayer froze with these backends but it worked fine with stock mplayer from Ubuntu repo and mplayer2. 

This problem was solved on monday's update to umplayer 0.97. You may want to build it again  and see if you still have the same problem.

---

### Post by andrew.46 on 2011-06-29
> **beew said:**
> Just tried my first update, the first 2 commands work (remove and replace a bunch of stuffs) but the third (./make)gave me "no such file or directory" Do you have any idea? thanks.

Oops, I made a small typo :(. Rather than *./make* try simply *make*.

---

### Post by mc4man on 2011-07-01
As a side note mplayer2 has been added to 11.10's repo, and is mt enabled thru the shared ffmpeg libs (libavcodec53, ect.

---

### Post by andrew.46 on 2011-07-01
> **mc4man said:**
> As a side note mplayer2 has been added to 11.10's repo, and is mt enabled thru the shared ffmpeg libs (libavcodec53, ect.

Interesting, I wonder if the standard MPlayer will be dumped in favour of uoti's fork. Very interesting times ahead :).

---

### Post by mc4man on 2011-07-01
> **andrew.46 said:**
> Interesting, I wonder if the standard MPlayer will be dumped in favour of uoti's fork. Very interesting times ahead :).
Both are still showing though the 'old' mplayer depends on different ffmpeg libs.
 Likely they'll drop the  older mplayer and the 0.6.X ffmpeg and libs sooner than later

---

### Post by mocha on 2011-07-02
I just updated a box to Natty and did a fresh download of mplayer, I haven't updated mplayer for about 6 months.  During config it said "No FFmpeg checkout" (even though I just downloaded and installed a git pull of ffmpeg) and it gave the option to download ffmpeg or cancel.  If you choose to download it, a git checkout of ffmpeg gets downloaded into the mplayer source directory.  What's going on, why doesn't it use the ffmpeg on your system?  Does this have something to do with all the project structural changes a few months ago?

---

### Post by mocha on 2011-07-02
> **mc4man said:**
> I'm on the road w/ just a laptop that has 11.10, but did try both building using the system ffmpeg libs (4.0.7, libav source) and just using the built-in scripts to statically link

Both worked fine - I'd be inclined to just use default method and statically link - it's a fast build and unless you had a specific reason to want to use your ffmpeg build nothing to be gained

I'm having similar problems.  I just updated a box to Natty and doing my usual fresh pulls of x264, ffmpeg, and regular mplayer.  When I pull mplayer2, do a configure and then make it errors out becuase of the libs installed by ffmpeg.  If I --enable-static it gives me this:

```
/usr/bin/ld: cannot find -lenca
/usr/local/lib/libavformat.a(rtsp.o): In function `get_sockaddr':
/usr/src/ffmpeg/libavformat/rtsp.c:120: warning: Using 'getaddrinfo' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
stream/librtsp/rtsp_rtp.o: In function `rtp_setup_and_play':
rtsp_rtp.c:(.text+0xb58): warning: Using 'gethostbyname' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
stream/tcp.o: In function `connect2Server_with_af':
tcp.c:(.text+0x14f): warning: Using 'gethostbyname2' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
```

---

### Post by mc4man on 2011-07-02
> **mocha said:**
> I'm having similar problems.  I just updated a box to Natty and doing my usual fresh pulls of x264, ffmpeg, and regular mplayer.  When I pull mplayer2, do a configure and then make it errors out becuase of the libs installed by ffmpeg.  If I --enable-static it gives me this:

```
/usr/bin/ld: cannot find -lenca
/usr/local/lib/libavformat.a(rtsp.o): In function `get_sockaddr':
/usr/src/ffmpeg/libavformat/rtsp.c:120: warning: Using 'getaddrinfo' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
stream/librtsp/rtsp_rtp.o: In function `rtp_setup_and_play':
rtsp_rtp.c:(.text+0xb58): warning: Using 'gethostbyname' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
stream/tcp.o: In function `connect2Server_with_af':
tcp.c:(.text+0x14f): warning: Using 'gethostbyname2' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
```
You could try installing libenca-dev if not already installed, though why not just build mplayer2 the default way?
Basically outlined in post 261, 262, though I'd use checkinstall and likely set it to take the place of mplayer

---

### Post by mocha on 2011-07-02
> **mc4man said:**
> You could try installing libenca-dev if not already installed, though why not just build mplayer2 the default way?
Basically outlined in post 261, 262, though I'd use checkinstall and likely set it to take the place of mplayer

Good question... I was cloning the repo for mplayer2.git instead of mplayer2-build.git.  It works now.

On a related matter, is there any advantage to adding options to the ffmpeg_options file?  Does it control what formats the binary can playback?

---

### Post by andrew.46 on 2011-07-03
> **mocha said:**
> During config it said "No FFmpeg checkout" (even though I just downloaded and installed a git pull of ffmpeg) and it gave the option to download ffmpeg or cancel.  If you choose to download it, a git checkout of ffmpeg gets downloaded into the mplayer source directory.  What's going on, why doesn't it use the ffmpeg on your system?  

Mind you the default MPlayer install has used an internal FFmpeg for some time which I have always thought made for an easier installation (as well as internal libdvdcss and a few others). The change to git by FFmpeg required the change in the original config that you have noted. Packagers such as Debian / Ubuntu like to use shared/system FFmpeg libraries rather than the internal one thus making the whole web of dependencies so much more complex. Interestingly enough the MPlayer used in this guide actually pulls in the original FFmpeg (Michael Niedermeyer's version) while Ubuntu has moved to libav I believe.

---

### Post by mocha on 2011-07-03
> **andrew.46 said:**
> Mind you the default MPlayer install has used an internal FFmpeg for some time which I have always thought made for an easier installation (as well as internal libdvdcss and a few others). The change to git by FFmpeg required the change in the original config that you have noted. Packagers such as Debian / Ubuntu like to use shared/system FFmpeg libraries rather than the internal one thus making the whole web of dependencies so much more complex. Interestingly enough the MPlayer used in this guide actually pulls in the original FFmpeg (Michael Niedermeyer's version) while Ubuntu has moved to libav I believe.

That makes sense now.  I looked back in some old mplayer source directories and noticed the ffmpeg directory.

---

### Post by frifrafry on 2011-07-16
Hi there.

I'm pretty new to building complex packages myself, so I need your help.

I followed this excellent guide to the letter, but get an error during compile of ffmpeg (after auto-fetching it from git).
```
CC    libavcodec/mpegvideo.o
libavcodec/mpegvideo.c: In function 'MPV_frame_start':
libavcodec/mpegvideo.c:1117:32: error: 'Picture' has no member named 'key_frame'
libavcodec/mpegvideo.c:1127:32: error: 'Picture' has no member named 'key_frame'
make[1]: *** [libavcodec/mpegvideo.o] Error 1
make[1]: Leaving directory `/home/friedrich/mplayer_build/mplayer/mplayer/ffmpeg'
make: *** [ffmpeg/libavcodec/libavcodec.a] Fehler 2

```Any ideas?

Thanks in advance.

---

### Post by andrew.46 on 2011-07-16
I am getting the same error. The best idea is to wait a day or so and then recompile, usually such errors are dealt with promptly by either the MPlayer or FFmpeg developers.

---

### Post by andrew.46 on 2011-07-16
Looks like the fix has been placed [in FFmpeg]("http://git.videolan.org/?p=ffmpeg.git;a=commit;h=7bda0c9a82eb3c9a58e0c9f170ac47fe7289f6f7") and compilation will now succeed and certainly has on my system:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer | head -n 1[/COLOR]**
MPlayer SVN-r33883-4.5.3 (C) 2000-2011 MPlayer Team

```

Hopefully you will have a shiny new version of MPlayer very shortly :).

---

### Post by frifrafry on 2011-07-18
Shiny new mplayer, thanks a lot for the quick response.

```
friedrich@Phoenix:~$ mplayer | head -n 1
MPlayer SVN-r33883-4.5.2 (C) 2000-2011 MPlayer Team

```

Though it does say 4.5.2 against your output of 4.5.3 - but it's up and running so it really doesn't matter to much anyway ;)

---

### Post by andrew.46 on 2011-07-18
> **frifrafry said:**
> Though it does say 4.5.2 against your output of 4.5.3 - but it's up and running so it really doesn't matter to much anyway ;)

Good to hear you are up and running :). The 4.5.3 is simply the compiler version:

```

andrew@skamandros~$ gcc --version | head -n 1
gcc (GCC) 4.5.3

```

so means not all that much...

---

### Post by andrew.46 on 2011-07-22
In a very interesting event I see that in my other distro (Slackware) SMPlayer has been replaced with UMPlayer in the [semi-official home of extra build scripts]("http://slackbuilds.org/"):

```

multimedia/smplayer: Removed (replaced by umplayer)
multimedia/umplayer: Added (Universal Media Player)

```

I may very well do the same when Oneiric comes out, unless SMPlayer development fires up again...

---

### Post by rickyrockrat on 2011-08-29
Here's a patch against the latest SVN that adds a crude popup menu when the directory 'VIDEO_TS' directory is found. It gives you an option to ignore and continue to browse, to open with dvd:// or with dvdnav://.  

It compiles and builds just fine on Lucid and Natty, but Natty gives a invalid pointer when shutting down. Just curious if anyone else can check and see if this is causing the same issue with your install.

Forum is here:
[http://ubuntuforums.org/showthread.php?p=11200257](http://ubuntuforums.org/showthread.php?p=11200257)
patch is here:
[mplayer.r34027.gui.dvdnav.patch.txt]("http://ubuntuforums.org/attachment.php?attachmentid=201073&stc=1&d=1314662745")

---

### Post by Andras888 on 2011-09-03
Thank you [andrew.46]("http://ubuntuforums.org/member.php?u=208550") for the step-by-step instructions on compiling SVN Mplayer!  I would not have been able to do this without you!

The other credit goes to the author of [http://blog.avirtualhome.com/2009/05/29/how-to-compile-mplayer-with-vdpau-support-on-ubuntu/](http://blog.avirtualhome.com/2009/05/29/how-to-compile-mplayer-with-vdpau-support-on-ubuntu/) where I found the way to compiling with VDPAU.

1. You need to download and install the correct NVIDIA LInux driver located at  [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

2. You need to download the two NVIDIA Include files from [ftp://download.nvidia.com/XFree86/vdpau/include/vdpau/](ftp://download.nvidia.com/XFree86/vdpau/include/vdpau/) and save them to [COLOR=#000000]**//**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]include[COLOR=#000000]**/**[/COLOR]vdpau/

3. On the first post of this thread, in the instructions, in either the Compiling or Updating section, insert  [FONT=monospace]to the "[/FONT].[COLOR=#000000]**/**[/COLOR]configure" command [COLOR=#660033]"--enable-vdpau" without the parenthesis of course.

The rest you just follow the instructions in the first post of this thread.  It worked for me!
[/COLOR]

---

### Post by andrew.46 on 2011-09-03
Glad the guide has worked for you :). A problem with this guide has always been the fact that I do not have a suitable card to test vdpau so I am always guessing a little. Just be aware though that normally you would not add any *--enable-xxxx* options to the ./configure string, although clearly this was worked for you!

All the best,

Andrew

---

### Post by Andras888 on 2011-09-04
Hi Andrew,

GeForce cards are relatively inexpensive, but even without a card, one could type "mplayer -vo help" to see if vdpau is listed as an available option.  I am sure there are more elegant ways to achieve what I did, including not adding any *--enable-xxxx* options to the ./configure string, and adding the information someplace else.  I know very little about Linux and compiling, so I came to this arguably unrefined solution using only my logic and common sense.

Best wishes and wholehearted thanks for your ongoing project,

Andras

---

### Post by bananagins on 2011-09-10
hi. i installed ffmpeg and x264 following fakeoutdoorsman's guide here:
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

i then installed mplayer using this guide. on the "compiling mplayer" step, i get this message midway through:


Checked out revision 34098.
No FFmpeg checkout, press enter to download one with git or CTRL+C to abort


what was i supposed to do? i did hit enter and i'm not sure what happened. did it install another ffmpeg? 

i'm not really sure if it's right but after that finished, i tried updating ffmpeg and x264 again according to fakeoutdoorsman's guide. however, i think there's a problem because his guide wants me to install libjack-jackd2-0 & libjack-jackd2-dev and remove  jackd1, jackd1-firewire, libjack-dev, & libjack0. but this guide wants to install libjack-dev & libjack0 while removing libjack-jackd2-0 & libjack-jackd2-dev! what do i do? i'm running 10.10. plz help. very confused. :(  :confused:

EDIT: also, reading through this thread, i noticed someone saying they skipped the codec step because they had w32codecs installed. i think i have it installed from medibuntu. should i keep it and skip the codec step? or should i remove it and do the codec step?

---

### Post by andrew.46 on 2011-09-10
> **bananagins said:**
> hi. i installed ffmpeg and x264 following fakeoutdoorsman's guide here:
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

An excellent guide :).


> i then installed mplayer using this guide. on the "compiling mplayer" step, i get this message midway through:
```
Checked out revision 34098.
No FFmpeg checkout, press enter to download one with git or CTRL+C to abort
```
what was i supposed to do? i did hit enter and i'm not sure what happened. did it install another ffmpeg? 

That is the expected behavior. MPlayer be default uses the most recent FFmpeg from within its own source tree rather than an external FFmpeg. You will see the FFmpeg source as a folder within the MPlayer source. This does not interfere with any other copies of FFmpeg on your system.

> i'm not really sure if it's right but after that finished, i tried updating ffmpeg and x264 again according to fakeoutdoorsman's guide. however, i think there's a problem because his guide wants me to install libjack-jackd2-0 & libjack-jackd2-dev and remove  jackd1, jackd1-firewire, libjack-dev, & libjack0. but this guide wants to install libjack-dev & libjack0 while removing libjack-jackd2-0 & libjack-jackd2-dev! what do i do? i'm running 10.10. plz help. very confused. :(  :confused:

Seems a little odd but I would suggest following FakeOutdoorsman's guide and then *re-compiling* MPlayer as suggested in my own guide.


> EDIT: also, reading through this thread, i noticed someone saying they skipped the codec step because they had w32codecs installed. i think i have it installed from medibuntu. should i keep it and skip the codec step? or should i remove it and do the codec step?

If you have the w32codecs installed from Medibuntu you can omit the codecs step but if you do this you would be best to also omit *--codecsdir=/usr/local/lib/codecs* from the MPLayer ./configure string.

I hope this post resolves these issues for you, I will be out of town and without computer access for a week as of today so my next response will be a little tardy....

---

### Post by bananagins on 2011-09-10
> **andrew.46 said:**
> 
Seems a little odd but I would suggest following FakeOutdoorsman's guide and then *re-compiling* MPlayer as suggested in my own guide.

thank you for the reply. i hope i catch you before you leave...

but do you know what the deal is with libjack0, libjack-dev and libjack-jackd2-dev? the ffmpeg guide installs libjack-jackd2-dev but in the process removes libjack0 and libjack-dev. your guide does the opposite. it installs libjack0 and libjack-dev and removes libjack-jackd2-dev. so i guess i'm just confused... which do i need?

right now, the last thing i ran was the ffmpeg guide so, i currently have libjack-jackd2-dev and NOT libjack0 and NOT libjack-dev.

could this cause problems with mplayer? also in the output, it says there are a number of other packages dependent on each library. here's a sample part of the output. there ae many more like these during the output of the second step under "preparation" in your guide:

dpkg: libjack-jackd2-0: dependency problems, but removing anyway as you requested:
 qjackctl depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
  Package libjack0 which provides libjack-0.116 is not installed.
 audacity depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
  Package libjack0 which provides libjack-0.116 is not installed.
...
and so forth, there are like 20-30 of these after audacity.

libjack-jackd2-0 is the one i'm worried about as it was just installed in the ffmpeg guide but it seems to be removed immediately in this guide.


i would like to point out that both programs seem to be working fine. (ran a few test encodes and played some movies) it's just that i wonder if this could cause issues as obviously, i have not tested every single capability/possibility. that and i'm severely OCD.

thanks again.

---

### Post by FakeOutdoorsman on 2011-09-10
You can omit **libjack-jackd2-dev** from the FFmpeg compile guide if you don't intend on using JACK with ffmpeg. I think **libjack-dev** will work too if you do want to use JACK with ffmpeg.

---

### Post by mc4man on 2011-09-10
> **bananagins said:**
> thank you for the reply. i hope i catch you before you leave...

but do you know what the deal is with libjack0, libjack-dev and libjack-jackd2-dev? the ffmpeg guide installs libjack-jackd2-dev but in the process removes libjack0 and libjack-dev. your guide does the opposite. it installs libjack0 and libjack-dev and removes libjack-jackd2-dev. so i guess i'm just confused... which do i need?

If you're not using or plan to use jack then you don't need it at all.
Most recent ubuntu/debian packages that have a libjack* dependency can use either, as can, in this case mplayer

Most how-to's are setup to include all users/uses, so the build-deps reflect that. You can adjust for yourself as needed or desired.

In the case of libjack I'd probably not install the -dev (either version) because I don't use jack or just use the dev of what's more commonly used, right now on 11.10 that's the newer libjack-jackd2. Ultimately it might not matter either way, - you can switch back and forth without other packages being uninstalled if handled correctly , usually in synaptic.
(Assuming your other dependent packages can use either version

Andrew might consider changing that dep to the newer version unless there is some mplayer specific reason not to.
(the build-dep list itself could be culled a bit - installing a -dev package will install the shared lib - edit - there only onlty 2 instances - no big deal

---

### Post by bananagins on 2011-09-11
was there a section on installing UMPlayer from source? i was readng thru the thread and i saw that andrew.46 mentioned it... but i do not see it anywhere. was it taken out? moved somewhere else?

i did notice this ppa: [http://www.webupd8.org/2011/04/umplayer-available-in-webupd8-ubuntu.html](http://www.webupd8.org/2011/04/umplayer-available-in-webupd8-ubuntu.html) but wanted to try installing the development version... should i just go with the ppa?

---

### Post by mc4man on 2011-09-11
You could try this - (there are other ways
```
sudo apt-get build-dep smplayer
```
```
mkdir umplayer_build; cd umplayer_build; \
svn co https://umplayer.svn.sourceforge.net/svnroot/umplayer/umplayer/trunk umplayer
```

```
 cd umplayer; chmod +x create_deb.sh; chmod +x ./debian/rules; \
./create_deb.sh
```

Hopefully on maverick the build deps on smplayer aren't an issue - I'm on 11.10 so can't check
This will build 2 debian packages for you - screen
The 1st. thing I do here is lower the cache for local files to 0, causes an issue here as is set by default

---

### Post by andrew.46 on 2011-09-17
> **bananagins said:**
> was there a section on installing UMPlayer from source? i was readng thru the thread and i saw that andrew.46 mentioned it... but i do not see it anywhere. was it taken out? moved somewhere else?

The guide was getting a bit scattered so I have decided to refocus on simply building the commandline player and leave the choice of gui to other enthusiasts, I see mc4man has given you some excellent guidance :).

I will revisit the guide when Oneiric comes out in a month and streamline a few other things as well, including the choice of '-dev' files, so the guide can continue being developed despite my many commitments to other areas.

---

### Post by Andras888 on 2011-09-18
Could someone please point me to a good svn SMplayer building page?

---

### Post by mc4man on 2011-09-18
> **Andras888 said:**
> Could someone please point me to a good svn SMplayer building page?
svn stuff
[http://sourceforge.net/apps/mediawiki/smplayer/index.php?title=Download_from_SVN](http://sourceforge.net/apps/mediawiki/smplayer/index.php?title=Download_from_SVN)
build
[http://sourceforge.net/apps/mediawiki/smplayer/index.php?title=Building_on_Linux](http://sourceforge.net/apps/mediawiki/smplayer/index.php?title=Building_on_Linux)

I'd just do as posted above for umplayer replacing umplayer w/ smplayer in the 6 instances  - (only 5 really needed, the current smplayer source is always on the umplayer.svn ..

---

### Post by andrew.46 on 2011-09-18
A decent Apple ProRes decoder is now available for the svn MPlayer which is great news especially for 64bit installations (32bit installations have been able to use a windows codec). Because of a licensing issue it is necessary at the moment to add:

```

  --disable-libopencore_amrnb \
  --disable-libopencore_amrwb

```

to the MPlayer ./configure string. I have not altered this in the main guide yet as this situation will probably change shortly. One option is that the libopencore libraries will by default *not* be used.

There is an admittedly uninspiring sample here for testing:

```
wget http://samples.mplayerhq.hu/V-codecs/HCPA/AppleProRes422.mov
```

and below is the commandline output using ffprores:

```

andrew@skamandros~/Desktop$**[COLOR="Red"] mplayer -vc ffprores AppleProRes422.mov [/COLOR]**
MPlayer SVN-r34111-4.5.2 (C) 2000-2011 MPlayer Team
Loading extension-related profile 'extension.mov'

Playing AppleProRes422.mov.
ISO: File Type Major Brand: Original QuickTime
Quicktime/MOV file format detected.
[mov] Video stream found, -vid 0
[mov] Audio stream found, -aid 2
[mov] Audio stream found, -aid 3
[mov] Audio stream found, -aid 4
[mov] Audio stream found, -aid 5
[mov] Audio stream found, -aid 6
[mov] Audio stream found, -aid 7
[mov] Audio stream found, -aid 8
[mov] Audio stream found, -aid 9
VIDEO:  [apch]  720x486  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in ./
==========================================================================
[B][COLOR="Red"]Forced video codec: ffprores
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffprores] vfm: ffmpeg (FFmpeg ProRes, GPL v2 only)[/COLOR][/B]
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 48000 Hz, 1 ch, s24le, 1152.0 kbit/100.00% (ratio: 144000->144000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [oss] 48000Hz 1ch s16le (2 bytes per sample)
Starting playback...
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x89a6760]BICUBIC scaler, from yuv422p10le to yuv420p using MMX2
VO: [xv] 720x486 => 720x486 Planar YV12 
A:  11.5 V:  11.5 A-V:  0.002 ct:  0.002 345/345 64% 10%  0.1% 0 0 


Exiting... (End of file)

```

Does anybody have a better sample available?

---

### Post by andrew.46 on 2011-09-26
OK Oneiric version in place now. Major change is with the dependencies where I have eliminated many of the libraries that provide external codecs where perfectly good libavcodec playback is possible. The Samba libraries have been omitted as well until somebody really wants it there :). Any and all comments welcome, on my system this version of the guide produces a nice tight and capable MPlayer installation... hopefully on yours as well!!

BTW I cannot believe how many years I have been running versions of this MPlayer guide... it still remains a lot of fun :).

---

### Post by andrew.46 on 2011-10-22
Added in the repository libbluray development library. Not worth tracking the git version at the moment but perhaps this will be useful for some?

---

### Post by Linuxisfast on 2011-10-22
Hi Andrew, any chance of instructions of compiling mplayer with vaapi and amd cards?

---

### Post by andrew.46 on 2011-10-24
> **Linuxisfast said:**
> Hi Andrew, any chance of instructions of compiling mplayer with vaapi and amd cards?

Unfortunately my own hardware is very, very basic and I usually only write about things that I can test :(.

---

### Post by Linuxisfast on 2011-10-24
> **andrew.46 said:**
> Unfortunately my own hardware is very, very basic and I usually only write about things that I can test :(.

Thanks Andrew, you have done enough. :)

---

### Post by andrew.46 on 2011-10-25
> **rajesh.kalapura said:**
> Nice tutorial,want to check now itself..Thanks again.:)

I hope it works well for you :). Perhaps add a gui such as SMPlayer or UMPlayer as well...

---

### Post by ron999 on 2011-10-30
Hi Andrew
If I needed to compile **Mencoder** as well as mPlayer using this How-to ...
will I need to change the config command to:-
```
./configure --confdir=/etc/mplayer --codecsdir=/usr/local/lib/codecs
```
Or something else?

And what about the "sudo checkinstall..." command?
Will the same command automatically install Mencoder too, or does it need to be changed?

---

### Post by andrew.46 on 2011-10-30
Hi Ron! Yes, leave out both the *--disable* commands and of course make sure you have the -dev files for faac and lame installed + the current x264. As for the checkinstall command I have not really looked into this but I remember a few people were using a *--provides* option though I am not sure if the Ubuntu package management system actually honours this.

---

### Post by andrew.46 on 2011-11-10
I have finally added in the necessary syntax to generate the html help files and incorporated this within the checkinstall installation. Upstream has changed a few things with the generation and hopefully have finished these changes now! Any problems or comments feel free to post here...

---

### Post by ron999 on 2011-11-18
> **andrew.46 said:**
> ...I have not really looked into this but I remember a few people were using a *--provides* option though I am not sure if the Ubuntu package management system actually honours this.

Hi Andrew
I didn't have any luck with "--provides".
Package management system completely ignored this.:mad:
So although MEncoder was compiled and installed, Synaptic had no record of it.:rolleyes:

I have now compiled and installed mPlayer with :-
```
./configure --confdir=/etc/mplayer --disable-mencoder --disable-x264
```
And:-
```
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname mplayer \
--pkgversion "2:1.0~svn$(LC_ALL=C svn info 2> /dev/null | grep Revision | cut -d' ' -f2)" \
--backup=no --default --deldoc=yes && \ 
make distclean
```
Then I have compiled and installed MEncoder with:-
```
./configure --confdir=/etc/mencoder --disable-mplayer
```
And:-
```
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname mencoder \
--pkgversion "2:1.0~svn$(LC_ALL=C svn info 2> /dev/null | grep Revision | cut -d' ' -f2)" \
--backup=no --default --deldoc=yes && \ 
make distclean
```

There was a problem when installing MEncoder, it needed to overwrite some of mPlayer's files.
Had to temporarily edit checkinstallrc:- 
**DPKG_FLAGS="--force-overwrite"**

It seems a bit dumb doing two separate compiles, but is OK till somebody has a better idea.8-)

---

### Post by andrew.46 on 2011-11-18
You have bumped into a shortcoming of using checkinstall in the manner I have suggested in this guide. A formal debian package would be a better idea but I will admit to a certain loathing of the complexity of the whole debian packaging system :(.

---

### Post by FakeOutdoorsman on 2011-11-18
> **andrew.46 said:**
> A formal debian package would be a better idea but I will admit to a certain loathing of the complexity of the whole debian packaging system :(.

I tried making a formal debian package once I think and that was enough.

---

### Post by mc4man on 2011-11-18
> **ron999 said:**
> Hi Andrew
I didn't have any luck with "--provides".
Package management system completely ignored this.:mad:
So although MEncoder was compiled and installed, Synaptic had no record of it

Ron - synaptic only will show an installed package, in this case mplayer

The test of the '--provides '  checkinstall option is if a mencoder dependency is satisfied when installing a package that depends on mencoder.

So for example - mencoder has never been installed here

```
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/mplayer_build" \
   --pkgname mplayer --provides "mplayer,mencoder" --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "2:1.0~svn$(LC_ALL=C svn info 2> /dev/null | \
     grep Revision | cut -d' ' -f2)" 
```

Then picking a random  package that depends on mencoder

```
$ sudo apt-get install h264enc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bsd-mailx faac gpac lame libao-common libao4 libboost-filesystem1.46.1 libboost-regex1.46.1 libboost-system1.46.1
  libgpac0.4.5 liblzo2-2 libopenjpeg2 lsdvd mkvtoolnix ogmtools postfix pv vorbis-tools
ect...


```

No mention of mencoder, the dep was provided by the mplayer build

---

### Post by ron999 on 2011-11-19
> **mc4man said:**
> 
...The test of the '--provides '  checkinstall option is if a mencoder dependency is satisfied when installing a package that depends on mencoder...

```
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/mplayer_build" \
   --pkgname mplayer [COLOR="Red"]--provides "mplayer,mencoder"[/COLOR] --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "2:1.0~svn$(LC_ALL=C svn info 2> /dev/null | \
     grep Revision | cut -d' ' -f2)" 
```

Hi mc4man
Thanks for your reply.
I previously used [COLOR="Red"]--provides mencoder[/COLOR] with checkinstall.
Then when I tried to install acidrip it wanted to install mencoder again.
I will try again, this time with [COLOR="Red"]--provides "mplayer,mencoder"[/COLOR].
Watch this space...

---

### Post by ron999 on 2011-11-19
... this space..
Hi mc4man
Using [COLOR="Red"]--provides "mplayer,mencoder"[/COLOR] has done the job.:D
Like you said, MEncoder does not show as installed in Synaptic.
But apt-get knows it's there now.
Thanks again.:guitar:

```
ron@ubuntu:~$ sudo apt-get install acidrip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  lsdvd
The following NEW packages will be installed
  acidrip lsdvd
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 80.1 kB of archives.
After this operation, 389 kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

### Post by andrew.46 on 2011-11-19
Hmmmmm.... almost tempting to add x264, faac + lame development libraries and MEncoder again....

---

### Post by mc4man on 2011-11-19
> **andrew.46 said:**
> Hmmmmm.... almost tempting to add x264, faac + lame development libraries and MEncoder again....

Ron999 may know better but just to mention - what may come up is that a mencoder enabled mplayer build may fail if x264* isn't current, so at times users would 1st. need to build a new x264 before mplayer

@ron999 - didn't realize ckinstall had that option. There is a 'flaw' in default ck.install when subsequent ck.install packages write to the same file, often seen with icon-theme.cache

Another alternative is if the install fails to use dpkg
sudo dpkg -i --force overwrite /path/to/new/package

I'd file a bug on but considering they still haven't 'fixed' that fstrans nonsense in ubuntu I'm not gong to bother

---

### Post by mckoz on 2011-12-27
Andrew, I'm a bit of newbie, mostly used to FreeBSD and the dark side.  Would you mind relaying the code I could change to use ffmpeg-mt, so I can take advantage of a servers multiple CPUs?

Thanks in advance,  David

---

### Post by andrew.46 on 2011-12-27
Hi David,

The FFmpeg-mt code has been absorbed into FFmpeg for a little while now and you will find that the default installation of the svn MPlayer downloads the latest git FFmpeg so no special actions required by you.

Andrew

---

### Post by mckoz on 2011-12-27
Thanks Andrew!  I'm hopefully building a media server for the house utilizing PS3 Media Server, and since this is at least the 10th time I've tried it (using various platforms), it's very helpful to have tutorials such as yours and a response to questions as well...

Cheers,

David

---

### Post by gillza on 2011-12-31
Andrew,

Thank you very much for this guide yet again. I have switched to Debian and managed to install mplayer on squeeze following your guide. So far all seems to be working great!

---

### Post by andrew.46 on 2011-12-31
> **gillza said:**
> Thank you very much for this guide yet again. I have switched to Debian and managed to install mplayer on squeeze following your guide. So far all seems to be working great!

Good to hear the guide is still proving useful :).

---

### Post by andrew.46 on 2012-01-03
I am a long way from Ubuntu at the moment but I thought I would leave a quick notice of the release of a new SMPlayer version. Compile your own which is not that difficult or download from rvm's ppa:

```

sudo add-apt-repository ppa:rvm/smplayer
sudo apt-get update
sudo apt-get install smplayer

```

Great to see a new release!

---

### Post by Segofam on 2012-01-04
> **andrew.46 said:**
> ...or download from rvm's ppa:

```

sudo add-apt-repository ppa:rvm/smplayer
sudo apt-get update
sudo apt-get install smplayer

```Great to see a new release!

Thanks Andrew :)

---

### Post by gillza on 2012-01-09
Just noticed something odd.

I have Nvidia powered laptop: G53SX-A1 (GeForce 560M)

Mplayer does not work with 10bit videos when VDPAU is the output. When I switch the output to VC everything is smooth again. 

All other videos work fine with VDPAU as the output driver.

---

### Post by andrew.46 on 2012-01-09
> **gillza said:**
> Mplayer does not work with 10bit videos when VDPAU is the output. When I switch the output to VC everything is smooth again. 

I believe this is a known limitation with MPlayer and vdpau:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2011-November/083674.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2011-November/083674.html)

Perhaps have a look at the vlc video output and see if it switches?

---

### Post by gillza on 2012-01-10
> **andrew.46 said:**
> I believe this is a known limitation with MPlayer and vdpau:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2011-November/083674.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2011-November/083674.html)

Perhaps have a look at the vlc video output and see if it switches?

My apologies. The output was switched to XV no VC :)

---

### Post by andrew.46 on 2012-02-03
New version of SMPlayer out now, well worth a look :). Note the youtube playback...

---

### Post by Linuxisfast on 2012-02-03
> **andrew.46 said:**
> New version of SMPlayer out now, well worth a look :). Note the youtube playback...

On it, works real nice, youtube as well. Thank heavens RVM started developing it again. I consider this to be an excellent mplayer front end.

---

### Post by andrew.46 on 2012-02-03
> **Linuxisfast said:**
> I consider this to be an excellent mplayer front end.

Seconded :).

---

### Post by gert3d on 2012-03-03
@ Andrew
I found this thread when searching for ways of displaying HD clips from my camera on an older laptop, using CrunchBang Linux on an USB stick. The VLC media player would make a begin playing a clip, but stalled because my system was too slow. 
So then I ran across the possibility of running mplayer-gui, but that would not install using apt-get install, since it has been discontinued. (and that was more or less what I am capable of doing).

Then I came across your initial manual (October 29th, 2009), which I just copied and pasted, and got stuck at the svn stuff. Reading on I arrived in 2010 and your updated guide (July 30th, 2010). This all worked an I got mplayer working!

You'll notice that I have no clue what I am doing exactly, and the laptop was chewing away, using 3Gb of the USB stick (df says 23% -> 42%). And now the reason for writing in this thread:
1. my compliments for writing the guide in a manner that I could even use it.
2. when playing 1080p clips from my camera (Toshiba Camileo X400) the audio goes realtime, but the video is lagging, resulting the audio to complete earlier. I realise that this is probably all due to the speed of my laptop (thinkpad r50p _Pentium M_ 2 GHz CPU) but it is much better than skipping frames. 

Is there any improvement to be expected from mplayer2, or other settings?
Thanks!

---

### Post by gillza on 2012-03-04
Andrew,

I have experimentally installed 12.04 beta 1 and tried installing mplayer following the guide. 

Everything seems to work up to mplayer compilation which fails with error:

```
./version.sh `cc -dumpversion`
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls  -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -fno-tree-vectorize -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -D__STDC_CONSTANT_MACROS -D__STDC_FORMAT_MACROS -D__STDC_LIMIT_MACROS -Ilibdvdread4 -I. -Iffmpeg  -D_REENTRANT -I/usr/include/directfb -I/usr/include/     -D_REENTRANT    -I/usr/include/freetype2 -I/usr/lib/live/liveMedia/include                   -I/usr/lib/live/UsageEnvironment/include                   -I/usr/lib/live/BasicUsageEnvironment/include                   -I/usr/lib/live/groupsock/include -c -o libmpdemux/demux_rtp.o libmpdemux/demux_rtp.cpp
libmpdemux/demux_rtp.cpp: In function 'char* openURL_rtsp(RTSPClient*, const char*)':
libmpdemux/demux_rtp.cpp:99:20: error: 'class RTSPClient' has no member named 'describeWithPassword'
libmpdemux/demux_rtp.cpp:101:20: error: 'class RTSPClient' has no member named 'describeURL'
libmpdemux/demux_rtp.cpp: In function 'demuxer_t* demux_open_rtp(demuxer_t*)':
libmpdemux/demux_rtp.cpp:155:82: error: invalid conversion from 'int' to 'const char*' [-fpermissive]
/usr/lib/live/liveMedia/include/RTSPClient.hh:36:22: error:   initializing argument 2 of 'static RTSPClient* RTSPClient::createNew(UsageEnvironment&, const char*, int, const char*, portNumBits)' [-fpermissive]
libmpdemux/demux_rtp.cpp:155:82: error: invalid conversion from 'const char*' to 'int' [-fpermissive]
/usr/lib/live/liveMedia/include/RTSPClient.hh:36:22: error:   initializing argument 3 of 'static RTSPClient* RTSPClient::createNew(UsageEnvironment&, const char*, int, const char*, portNumBits)' [-fpermissive]
libmpdemux/demux_rtp.cpp:155:82: error: invalid conversion from 'int' to 'const char*' [-fpermissive]
/usr/lib/live/liveMedia/include/RTSPClient.hh:36:22: error:   initializing argument 4 of 'static RTSPClient* RTSPClient::createNew(UsageEnvironment&, const char*, int, const char*, portNumBits)' [-fpermissive]
libmpdemux/demux_rtp.cpp:245:21: error: 'class RTSPClient' has no member named 'setupMediaSubsession'
libmpdemux/demux_rtp.cpp:257:24: error: 'class RTSPClient' has no member named 'playMediaSession'
libmpdemux/demux_rtp.cpp: In function 'void teardownRTSPorSIPSession(RTPState*)':
libmpdemux/demux_rtp.cpp:646:27: error: 'class RTSPClient' has no member named 'teardownMediaSession'
libmpdemux/demux_rtp.cpp: In function 'char* openURL_rtsp(RTSPClient*, const char*)':
libmpdemux/demux_rtp.cpp:103:1: warning: control reaches end of non-void function [-Wreturn-type]
make: *** [libmpdemux/demux_rtp.o] Error 1

```

I'll start googling for solution :)

---

### Post by andrew.46 on 2012-03-05
I have just built the latest:

```

andrew@skamandros~$**[COLOR="Red"] mplayer | head -n 1[/COLOR]**
MPlayer SVN-r34799-4.6.2 (C) 2000-2012 MPlayer Team

```

Admittedly not on Precise but it compiled well enough. Perhaps* svn up* may cure the problem?

---

### Post by mc4man on 2012-03-05
> **gillza said:**
> Andrew,

I have experimentally installed 12.04 beta 1 and tried installing mplayer following the guide. 

Everything seems to work up to mplayer compilation which fails with error: 

That seems to be what will happen with the latest live555 when doing in 12.04 - 
The repo liblivemedia works ok or one could not build live555 support if it doesn't clear up or some other solution.

---

### Post by gillza on 2012-03-05
mc4man, andrew.46,

Thank you. I will try compiling it today again.

---

### Post by andrew.46 on 2012-03-05
> **gillza said:**
> Thank you. I will try compiling it today again.

This may help:

```

------------------------------------------------------------------------
andrew@skamandros~$ **[COLOR="DarkRed"]svn log svn://svn.mplayerhq.hu/mplayer/trunk -r 34800[/COLOR]**
------------------------------------------------------------------------
r34800 | cehoyos | 2012-03-06 05:14:38 +1100 (Tue, 06 Mar 2012) | 4 lines

Fix compilation with new LIVE555 libraries.

Patch by Marty Jack, martyj19 comcast net 

------------------------------------------------------------------------

```

---

### Post by andrew.46 on 2012-03-07
Hmmm.... I am having a little trouble with live555 as well. Perhaps for Precise the repository live555 might be enough, I note that it is reasonably recent anyway: 2011.12.23. I will do this for the next version of this guide...

---

### Post by gillza on 2012-03-07
I tried compiling again with no improvement. Will try without building live555.



p.s.
Installed with Precise version of live555 and mplayer compiled ok. Just tried it and everything seems to work.

Thank you.

---

### Post by andrew.46 on 2012-03-08
I have retreated to live555.2011.12.23 on my other system and I think this is a better option than chasing live555 changes which for usage with MPlayer and vlc are just not worth the pain... Anybody wishing to follow my example will find the file here:

[http://live555sourcecontrol.googlecode.com/files/live.2011.12.23.tar.gz](http://live555sourcecontrol.googlecode.com/files/live.2011.12.23.tar.gz)

---

### Post by andrew.46 on 2012-03-15
Those who own bluray drives may be interested to see this:

[http://vlc-bluray.whoknowsmy.name/](http://vlc-bluray.whoknowsmy.name/)

Not sure of the legal status of this in *your* country so don't break any laws...

---

### Post by BicyclerBoy on 2012-03-15
You can just get libaacs with git from videolan website, compile & install.
Works with MythTV..

---

### Post by andrew.46 on 2012-03-15
> **BicyclerBoy said:**
> You can just get libaacs with git from videolan website, compile & install.

And the keys database?

---

### Post by BicyclerBoy on 2012-03-16
doom9 is a wonderful place..
Look for aacskeys & dumpHD.
These threads document a fascinating reverse engineering effort.

Note the slight difference in the formatting of the keys database between aacskeys & libaacs.

I add my extracted keys (or from 'external' database) into a working key database (for mythtv) as needed.

I guess that mplayer is built with libbluray & this dynamically loads libaacs if present.

---

### Post by andrew.46 on 2012-03-16
Thanks for that information BicyclerBoy! My newly built computer does not have a bluray drive but I see[ bluray readers/writers for $100 on ebay]("http://www.ebay.com.au/itm/LG-BH12LS38-Blu-Ray-Burner-12xBD-R-12xBD-RE-2xBD-RE-DL-16xDVD-R-8xDVD-R-DL-OEM-/140630716216?pt=AU_Components&hash=item20be3e6f38") so I suspect that when I get back from my holiday I may very well invest in one. I suspect that in this guide and my vlc one I will not be able to publish too many details about aacskeys but looks like details about libbluray and libaacs themselves should not upset anyone. Interesting times indeed :).

**Edit:** A gratuitous gkrellm screenshot showing my new 8 core computer (AMD FX-8150) compiling the latest svn MPlayer using *-j 12*. abcde is also ripping and converting in the background :).

---

### Post by andrew.46 on 2012-03-18
I have filched the bluray information from my own vlc-git guide and placed it on the MPlayer guide. I don't have a blueray drive yet (should have in 3-4 weeks) so I will be keen to hear of any problems with this build.

**Edit:** Somewhat belatedly added in a Live555 version that MPlayer is happy with...

---

### Post by mc4man on 2012-03-22
> r34823 | cehoyos | 2012-03-22 17:04:32 -0400 (Thu, 22 Mar 2012) | 1 line

Support FFmpeg WMA lossless decoder.

Will have to give a test

Edit: works fine (ffwmall

(- currently an opencore* issue, did build without it

---

### Post by andrew.46 on 2012-04-01
The very best of 'Welcome Home!' presents:

```

andrew@skamandros~/media/testing$ mplayer luckynight.wma 
MPlayer SVN-r34836-4.6.2 (C) 2000-2012 MPlayer Team

Playing luckynight.wma.
libavformat version 54.3.100 (internal)
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 title: Lucky Night
 author: Jody Marie Gnant
 copyright: 1995 Sirius Publishing
 comments: 1-minute song sample demonstrating Windows Media lossless audio compression
Load subtitles in ./
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 54.12.100 (internal)
AUDIO: 44100 Hz, 2 ch, s16le, 868.7 kbit/61.55% (ratio: 108583->176400)
**[COLOR="Red"]Selected audio codec: [ffwmall] afm: ffmpeg (WMA lossless audio (FFmpeg))[/COLOR]**
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  60.6 (01:00.5) of 60.5 (01:00.4)  2.7% 


Exiting... (End of file)

```

:)

---

### Post by mc4man on 2012-04-07
Just to note - starting with checkinstall 1.6.2-3ubuntu1 fstrans is now disabled by default again

* I'm gathering that if the wiki deal proceeds that a link to & support of can remain here, ect.

---

### Post by andrew.46 on 2012-04-08
April 29th 2012

Due to the upcoming changes to this guide's old home on these Forums I have, with much regret, moved this guide to my own personal website:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://www.andrews-corner.org/mplayer.html](http://www.andrews-corner.org/mplayer.html)

where I have just now released an updated version for Ubuntu 12.04, Precise Pangolin.

I attach a complete copy of the older guide as *mplayer_guide.gz* in case anybody wishes to make a wiki, blog, web page etc of this guide as it was for Oneiric Ocelot.

Andrew

---

### Post by andrew.46 on 2012-04-09
OK I have archived the guide (attached to the first post) [...]

If anybody wishes to produce a wiki page from this guide please go ahead, all the information is contained as *mplayer_guide.gz* attached to the first post of this thread.

Andrew

---

### Post by Jose Catre-Vandis on 2012-04-09
Actions speak louder than words, eh ?  :) I may not be far behind you......

---

### Post by andrew.46 on 2012-04-09
Mind you I have also converted a couple of guides, one today and a few less recently:

[https://help.ubuntu.com/community/Leafnode2](https://help.ubuntu.com/community/Leafnode2)
[https://help.ubuntu.com/community/slrn](https://help.ubuntu.com/community/slrn)
[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

But these are guides that work fine in a wiki environment, others such as my MPLayer and vlc guides are not suited. Personal website is ok, an atmosphere such as T&T would be better for these...

---

### Post by andrew.46 on 2012-04-14
> **mc4man said:**
> (- currently an opencore* issue, did build without it

Looks like the --disable-mencoder option is implicated, certainly builds ok if mencoder builds as well. I have [asked for help....]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2012-April/084507.html").

BTW you may have noticed that opencore-amr has released a new version with some small but worthwhile changes:

```

0.1.3
 - Adjusted libtool flags for building DLLs for windows
 - Update to the latest upstream opencore source
 - Updated and improved example applications
 - Add options for enabling the arm inline assembly
 - Add options for disabling the encoder or decoder in the amrnb library
 - Avoid dependencies on libstdc++ if building the source as C
 - Hide internal symbols in shared libraries
 - Minor tweaks
 - Remove old static makefiles and corresponding build scripts

```

Looks like this will not be in Precise, but it is installed on my system :)

---

### Post by sudodus on 2012-04-14
Hi!

I found this thread, and hope to get some help from you. I have used linux for a while, and I can help people with simple tasks, but the kind of stuff you are discussing in this thread is way beyond my knowledge and skill.

I'm testing Precise beta (12.04) with particular focus on the i386 version, to make sure it will work on old computers, for example without pae. The default media player in Lubuntu is mplayer, but unfortunately there is a bug in the version that comes with the iso files. It works well on my two 64-bit computers, but doesn't work on my

- IBM Thinkpad T41 without pae and
- Dell Dimension 4600 (P4, 2.8 GHz)

*Yes*, I have booted all computers from the same USB pendrive made from the same 32-bit 'i386' iso file. And *yes*, I have installed vlc into this precise beta version, and it works on all my computers, but vlc needs more horsepower than mplayer to play video with the same quality.

See more details in this link [[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1955027_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1955027")
You find the daily build here [[COLOR="Red"]_http://iso.qa.ubuntu.com/_[/COLOR]]("http://iso.qa.ubuntu.com/")
and the lubuntu iso file in particular for example via the following command
```
rsync -tzhhP rsync://cdimage.ubuntu.com/cdimage/lubuntu/daily-live/current/precise-desktop-i386.iso .
```

Can you help solving this problem, please!

1. The software issue
- to find the problem
- to make mplayer work

2. The logistics issue
- to make the the development team aware of the problem
- to make them update the included version

We are many users who are happy that we can select and update the software, but we are far from developing or even compiling from source code.

best regards
sudden

---

### Post by andrew.46 on 2012-04-14
You have come at a time when this thread is slowly withering away I'm afraid, and the guide itself gone :(. I see the nub of the error on your launchpad page:

```
MPlayer interrupted by signal 4 in module: read_subtitles_file
- MPlayer crashed by an 'Illegal Instruction'.
  It usually happens when you run it on a CPU different than the one it was
  compiled/optimized for.
  Verify this!
```

The 'different cpu' thing would be unusual as most MPlayer packages can have the option *--enable-runtime-cpudetection* which runs MPlayer according to the capabilities of the host system. I am not sure if the Lubuntu package is compiled in this way. Have you tried running MPlayer without subtitles in either of the following ways:

```

mplayer -noautosub majaa.mp4
mplayer -nosub majaa.mp4

```

This might eliminate a few possibilities. And on top of the slow withering of this thread I am afraid that I am not terribky familiar with MPlayer2, I use and describe the original MPlayer :(.

A final thought: have you thought of getting on irc and going to Freenode #lubuntu? You might get some lubuntu-centric advice perhaps...

---

### Post by sudodus on 2012-04-14
> **andrew.46 said:**
> You have come at a time when this thread is slowly withering away I'm afraid, and the guide itself gone :(. I see the nub of the error on your launchpad page:

```
MPlayer interrupted by signal 4 in module: read_subtitles_file
- MPlayer crashed by an 'Illegal Instruction'.
  It usually happens when you run it on a CPU different than the one it was
  compiled/optimized for.
  Verify this!
```

The 'different cpu' thing would be unusual as most MPlayer packages can have the option *--enable-runtime-cpudetection* which runs MPlayer according to the capabilities of the host system. I am not sure if the Lubuntu package is compiled in this way. Have you tried running MPlayer without subtitles in either of the following ways:

```

mplayer -noautosub majaa.mp4
mplayer -nosub majaa.mp4

```

This might eliminate a few possibilities. And on top of the slow withering of this thread I am afraid that I am not terribky familiar with MPlayer2, I use and describe the original MPlayer :(.

A final thought: have you thought of getting on irc and going to Freenode #lubuntu? You might get some lubuntu-centric advice perhaps...
Thank you for trying to help.

Both your commands lead to the following output: ```
Otillåten instruktion (minnesutskrift skapad)
```
which means illegal instruction (memory output written). But where is that (is it a core dump)? by the way, I made the clip(s) myself with a camera and then I have converted them with avidemux and/or ffmpeg. There are no subtitles, only the video and audio streams.

It makes a difference, since the output without the sub options is as follows:
```
MPlayer2 UNKNOWN (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 00007_720-50p.mp4.
Detected file format: QuickTime/MPEG-4/Motion JPEG 2000 format (libavformat)
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang und
VIDEO:  [H264]  1280x720  24bpp  50.000 fps  4125.5 kbps (503.6 kbyte/s)
Clip info:
 major_brand: isom
 minor_version: 512
 compatible_brands: isomiso2avc1mp41
 creation_time: 1970-01-01 00:00:00
 encoder: Lavf52.64.2
Load subtitles in .


MPlayer interrupted by signal 4 in module: read_subtitles_file
- MPlayer crashed by an 'Illegal Instruction'.
  It usually happens when you run it on a CPU different than the one it was
  compiled/optimized for.
  Verify this!
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

---

### Post by andrew.46 on 2012-04-14
Interesting... can you post the troublesome file somewhere so I can have a look?

---

### Post by sudodus on 2012-04-14
> **andrew.46 said:**
> I am afraid that I am not terribky familiar with MPlayer2, I use and describe the original MPlayer :(.

A final thought: have you thought of getting on irc and going to Freenode #lubuntu? You might get some lubuntu-centric advice perhaps...
I don't know the difference. Would it be possible to install the original MPlayer from the ubuntu repositories? Or would I have to compile it. It need not be the latest and greatest version, as long as it runs in oneiric and/or precise.

I have no irc account, and I have not done any programming for decades, so maybe I wouldn't ask the right questions or maybe I wouldn't understand the answers. But if that's the best way to go, maybe I'll try ...

---

### Post by sudodus on 2012-04-14
> **andrew.46 said:**
> Interesting... can you post the troublesome file somewhere so I can have a look?

Which file? The dump file, (where would it be written)? Or the video clip?

---

### Post by andrew.46 on 2012-04-14
Video clip would be great.

---

### Post by sudodus on 2012-04-14
> **andrew.46 said:**
> Video clip would be great.
Did you get the link, and could you download the file?

---

### Post by andrew.46 on 2012-04-14
Thanks for the clip :). There is absolutely nothing wrong with the clip that I could find and certainly it played well enough on my 64bit non-ubuntu system. I will download the Lubuntu live cd but because of bandwidth restrictions this will take a little while ---> a couple of days as I am going back to work as well. In the meantime you should chase up the Lubuntu developers as well :).

---

### Post by sudodus on 2012-04-14
Hi again Andrew,

Now I have done some more testing. I had a thorough look at the available mplayer versions via Synaptic and found that both mplayer and mplayer2 were installed. But that is the names of the packages. The executable file (the command) is always the same. I guess mplayer2's mplayer somehow puts a link before the original mplayer in PATH. Anyway, after removing mplayer2, I had 'your' mplayer. The output of
```
mplayer -version
``` switched from something including mplayer2 to
```
$ mplayer -version
Unknown option on the command line: -version
Error parsing option on the command line: -version
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
```
Does this tell you anything about the version (if it is reasonably up to date and efficient according to your standards)?

And it was not buggy. 'Your' mplayer can play video, the clip in the link as well as other clips. But I found that it is actually not as efficient as vlc, while on the 64-bit computers, this same 32-bit mplayer2 was outperforming vlc. Could it be that mplayer2 is using some speed boost function, that is not available in old CPUs?

What do you think?

best regards
sudden

---

### Post by sudodus on 2012-04-14
> **andrew.46 said:**
> Thanks for the clip :). There is absolutely nothing wrong with the clip that I could find and certainly it played well enough on my 64bit non-ubuntu system. I will download the Lubuntu live cd but because of bandwidth restrictions this will take a little while ---> a couple of days as I am going back to work as well. In the meantime you should chase up the Lubuntu developers as well :).

Thanks for your help :-)

I was writing my previous post while you posted this one. I will try to find some way to the Lubuntu developers...

---

### Post by mc4man on 2012-04-15
Tried lubuntu last night (very quick  - I tend forget how fast Ubuntu used to be

mplayer2 is installed by default so if building an mplayer(svn) you'd want to remove it first

Just to note - on nvidia systems the svn mplayer will default to a -vo vdpau
If you're playing vdpau supported files without  specifying the correct -vc either directly in cli or thru the config file then that can impact performance. If not going to use vdpau the use a -vo xv

---

### Post by sudodus on 2012-04-16
> **mc4man said:**
> Tried lubuntu last night (very quick  - I tend forget how fast Ubuntu used to be

mplayer2 is installed by default so if building an mplayer(svn) you'd want to remove it first

Just to note - on nvidia systems the svn mplayer will default to a -vo vdpau
If you're playing vdpau supported files without  specifying the correct -vc either directly in cli or thru the config file then that can impact performance. If not going to use vdpau the use a -vo xv

Thank you mc4man,

I have already removed mplayer2 as you can see in post #370, and the original mplayer works, but I hope it can be more efficient.

Your tips will also be valuable, when I run mplayer in higher-end computers, that support vdpau. Now I am focusing on lubuntu for low end computers, trying to get decent graphics performance without any vdpau capability.

I played with the video driver selection and tried to get better performance. Your tip [FONT="Courier New"][SIZE="3"]-vo xv[/SIZE][/FONT] doesn't improve the playback quality significantly. I was not able to reach the level of vlc (in the same lubuntu 12.04 daily build version).

My experience is that it should be possible to do better with mplayer. I have tried several options, for example
```
-lavdopts fast:skiploopfilter=nonref
```
What other options should I try?

---

### Post by Cincinnatux on 2012-04-19
> **andrew.46 said:**
> April 09 2012

It is with great sadness, after almost 5 years of work, that I remove this guide and place it on my personal web site:


Why not simply move it to the Wiki?  (Sorry if I'm being ignorant here; I honestly don't know what's really going on between the forum and the wiki regarding tutorials, just that they're 'moving'.)

---

### Post by andrew.46 on 2012-04-21
I have left the full guide attached to the first post in this thread so anybody who wishes can add it to the wiki :).

---

### Post by andrew.46 on 2012-04-23
New version of SMPlayer released (0.8.0), good to see development is continuing :).

---

### Post by Jose Catre-Vandis on 2012-04-28
Thank you Andrew. Just run the guide on my 12.04 Xubuntu installation, works great :)

---

### Post by andrew.46 on 2012-04-28
> **Jose Catre-Vandis said:**
> Thank you Andrew. Just run the guide on my 12.04 Xubuntu installation, works great :)

Great news! I admit that I still get a huge buzz from building MPlayer and I look on the new venue for the guide as opening up new possibilities and perhaps a bigger audience. Interesting times indeed :).

---

### Post by andrew.46 on 2012-04-29
Wooooo hoooooooo!!! Victory is mine:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer br:// -vo vdpau -xy 1280 -bluray-device /media/THE_MATRIX/[/COLOR]**
MPlayer SVN-r34867-4.7.0 (C) 2000-2012 MPlayer Team
Loading extension-related profile 'vo.vdpau'

Playing br://.
libavformat version 54.3.100 (internal)
TS file format detected.
VIDEO VC1(pid=4113) AUDIO A52(pid=4352) NO SUBS (yet)!  PROGRAM N. 1
Searching for VC1 sequence header... found
VIDEO:  VC-1  1920x1080, 23.976 fps, header len: 33
==========================================================================
Forced video codec: ffmpeg12vdpau
Forced video codec: ffwmv3vdpau
Forced video codec: ffvc1vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 54.14.101 (internal)
[VD_FFMPEG] Trying pixfmt=0.
Movie-Aspect is undefined - no prescaling applied.
VO: [vdpau] 1920x1080 => 1280x720 VC1 VDPAU acceleration 
[VD_FFMPEG] XVMC-accelerated MPEG-2.
[VD_FFMPEG] XVMC-accelerated MPEG-2.
Selected video codec: [ffvc1vdpau] vfm: ffmpeg (FFmpeg WVC1 (VDPAU))
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 640.0 kbit/41.67% (ratio: 80000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[VD_FFMPEG] Trying pixfmt=0.
[VD_FFMPEG] XVMC-accelerated MPEG-2.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vdpau] 1920x1080 => 1280x720 VC1 VDPAU acceleration 
[VD_FFMPEG] XVMC-accelerated MPEG-2.
A: 803.6 V: 803.6 A-V:  0.025 ct:  0.092 3599/3599  0%  0%  6.2% 27 0 

```

So it can be done :).

---

### Post by FakeOutdoorsman on 2012-04-29
Very nice. I've found this to be an interesting resource: [Blu-Ray Picture Quality Tier List](http://www.avsforum.com/avs-vb/showthread.php?t=1168342).

---

### Post by Jose Catre-Vandis on 2012-04-29
A couple of things:

1. Should mplayer be installed before or after ffmpeg/x264 compiles (FakeOutdoorsman guide), or doesn't it matter?

2. Why not install mencoder? How to install mencoder with script?

3. How to enable mplayer menu ?

(I tried with 2 & 3 but it didn't appear to work)

---

### Post by andrew.46 on 2012-04-29
> **FakeOutdoorsman said:**
> Very nice. I've found this to be an interesting resource: [Blu-Ray Picture Quality Tier List](http://www.avsforum.com/avs-vb/showthread.php?t=1168342).

An interesting page, I see my chosen demo movie 'The Matrix' scores a Silver. Pretty amazing graphics actually, I will be interested to try one of the top ranked movies. Even more interested to test out FFmpeg's ability with bluray, I have just compiled with *--enable-libbluray*...

**Edit:** This quick job works well enough:

```

ffmpeg -i bluray:/media/THE_MATRIX/ -vf crop=1920:784:0:148 \
       -c:v libx264 -preset slow -tune film -crf 22 \
       -c:a libfaac -b:a 128k -ac 2 \
        matrix.mp4

```

although of course encode would be a lot quicker from HDD, by new best friend makemkv would be the tool for that.

---

### Post by andrew.46 on 2012-04-29
> **Jose Catre-Vandis said:**
> 1. Should mplayer be installed before or after ffmpeg/x264 compiles (FakeOutdoorsman guide), or doesn't it matter?

It should make no difference. There could be duplicates of some of the dependencies but this of course does not matter. And as this MPlayer guide does not use MEncoder it does not use x264, also MPlayer as compiled here uses a current FFmpeg but internally so it will not clash with either repository FFmpeg or current git as per FakeOutdoorsman.

> 2. Why not install mencoder? How to install mencoder with script?

I was a former MEncoder user who was converted to FFmpeg through FakeOutdoorsman's guide so in part this guide reflects my own usage :). However MEncoder is pretty much dead in the water: it receives little active development, it aims *primarily* at the avi container, results are always better, with vastly more flexible usage, using FFmpeg. However if you wish to use it simply remove the *--disable mencoder --disable x264 *options, make sure you have x264 installed as per FakeOutdoorsman (and the dev files for faac and lame) and recompile. MEncoder should then be available.

> 3. How to enable mplayer menu ?

I have not looked at this for a long time but the option is:

```

**[COLOR="Red"]--enable-menu[/COLOR]**          enable OSD menu (not DVD menu) [disabled]

```

and I believe there are no extra dependencies needed for this. You can see that by default this is disabled which is not always a promising sign from the MPlayer developers :). Some [scant details here]("http://www.mplayerhq.hu/DOCS/HTML/en/fonts-osd.html#osdmenu")...

---

### Post by mc4man on 2012-04-29
If enabling mencoder then probably should have in your checkinstall command
```
--provides "mplayer,mencoder"
```

---

### Post by andrew.46 on 2012-04-29
> **mc4man said:**
> If enabling mencoder then probably should have in your checkinstall command
```
--provides "mplayer,mencoder"
```

Oooops, forgot that bit :). BTW congrats mc4man on 10,000 informative and useful posts!

---

### Post by Jose Catre-Vandis on 2012-04-30
Thanks Andrew and megaposter mc4man :)

---

### Post by qyot27 on 2012-04-30
My reason for chiming in now was to touch base on this thread since I was only subscribed to the vlc-git guide.  Also be forewarned because most of what I'm about to say isn't all that relevant to the original branch described here.




> **andrew.46 said:**
> It should make no difference. There could be duplicates of some of the dependencies but this of course does not matter. And as this MPlayer guide does not use MEncoder it does not use x264, also MPlayer as compiled here uses a current FFmpeg but internally so it will not clash with either repository FFmpeg or current git as per FakeOutdoorsman.
For completeness' sake, it doesn't even matter when building mplayer2, so long as you use the build scripts.  The relevant versions of the libraries (FFmpeg and lib[color="black"]a[/color]ss) that it uses are contained in the build directories, and statically linked into the player afterward.  The external libs (like libx264, libxvidcore, and so on) can be picked up from the system, but that's less of a concern unless you're using the encoding branch - in which case, I would recommend installing the external libs first.

> I was a former MEncoder user who was converted to FFmpeg through FakeOutdoorsman's guide so in part this guide reflects my own usage :). However MEncoder is pretty much dead in the water: it receives little active development, it aims *primarily* at the avi container, results are always better, with vastly more flexible usage, using FFmpeg. However if you wish to use it simply remove the *--disable mencoder --disable x264 *options, make sure you have x264 installed as per FakeOutdoorsman (and the dev files for faac and lame) and recompile. MEncoder should then be available.
There's really only one use-case that I can think of where FFmpeg is still not totally adequate, and that's in hardcoding styled softsubs without jumping through a bunch of demuxing hoops or falling victim to the styling screwing up because it requires additional commands to preserve instead of do so by default.  For that purpose, I can't in good conscience recommend mencoder either, because while there was a patch that enabled this capability, it broke spectacularly a couple years ago.  Another point being that it also will choke on some features of MKV that have been made default through mkvmerge in recent memory (like header removal compression), unless this was actually a limitation of libavformat at the time.  And since mplayer2's encode branch eclipses this functionality in both areas, I've seen no need to find out if they've been fixed against the current SVN.

Your only viable solution in these scenarios is to use the encoding branch of mplayer2, which is basically FFmpeg soldered into the actual video player as a -vo module (and only a change from normal FFmpeg syntax to account for migration from mencoder).  It's not a total replacement for all of mencoder's functionality (it can't use direct stream copy, or AFAIK, have its syntax simplified by using custom profiles), but for that you have the normal FFmpeg or mencoder builds to fall back on.

---

### Post by Jose Catre-Vandis on 2012-05-05
Hi Andrew

If I run an mplayer command to play a file in the terminal (can be avi/mp4/mkv), 

```
mplayer output.avi
```I always get these "error" messages if I close the player window:

```
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
``` which I didn't get before. How to fix this?

---

### Post by andrew.46 on 2012-05-05
Not completely sure (I get the same error) but perhaps select a different ao device, choices here:

```

andrew@mycenae:~$ **[COLOR="Red"]mplayer -ao help[/COLOR]**
MPlayer SVN-r34879-4.6 (C) 2000-2012 MPlayer Team
Available audio output drivers:
	oss	OSS/ioctl audio output
	alsa	ALSA-0.9.x-1.x audio output
	esd	EsounD audio output
	pulse	PulseAudio audio output
	jack	JACK audio output
	sdl	SDLlib audio output
	mpegpes	DVB audio output
	v4l2	V4L2 MPEG Audio Decoder output
	null	Null audio output
	pcm	RAW PCM/WAVE file writer audio output

```

On my Ubuntu setup I have:

```
ao=alsa
```

in ~/.mplayer/config and this manages to at least bypass the problem. **Edit**: And is [a suggested solution here]("http://www.mplayerhq.hu/DOCS/HTML/en/faq.html#idp11152816") as well.

Version bump for libbluray and libaacs in the guide for keen owners of bluray drives btw :). Note this version bump puts the guide one step in front of Precise Pangolin already!

---

### Post by Jose Catre-Vandis on 2012-05-05
OK

```
ao=alsa
``` in /.mplayer/config does the trick. :)

---

### Post by andrew.46 on 2012-05-05
Good to hear :). My ~/.mplayer/config tends to be a little bare, has the following at the moment (for my slackware, vdpau-powered version):

```

# Andrew's choices for MPlayer defaults!

# I prefer mpg123 playback for all mp3 files:
#--------------
[extension.mp3]
profile-desc="profile for .mp3 files"
ac=mpg123
#--------------

# Seems to work better for .mov files:
#--------------
[extension.mov]
demuxer=mov
#--------------

# Try FFmpeg/libavcodec codecs first, they usually work best:
#--------------
afm=ffmpeg
vfm=ffmpeg
#--------------


# If I use vdpau I prefer these video codecs:
#--------------
[vo.vdpau]
vc=ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,ffh264vdpau,ffodivxvdpau,
#--------------

```

Any other settings I add from the commandline. The mpg123 setting is set to become the default soon enough when the default mp3lib is finally removed.

---

### Post by Jose Catre-Vandis on 2012-05-07
Hmmm...problems with mplayer.

Resizing the window will cause the picture/playback to seize up, unrecoverable and window either closes or has to be closed.

Open a video file picture/playback will seize after a few frames, requires right arrow to get it going again

If video playback is paused for @ 5 minutes, picture/playback seizes, cannot be recovered.

(this happens with media files and dvb output)

Xubuntu 12.04
NVidia Ion proprietary drivers
No Compositor

Not had this before on previous installations (although haven't always compiled, just used the repo)

Any suggestions welcome. May try reverting to repo version?

---

### Post by andrew.46 on 2012-05-08
Which -vo are you using? Certainly might be worthwhile trying a different one:

```

andrew@skamandros~$**[COLOR="Red"] mplayer -vo help[/COLOR]**
MPlayer SVN-r34885-4.7.0 (C) 2000-2012 MPlayer Team
Available video output drivers:
	vdpau	VDPAU with X11
	xv	X11/Xv
	gl_nosw	OpenGL no software rendering
	x11	X11 ( XImage/Shm )
	xover	General X11 driver for overlay capable video output drivers
	sdl	SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
	gl	OpenGL
	gl2	X11 (OpenGL) - multiple textures version
	dga	DGA ( Direct Graphic Access V2.0 )
	fbdev	Framebuffer Device
	fbdev2	Framebuffer Device
	svga	SVGAlib
	matrixview	MatrixView (OpenGL)
	aa	AAlib
	caca	libcaca
	v4l2	V4L2 MPEG Video Decoder Output
	xvidix	X11 (VIDIX)
	cvidix	console VIDIX
	null	Null video output
	mpegpes	MPEG-PES to DVB card
	yuv4mpeg	yuv4mpeg output for mjpegtools
	png	PNG file
	jpeg	JPEG file
	gif89a	animated GIF output
	tga	Targa output
	pnm	PPM/PGM/PGMYUV file
	md5sum	md5sum of each frame
	mng	MNG file


```

and it certainly would not hurt to try the repository MPlayer, but my suspicions lie with your video output device....

---

### Post by Jose Catre-Vandis on 2012-05-08
Am in the wrong place at present, but from memory I have:
```
vo=vdpau,xv,gl
```in my config file. Same as with 11.10. I'll have a play around later.

EDIT (didn't have any vo configured in mplayer config)

Tried various -vo settings, none made any difference. Uninstalled compiled version, installed from repo, still no change.

vlc and parole are fine.

Video driver settings?

---

### Post by andrew.46 on 2012-05-09
If you run vdpau best to specify the -vc as well, an example a couple of posts up (in my ~/.mplayer/config. Other than this I am not sure what the problem could be I'm afaraid :(.

---

### Post by Jose Catre-Vandis on 2012-05-09
Here are some errors when it seizes and is restarted using right arrow. These come at startup of film, and from moving the window.

```
mplayer A.Movie.mkv
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
Loading extension-related profile 'extension.mkv'
Loading extension-related profile 'vo.vdpau'

Playing A.Movie.mkv.
Cache fill:  0.00% (0 bytes)   

libavformat version 53.21.0 (external)
Mismatching header version 53.19.0
libavformat file format detected.
[matroska,webm @ 0x10c3d80]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0
[lavf] stream 2: subtitle (text), -sid 0
VIDEO:  [H264]  1280x720  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 title: A.Movie.mkv
Load subtitles in ./
==========================================================================
Forced video codec: ffmpeg12vdpau
Forced video codec: ffwmv3vdpau
Forced video codec: ffvc1vdpau
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->192000)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[VD_FFMPEG] Trying pixfmt=0.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vdpau] 1280x720 => 1280x720 H.264 VDPAU acceleration 
[VD_FFMPEG] XVMC-accelerated MPEG-2.
A:  17.4 V:  17.4 A-V: -0.073 ct:  0.341   0/  0  0% 33%  2.8% 8 0 92% 
[h264_vdpau @ 0x5eb06a0]Missing reference picture
[h264_vdpau @ 0x5eb06a0]Missing reference picture
[h264_vdpau @ 0x5eb06a0]Missing reference picture
A:  28.1 V:  27.9 A-V:  0.160 ct:  0.020   0/  0 ??% ??% ??,?% 0 0 83% 
[h264_vdpau @ 0x5eb06a0]Missing reference picture
[h264_vdpau @ 0x5eb06a0]Missing reference picture
[h264_vdpau @ 0x5eb06a0]Missing reference picture
A:  28.1 V:  28.0 A-V:  0.148 ct:  0.024   0/  0 ??% ??% ??,?% 0 0 83% 
[h264_vdpau @ 0x5eb06a0]mmco: unref short failure
[h264_vdpau @ 0x5eb06a0]mmco: unref short failure
[h264_vdpau @ 0x5eb06a0]mmco: unref short failure
[h264_vdpau @ 0x5eb06a0]mmco: unref short failure
A:  32.4 V:  32.4 A-V:  0.001 ct:  0.170   0/  0  0%  8%  3.1% 0 0 81% 

Exiting... (Quit)
```

Doesn't seem to matter which -vo I use, I get the same behaviour. Thanks for you help Andrew :)

---

### Post by Jose Catre-Vandis on 2012-05-09
Found the problem:
```
ao=alsa
```
fix one thing, break another :)

Recommended fix to compile with "--enable-pulse" ???

---

### Post by andrew.46 on 2012-05-09
That is a little odd, but you should have access to pulse as an ao following this guide so no need to recompile. For most of the libraries which MPlayer the *--enable xxxxx* option is not usually needed or indeed recommended.

---

### Post by Jose Catre-Vandis on 2012-05-09
Agreed there is no need to compile for pulse. .mplayer/config now pared right back to:

lirc=no
vf=yadif

and all is well

:)

---

### Post by cariboo on 2012-05-17
Closed, by request.

---

