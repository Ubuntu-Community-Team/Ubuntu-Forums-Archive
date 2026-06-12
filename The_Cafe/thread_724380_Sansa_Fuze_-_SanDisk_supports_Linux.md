---
title: "Sansa Fuze - SanDisk supports Linux"
date: 2008-03-14
forum: The Cafe
---

### Post by jespdj on 2008-03-14
SanDisk has a new music player, the [Sansa Fuze](http://www.sandisk.com/Products/Catalog(1256)-SanDisk_Sansa_Fuze.aspx).

Good news: Linux is officially supported by SanDisk for the Fuze.
Bad news: As far as I can see, it does not support open formats such as OGG.

It looks like a nice alternative to an iPod or Zune.

---

### Post by DeadSuperHero on 2008-03-14
Maybe we ought to petition them to make it support OGG?
That'd be great!

---

### Post by bilal.17 on 2008-03-14
i have a sansa e250 which isnt "officially" supported for linux by Sandisk.. but it works perfectly on linux ...its a great alternative to the ipod or zune because it costs almost the same as a shuffle but has the same features as nano and more

---

### Post by pt123 on 2008-03-14
how do you recharge these mp3 players?

I currently have a Sony Mp3 player and it recharges by USB, which is so convenient. 
That I would find it a hassle to use other means.

---

### Post by bilal.17 on 2008-03-14
same way .. it recharges when it is plugged into the usb port..

---

### Post by pt123 on 2008-03-14
cool how good is the sound quality?
Sometime back when I compared the Sonys to Ipods, I felt the Sony produced better sound.

---

### Post by p_quarles on 2008-03-14
> **pt123 said:**
> how do you recharge these mp3 players?

I currently have a Sony Mp3 player and it recharges by USB, which is so convenient. 
That I would find it a hassle to use other means.
There are AC to USB adapters available if you don't like plugging it into your computer.

EDIT: Oops, I completely misread your post. I thought you said "inconvenient." My bad. :D

---

### Post by 50words on 2008-03-14
Unfortunately, the firmware updater is Windows-only, so we have to hope they fix this to go with the Fuse's Linux "compatibility."

[http://www.sandisk.com/Retail/Default.aspx?CatID=1376](http://www.sandisk.com/Retail/Default.aspx?CatID=1376)

---

### Post by regeya on 2008-05-19
If you want to update the firmware, you don't need the Windows software.  Just put the Fuze in MSC mode (or leave it in Auto) and copy the .bin to the root of the Fuze's filesystem.  *Et viola.*

Photos:  All I've tried so far is scaling it to 320px wide and save it with a thumbnail; seems to work.  If anyone knows how to automate that, that'd be great.  I'm assuming it can be done with ImageMagick or similar.

Playlists:  I'm told that the XMMS .m3u files work fine, if you convert them to use relative paths (like filtering 'em through sed, perl, or a regexp in vim.)  I've not tried it; just having the filenames in a .m3u file apparently isn't enough.  I'm going to give EasyTAG a try later.

Video:  Hey, if anyone can figure this one out, that'd be great; let the rest of us know!  I've created 20fps DIVX AVIs with 128kbps MP3 audio track, to no avail.  I'd do a hexdump of the file that shipped with the player...but one of the first thigns I did was format the player.  D'oh!

---

### Post by dasunst3r on 2008-05-19
> **regeya said:**
> If you want to update the firmware, you don't need the Windows software.  Just put the Fuze in MSC mode (or leave it in Auto) and copy the .bin to the root of the Fuze's filesystem.  *Et viola.*

Photos:  All I've tried so far is scaling it to 320px wide and save it with a thumbnail; seems to work.  If anyone knows how to automate that, that'd be great.  I'm assuming it can be done with ImageMagick or similar.

Playlists:  I'm told that the XMMS .m3u files work fine, if you convert them to use relative paths (like filtering 'em through sed, perl, or a regexp in vim.)  I've not tried it; just having the filenames in a .m3u file apparently isn't enough.  I'm going to give EasyTAG a try later.

Video:  Hey, if anyone can figure this one out, that'd be great; let the rest of us know!  I've created 20fps DIVX AVIs with 128kbps MP3 audio track, to no avail.  I'd do a hexdump of the file that shipped with the player...but one of the first thigns I did was format the player.  D'oh!If you need some way to automate scaling down your photos, you could try Phatch.  This project appeared about six months ago and should be in the repositories now.

---

### Post by madjr on 2008-05-20
> **regeya said:**
> 
Video:  Hey, if anyone can figure this one out, that'd be great; let the rest of us know!  I've created 20fps DIVX AVIs with 128kbps MP3 audio track, to no avail.  I'd do a hexdump of the file that shipped with the player...but one of the first thigns I did was format the player.  D'oh!

you'll need winFF, convert to mp4 or something

