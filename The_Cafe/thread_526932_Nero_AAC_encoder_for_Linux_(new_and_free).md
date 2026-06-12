---
title: "Nero AAC encoder for Linux (new and free)"
date: 2007-08-16
forum: The Cafe
---

### Post by stmiller on 2007-08-16
Nero has released their AAC encoder for Linux for free. Here is the link:

[http://www.nero.com/nerodigital/enu/Audio.html](http://www.nero.com/nerodigital/enu/Audio.html)

Check it out!

---

### Post by ssam on 2007-08-16
is it any better than libfaac and libfaad that we already have?

---

### Post by stmiller on 2007-08-16
The Nero AAC encoder is generally highly regarded as quite good. 

Here's one test with some interesting info:

[http://www.hydrogenaudio.org/forums/index.php?showtopic=36465](http://www.hydrogenaudio.org/forums/index.php?showtopic=36465)

Many of the faac developers are now working for Nero, working on this encoder.

---

### Post by hugmenot on 2007-08-19
The difference between FAAC and the Nero encoder is enormous. FAAC is really far behind in the implementation of the technologies of the AAc standard.

---

### Post by salsafyren on 2007-08-19
If its not open source, it's irrelevant for the Open Source / Free Software community.

---

### Post by Andrewie on 2007-08-19
> **salsafyren said:**
> If its not open source, it's irrelevant for the Open Source / Free Software community.

troll please...just leave us along for one thread

could I use this with gstreamer or the kde 4 technology and use it that way, or is it a whole program to encode my music?

---

### Post by hugmenot on 2007-08-19
Right, it is a command line encoder. There is no library or anything; just a binary to encode WAV files with.

---

### Post by Andrewie on 2007-08-19
> **hugmenot said:**
> Right, it is a command line encoder. There is no library or anything; just a binary to encode WAV files with.

so if I wanted, I could make a simple gui to convert files then

---

### Post by hugmenot on 2007-08-20
Or a simple script for that matter.
I tried to hack one together but I ran out of time. For starters I looked at nautilus-script-audio-convert, because it has a "GUI" approach, but I realized that the nero bundle doesn't ship a tagger, which needs to be via other means.
Then I found dir2ogg, and I think it has a good approach. It uses python-mutagen as the tagging library. It should be simple to swap out the ogg stuff for AAC stuff.

Perhaps later today ...

---

### Post by BinaryMadman on 2007-08-23
For the time being i'm using Grip with it, but of course there isn't a way to get tagging - think.  Under encoder i chose 'Other', enter the neroAacEnc path, enter the encoder commandline '-if %w -of %m -br 256000 -2pass', and set the file type to m4a'.

Yes, that's a high bitrate and i have no clue if 2pass even makes a difference at that rate. :P  It's so great that they finally brought a version out for Linux! :)

---

### Post by stmiller on 2007-08-23
Yeah you can use this with K3B, Grip, or any other CD ripper in Linux. Just set it up in the program as your encoder. No need to write a GUI or fancy script.

---

### Post by hugmenot on 2007-08-24
Yes, but if rip your CDs to another format like FLAC you need a method to convert to MP4 on a case-by-case basis. To preserve the tags would be a concern for me.
I actually got the dir2ogg-based script working, but I'm not entirely happy with it. Curently it will not convert all tags in the original files, only the most important ones.

---

### Post by JOWIROMA on 2007-09-09
> **BinaryMadman said:**
> For the time being i'm using Grip with it, but of course there isn't a way to get tagging - think.  Under encoder i chose 'Other', enter the neroAacEnc path, enter the encoder commandline '-if %w -of %m -br 256000 -2pass', and set the file type to m4a'.

Yes, that's a high bitrate and i have no clue if 2pass even makes a difference at that rate. :P  It's so great that they finally brought a version out for Linux! :)

Hey man! I am trying to use it with grip but I got this message after the rip "NO WRITE ACCESS TO WRITE ENCODED FILE"

DO you have any idea what could be my problem???
I put like you the path for the encoder and the command line options.

---

