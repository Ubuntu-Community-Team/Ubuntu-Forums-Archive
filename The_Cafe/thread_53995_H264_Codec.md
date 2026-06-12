---
title: "H264 Codec"
date: 2005-08-03
forum: The Cafe
---

### Post by Teroedni on 2005-08-03
Theres coming a newc codec with improved quality. The article is here
[http://www.theinquirer.net/?article=25057](http://www.theinquirer.net/?article=25057)

My question is if anybody knows if this codecs will be availbe to linux , or will we be shut out??

---

### Post by pmj on 2005-08-03
h.264 is another mpeg-4 codec. It is patent encumbered and I'm guessing that it won't be legal to support it out of the box.

Same as with earlier mpeg-4 standards, there are free implementations. I have no idea if they work in Linux *right  now*, but if XviD came to Linux I'm sure h.264 will as well. It's possible that vlan and mplayer can play a few h.264 videos already.

Edit: x264 is available for Linux:  [http://developers.videolan.org/x264.html](http://developers.videolan.org/x264.html)

---

### Post by sapo on 2005-08-03
> In order to play Full High Definition 1920x1080 (1080p) video at 24-30 FPS you will need a MAC machine only. You actually need dual 2.0 GHz PowerMac G5 or faster computer with at least 512MB of RAM and a 128MB or greater video card.

OMFG  ](*,)

---

### Post by NoTiG on 2005-08-03
> At this time there is no graphic card hardware acceleration for this fancy codec. 

.

---

### Post by Hamman on 2005-08-03
[QUOTE=NoTiG].[/QUOTE]
 x264 is under heavy development. You can use it with mencoder or avidemux (to mention a few), And yes, h264 requires a lot of cpu-power, I don't think any current mainstream CPU can decode a 1080p stream. Hopefully acceleration will be built in to new graphic cards.

---

### Post by Nylira on 2005-08-16
Ok now this is getting quite annoying. Seems everyone in windows land is starting to jump on the H264 codec band wagon. Because people that use that tend to have a ton hardware needed for their OS the nix users pay the price.

From the looks of it the H264 is being tested/beta-ed in VLC 0.8.2 and Mplayer pre7. Both of which are probably not gonna be in ubuntu for a while  :???: 

This is a royal pain. Does anyone have any good guesses when H264 support will be in Ubuntu? I can probably already guess the answer will be: when its done. 

Which means I guess that I start destabilizing my machine will compiled beta stuff. *sigh*

---

### Post by Ampersand on 2005-08-16
I think VLC 0.8.2 is in Breezy now...

---

### Post by wantilles on 2005-11-03
Xine-lib 1.1.0 supports x264/H264.

So when it gets into Totem, it will be supported in Ubuntu.

Right now, Totem has Xine-lib 1.0.1.

I am also using Gentoo, and I know.

---

### Post by CompShrink on 2006-02-04
been trying to get this to work, and just wanted to share with everyone gstreamer-ffmpeg (along with totem-gstreamer of course) plays my h264 mkvs.

It doesn't however let me select subtitles. Xine seems to have the best subtitle suport, including mkv subtitles. But as mentioned, the xine in ubuntu doesn't support h264/x264. I tried getting it in through aliening some mandrake packages, but just had to keep getting more stuff from mandrake, didn't work out.

So, now I've got playback of h264 at least, but without subs. Heh, forcing me to put my language skills to the test...

---

### Post by Lovechild on 2006-02-04
Call me when Project Schrondinger (Dirac) is ready

---

### Post by BoyOfDestiny on 2006-02-04
In breezy vlc handles it fine. In dapper I've tested mplayer with it... However, I've only played lower res fansubs (704x396), and it barely uses any cpu (I have an opteron 144, it's almost 4 years old :) ) running with 64-bit and a dell inspiron laptop with 1.8ghz centrino plays them as well (breezy 32)...

I'm glad people are using this. 
I greatly dislike wmv's, even when I had windows I disliked it... Anyway don't fret

---

### Post by Malphas on 2006-02-04
Speaking of x264, anyone know of a native Linux application with similar fuctionality to MeGUI?

Edit: Failed to notice how old this thread is.  I thought it was kinda odd that H.264 was being announced as a *new* codec.

---

### Post by joplass on 2006-02-05
Avidemux plays all my H264 files.  The picture quality is unbelievable.  Best I have seen \\:D/ \\:D/ \\:D/ .

---

### Post by Sirin on 2006-02-05
Ah, well, the OSS community will develop an imitation of the codec with a strange name, like "hdlinuxCodecOSSi386intelx86".

---

### Post by WildTangent on 2006-02-05
> At this time there is no graphic card hardware acceleration for this fancy codec. 
The Geforce 6 and 7 series can decode/encode h.264 in hardware. nvidia hasnt released a driver update supporting it yet.

-Wild

---

### Post by joplass on 2006-02-05
[QUOTE=WildTangent]The Geforce 6 and 7 series can decode/encode h.264 in hardware. nvidia hasnt released a driver update supporting it yet.

-Wild[/QUOTE]
huh my ATI handles h.264 with no hicups.  Let me just say that besides playing H.264 files, Avidemux encode them to other formats as well.

---

### Post by WildTangent on 2006-02-06
[QUOTE=joplass]huh my ATI handles h.264 with no hicups.  Let me just say that besides playing H.264 files, Avidemux encode them to other formats as well.[/QUOTE]
But you're using software decoding, in other words: your CPU is handling it. With the next driver update, Geforce 6 and 7 series will be able to do it with the GPU itself, thus saving your CPU alot of work.

-Wild

---

### Post by CompShrink on 2006-02-07
Personally, the VLC in the default Breezy repositories (including universe & multiverse of course) cannot playback h264 for me.

And my previous post... well now I found my first test video was lucky. Most videos using totem-gstreamer & gstreamer-ffmpeg have bad audio/video sync issues.

mplayer from CVS debs from this thread work great though: [http://ubuntuforums.org/showthread.php?t=85190](http://ubuntuforums.org/showthread.php?t=85190)

Can't wait for hardware decoding/encoding for it!

---

### Post by erk on 2006-03-04
[QUOTE=WildTangent]But you're using software decoding, in other words: your CPU is handling it. With the next driver update, Geforce 6 and 7 series will be able to do it with the GPU itself, thus saving your CPU alot of work.

-Wild[/QUOTE]

Nvidia just anounced the Windows drivers yesterday, hopefully it wont be too long for linux support.
[http://www.reghardware.co.uk/2006/03/03/nvidia_ship_h264_purevideo/](http://www.reghardware.co.uk/2006/03/03/nvidia_ship_h264_purevideo/)

Mind you the real fun would be getting the GPU to do H.264 encoding, it is sooo slow using the CPU to do it.

---

### Post by Malphas on 2006-03-04
[QUOTE=Sirin]Ah, well, the OSS community will develop an imitation of the codec with a strange name, like "hdlinuxCodecOSSi386intelx86".[/QUOTE]
You mean x264.

---

### Post by ketsugi on 2006-05-14
So is there a way yet to get h264 support in Totem, on Dapper? I can play my x264-encoded .mp4 files in mplayer and VLC just fine, but Totem just crashes.

It isn't really a big issue; I'd just like to get some thumbnailing in for those files.

---

### Post by MattCarp on 2006-05-20
I have the same question/problem.  I'm not sure where the right place is for this discussion, but I found this thread. So:

How can I enable full H.264 support with Totem?  I'm trying to play a video and get this message:

Video codec 'Advanced Video Coding (H264)' is not handled.

Of course, I added all of the restricted format codecs listed in the wiki.

Or, should I go with another media viewer?

It does appear to me that exactly what codecs you have installed is as just as opaque as Windows Media Player - it's not clear which ones I have installed, or which ones I need.

---

### Post by BoyOfDestiny on 2006-05-20
[QUOTE=MattCarp]I have the same question/problem.  I'm not sure where the right place is for this discussion, but I found this thread. So:

How can I enable full H.264 support with Totem?  I'm trying to play a video and get this message:

Video codec 'Advanced Video Coding (H264)' is not handled.

Of course, I added all of the restricted format codecs listed in the wiki.

Or, should I go with another media viewer?

It does appear to me that exactly what codecs you have installed is as just as opaque as Windows Media Player - it's not clear which ones I have installed, or which ones I need.[/QUOTE]

If you are running dapper, I can vouch for gstreamer .10. 

EDIT: NM my h264 files won't play in totem anymore. Even those that had made thumbnails... Maybe there was some update that broke it...

EDIT: Again, ran an update, made sure all the ugly and multiverse gstreamer.10 was in. Now it works, and rethumbnailed... 

Anyway don't know about the wiki (I just use what's in the repos enable universe and multiverse if you haven't), but gstreamer plugins have a description, it's not hidden like windows. As to which you need... Only you really get to know that...

On the "plus" side, they added those fluendo plugins for mp3 and mpeg2... 
Not a huge deal, but if I ever sell any machines with ubuntu on it, now I don't have to risk going to jail/getting fined (whatever the horrible consequences are) for including mp3 and dvd playback...

---

### Post by jdong on 2006-05-20
Dapper has h264 support in all the major media player packages, as well as mencoder/x264-bin for creating h.264's.

This is truly an amazing video format. I can use bitrates 40-50% lower than xvid/divx and still get similar quality :)

The clear downside is CPU usage. H264 is extremely heavy on CPU... I would not try using anything slower than a P4 equivalent to play the average H.264... and the hi-def ones will require a hefty high-end processor (preferably a dual-core or multiprocessor)

---

### Post by MattCarp on 2006-05-22
[QUOTE=BoyOfDestiny]If you are running dapper, I can vouch for gstreamer .10. 

EDIT: NM my h264 files won't play in totem anymore. Even those that had made thumbnails... Maybe there was some update that broke it...

EDIT: Again, ran an update, made sure all the ugly and multiverse gstreamer.10 was in. Now it works, and rethumbnailed... 
[/QUOTE]

Thanks - I definitely appreciate the help, but I'm still having trouble with this video:  [http://mp3.geekbrief.podshow.com/gbtv.adam.001.mov](http://mp3.geekbrief.podshow.com/gbtv.adam.001.mov)

I hate to send anyone on a quest for a silly vidcast, but I do happen to this this chick is hot.

I've got the following repositories enabled:

Dapper Updates (source) - official, restricted
Dapper Updates (binaries) - official, restricted
Dapper Drake (binaries) - official, restricted, universe, multiverse
Dapper Drake (source) - official, restricted
Backports (binary) - official, restricted, universe, multiverse
Security Updates - official, restricted

I just ran the following updates:

sudo apt-get install gstreamer0.10-plugins-good
sudo apt-get install gstreamer0.10-plugins-ugly
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
sudo apt-get install gstreamer0.10-plugins-bad
sudo apt-get install gstreamer0.10-plugins-bad-multiverse
sudo apt-get install gstreamer0.10-pitfdll
sudo apt-get install gstreamer0.10-ffmpeg

And I still get the error, "Video codec 'Advanced Video Coding (H264)' is not handled." from Totem...

---

### Post by jdong on 2006-05-22
xine with totem works *for sure*...

---

### Post by MattCarp on 2006-05-22
[QUOTE=jdong]xine with totem works *for sure*...[/QUOTE]

I am a noob - that might have something to do with it.

However, I just installed mplayer (to play with LiVES) and was able to view the video in mplayer!

EDIT: the progress bar doesn't correctly scale to reflect the progress of the playback, but it does advance the video properly, but hey, that's a different issue

Anyway, don't they use the same codecs?

---

### Post by jdong on 2006-05-22
No; many of the different players have different codecs that they use, though most of them share the ffmpeg decoders.

As far as my totem content, try installing the totem-xine package, which turns the totem player backend from gstreamer to xine. I've had better general luck with xine.

---

### Post by samir85 on 2006-05-23
I've some h.264 encoded videos here and they play with totem-gstreamer flawless.
I wonder why it's not working for you ...

---

### Post by MattCarp on 2006-05-30
hmmm... Totem's Help > About reports that I'm already using xine:

"Movie Player using xine-lib version 1.1.1"

To be sure, Synaptic shows that I do havethe  totem-xine package installed, version 1.4.1-0ubuntu4.

I suppose since I can play these with mplayer, this isn't a big issue, but I'd like to better understand you the video setup works and fix it.  It would probably be helpful for other newbies who don't take the trouble to install mplayer.

---

### Post by c-m on 2006-06-04
who gives codecs these h.??? names.?

Could create a codec and call it bad hairy *** codec, and get it patented or something, or would someone then come along and say this is now h.???

---

### Post by pmj on 2006-06-04
[QUOTE=MattCarp]hmmm... Totem's Help > About reports that I'm already using xine:

"Movie Player using xine-lib version 1.1.1"

To be sure, Synaptic shows that I do havethe  totem-xine package installed, version 1.4.1-0ubuntu4.

I suppose since I can play these with mplayer, this isn't a big issue, but I'd like to better understand you the video setup works and fix it.  It would probably be helpful for other newbies who don't take the trouble to install mplayer.[/QUOTE]

I haven't had much luck with h.264 in xine (or totem-xine) either. To use gstreamer with totem, just install totem-gstreamer (sudo apt-get install totem-gstreamer).

---

### Post by icaughtfire818 on 2007-08-27
> **pmj said:**
> I haven't had much luck with h.264 in xine (or totem-xine) either. To use gstreamer with totem, just install totem-gstreamer (sudo apt-get install totem-gstreamer).



sudo apt-get install totem-gstreamer worked for me ^.^

thanks luvvies <3

---

### Post by jdong on 2007-08-27
I have my entire movie collection in H.264+AAC/MP4 and every media player that ships with Feisty can play it fine. Look at that progress :)

---