[http://www.winff.org/](http://www.winff.org/)

[IMG]http://winff.org/images/stories/screenshots/screenshot-phorolinux-mainwindow.png[/IMG]

---

### Post by jrusso2 on 2008-05-20
> **jespdj said:**
> SanDisk has a new music player, the [Sansa Fuze](http://www.sandisk.com/Products/Catalog(1256)-SanDisk_Sansa_Fuze.aspx).

Good news: Linux is officially supported by SanDisk for the Fuze.
Bad news: As far as I can see, it does not support open formats such as OGG.

It looks like a nice alternative to an iPod or Zune.

Thats crazy to support Linux and not support open formats.  What are they thinking?

---

### Post by p_quarles on 2008-05-20
> **jrusso2 said:**
> Thats crazy to support Linux and not support open formats.  What are they thinking?
It might seem that way, but what Sandisk means when they say they "support" Linux is that Linux includes the tools to work with Sandisk players. Their "support" consists of testing it before they ship it. 

As far as I know, there's nothing real special about any of the Sandisk players: they just work as mass storage devices and MTP devices. Ultimately, it's no more than a hard drive manufacturer claiming they "support" Linux.

---

### Post by 3rdalbum on 2008-05-20
> **regeya said:**
> Video:  Hey, if anyone can figure this one out, that'd be great; let the rest of us know!  I've created 20fps DIVX AVIs with 128kbps MP3 audio track, to no avail.  I'd do a hexdump of the file that shipped with the player...but one of the first thigns I did was format the player.  D'oh!

Is that what the manual tells you to create? It's probably more likely that you need 25 or 30 frames per second. Also, try reducing the video bitrate.

The Walkmans are so incredibly fussy about what videos they accept... it actually took me days before I discovered how to get ffmpeg to create the correct sort of video file, and back then you needed to compile a new ffmpeg to get it to work!

---

### Post by _sAm_ on 2008-05-20
> **jespdj said:**
> SanDisk has a new music player, the [Sansa Fuze](http://www.sandisk.com/Products/Catalog(1256)-SanDisk_Sansa_Fuze.aspx).

Good news: Linux is officially supported by SanDisk for the Fuze.
Bad news: As far as I can see, it does not support open formats such as OGG.

It looks like a nice alternative to an iPod or Zune.

What about Cowon D2:
Linux os officially supported(- Linux kernel v2.2 or higher (Only data transfer supported) 
Formats it can use: MP3, OGG, WMA, FLAC, WAV, APE
Playtime: 
Music : Max. 52 Hours Continuous Playback
Movie : Max. 10 Hours Continuous Playback

If you want a player with good sound quality Cowon is the best I think.:) And it can show coverarts, has radio, and mic.

---

### Post by Phenax on 2008-05-20
I just buy music players that act as Mass Storage Devices. Works well on all operating systems within reason.

---

### Post by Harkainos on 2008-05-25
I am currently using Rhythembox to organize/play my music. When I plug the Fuze into my compy Rhythembox doesn't recognize it (no errors or anything). This is in MSC and MTP (I have MTP plugins for rhythembox). Any idea how to get Rhythembox to recognize that there is a Fuze plugged into it?

Other than that it works great, drag and drop and it plays em. I'll need to figure out how to actually make a playlist for it.

---

### Post by eragon100 on 2008-05-25
> **jrusso2 said:**
> Thats crazy to support Linux and not support open formats.  What are they thinking?

I don't care.

Linux plays mp3 perfectly, ubuntu ultimate 1.8 (which I have installed, great system) has the codecs out of the box and regular ubuntu can install them with a single mouse click. So what's the problem? It plays music, right? :popcorn:

---

### Post by eragon100 on 2008-05-25
> **Phenax said:**
> I just buy music players that act as Mass Storage Devices. Works well on all operating systems within reason.

+ 1

---

### Post by LightB on 2008-05-25
There's a bunch of other players which support open formats, apart from the already mentioned Cowon. iRiver is another good one. A lot of them are just better overall. And yes, the ones that don't act like regular storage devices are lame, I wouldn't bother with any of those.

---

### Post by grossaffe on 2008-05-25
as the owner of a sansa e200 series mp3 player, i can tell you that they make a very good product.  I loaded a third-party firmware onto the machine that allows it to play OGG files, fully customizeable While Playing Screen, games (including Doom and a gameboy emulator).  being linux people, I think this kind of thing suits you guys.  if your interested, go to their homepage [http://www.rockbox.org](http://www.rockbox.org) and see what all they do and what mp3 players are supported.

---

### Post by ChameleonDave on 2008-05-25
What I want is a digital audio player that runs Linux.

> **regeya said:**
>  *Et viola.*
!


Not sure what actual musical instruments have to do with this, though.

---

### Post by geoken on 2008-05-26
> **regeya said:**
> 

Video:  Hey, if anyone can figure this one out, that'd be great; let the rest of us know!  I've created 20fps DIVX AVIs with 128kbps MP3 audio track, to no avail.  I'd do a hexdump of the file that shipped with the player...but one of the first thigns I did was format the player.  D'oh!

Unless you can find extremely detailed specs or you have some windows based app that shipped with the player which is capable of transcoding videos for the player you're going to have to deal with a lot of trial and error.

These players are extremely picky about their video codecs. Using (or not using) a single, seemingly trivial encoding option/flag could result in an unreadable file. I went through multiple encodes with aviDemux trying every combination trying to get playable video on my Zen. I got lucky and found a thread on these forums where someone wrote a script which used mencoder to produce playable files. Maybe if you look you'll be able to find one as well.

---

### Post by zelldinchtof8 on 2008-06-25
i just got the sansa fuze (it's in the same line of the E2xx series, i guess) and i find that the interface is not that difficult to understand. sure, i might think of installing rockbox or some python firmware run this thing, but it's too pretty (and not to mention - new!) to mess around with. so far, it has not been a hassle and it fits my shirt pocket easily. i have a 2gb microsd memory card that i have from my motorola and it works here - planning to get the 8gb microsdhc, or wait for sandisk's 16gb (which should be any time soon ^_^). i can vouch for 21+ hours of non-stop audio playing time on this, but then again, i was using a sennheiser px200, and almost at full volume mostly....

as for playlists and mp3 managing, i have always made it a point to put my music in artist>album>song<. every time i rip a cd, i always make sure that i get the appropriate album artwork and id3 tags, to make sync and copy easier. i have not tried it in a while but there was a music player for xp (sorry, not sure if there is an ubuntu version) that allows you to easily edit id3 tags. it was musicmatch, or something like that. hope that helps.

---

### Post by MONODA on 2008-06-25
the iaudio 7 support linux and ogg. The battey lasts 60 hours too!

---

### Post by Changturkey on 2008-06-25
I wish they would being these up to Canada.

---

### Post by grossaffe on 2008-06-25
> **zelldinchtof8 said:**
> i just got the sansa fuze (it's in the same line of the E2xx series, i guess) and i find that the interface is not that difficult to understand. sure, i might think of installing rockbox or some python firmware run this thing, but it's too pretty (and not to mention - new!) to mess around with. so far, it has not been a hassle and it fits my shirt pocket easily. i have a 2gb microsd memory card that i have from my motorola and it works here - planning to get the 8gb microsdhc, or wait for sandisk's 16gb (which should be any time soon ^_^). i can vouch for 21+ hours of non-stop audio playing time on this, but then again, i was using a sennheiser px200, and almost at full volume mostly....

Rockbox isn't exactly available on the fuze...

---

### Post by Commander_Bob on 2008-07-18
Maybe this could help someone find a way to convert videos for the Fuze.
[quote="http://www.anythingbutipod.com/forum/showthread.php?t=27460"]General #0
Complete name : C:\Users\EnzoTen\Desktop\WAZ.MineToRemember.SansaP layer.avi
Format : AVI
Format/Info : Audio Video Interleave
Format/Family : RIFF
File size : 20.0 MiB
PlayTime : 3mn 26s
Bit rate : 812 Kbps
Writing application : InterVideo

Video #0
Codec : DivX 5
Codec/Family : MPEG-4
Codec profile : Unknown
Codec settings/Packe : No
Codec settings/BVOP : Yes
Codec settings/QPel : No
Codec settings/GMC : 0
Codec settings/Matri : Default
PlayTime : 3mn 26s
Bit rate : 667 Kbps
Width : 224 pixels
Height : 176 pixels
Display Aspect ratio : 1.273
Frame rate : 20.000 fps
Resolution : 8 bits
Interlacement : Progressive

Audio #0
Codec : MPEG-1 Audio layer 3
PlayTime : 3mn 26s
Bit rate : 128 Kbps
Bit rate mode : CBR
Channel(s) : 2 channels
Sampling rate : 44.1 KHz
Resolution : 16 bits
Writing library : Xing (new)[/quote]

Justin

---

### Post by OutOfReach on 2008-07-18
The Sansa Fuze looks like a good deal. I might consider replacing my iPod Nano with it.

---

### Post by days_of_ruin on 2008-07-18
> **regeya said:**
> If you want to update the firmware, you don't need the Windows software.  Just put the Fuze in MSC mode (or leave it in Auto) and copy the .bin to the root of the Fuze's filesystem.  *Et viola.*

Photos:  All I've tried so far is scaling it to 320px wide and save it with a thumbnail; seems to work.  If anyone knows how to automate that, that'd be great.  I'm assuming it can be done with ImageMagick or similar.

Playlists:  I'm told that the XMMS .m3u files work fine, if you convert them to use relative paths (like filtering 'em through sed, perl, or a regexp in vim.)  I've not tried it; just having the filenames in a .m3u file apparently isn't enough.  I'm going to give EasyTAG a try later.

Video:  Hey, if anyone can figure this one out, that'd be great; let the rest of us know!  I've created 20fps DIVX AVIs with 128kbps MP3 audio track, to no avail.  I'd do a hexdump of the file that shipped with the player...but one of the first thigns I did was format the player.  D'oh!

Easytag works for playlists.You just have to set the filepath separators 
to DOS '\' otherwise it wont work.You can make playlists manually of course(Just a text file with a '.m3u' extension, each line being a relative path to each song you want in the playlist).
btw the fuze doesn't recognize embedded album art.You have to put a file
called "Folder.jpg" in the same folder as all the songs in the album.
If the album art is black and messed up try opening it up in gimp and
just saving it again, that always works for me.

btw I love the wheel!Very often when I am listening to something I will
hit the home button so it won't mess anything up and just spin through
all the icons again and again and again.

Sandisk is releasing a new firmware that will have **support for ogg (vorbis) and flac**
[http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&thread.id=1564]("http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&thread.id=1564")

---

### Post by SilverWolf240 on 2008-07-24
I just got my Fuze on Monday aand I would like to get playlists on my Fuze, but my Fuze doesn't recognize the .m3u file that I put on it at all. Help me!

---

### Post by spicifer on 2008-08-02
I'm glad that Sandisk mentions Linux, but there are far too many  problems with this player on Ubuntu, at least, to call it completely "compatible". I've chronicled  [my own problems]("http://spicifer.blogspot.com/2008/07/sandisk-sansa-fuze-8gb-on-ubuntu-804.html") and especially the video support is simply nonexistant. Playlists weren't easy either.

I collected  [some further information]("http://spicifer.blogspot.com/2008/08/video-on-sandisk-sansa-fuze.html") about Sansa's video format while trying to convert videos. Apparently the AVI container must be in a very specific format. I suspect that only non-interleaved videos are supported, and I haven't found a way of making them with mencoder, at least.

Does anyone know if there is a way to get non-interleaved AVI's in Ubuntu (or perhaps with some Windows program in Wine)?

---

### Post by stevenpusser on 2008-08-09
Hmmm....have you tried Avidemux?  It seems to have many options, and I see it mentioned for doing just that.

---

### Post by spicifer on 2008-08-11
> **stevenpusser said:**
> Hmmm....have you tried Avidemux?  It seems to have many options, and I see it mentioned for doing just that.

Yeah, I tried it. It does have some options for the container format, but non-interleaved AVI doesn't seem to be one of them, unfortunately. Thanks for the suggestion, though!

---

### Post by regeya on 2008-09-01
It's been a while since I messed with this--I mainly use my Fuze as an overpriced iPod Shuffle--but I did mess with it a little this weekend.

Playlists:  Relative paths, backslashes instead of forward slashes in paths, DOS CRLF instead of newlines.  I intend to throw together a script for that, but as a test I ran todos against a VLC playlist, looked to see what the path was to my Fuze (/media/disk), and did a couple of regexes in vim:

:s/\/media\/disk///g
:s/\//\\/g

So if you have 

/media/disk/MUSIC/Foo/Bar/Baz.mp3

that becomes

MUSIC\Foo\Bar\Baz.mp3

And that works.

Photos:  If you scale your pictures down, they'll work fine.  You can save 'em out of GIMP, use a batch GUI app, whatever.  IIRC the thing I tested a while back was this:

convert -scale 320x in.jpg /media/disk/PHOTOS/out.jpg

and that worked.  (EDIT: 'convert' is part of ImageMagick)

Video:  From what I read today, it sounds like the SMC software might dump some sort of proprietary metadata in the AVI file.  More than one of us has tested just using mencoder -oac copy -ovc copy on working files, then confirm that the resulting file does NOT work on the Fuze.  Weird.  Definitely not just a video codec issue, then.  EDIT: Turns out the source of that was the person who commented before me.  Thanks, spicifier!

---

### Post by glantela on 2008-11-09
Hey guys, 

I just wanted to mention, it says in the tech specs that the Sansa Fuze does support ogg.  Maybe this is a newer version though.  Check it out:

[http://www.sansa.com/players/sansa_fuze/tech](http://www.sansa.com/players/sansa_fuze/tech)

---

### Post by echovolutionx on 2008-11-09
WOW! Thats Great!

---

### Post by days_of_ruin on 2008-11-09
> **glantela said:**
> Hey guys, 

I just wanted to mention, it says in the tech specs that the Sansa Fuze does support ogg.  Maybe this is a newer version though.  Check it out:

[http://www.sansa.com/players/sansa_fuze/tech](http://www.sansa.com/players/sansa_fuze/tech)

Yep, get the new firmware [here]("http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&thread.id=4880")

---

### Post by Commander_Bob on 2008-11-10
YAY I love the wrap around scrolling now!

Under supported files it says MPEG4 is that audio (AAC) or video? If it is video has anyone played a video with the new firmware?

Justin

---

### Post by Commander_Bob on 2008-11-10
Sorry an error appeared and this post was posted twice. Can I delete it?

---

### Post by Commander_Bob on 2008-11-10
One more thing...

With the new firmware it now shows the albumart that is embedded in the mp3. However I am gussing most of the songs don't have it embedded. Only the more recent songs I purchanged off amazon have it. Rhythmbox shows almost all the artwork which I read it gets from Amazon.com. There are programs like easytag that will embedded an image into the mp3 but is there a program that will mix these two thing, fetch the albumart from amazon then embedded it into the mp3? I have 1711 songs and I don't want to do each one by hand.

Thanks,
Justin

---

### Post by JA2 on 2008-11-23
Just wanted to add for those who aren't aware that Intrepid (8.10) automatically detects, mounts and charges the Fuze when plugged directly to a USB port - regardless of whether USB Mode is set to Autodetect.  

No more USB hubs needed to mount filesystems and charge the unit while running Linux - Whoohoo! :)

---

### Post by jdong on 2008-11-23
Neat that now it supports Ogg, but by Supports linux, we just mean that the box says that it works with Linux, right? This is primarily due to the device sticking with the UMS and MTP standards, and so has every Sandisk device I've owned.

---

### Post by zmjjmz on 2008-11-23
I guess they now *officially* support Linux.

---

### Post by Yes on 2008-11-23
Does that mean you can transfer videos in Linux with the new firmware?  Before you had you use their Windows-only software to put them on.

---

### Post by jdong on 2008-11-23
> **Yes said:**
> Does that mean you can transfer videos in Linux with the new firmware?  Before you had you use their Windows-only software to put them on.

Really? With my Sansa e2xx series I could just directly put properly encoded MPEG2-container videos on there and the scan catches it.

---

### Post by MunkyJunky on 2008-11-24
> **JA2 said:**
> hat Intrepid (8.10) automatically detects, mounts and charges the Fuze when plugged directly to a USB port

I got a Fuze this weekend. Although when I plug it in, it's auto mounted, I can't see any of my music on it. Is this just my machine being funny then?

---

### Post by doug1212 on 2008-11-25
Here is a little playlist maker for the sansa players i found:

[HTML]http://www.mazleg.com/sansa/[/HTML]

Just drop it in /usr/local/bin.
Doug.

Edit: MTP mode can be made to work on Hardy but requires some hacking of the source code, someone on the sansa forum has written a howto.

---

### Post by Luke has no name on 2008-11-25
> **MunkyJunky said:**
> I got a Fuze this weekend. Although when I plug it in, it's auto mounted, I can't see any of my music on it. Is this just my machine being funny then?

Any music I add through RB or Exaile, I cannot see in Nautilus afterwards. I dont' know why.

---

### Post by jdong on 2008-11-25
Isn't the device in MTP mode? MTP modes doesn't use a flat file data layout unlike MSC mode.

---

### Post by MunkyJunky on 2008-11-25
> **Luke has no name said:**
> Any music I add through RB or Exaile, I cannot see in Nautilus afterwards. I dont' know why.

Ah that's OK then! Just need to get it working with Banshee now. I don't even know if Banshee is capable of it, but.. I'll try anyway!

---

### Post by tom66 on 2008-11-26
Unfortunately, they probably don't support Ogg because:
 a) it would take up too much firmware, if they use a CPU to decode it; or
 b) a microprocessor used to decode mp3s is used only for mp3s. It cannot be used to decode oggs, as it does not have the hardware and that would cost significantly more.

Remember, it's very tight margins in the electronics industry. Adding ogg playback to satisfy 2-5% of the player market is not going to offset the cost of adding an ogg decoder.

---

### Post by spicifer on 2008-11-26
> **jdong said:**
> Really? With my Sansa e2xx series I could just directly put properly encoded MPEG2-container videos on there and the scan catches it.

Not with the Fuze, though. As far as I can tell, the videos have to be in a very specific format in a non-interleaved avi container. And unfortunately no one has found a way to convert them without the Sansa Media Converter, which is Windows only. The new firmware doesn't seem to help at all with this.

(If anyone knows a way to make non-interleaved avi-files in Linux, please let me know. The closest I've gotten is with Wine and Windows program VirtualDub, which unfortunately couldn't set the other parameters right.)

Sandisk hasn't been too helpful, see [http://forums.sandisk.com/sansa/board/message?board.id=smc&thread.id=1131](http://forums.sandisk.com/sansa/board/message?board.id=smc&thread.id=1131) for example.

---

### Post by jdong on 2008-11-26
> **tom66 said:**
> Unfortunately, they probably don't support Ogg because:
 a) it would take up too much firmware, if they use a CPU to decode it; or
 b) a microprocessor used to decode mp3s is used only for mp3s. It cannot be used to decode oggs, as it does not have the hardware and that would cost significantly more.

Remember, it's very tight margins in the electronics industry. Adding ogg playback to satisfy 2-5% of the player market is not going to offset the cost of adding an ogg decoder.

These things use PortalPlayer "dual-core" ARM type chips. There are premade FOSS and even more Free OGG decoder routines -- for example, RockBox uses one. It probably doesn't take too much firmware space as these things have pretty large firmware partitions.

The most likely explanation is the number of man-hours it'd take to implement and support such a decoder, and as you mentioned, for the slim minority of people they'd satisfy to include OGG abilities, it's not worth it on a financial sense.

---

### Post by regeya on 2008-11-28
> **tom66 said:**
> Unfortunately, they probably don't support Ogg because:
 a) it would take up too much firmware, if they use a CPU to decode it; or
 b) a microprocessor used to decode mp3s is used only for mp3s. It cannot be used to decode oggs, as it does not have the hardware and that would cost significantly more.