### Post by BinaryMadman on 2007-09-12
JOWIROMA, i'm still kind of new to this myself but it sounds like you don't have the permissions to the directory where your encoded files will be placed.  What path are you using under the 'Encode file format' setting?  Make sure that path is pointing to a folder you have "write" permission to (like your home directory).

Personally, i use the path "~/music/%A/%d/%n.%x" without the quotes.  That creates a file under: /home/user/music/Artist/Album/Name.m4a

Also, I put the neroAacEnc file in my home directory, /home/user/neroAacEnc, and used that as the "Encoder executable' path.  Not sure if any of that will help you.

---

### Post by rootkit on 2007-12-04
I have this linux AAC+ encoder: [http://teknoraver.net/software/mp4tools/](http://teknoraver.net/software/mp4tools/)

Give it a try.

Packages are in this repository:

deb [http://ppa.launchpad.net/teknoraver/ubuntu](http://ppa.launchpad.net/teknoraver/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/teknoraver/ubuntu](http://ppa.launchpad.net/teknoraver/ubuntu) hardy main

---

### Post by bruce89 on 2007-12-04
Since when was AAC better than Vorbis?

---

### Post by n3tfury on 2007-12-04
nero's AAC is incredible. i use it exclusivlely for low bitrates.

---

### Post by n3tfury on 2007-12-04
> **bruce89 said:**
> Since when was AAC better than Vorbis?

sub

ject

ive

---

### Post by bruce89 on 2007-12-04
> **n3tfury said:**
> sub

ject

ive

[http://www.hydrogenaudio.org/forums/index.php?showtopic=35438](http://www.hydrogenaudio.org/forums/index.php?showtopic=35438) would suggest that Vorbis is better than AAC.

---

### Post by timcredible on 2007-12-04
don't understand why anyone would want aac files.

---

### Post by harold4 on 2007-12-04
AAC for my cell ringers.  Will give this a once over, thanks.

---

### Post by panaretos22 on 2007-12-04
thats great i am going to install it

---

### Post by n3tfury on 2007-12-04
> **bruce89 said:**
> [http://www.hydrogenaudio.org/forums/index.php?showtopic=35438](http://www.hydrogenaudio.org/forums/index.php?showtopic=35438) would suggest that Vorbis is better than AAC.

congratulations linking to a test that's two years old.  again.  NERO's AAC is better to my ears.  closed case.

---

### Post by n3tfury on 2007-12-04
> **timcredible said:**
> don't understand why anyone would want aac files.

what's the problem.

---

### Post by hugmenot on 2007-12-04
> **bruce89 said:**
> [http://www.hydrogenaudio.org/forums/index.php?showtopic=35438](http://www.hydrogenaudio.org/forums/index.php?showtopic=35438) would suggest that Vorbis is better than AAC.

Way to selectively quote single person taste-related tests!

The matter is more complicated. First of all HE-AAC-&#945;&#946;&#947; has more bells and whistles for really low bitrates encoding. Then it allows mutichannel, and it is supported by more platforms out of the box. Together with H264 and an MP4 container you get a lot of platform support.

Second, listening tests (64, 48, 128 kbps):
[IMG]http://www.listening-tests.info/mf-64-1/resultsz.png[/IMG]
[IMG]http://www.listening-tests.info/mf-48-1/resultsz.png[/IMG]
[IMG]http://www.listening-tests.info/mf-128-1/resultsz.png[/IMG]

SUMMARY: Nero wins at really low bitrates. Besides, all my /music/ is in Flac and Vorbis.

---

### Post by uggeli on 2007-12-16
Sorry for stupid question, but how do I set k3b to use this Nero AAC? I found quide how to do it for windows version with wine in here: [http://wiki.hydrogenaudio.org/index.php?title=K3b_and_Nero_AAC](http://wiki.hydrogenaudio.org/index.php?title=K3b_and_Nero_AAC)

But I don't quite get it. I tried to use that guide as base, but leave that wine part away etc. but I don't know how to get this Nero AAC Linux version work in k3b. Any help would be appreciate.

PS. Sorry for my bad English.

---

### Post by bruce89 on 2007-12-16
> **hugmenot said:**
> SUMMARY: Nero wins at really low bitrates. Besides, all my /music/ is in Flac and Vorbis.

Who uses low bitrates?

---

### Post by hugmenot on 2007-12-17
Web radios. Movie encoders. People with cell phones and small memory.

---

### Post by DeadSuperHero on 2007-12-17
Question: If it's in the AAC format, will it work on an iPod?

---

### Post by hugmenot on 2007-12-17
Yes. I think they even play gapless.

---

### Post by zietbukuel on 2007-12-19
Where can I download this program? I've navigated the Nero website but found nothing, thanks.

---

### Post by ron999 on 2007-12-19
Hi
It's not a program.
It's a file to download named **NeroDigitalAudio.zip** and inside it are two folders.

Linux and Win32.

Inside the Linux folder are two files.

**neroAacDec** (the decoder)
**neroAacEnc **(the encoder)

This is the link:-[http://www.nero.com/eng/nero-aac-codec.html]("http://www.nero.com/eng/nero-aac-codec.html")
8)

---

### Post by rootkit on 2008-01-20
Not to push my encoder ([http://teknoraver.net/software/mp4tools/](http://teknoraver.net/software/mp4tools/)), but the linux version of the Nero one is buggy compared to the windows binary.
It's fully explained here: [http://www.hydrogenaudio.org/forums/index.php?showtopic=58582](http://www.hydrogenaudio.org/forums/index.php?showtopic=58582)
Also, i very dislike they answer when I asked more support:
```
Don't count on that anytime soon. It requires a lot of testing normally, and that is hard to justify here for a linux version that we give away for free :)
```

---

### Post by DoktorSeven on 2008-01-20
Even if it sounds better, I'd rather use a truly Free and open format (Ogg Vorbis) than a proprietary one.

---

### Post by rootkit on 2008-07-17
Hot update, aacplusenc works fine in 64 bit now.
Go fetch it from the usual url: [http://teknoraver.net/software/mp4tools/](http://teknoraver.net/software/mp4tools/)

---

### Post by hugmenot on 2008-09-30
There&#8217;s a new version of the free beer nero encoder out.
[http://www.nero.com/eng/downloads-nerodigital-nero-aac-codec.php](http://www.nero.com/eng/downloads-nerodigital-nero-aac-codec.php)

---

### Post by eragon100 on 2008-10-02
> **DoktorSeven said:**
> Even if it sounds better, I'd rather use a truly Free and open format (Ogg Vorbis) than a proprietary one.

I just want my music to sound good. Also, my MP3 player only supports MP3, AAC en WMA. There where players that supported OGG, but they where more expensive.

---

### Post by raffraffraff on 2009-06-12
When I used Windows, I used iTunes (because I liked the library interface and complete abstraction from files). I was always a big fan of LAME, and used my own 224kbps VBR settings. I did a few double-blind tests with really good headphones and found that I couldn't really tell the difference between the original and the MP3. 

But I started running out of disk space at one point, and decided to re-rip my collection to lower bitrate AAC with Nero's encoder. I got great results at 192kbps, and to be honest, I found 160 to be perfectly good for certain recordings.

Problem: After switching to linux I found AAC / MP4 / M4a to be a complete pain in the a$s. Few players use it, and those that claim to (eg Creative F*cking Labs 'Zen X-Fi') only work on about 20% of my files. I've spent hours mucking about with AtomicParsley and MP4Box to fix various container problems, 'brand' issues, tag compatibilities etc. I've had to recompile Amarok 1.4.9 to enable tag support. I've come close to angrily throwing my wife's Zen X-fi at a wall screaming "DIE!!!!".

Ogg sounds great, but it's an idealist's format. Good luck finding support.
M4a is great with the right encoder and hardware, but again, good luck.
LAME is good. In fact, it's perfect with the right settings. And it works on all phones, players, streamers, set-top-boxes and refrigerators.

Bottom line for me: I'm too old to f*ck about with this format sh*t any more. I just want to listen to music, not fight with it. I'll come back occasionally and read about new formats. I might even demo a few if they're really hyped. But frankly, unless I get perfect quality at 96kbps that works on every player, I'm sticking with LAME. Hard disk space is so much cheaper than time these days.


Update!! It's near the end of Two Thousand And Ten, and Nero, not Creative, have solved the compatibility issue! I rebuilt my Wife's work PC with Windows 7, installed MusicBee (which is an excellent little music library by the way) and decided to install Nero's latest codec with my fingers crossed. Thankfully it worked. Well done Nero! Top marks for an excellent codec.

---

### Post by 3rdalbum on 2009-06-12
FAAC is lacking, just a smidgen, for "CD-quality" audio (yeah I know it's not really CD-quality). But I'd prefer to stick to MP3 wherever possible as there's wide support and relatively little chance of becoming a patents problem.

I've never felt safe using AAC. I know AAC and MP3 are both patented, but AAC does support DRM and it feels like there's more chance of AAC patents being enforced.

---

### Post by pwnst*r on 2009-06-12
> **raffraffraff said:**
> When I used Windows, I used iTunes (because I liked the library interface and complete abstraction from files). I was always a big fan of LAME, and used my own 224kbps VBR settings. I did a few double-blind tests with really good headphones and found that I couldn't really tell the difference between the original and the MP3. 

But I started running out of disk space at one point, and decided to re-rip my collection to lower bitrate AAC with Nero's encoder. I got great results at 192kbps, and to be honest, I found 160 to be perfectly good for certain recordings.

Problem: After switching to linux I found AAC / MP4 / M4a to be a complete pain in the a$s. Few players use it, and those that claim to (eg Creative F*cking Labs 'Zen X-Fi') only work on about 20% of my files. I've spent hours mucking about with AtomicParsley and MP4Box to fix various container problems, 'brand' issues, tag compatibilities etc. I've had to recompile Amarok 1.4.9 to enable tag support. I've come close to angrily throwing my wife's Zen X-fi at a wall screaming "DIE!!!!".

Ogg sounds great, but it's an idealist's format. Good luck finding support.
M4a is great with the right encoder and hardware, but again, good luck.
LAME is good. In fact, it's perfect with the right settings. And it works on all phones, players, streamers, set-top-boxes and refrigerators.

Bottom line for me: I'm too old to f*ck about with this format sh*t any more. I just want to listen to music, not fight with it. I'll come back occasionally and read about new formats. I might even demo a few if they're really hyped. But frankly, unless I get perfect quality at 96kbps that works on every player, I'm sticking with LAME. Hard disk space is so much cheaper than time these days.

i hear ya. i love nero's AAC, but it's finicky when it comes to players.  i still rip to FLAC, then depending on which DAP i'm using, i'll use a higher bitrate VBR mp3 or a 160 bitrate AAC like you.

i also agree about ogg. it'd be nice, but total lack of support from most big name companies kills it for me.

---

### Post by qyot27 on 2009-06-12
> **3rdalbum said:**
> ...but AAC does support DRM...
Not exactly.  The DRM implementation included in MPEG-4 (AAC is defined in MPEG-4 Part 3 - likewise, Part 2 is the video standard Xvid implements and Part 10 is H.264/AVC), known as Intellectual Property Management and Protection or IPMP, is standard-practice for the specification (in fact, the MPEG-2 spec also includes IPMP).  But, that's not the DRM usually used, of which most people would be familiar with.  What ***is*** typically found instead is Apple's FairPlay DRM, which has no connection to the MPEG-4 standard at all.  Feasibly they could repackage MP3s or Vorbis files in the MP4 container and slap FairPlay on them too, but the likelihood of that is very very small, IMO.

Case in point: the audio ID tag for a FairPlay'ed file isn't mp4a, which it normally would be, but drms (the corresponding video ID is drmv rather than the normal mp4v, avc1, etc.).  I'm not even sure if it even lies in the audio sector of the MP4 files at all, because MP4 allows for the use of private sectors (which I understand to be roughly similar to the Attachments feature of MKV, but I could be wrong).

At most the argument could be made for the MP4 container allowing for DRM (AAC is simply the audio format, much like Vorbis is the audio format and Ogg is the container), but even then the standard scheme used is third-party and could probably be done even on other MPEG standard files, if they chose to.  Basically my view of it is that the standard is left somewhat open-ended, so the ability to use DRM is there, but doing it properly (according to official spec) just isn't done.

---

