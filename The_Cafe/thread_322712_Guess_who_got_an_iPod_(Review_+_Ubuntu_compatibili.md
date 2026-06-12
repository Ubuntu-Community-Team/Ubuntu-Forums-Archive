---
title: "Guess who got an iPod? (Review + Ubuntu compatibility)"
date: 2006-12-20
forum: The Cafe
---

### Post by jdong on 2006-12-20
As an early holiday present, I got a 30GB White iPod video. Before, I've had a 2GB no-name video/MP3 player with a 1.5" screen (it takes 220x176 xvid+mp2 audio), and it was starting to fail on me after a few months of service.

By now, I think everyone's seen the iPod, so I'll spare the trouble of pictures and focus on my two cents about the device, and also my experiences of how well it works under Linux and my contributions here and there to documenting the device.

I've owned it for almost a week now, so I'm purely going by that experience:

**Initial Impression**
I've done a lot of research into the various audio/video player devices, so I'm no stranger to the iPod's appearance. However, I'll have to say that it definitely looks more stunning in person than in picture.

The case is a blend between the classic Apple cream-white and the back is a chrome-like silver. The silver stuff scratches real easily, and iPod owners tell me that so does the screen. So far my screen has not taken any scratches, but I am going to buy a case for it this weekend to be safe.

From initial impressions, it looks like a very attractive device.

**Audio Performance**
I'm not a terribly picky music listener, I've lived through years of using cheap audio players. I'd have to say that with identical headphones/speakers and music files, the iPod seems to play them back better. Maybe it's my imagination, but I definitely perceive a difference.

I found it easy to browse through my collection of songs and find what I'm looking for. The search feature really helps, too. Even when browsing a list of 4000 songs or so, the iPod did not feel laggy or slow, unlike my previous players.

During playback, it was very convenient to navigate within the songs. I found everything a breeze to use!

**Video Performance**
When I first got the iPod, I did some quick sloppy xvid 500kbit 320x240 rips so that within an hour I had around 5-6 hours of watching material on the iPod to entertain myself. Then I slowly went back and did high-quality 640x480 H.264 encodes.

With both types of video, the quality was very respectable. I didn't feel cramped about the 2.5" screen at all. It was crystal clear and quite bright.

Finding movies is a bit more of a challenge, as there's no built-in sorting mechanism by tags for the most part. Instead, you have to organize everything yourself using video playlists. It's not a bad thing, but it took me a while to realize that!

During playback, there's very nice volume control, FF/REW, scrollwheel seeking, and brightness control. It wasn't difficult to navigate to a specific segment of video. The only complaint is, most of the times when you start seeking there's a 5-second hard disk spinup lag. It's a bit annoying, but it's understandable. Would you rather deal with some seek lag or have less battery life? Another thing was, upon completion of a video, the iPod loved to go back to the main menu / list rather than playing the next video in the list. Kind of troublesome, but no big deal.

I've yet to get a TV-out cable for my iPod, but some of my friends have them already. Testing my video files on their TV/iPod setup, I was quite impressed. The quality of the 320x240 on a 35" plasma HDTV was quite watchable, but the 640x480's were stunningly clear, as if it were directly from the DVD source. At 550MB for a 2-hour DVD (500kbit H.264), that's quite impressive!

**Battery life**
Battery life is quite decent. For music, I estimate at least 15 hours of playback with my usual habits (mostly following a playlist but skipping a song here and there, and a bit of screwing around with games or settings). For video, I've been able to get about 4 or so hours of playback after a bit of light music listening, so I'd actually say video playback time is higher than advertised. Note that the advertised playback times are with the iTunes store high-quality h264 movies, so I'd venture to say that lower-bitrate movies would yield longer playtime.

Another interesting thing to note is that when you turn off the iPod, it actually goes to sleep instead of shutting off completely. This leads to quick 1-second shut down and startup, and you don't lose where you left off. My other media players would need to start up completely again, and I'd have to navigate back to where I was, and so on.

Charge time was quite reasonable. I'd say a full charge takes around 3 hours or so, but I haven't exactly sat there and watched it charge ;-)


**Linux Compatibility:**
Ok, the fun part we've all been waiting for... How well does it work under Linux? In a quick sentence: quite well -- you can encode audio, video, and transfer them very smoothly with Linux and Open Source software. Allow me to elaborate:

**Encoding Audio**
The iPod is very lenient in accepting standard MP3's, also several uncompressed formats, and also AAC in a MP4 container (Apple gives that a m4a extension). A wide assortment of Linux tools, many even GUI, can generate files complying with these requirements, so I won't delve deeply into this. Notable is the lack of ogg support.

**Encoding Video**
Well, well, video is not as lenient as Audio, though much more lenient than my previous audio device. Shortly summarizing, the iPod takes limited variants of MPEG-4 ASP (aka xvid, divx, h263, ffmpeg mpeg4) or MPEG-4 AVC (aka h264) video with AAC audio in a MP4 container. The long story is that  the "limited variants" part expands to all kinds of esoteric restrictions on encoding settings that's different for each codec and even each resolution within each codec!

I readily found definitive guides for using ffmpeg to generate iPod-compatible MPEG-4 ASP videos, but H264 was quite harder. Not a single guide I found was accurate or worked flawlessly. After around 30 hours of constant experimentation and nearly 100 iPod reboots from my various disfigured mp4 attempts, I finally perfected an all-encompassing H.264 setting that generated great quality.

In the spirit of spreading the h264 love and saving other iPod users from this pain and misery, I've fully documented my findings on the Wiki and in our own HOWTO section:
[https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding)
[http://ubuntuforums.org/showthread.php?t=321943](http://ubuntuforums.org/showthread.php?t=321943)

The Wiki article is much easier to follow, but the forum version shows how to do that with script files and also automate batch-encodes. I do intend on adapting the HOWTO's additional contents to the Wiki article in the near future, but I need a break now, I'm tired!

**Transferring to the iPod**
Edgy's GtkPod version handles audio and video files without a hitch, and Edgy's Rhythmbox and Amarok both deal effortlessly with audio, too. You can use any combination of those programs, but common sense would say only use one at a given time!

For transferring AAC audio files and also all video files properly, you need the **gtkpod-aac** variant that supports the MP4 container. Else, gtkpod complains loudly about not understanding the MP4 container and tells you that you need to rebuild gtkpod!

Actually, that's not completely true :). You can transfer videos using regular gtkpod with a caveat. Rename the .mp4 to .mov, and gktpod deals with it happily. Downside? Seeking through the video using the wheel won't work, it'll just go back to the beginning. FF/REW works though. I've heard that if you manually set the Play time in the properties, that'd make it work too, but save yourself the trouble and just install gtkpod-aac!


The new GtkPod 0.99.8 release supports dealing with multiple iPods and apparently also sports some bugfixes, but getting it working in Edgy is a involved process. You must backport a newer libgpod, and also gtkpod from Feisty (you also have to tweak the build dependencies to build AAC support, as gtkpod-aac hasn't been updated to 0.99.8 yet!). In addition, any programs on your system using libgpod, such as rhythmbox or amarok, have to be rebuilt against the new libgpod, else they will **corrupt your iPod**'s database! If you think you have the technical know-how to deal with it, be my guest! Most of this work is doable through the assistance of prevu.

Otherwise, just wait for Feisty and be happy that the Edgy tools work!

**Firmware Updates**
BAD news: Firmware updating can only be done through iTunes, so you need a OSX or Windows install to update the iPod's firmware. The procedures for cutting iPodUpdate.exe firmware no longer works since iTunes 7 handles the updates. If someone has found a way to do this natively with Linux, please let me know!

**Alternative Firmware**
Right now (late 2006/early 07) Rockbox runs well on the 30GB 5.5G video ipod. It **does not yet run on the 80GB version** because they are having issues interfacing with its hard disk controller.

I loaded RockBox on from the beta installation wiki page on their site. It was pretty straightforward to follow with instructions for every platform. It does require a bit of terminal usage and make you cringe, but you can't cause any permanent damage to your iPod.

Most importantly, after installing Rockbox you can still dual-boot the original iPod firmware so in no way would you 'lose' any functionality. So I guess I have to do a mini Rockbox review here. I've been only using it for a few days so excuse my ignorance :D

**Rockbox Pros:**
(1) Flat-tree storage model over standard USB Mass Storage. No need to use any special database updating apps, you just drag files on and they'll play.
(2) Vast array of music formats. Most importantly, this brings ogg support to the iPod, and from my testing it's a pretty solid and wide-range ogg decoder, capable of dealing with a lot more codec configurations than the Cowon players and other hardware ogg decoders.
(3) Better sound quality. Especially when either the equalizer, high volumes, or both are used, rockbox's audio quality sounds significantly better than the stock iPod firmware's. It's definitely noticeable and we did some blind tests between friends of rockbox vs stock, and no doubt Rockbox sounded better.
(4) More discrete volume control. Rockbox's volume setting can reach far softer volumes than stock firmware. In a quiet environment even the stock firmware's softest setting is blaring loud.
(5) More control over audio playback -- the flexibility and configurability of audio playback on Rockbox is nothing short of amazing -- I've rarely even seen a desktop music playing program offer so many options!
(6) Hacker/geek appeal: plugins and added capability. The rockbox turns the iPod into nearly a PDA-like device with games, file managers, text viewer/editors, etc. I've actually had it come in very handy before viewing some source code on the road and also reorganizing or deleting some files without a troublesome computer hookup.
(7) Works great with any OS. Requires no more than USB mass storage support to add music/media or upgrade firmware. This is a great bonus! As long as you have the usb cable around, you can use your iPod to its full potential from any computer.
(8) Plug in to charge with no interruptions to playback. With standard firmware whenever you plug into USB, the player will cease playback and switch into USB/disk mode. Rockbox, if you hold MENU while plugging in the cable, will allow it just to register as a charger and continue what you're doing uninterrupted. Since I always work near my computer it's very convenient for me to plug in and charge.

I'm probably still missing a lot of pluses, but you can go to the Rockbox site for more about its capabilities. They aren't exaggerating or lying :D

**Rockbox Cons**:
Sadly I do have to report some cons for Rockbox:
(1) Greatly diminished battery life: My battery life under Rockbox is around 8 hours while stock firmware delivers a good 15-18 hours when doing a combination of playing music and organizing playlists. It's not enough to drive me away from Rockbox as I'm always close to a USB port, but I can see where it'd get irritating. Rockbox team acknowledges this and says they have more room for improvement.
(2) No video playback. Well, no practical video playback. There's an experimental mpeg2 video-only (no sound) decoder and a rvf greyscale video player but both come nowhere close to TV-projectable 640x480 h.264 of the native iPod. This is the only reason that I reboot into iPod firmware at all.
(3) Intimidating initial install -- the installation procedure, while meticulously and clearly documented, is frightening to do, and will no doubt scare off many non-technically-inclined. Rockbox can really benefit from either a GUI installer or an automatic CLI script installation.
(4) Unintuitive interface. Ok, before you all flame me at once, allow me to explain. The stock iPod firmware was very intuitive, in the sense that 15 seconds into using my iPod, I was choosing out songs and working through the menus and beginning to understand how to do On-the-go playlists. The UI had almost no learning curve and it was easy to become immediately productive. The same cannot be said about Rockbox. It took nearly 30 minutes of trial-and-error before I could effectively negotiate the UI to the point where I can efficiently play music, stop music, and so on. I think this may be just due to the explosive number of features that Rockbox offers over iPod's simple interface. Fortunately they have a wonderful manual that's highly relevant to each device's specific controls. This is definitely a program where you'd highly benefit from reading the manual!
(5) Ugly initial interface -- the default Rockbox theme is very minimalistic and ugly. Very small and difficult to read fonts coupled with a playback interface that looks worse than my Sandisk Sansa m240's charcell pixelized black-and-white screen. Theming , I'd say, is a must!
(6) High post-install configuration overhead. This goes with 4 and 5, and also with the way most traditional Linux distros are stereotyped. You need to do a lot of option/menu/theme tweaking and customizing to make it feel usable. The iPod stock firmware is pretty usable right the way it was.
(7) Decoders not as powerful/optimized as stock firmware. Comparing max bitrate for AAC and MP3, they are much lower for Rockbox than Apple's firmware. Not enough for most people to run into trouble, but it did make me have to re-encode some 384kbit MP3's (don't ask. it's better left unanswered :D) before they'd play smoothly!
(8) Sometimes sluggish menus during audio playback. This seems to be a problem with the multitasking scheduler of Rockbox, in that while music is playing everything else has at times quite noticeable lag.
(9) Unaccelerated scrolling -- the touchwheel drivers don't support acceleration... scrolling through a large amount of data is not a pleasant experience sadly.
(10) Loss of DRM format playback. Whether this is a pro or con, everyone can interpret in their own way, but if you have a large collection of iTunes-purchased music, tough luck, there's no legal way to play them back on Rockbox.
(11) Possible legal issues? IANAL but I don't think Rockbox is in the legal clear for its ability to play back mp4-containers, AAC, MP3, and encode to MP3?
(12) Still shows its beta-ness. Rockbox is still not production-quality, of course. It's still quite possible to activate some features or plugins that lock up or otherwise glitch.

Overall I really enjoy Rockbox and use it from now on as my primary music playing environment.

**Conclusion**
Overall I'm very satisfied with my new iPod Video. It's a wonderful device that's both elegant in appearance and great in performance. In addition, for the most part it's very smooth-sailing in Linux.

---

### Post by pay on 2006-12-20
Thank you for this review. I'm now split between then Creative Vision M 30gb and the Ipod Video 30gb.

---

### Post by Polygon on 2006-12-20
good to hear. If apple would just support .ogg format, im sure a bunch of linux users would have no problem using an ipod.

---

### Post by fatbastard spice on 2006-12-20
You might want to give Fusepod a go. It's certainly a novel way of approaching the transfer/usage of media on the ipod.

---

### Post by pay on 2006-12-20
There is a project called rockbox that puts a new operating system on the ipod which then supports ogg vorbis.. Might be worth a try.

---

### Post by jdong on 2006-12-20
> **pay said:**
> There is a project called rockbox that puts a new operating system on the ipod which then supports ogg vorbis.. Might be worth a try.

I briefly touched on that in my Alternative Firmware section; support for the 5.5G iPod is experimental at best , and you'll also lose video support. iPodLinux also has experimental/little 5.5G support and their video player only plays uncompressed AVI's currently.

If audio is all you do, then I guess RockBox would suit you well, but until Rockbox has H.264 video capabilities unfortunately it won't be for me :(

---

### Post by pay on 2006-12-20
Oppps. Missed that bit.

---

### Post by tenshi-no-shi on 2006-12-20
You may want to look into a brand called Cowon. They make a mp3/video player that supports both .ogg and .ogm (Video ogg) and best of all they support linux, mainly because they use no software to tranfer to the media player, it acts like portable HD in that respect. My Friend has one and hase been very happy with it.

---

### Post by jpkotta on 2006-12-21
> **tenshi-no-shi said:**
> You may want to look into a brand called Cowon. They make a mp3/video player that supports both .ogg and .ogm (Video ogg) and best of all they support linux, mainly because they use no software to tranfer to the media player, it acts like portable HD in that respect. My Friend has one and hase been very happy with it.

Cowon++  

I have a M5 (no video for me, thanks) and I'm quite happy.

---

### Post by jdhore on 2006-12-21
> **jdong said:**
> I briefly touched on that in my Alternative Firmware section; support for the 5.5G iPod is experimental at best , and you'll also lose video support. iPodLinux also has experimental/little 5.5G support and their video player only plays uncompressed AVI's currently.

If audio is all you do, then I guess RockBox would suit you well, but until Rockbox has H.264 video capabilities unfortunately it won't be for me :(

if you wanted the nice-ness of an alternative firmware, but don't want to leave the video-playing-ability of the Apple FW, do what i do, dual-boot your iPod...i installed Rockbox and Loader2 and when i "reboot/reset" my iPod, i get a bootloader menu that lets me choose if i want to boot into the Apple FW, Rockbox, Disk mode or sleep mode.

---

### Post by matthew on 2006-12-21
> **jpkotta said:**
> Cowon++  

I have a M5 (no video for me, thanks) and I'm quite happy.I'm another happy M5 user, so if someone's reading this and in the process of deciding, I recommend Cowon highly.

@jdong: nice review. Thanks!

---

### Post by BarfBag on 2006-12-21
Thanks for the review.  I'm considering an mp3 player to drown out the creep-o's at work.  This has made me consider iPod.

---

### Post by happyisland on 2006-12-25
I want to second (it might be a third by now) the recommendation for Cowon. I have an X5 and it works great, plays FLAC, OGG, etc and hooks up to any computer (Windows, Mac, and Linux) without any software required. From what I understand they have a more video-centric player, the A2, that is also really nice. 
Support the companies that support our open standards!

---

### Post by jdong on 2007-01-02
I had the time to play around with Rockbox and added a Rockbox review. I have not yet played with iPodLinux, because:

(1) Lack of time
(2) Support for 5.5G ipods is pretty unclear. There's really sketchy details on if it works or not, and apparently it only works now on Macpods, which is in direct conflict with rockbox
(3) From everything I've read on both, it would look like Rockbox at this point is more usable/mature/featureful as a DAP which is what I want.

---