Remember, it's very tight margins in the electronics industry. Adding ogg playback to satisfy 2-5% of the player market is not going to offset the cost of adding an ogg decoder.

The current firmware (out well before you made that comment) supports Ogg Vorbis and FLAC.  Sadly, it does not support ReplayGain tags in Ogg Vorbis; not sure about FLAC, because, erm, well, I'm not going to bother with lossless on an 8gb device. :)

Thanks for letting us know why they won't support a file format that they, um, actucally do support.

---

### Post by jelly bean on 2009-01-06
I have a sansafuza and Ubuntu operating system and I can't seem to figure out how to work it. Pluggne the fuza and it dosen't do anything.

---

### Post by ArgentSilver on 2009-01-06
> **jelly bean said:**
> I have a sansafuza and Ubuntu operating system and I can't seem to figure out how to work it. Pluggne the fuza and it dosen't do anything.

I've seen posts that say there have been driver issues under earlier versions of Ubuntu, but I have 8.10 on my laptop, and my new Fuze connects flawlessly. Shows up auto-mounted with an icon on the desktop labelled SANSA FUZE.

Are you running Intrepid?

---

### Post by jelly bean on 2009-01-07
well I'm not sure what version I have. I got this computer two months ago. Its still the same way as it was when I got because I'm not real good with a computer.

---

### Post by ArgentSilver on 2009-01-07
> **jelly bean said:**
> well I'm not sure what version I have. I got this computer two months ago. Its still the same way as it was when I got because I'm not real good with a computer.

You can find out your version by giving the following command in a terminal window: cat /etc/lsb-release

Sample output from my system:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

For the Fuze problems with Hardy (8.04) I found this:
[http://ubuntuforums.org/showpost.php?p=5949799&postcount=27](http://ubuntuforums.org/showpost.php?p=5949799&postcount=27))

You can look into doing a dist-upgrade if you want to get up to Intrepid (8.10), but that may be a little more advanced than you are ready for right now.

Good luck!

---

### Post by doug1212 on 2009-01-24
Hi,
Here is a playlist editor modified to produce playlists suitable for the Sansa Fuze player, the original was written for the e280 player that used .pla type lists and can be found here:

[HTML]http://www.mazleg.com/sansa/[/HTML]

I have modified it to produce .m3u lists and save them to the root of the player. It mostly works ok producing new lists but it is not showing the content of existing lists.
I am not a coder so probably needs looking at by a perl guru :)
Have fun,
Doug.

[IMG]http://download349.mediafire.com/1wumjmy1jwbg/vo2mt1tk3mm/Fuze-playlist.png[/IMG]

---

### Post by slugicide on 2009-01-27
> **ChameleonDave said:**
> What I want is a digital audio player that runs Linux.





Then you want the Sansa Connect.  Which is famous for being a MONO/Linux creation that doesn't work with Linux.  At all.

---

### Post by directhex on 2009-01-28
> **slugicide said:**
> Then you want the Sansa Connect.  Which is famous for being a MONO/Linux creation that doesn't work with Linux.  At all.

The Toshiba Gigabeat F-series also combined a Linux base with a Windows-only software stack.

Honestly, Linux isn't the best basis for a device like this. Rockbox does it better

---

### Post by alof8k on 2009-02-21
> **jelly bean said:**
> I have a sansafuza and Ubuntu operating system and I can't seem to figure out how to work it. Pluggne the fuza and it dosen't do anything.


I got a Sansa Fuze 8GB today.  I found it to be incompatible with windows Vista which was annoying as hell.  But then I looked around and found that one can use it as a USB Mass Storage device and decided to boot into Ubuntu and give it a go.  To my surprise, it worked! Not only that, I could drag and drop MP3's.  Even better: I launched Banshee and it recognized the player and lets me use it from there aswell :D

But in order to use it as a usb mass storage device, make sure on the player, you go into Settings | System Settings | USB Mode, and set it to "MSC" .  This allows the player to be used as a mass storage device.  

Then plug in the device and it should be recognized.  Make sure you don't plug in the device ahead of time and try to change the settings from there.  It might cause issues.

---

### Post by dragos240 on 2009-02-21
I got this device for christmas :D

---

### Post by cptrohn on 2009-03-06
Is there any other news on video support with the Fuze on Ubuntu?

My girlfriend got one the other day, and we got music onto the player after fiddling with it for a little while...

But I've heard that Video is darn near impossible with it.  I am really quite upset that they advertise that it works and is supported with Linux, when it obviously really isn't supported.  I've searched for the last 3 days all over the place for information on this and can't find a video solution that works for this....


Any chance that Sansa would let the Ubuntu developers get something going to get one fully working with Ubuntu?

---

### Post by slugicide on 2009-03-06
> **cptrohn said:**
> Is there any other news on video support with the Fuze on Ubuntu?

My girlfriend got one the other day, and we got music onto the player after fiddling with it for a little while...

But I've heard that Video is darn near impossible with it.  I am really quite upset that they advertise that it works and is supported with Linux, when it obviously really isn't supported.  I've searched for the last 3 days all over the place for information on this and can't find a video solution that works for this....


Any chance that Sansa would let the Ubuntu developers get something going to get one fully working with Ubuntu?


As far as I know (and I have no desire to put video on mine so haven't tried) there's a media converter that will convert it into the necessary format, but it's Windows-only. If you want video, you should find out what format is needed and use a Linux-based tool to do the conversion.

---

### Post by cptrohn on 2009-03-06
> **slugicide said:**
> As far as I know (and I have no desire to put video on mine so haven't tried) there's a media converter that will convert it into the necessary format, but it's Windows-only. If you want video, you should find out what format is needed and use a Linux-based tool to do the conversion.

Well from what I have been able to find is that nobody knows what this is...

I've searched the Sansa forums to no avail, Ubuntu forums, google searches etc... No real solutions that are something that works for sure....


But in that same vein, they shouldn't be avertising that it is completely Linux compatible if it isn't....   The very least they could do would be to give a linux compatible version of their media converter software if they are going to advertise the device as being linux compatible to be honest.  Since it seems from everything I have been able to find you HAVE to use their media converter software to be able to put video on the PMP.  I haven't tried the converter software in wine yet (but seem to remember reading somewhere it didn't work though, which is why I didn't try it.)

I like the device really, but to advertise that it is supported and then it's not is NOT a good business practice.  Because we would have bought something else and saved our hard earned money if this was known.

---

### Post by jdong on 2009-03-08
If someone can post a sample of the format for a short video clip converted by its windows tool, I think we can figure out what kind of video it needs.

---

### Post by spicifer on 2009-03-10
> **jdong said:**
> If someone can post a sample of the format for a short video clip converted by its windows tool, I think we can figure out what kind of video it needs.

Well, I don't have a clip here but I wrote two blog posts [with details]("http://spicifer.blogspot.com/2008/08/video-on-sandisk-sansa-fuze.html") and [some analysis]("http://spicifer.blogspot.com/2008/12/sansa-fuzes-video-format.html") of a working clip I had last year. The main issue, as far as I can tell, is that Fuze requires OpenDML (AVI2) indexing, but mencoder, for example, only creates odml chunks for very large AVI files. Also mencoder's odml files have multiple RIFF chunks which Fuze probably doesn't understand at all.

---

### Post by cptrohn on 2009-03-10
> **jdong said:**
> If someone can post a sample of the format for a short video clip converted by its windows tool, I think we can figure out what kind of video it needs.

I've been able to find this link about the video format..

[http://www.anythingbutipod.com/forum/showthread.php?t=27460](http://www.anythingbutipod.com/forum/showthread.php?t=27460)

---

### Post by jdong on 2009-03-10
> **spicifer said:**
> Well, I don't have a clip here but I wrote two blog posts [with details]("http://spicifer.blogspot.com/2008/08/video-on-sandisk-sansa-fuze.html") and [some analysis]("http://spicifer.blogspot.com/2008/12/sansa-fuzes-video-format.html") of a working clip I had last year. The main issue, as far as I can tell, is that Fuze requires OpenDML (AVI2) indexing, but mencoder, for example, only creates odml chunks for very large AVI files. Also mencoder's odml files have multiple RIFF chunks which Fuze probably doesn't understand at all.



Eep groan, that looks like a pain!

---

### Post by Faolan84 on 2009-03-10
A Sansa e200 series with Rockbox installed has the best support for linux you can get. Plus it can play literally ANYTHING you can throw at it including Ogg Vorbis, SPF (super nintendo sound files), and MP4.

---

### Post by Frijolie on 2009-03-12
> **alof8k said:**
> I launched Banshee and it recognized the player and lets me use it from there aswell :D

I have yet to get Rhythmbox or Banshee to recognize the player. Sounds like you got it plug-n-play. Lucky you, I don't know what I've done different. I have the 4GB model and the latest firmware and it's in MSC mode. It automagically mounts and I can transfer files via Nautilus but just can't get any music player to recognize it in Intrepid .

---

### Post by nova on fire on 2009-03-15
I got a Fuze a while ago:). If you want Rhythmbox to see it, you need to place a blank text file in the root folder of the Fuze. The file should be blank but titled ".is_audio_player" (without the quotes) I really like the Fuze. I only wish I could get videos to play easily. :D

---

### Post by Frijolie on 2009-03-16
> **nova on fire said:**
> I got a Fuze a while ago:). If you want Rhythmbox to see it, you need to place a blank text file in the root folder of the Fuze. The file should be blank but titled ".is_audio_player" (without the quotes) I really like the Fuze. I only wish I could get videos to play easily. :D

YOU ARE A GENIUS! \\:D/ THANKS!

Now only one more pet-peeve to take care of. I would like to change the volume label. Currently, it's mounting as "7.9 GB Media". I would like to change that to "8GB Sansa Fuze" or whatever. I have tried to manually edit volume names via Nautilus in the past and it didn't turn out very well. With the HAL controlling the (un)mounting of external media these days can you tell it what to call the volume?

---

### Post by nanotube on 2009-03-16
assuming it uses a simple fat32 partition for the disk, you could use mtools to rename it. see here:
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)


by the way, i'm thinking of getting this one:
[http://www.amazon.com/SanDisk-Sansa-Video-Player-Black/dp/B0015L0T3G/ref=sr_1_2?ie=UTF8&s=electronics&qid=1237176441&sr=1-2](http://www.amazon.com/SanDisk-Sansa-Video-Player-Black/dp/B0015L0T3G/ref=sr_1_2?ie=UTF8&s=electronics&qid=1237176441&sr=1-2)

and sticking like an 8 or 16g expansion card in there...
any issues i should be aware of (besides the well-known video problem)? 

or maybe there is another player with similar features and price, which would be even better supported on linux? i haven't found one with the [somewhat limited] amount of looking... e.g., there's the cowon iaudio7 ([http://www.amazon.com/Cowon-iAUDIO-Portable-MP3-Player/dp/tech-data/B000TB0RY4/ref=de_a_smtd](http://www.amazon.com/Cowon-iAUDIO-Portable-MP3-Player/dp/tech-data/B000TB0RY4/ref=de_a_smtd)) that looks pretty nice, but it has no expansion slot, and costs twice as much - although it does support xvid out of the box, it appears. :)

---

### Post by Commander_Bob on 2009-03-16
If you plan to use the recording features then you should know you can only record to the internal memory not the microSD card.

I have the 8GB version and other then the problem above, I like this player a lot. One other thing I find kinda odd is if you put the power switch on hold while it is booting it will give you "Please unlock the HOLD switch to power on System shutdown".

---

### Post by Frijolie on 2009-03-16
> **nanotube said:**
> assuming it uses a simple fat32 partition for the disk, you could use mtools to rename it. see here:
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

I can't get mtools to work. The drive volume label is "SANSA FUZE" according to mtools, but it's still mounted on my desktop as "7.9 GB Media". Hmm, I can't figure this one out.


> **nanotube said:**
> 
by the way, i'm thinking of getting this one:
[http://www.amazon.com/SanDisk-Sansa-Video-Player-Black/dp/B0015L0T3G/ref=sr_1_2?ie=UTF8&s=electronics&qid=1237176441&sr=1-2](http://www.amazon.com/SanDisk-Sansa-Video-Player-Black/dp/B0015L0T3G/ref=sr_1_2?ie=UTF8&s=electronics&qid=1237176441&sr=1-2)


All-in-all I really dig this player! Native support for flac, ogg, and easy transfer via MSC mode. "Support" in linux, easy firmware updates, small form factor, not an iPod, and lightweight. No problems, just minor tweaking.

---

### Post by Bart_D on 2009-03-16
> **nova on fire said:**
> I got a Fuze a while ago:). If you want Rhythmbox to see it, you need to place a blank text file in the root folder of the Fuze. The file should be blank but titled ".is_audio_player" (without the quotes) I really like the Fuze. ...

What are the steps to do this?  Can it be done from the via the command line.....easily?

> **Faolan Devyn Aodfin said:**
> A Sansa e200 series with Rockbox installed has the best support for linux you can get. .....

Is it plug'n play(Ubuntu 8,10 or higher) or are there tweaks required?

---

### Post by Commander_Bob on 2009-03-16
When I added the ".is_audio_player" file it stopped working on Linux and I had to use a Windows computer to remove the file. It works fine with Rhythmbox for me without it.

The Fuze is plug and play in mass media storage mode.

---

### Post by Frijolie on 2009-03-16
> **Bart_D said:**
> What are the steps to do this?  Can it be done from the via the command line.....easily?

touch <enter device path here> .is_audio_player.txt

e.g. touch /media/disk/ .is_audio_player.txt


> **Bart_D said:**
> 
Is it plug'n play(Ubuntu 8,10 or higher) or are there tweaks required?

it's plug-n-play, it was automagically mounted as soon as I plugged it in. You can begin draggin' and droppin' songs and podcasts instantly.

---

### Post by mamamia88 on 2009-03-16
i have to say this if you are planning on getting one my sansa that i had just over a year decided to stop working yesterday just thought i'd warn you

---

### Post by Frijolie on 2009-03-16
That happened with my iPod, that's why I bought a Fuze!

---

### Post by nanotube on 2009-03-18
well... i ordered a fuze on amazon - will let you guys know how it turns out. :)

---

### Post by gackt on 2009-03-22
I'm getting mine on Tuesday, been hearing a lot about how great is the sound.I think The Linux compatibility is just another marketing strategy to attract linux community (which i can tell somewhat working ^^). I'll tested it out and post the review.

---

### Post by nanotube on 2009-03-22
well, I got it in the mail.
posted my brief review in another thread, here:
[http://ubuntuforums.org/showpost.php?p=6935839&postcount=73](http://ubuntuforums.org/showpost.php?p=6935839&postcount=73)

overall - pretty good. :)

---

### Post by gackt on 2009-03-24
Fuze works fine with ubuntu, and I'm using amarok to transfer my song and it works flawlessly well almost, i'm suffering very low transfer rate (around 1 mb/sec) though not sure why.

---

### Post by abrahamsmith on 2009-03-27
> **gackt said:**
> Fuze works fine with ubuntu, and I'm using amarok to transfer my song and it works flawlessly well almost, i'm suffering very low transfer rate (around 1 mb/sec) though not sure why.

The USB1/2 speed negotiator on the Fuze is a little buggy in such a way that some (also lightly buggy) USB host ports revert it to USB1. 
I have this problem with my Thinkpad laptop, but not on several other machines by different manufactururers

The workaround is to unload the ohci_hcd or uhci_hcd modules altogether and when you plug in the Fuze, "modprobe -r ehci_hci && modprobe ehci_hcd"

---

### Post by gnomeuser on 2009-03-27
I bought an 8GB Fuze the other day to replace my iPod, the primary factor for me was the fact that SanDisk officially lists Linux as being supported and the device has support for Ogg Vorbis.

I love it, I absolutely love it. It is easy to use, the interface is pleasant to work with and after updates to the fdi file it works pretty much flawlessly in Banshee which is something I can't say about the iPod.

The only downsides is the proprietary connector and the bug causing slow file transfer. Also the interface could do with some shining up for prettiness. Finally I could use more space,my iPod is 80 gigs and that was a bit cramped for all my podcasts and my music since I like to take everything with me

I send SanDisk a mail explaining why I bought their device hoping that will help be a determining factor in supporting Linux and open formats on future devices.

---

### Post by cubeist on 2009-03-27
I've had my fuze since boxing week, and I love it.  With some decent headphones it sounds very nice, almost better than my home system.

I don't have a problem with transfer speeds using banshee and MSC mode, but I am also using a custom 2.6.28 kernel, so it may have been an ehci bug in the kernel.

In my opinion this is a really great player for the price, I paid around 50 cdn for the 4gb model, then recently a 8gb microsd for another 20... still over half the price of an ipod.

My favorite feature though is actually the material, the front is a glossy plastic that blends nicely with the screen, but the back is a really cool plastic that feels like it has some rubber embedded in it, which makes it a little grippy.  After a few months of hard use, there is not a single scratch, dent, or mark on the surface.  If you have experience with ipods you know that after a few months of use they scratch up nicely, thus I would say that Sandisk is way ahead in their materials R & D over apple.

The only flaw is lack of linux video support... but who wants to watch videos on a 2" screen anyway!

---

### Post by CTenorman on 2009-04-16
I've got the Fuze v1. with the latest firmware, and the only issues I'm having with it are connectivity-related. With a fully-updated jaunty, the player only works in MTP mode. In MSC mode the drive shows up, but every folder shows as empty. Also, it's running in USB1 mode, as noted earlier. Anyone having the drive not show up in MSC in Jaunty?

Otherwise, a fine little player!

---

### Post by CTenorman on 2009-04-16
Update: USB 2 works, but you have to restart the computer with the device attached for some reason (See [http://ubuntuforums.org/showthread.php?t=1113343]("http://ubuntuforums.org/showthread.php?t=1113343")). Until a better workaround is found, I'm thankful for Jaunty's better boot times when copying lots of files!

---

### Post by nanotube on 2009-04-16
> **CTenorman said:**
> I've got the Fuze v1. with the latest firmware, and the only issues I'm having with it are connectivity-related. With a fully-updated jaunty, the player only works in MTP mode. In MSC mode the drive shows up, but every folder shows as empty. Also, it's running in USB1 mode, as noted earlier. Anyone having the drive not show up in MSC in Jaunty?

Otherwise, a fine little player!

you can't see stuff in MSC mode that was put on there in MTP mode (and vice versa, i understand). It's not a special linux-only bug, just the way the player handles the two different modes. 

If you want to use the player in MSC mode, and manage all the MTP-managed content, just suck off all the stuff you put on there in MTP mode (that includes the default sample content, which also is there in MTP mode), delete it, then re-upload it onto the device in MSC mode.

---

### Post by CTenorman on 2009-04-17
Ah, great stuff, thanks nanotube! What a nice little player once you get used to it! :)

---

### Post by rugbert on 2009-04-27
I love the Sansa line, tho I wish there was a dedicated app for linux to connect to it. Something like EphPod. I just want to click and drag folders in there and have it make playlists for me.

---

### Post by ninotsmindelivar on 2009-05-06
> **CTenorman said:**
> Update: USB 2 works, but you have to restart the computer with the device attached for some reason (See [http://ubuntuforums.org/showthread.php?t=1113343]("http://ubuntuforums.org/showthread.php?t=1113343")). Until a better workaround is found, I'm thankful for Jaunty's better boot times when copying lots of files!

Still no idea as to WHY this even is so?

---

### Post by 0per4t0r on 2009-05-06
Who needs a mp3 player when you have a flash drive with vlc media player portable?
Anyway, it's good that **something** finally "officially" supports linux.

---

### Post by jolx on 2009-05-06
> **0per4t0r said:**
> Who needs a mp3 player when you have a flash drive with vlc media player portable?

Would that work without access to a computer?

---

### Post by CTenorman on 2009-05-06
> **ninotsmindelivar said:**
> Still no idea as to WHY this even is so?

Well, I think I saw something in passing at the Sansa forums that that a newer kernel would fix the problem, but I'm not sure, I was just glancing through the thread quickly. However, plugging in a new kernel might just do it if one's feeling adventurous. I'm not quite that kernel-happy at the moment. :)

---

### Post by nanotube on 2009-05-07
by the way, in case you haven't seen this yet, there's a new firmware out for the fuze:

[http://www.anythingbutipod.com/forum/showthread.php?t=41988](http://www.anythingbutipod.com/forum/showthread.php?t=41988)

bunch of bug fixes and a few new features, most notable of which (i think) is direct folder navigation.

---

### Post by 0per4t0r on 2009-05-22
> **jolx said:**
> Would that work without access to a computer?
Just carry around a tiny netbook.

---

### Post by Commander_Bob on 2009-06-05
I don't know if anyone is still trying to get videos to work on this thing but I just got a new computer that has windows on it so I'm dual booting now.

I installed the SanDisk media converter and converted the sample videos that come with Vista. Two files are added per video, a jpeg image with a .thm extension and the .avi video. 

They are available for a limited time here.
[http://embeddedmicro.com/extra/gz/Bear.tar.gz]("http://embeddedmicro.com/extra/gz/Bear.tar.gz")
[http://embeddedmicro.com/extra/gz/Butterfly.tar.gz]("http://embeddedmicro.com/extra/gz/Butterfly.tar.gz")
[http://embeddedmicro.com/extra/gz/Lake.tar.gz]("http://embeddedmicro.com/extra/gz/Lake.tar.gz")

If any can figure out how to recreate these files that would be great!

Justin Rajewski

---

### Post by napzilla on 2009-08-19
> **regeya said:**
> 
Video:  Hey, if anyone can figure this one out, that'd be great; let the rest of us know!  I've created 20fps DIVX AVIs with 128kbps MP3 audio track, to no avail.  I'd do a hexdump of the file that shipped with the player...but one of the first thigns I did was format the player.  D'oh!


The short version seems to be "it doesn't work." Someone took the time to wade through the whole video codec mess, and he posted his findings here: [http://spicifer.blogspot.com/2008/08/video-on-sandisk-sansa-fuze.html]("http://spicifer.blogspot.com/2008/08/video-on-sandisk-sansa-fuze.html")

Apparently, the video specifications are too obscure to be properly set by anything other than Sansa propriety utility. The utility itself is also quite rigid, and won't even cooperate with Wine. I am having to resort to adding videos via my Windows box. The MP3 player works well, though.

---

### Post by glennph93 on 2009-08-23
Has anyone tried this converter released two days ago on this site [http://code.google.com/p/video4fuze/downloads/list]("http://code.google.com/p/video4fuze/downloads/list")
There is deb package (wine needed?).
Oh by the way newegg has the fuze on sale today(egg shocker) recertified for $38 free shipping.

---

### Post by days_of_ruin on 2009-08-23
> **glennph93 said:**
> Has anyone tried this converter released two days ago on this site [http://code.google.com/p/video4fuze/downloads/list]("http://code.google.com/p/video4fuze/downloads/list")
There is deb package (wine needed?).
Oh by the way newegg has the fuze on sale today(egg shocker) recertified for $38 free shipping.

I installed it, but I am getting errors trying to convert.

---

### Post by glennph93 on 2009-08-23
> I am getting errors trying to convert
I wonder if that has to do with the stock mencoder(ubuntu)

---

### Post by glennph93 on 2009-08-23
Here's what the program(video4fuze) passes off to mencoder.
 1st pass
```
mencoder -ffourcc DX50 -ofps 20 -vf pp=li,expand=:::::224/176,scale=224:176,harddup     -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=683:vmax_b_frames=0:keyint=15:turbo:vpass=1 -srate 44100 -af resample=44100:0:1,format=s16le -oac mp3lame -lameopts cbr:br=128
```

2nd pass
```
mencoder -ffourcc DX50 -ofps 20 -vf pp=li,expand=:::::224/176,scale=224:176,harddup     -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=683:vmax_b_frames=0:keyint=15:vpass=2 -srate 44100 -af resample=44100:0:1,format=s16le -oac mp3lame -lameopts cbr:br=128
```

It seems to work on the command line, but I just ordered my fuze and can't try it out.

---

### Post by skyychild on 2009-08-24
I'm new to linux, so bare with me.  I just installed video4fuze.  converted a avi video.  when it finished i got a error no such file /home/justin/.wine/drive_c/finish.avi

i went to my .wine/drive_c/ dir and there was a video.temp.avi file there.  it was a converted video of the one i was trying to convert.  i copied to to my fuze 8g and tried to play it.  i got an error on my fuze of incorrect file type.  so either i did something wrong or the program does not work with the corrent paramiters set.  i hope this helps anyone that knows more about this stuff then me.

---

### Post by glennph93 on 2009-08-24
> **skyychild said:**
> 

i went to my .wine/drive_c/ dir and there was a video.temp.avi file there.  it was a converted video of the one i was trying to convert.  i copied to to my fuze 8g and tried to play it.  i got an error on my fuze of incorrect file type.  so either i did something wrong or the program does not work with the corrent paramiters set.  i hope this helps anyone that knows more about this stuff then me.

Did you try to rename the file, that extra . might screw up the fuze. The program also gives me errors, I'm going to try the mencoder parameters it shows under preferences. But my fuze hasn't come yet.

---

### Post by BoogeyOfTheMan on 2009-08-25
Oh please tell me this works...

---

### Post by skyychild on 2009-08-30
> **glennph93 said:**
> Did you try to rename the file, that extra . might screw up the fuze. The program also gives me errors, I'm going to try the mencoder parameters it shows under preferences. But my fuze hasn't come yet.


I took out the .temp and left the file as pilot.avi and i still get an error on my Fuze.

error: unsupported media format.

i do not know enough about video and Linux to be of much help,  but i can test stuff.

i currently get video on my Fuze using virtual box, so i can verify that video does work on my fuse, and i am using the same original file for conversions.


Justin

---

### Post by glennph93 on 2009-09-03
Well it looks like there's a solution posted here [http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&view=by_date_ascending&message.id=31762#M31762]("http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&view=by_date_ascending&message.id=31762#M31762")
It uses a combination of mencoder and a avi editor under wine. I haven't tried it yet, but they say it works

---

### Post by glennph93 on 2009-09-11
> **glennph93 said:**
> Well it looks like there's a solution posted here [http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&view=by_date_ascending&message.id=31762#M31762]("http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&view=by_date_ascending&message.id=31762#M31762")
 I haven't tried it yet, but they say it works

Well I've tried it and it does work perfectly. Had to convert the bash script from DOS to Unix.:D

---

### Post by nathanhammontree on 2009-09-13
I bought a Sansa Fuze because iPod is a pain with Ubuntu, and because it has a slot for the micro card, which I can pop in and out of my computer also to quickly move files etc.  But for now I'm working with the internal memory and I have a problem.   I can connect the player via USB and behold, see all the folders.  So, open the Music folder, copy over a bunch of neatly organized files and folders, unmount, disconnect.  So I expect it all to work as I didn't have any problems so far.  My Fuze shows the memory mostly full, but NO SONGS AVAILABLE?  What?  The files are all there, but not functioning.  I updated my player to the latest firmware, deleted all files, tried again.  Same problem.   ...  My wife's computer has Windows, and happens some songs I want there too, so I copy them over.  They work just fine.  HMM, so I boot my computer to Windows, Wipe out my player, transfer files to the player using explorer (no mp3 or fuze software, just copy them) and presto.  Same exact files from Ubuntu, but they would not work until I coppied them using Windows.  What gives?  I could see all the files, they were copied fine, but the player wouldn't read them!

---

### Post by slugicide on 2009-09-13
You need to look up the difference between moving files via MTP or MSC (you can change this in the Settings menu. I believe if you move files with one method, they won't show up in the other. I quick google should point you in the right direction.

---

### Post by nathanhammontree on 2009-09-14
Bingo,  The player has to be set to MSC, then it worked fine.   The auto or MTU workes to transfer them, so you would expect to be able to read and play the files, but Nope.  Thanks!  Oh, it even plays my ogg files!  Now I can say goodby to Windows forever... kinda, except at work, my wife's computer, my kids and school....  My own personal victory at least.

---

### Post by ssorgatem on 2009-09-26
Hi! I'm video4fuze's developer.

The first .deb package was buggy, but it got fixed.  Could you try it and report feedback? :)

Latest version also features image conversion and .pla playlist creation and edition for msc mode.

It needs wine because it uses a windows-only (but GPL) program to do a necessary step in the conversion.

---

### Post by highfructose327 on 2009-10-24
ssorgatem, gave video4fuze a test spin in Ubuntu 9.10RC it worked perfect with my fuze.
Thanks

---

### Post by Bartender on 2009-11-19
Hey, guys -
I know this is a lame question, but I downloaded/installed the latest video4fuze package.  It appears to be working, but I had to hunt it down in usr/bin, then click the "Run" button.  Can anyone give me a few suggestions for making a more convenient way to start it?
I was able to make a launcher in the upper panel.  That works OK as long as I don't make too many other launchers!

Never mind.  I found video4fuze in "Other" category under Applications.  :)

---

### Post by alh on 2009-12-26
> **ssorgatem said:**
> Hi! I'm video4fuze's developer.
 
The first .deb package was buggy, but it got fixed. Could you try it and report feedback? :)
 
Latest version also features image conversion and .pla playlist creation and edition for msc mode.
 
It needs wine because it uses a windows-only (but GPL) program to do a necessary step in the conversion.
 
Top job mate. Where would the linux community be without folks like you. My Sansa Fuze now does everyting expected of it. Top little machine. Mucho happy :P

---

### Post by dragos240 on 2009-12-26
Oh, and I emailed sandisk about the video converter. Because they "support" linux, I thought that they should make a converter for it. Instead they emailed me back saying that by supporting linux, they meant that ogg could be played from the official firmware, they said that they will not support it any more than that. What a shame :(

---

### Post by gnomeuser on 2009-12-26
> **dragos240 said:**
> Oh, and I emailed sandisk about the video converter. Because they "support" linux, I thought that they should make a converter for it. Instead they emailed me back saying that by supporting linux, they meant that ogg could be played from the official firmware, they said that they will not support it any more than that. What a shame :(

Perhaps you could follow up and ask them to change the wording to "Supports Open Standards" rather than Linux, and it wouldn't hurt to thank them for that rather than focus on the Linux thing.

Now here is what I propose we do. Ask SanDisk if they would be open to sharing specifications under NDA with a set of qualified developers so that Linux users might get full support. By doing this they gain support for the Linux platform for free, they can push the support burden largely onto the distribution and relevant developers (no worries once this works the burden should be very minimal). As Linux users by enabling an application such as Arista to have the profile for the Sansa devices and support for the format in Gstreamer with some dbus magic we could hook this support into the application of our choice.

I think that would mean that everyone wins.

Some people/projects I would suggest putting them in touch with.

[http://programmer-art.org/projects/arista-transcoder](http://programmer-art.org/projects/arista-transcoder)
[http://www.linuxrising.org/transmageddon/](http://www.linuxrising.org/transmageddon/)

---

### Post by uid0 on 2009-12-27
Slightly off topic, but woot.com has re-furb Sansa Fuze players for $22.99 today.  I just ordered mine.

---

### Post by doncristobal on 2009-12-27
> **MONODA said:**
> the iaudio 7 support linux and ogg. The battey lasts 60 hours too!

And sound quality is very good (if you turn off all the sound 'enhancing' features like extra bass, mp3-enhancement etc). I even like it for instrumental jazz or classical music. I have been using mine for two or three years now, never had any trouble and the battery still lasts forever. 

You feed it with energy and music through any standard mini usb cable without any special software. 

But get a good cover to protect it, it's worth it!

---

### Post by sovesky on 2010-01-07
Just to know if I'm the only one having a lot of problems with Sansa Fuze and the microSD, after my installation of Karmic?

At first, ubuntu only detected the card once in 2 or 3 tries, but now that I formatted the Fuze, ubuntu completely stop detecting the SD card!

I know Karmic has some USB issues, but I find it odd, that it got worse after a simple Fuze format...

Searched google and found nothing.

---

### Post by maybeway36 on 2010-01-07
The iAudio 7 also has FLAC support, which I rip my CDs into (it's 8GB, why not?) For its shuffle feature I think you can only do one folder or everything on the device, but I usually listen to albums in order so that's OK.

---

### Post by highfructose327 on 2010-01-07
sovesky, I just fired up my netbook to see if connected and it was fine. However about a month ago I updated my firmware of the Fuze and when I did it reset all of my settings. I had to go to Settings> USB mode and set it to MSC. The automatic setting was hit or miss and I have never bothered with MTP so I can not speak to that. I like drag and drop better. So maybe when you formatted it reset everything to factory defaults. 

good luck

---

### Post by sovesky on 2010-01-07
Yes, I thought of it, but MSC was still activated.

Meanwhile I installed rockbox using another machine, windows oriented, and it detected me the microSD, so I doubt it's a Fuze's problem.

What I find strange, is that I didn't changed a thing in my ubuntu, except for a kernel update, but I doubt that's the problem, because I didn't found anyone complaining.

Thank you. ;)

---

### Post by nardis_Miles1 on 2010-01-16
I have installed the latest video4linux. The interface looks great. How do I use it to create, rather than edit, a playlist?

---

### Post by Nick_Jinn on 2010-03-12
I dont know if this has been posted yet, but the Fuze now supports OGG.



Is there a way to add new codecs with Ubunut to get AVI support?

---

### Post by trig on 2010-04-09
has anyone found a solution to the computer not seeing the sandisk fuze.

---

### Post by SeijiSensei on 2010-05-18
Kubuntu 10.04 with older kernel 2.6.28 to avoid a wifi regression in 2.6.32

Just had this problem tonight with my daughter's new Fuze.  You need to change the USB setting on the device to MSC rather than Auto-Detect.  After that it appears as a USB mass storage device.  

Watching /var/log/messages I noticed that Linux sees the device in MTP mode, but doesn't load the SCSI drive emulation module.  In MSC mode, it loads the module and mounts the device as a disk drive.

I was a bit annoyed to discover that copying jpeg's that are "too large" brings up an  "Incorrect format" error.  So far I've been unable to determine what the requirements are for graphics files in terms of file sizes or resolutions.  Of course, Sandisk wants me to manage all my photos with its Windows application.  Apparently video4fuze can handle this, but really, why are these filesize and resolution limits such secrets?  Should I assume that it can't handle photos larger than the screen resolution?  Doesn't it have a built-in scaler to fit larger photos onto the screen?  Inquiring minds want to know, but apparently we're not supposed to ask questions like these.

---

### Post by Nick_Jinn on 2010-05-19
Hmmm....I will check this out. If its too much of a problem i may go back to the last stable release.

---

### Post by sites on 2010-06-24
Just joined the club, with my 4GB Fuze.  I was having issues with Rhythmbox freezing up when the Fuze was connected, until i changed USB mode to MSC.  Upgrading firmware was stupid simple.  Just dropped the .bin file to the root of the drive and unplugged it.  It's got a decent FM receiver.  Next up, adding photos and video, then testing it out recording conversations.  So far i'm pleased with it.

---

### Post by gnomeuser on 2010-06-24
> **sites said:**
> Just joined the club, with my 4GB Fuze.  I was having issues with Rhythmbox freezing up when the Fuze was connected, until i changed USB mode to MSC.  Upgrading firmware was stupid simple.  Just dropped the .bin file to the root of the drive and unplugged it.  It's got a decent FM receiver.  Next up, adding photos and video, then testing it out recording conversations.  So far i'm pleased with it.

I would like to note that Device Stage in Windows 7 is even more stupidly easy. You plug the device in and it checks if there is new firmware. I wish we could compete with that, for every device.

As for the Fuze, I have been very happy with mine, though now I replaced it with my N900 so it is mostly used for testing Banshee these days.

A couple of sticking items, the Fuze can't be filled to capacity as it doesn't reserve the space it's database requires and to my knowledge no media player currently supports doing this automatically. 

Also mtp support is kinda shaky at times and msc mode tends to leave files in the wrong order. I prefer MTP since that yields the most pleasuable result overall.

---

### Post by Nick_Jinn on 2010-06-25
I kind of stopped using my mp3 player now that I have a smartphone as my "device". 

My goal is to have bluetooth sound system with a bluetooth to stereojack, so I can broadcast from any device to any device through any device in my house. 


I would love to be able to have programed messages and for them to go off when I want them to, so people think there is a ghost in the house or maybe I can broadcast my thoughts telepathically, all from my phones Internet connection.



The fuze has been working last time I checked, but maybe I should see how its working now.

---

### Post by spoons on 2010-06-25
I really like my 8GB fuze. Great player.

---

### Post by Nick_Jinn on 2010-06-25
I have found them to be more reliable than Creative Zen....not as pretty, but definitely more reliable.

I hate Creatives customer service. I will never buy from them again. Also, their products have short lives.


Get a Fuze instead.

---

### Post by khelben1979 on 2010-06-27
Sounds nice!

---

### Post by andrewabc on 2010-06-27
Might not have been mentioned recently, but [rockbox](http://www.rockbox.org/) works on Fuze V1. [V2 support](http://www.rockbox.org/wiki/SansaAMS) seems almost complete.

---

### Post by Dustin2128 on 2010-06-27
I bought my sansa fuze because it said it supported OGG on the box, and did. Took a quick external hard drive settings change to work right but I'm quite satisfied indeed.

---

### Post by cooksw74 on 2010-09-28
"As far as I can see, it does not support open formats such as OGG"

It DOES support OGG. That's the whole reason why I bought it. 
Works great with Linux. Rhythmbox recognizes it (although I don't use it that way).
I just copy all my music onto it and listen to it that way.

---

### Post by Spice Weasel on 2010-09-28
I have one of their 8GB USB sticks, pretty much works great under everything.

Came with Tux, Puffy and that BSD dragon on the back of the packaging to accompany the Apple and Windows logos. :D

---

### Post by ubunterooster on 2010-09-28
SanDisk players are very nice. Both the Fuze and Clip+> **Spice Weasel said:**
> I have one of their 8GB USB sticks, pretty much works great under everything.

Came with Tux, Puffy and that BSD dragon on the back of the packaging to accompany the Apple and Windows logos. :DI know, I also have one (actually three):D

---

### Post by Dustin2128 on 2010-09-28
> **cooksw74 said:**
> "As far as I can see, it does not support open formats such as OGG"

It DOES support OGG. That's the whole reason why I bought it. 
Works great with Linux. Rhythmbox recognizes it (although I don't use it that way).
I just copy all my music onto it and listen to it that way.
that was posted in 2008, when it didn't support OGG.

---

### Post by perspectoff on 2010-09-28
Here's how I use the Sanza Fuze for videos.

I have lots of converted movies which I now have on the thing.

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Sansa_Fuze](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Sansa_Fuze)

or

[http://kubuntuguide.org/Lucid#Sansa_Fuze](http://kubuntuguide.org/Lucid#Sansa_Fuze)

---

