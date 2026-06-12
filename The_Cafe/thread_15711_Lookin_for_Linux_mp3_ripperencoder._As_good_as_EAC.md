---
title: "Lookin for Linux mp3 ripper/encoder. As good as EAC or Audiograbber"
date: 2005-02-16
forum: The Cafe
---

### Post by MetalMusicAddict on 2005-02-16
So far my Ubuntu experience has been great. I only have a handful of things to get done to make a switch. :) 1 thing is a full featured CD ripper/encoder. I use Audiograbber on the win side. Im tryin to avoid using WINE. Lookin for something native.

---

### Post by rufius on 2005-02-16
[QUOTE=MetalMusicAddict]So far my Ubuntu experience has been great. I only have a handful of things to get done to make a switch. :) 1 thing is a full featured CD ripper/encoder. I use Audiograbber on the win side. Im tryin to avoid using WINE. Lookin for something native.[/QUOTE]
 Try looking into grip. I use it all the time, it allows for encoding of several different formats including mp3, ogg, flac and a few more I can't remember.

---

### Post by ember on 2005-02-16
Hi,

there is SoundJuicer and Grip, of which I prefer grip. But I'm afraid there's nothing as good as EAC on the Linux side (it's actually one of the apps I really miss).

Yet I have encoded several albums with grip at quality 6 and they sound reasonalby good - actually these were mainly metal bands, so if you like, I can post my configuration, should work for you too.

Best,
Ember

---

### Post by Dylanby on 2005-02-16
I use Sound Juicer.

---

### Post by MetalMusicAddict on 2005-02-16
Ill look at both. Thanx guys. \m/

---

### Post by rwabel on 2005-02-17
there is also ripperX, but I so far prefer grip!

---

### Post by MetalMusicAddict on 2005-02-17
Its funny I new of ripperx before I knew about EAC or Audiograbber. :) I have it on now. APT-GET is great.

---

### Post by rwabel on 2005-02-17
I prefer GRIP because if hat more features, especially with ID TAGS. Maybe I'm wrong, but with RipperX you can't define them.

---

### Post by rwabel on 2005-02-17
If someone achieves to make special character like äöüéàè etc work within one of them, please let me know.
 In grip I tried with UTF-8 as it shoudl be and with the ISO stuff. In ripperx I even didn't find a way to define it. That's sad

---

### Post by kassetra on 2005-02-17
have you tried [goobox]("http://www.gnomefiles.org/app.php?soft_id=531")? goobox has encoding settings that should allow you to specify quality, plus some other nice features. It's a cd-player/ripper... goobox and sound juicer are actually in competition to be the "replacement for gnome-cd" ...
  
  [screenshots of goobox]("http://www.gnome.org/%7Epaobac/goobox/")
  
  I'm going to try it because sound juicer just isn't doing it for me right now.

---

### Post by K6-III on 2005-02-17
Speaking of goobox, the version in Universe needs an update.   Current is 0.7.2, but Universe has 0.6

---

### Post by rwabel on 2005-02-18
goobox looks sweet, but the mp3 encoding preferences are very limited and he doesn't recognize my mp3 endoer :-(
 And no way to set ID Tags, Filename, etc for extracting the songs.

---

### Post by kassetra on 2005-02-18
rwabel: I know this is going to sound like a hassle, but until Ubuntu's universe is updated with version 0.7.2 (which has more features such as track editing), you could probably use [easytag]("http://www.gnomefiles.org/app.php?soft_id=415") to edit the id3tags, filenames, etc. in bulk..
 
 Also, make sure you write to the developers of goobox and let them know what you think is missing from their app.

---

### Post by wolovids on 2005-02-18
[Debian Sid](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=goobox&searchon=names&subword=1&version=unstable&release=all) has goobox 0.7.2.  I just added a good Sid repository and installed it no problem.

Good luck.

---

### Post by rwabel on 2005-02-18
[QUOTE=kassetra]rwabel: I know this is going to sound like a hassle, but until Ubuntu's universe is updated with version 0.7.2 (which has more features such as track editing), you could probably use [easytag]("http://www.gnomefiles.org/app.php?soft_id=415") to edit the id3tags, filenames, etc. in bulk..
  
  Also, make sure you write to the developers of goobox and let them know what you think is missing from their app.[/QUOTE]
 
 I took the it from source, so I'm using also 0.7.2 :-)
 I know I could use easytag, but the use of such tools is to have it all automated. Means getting id tags from feecdb or similar. then be able to add or change what you need in the id tags. Then be able to rip and encode (mp3 or whatever with optional commands) on the fly. Then you should be able to define how he writes the filename and generates the directory.
 
 I know it's a lot but, ripperX and Grip are both very close to it.
 
 The idea to write the developers is good. Will see what they can do.
 thanks

---

### Post by oddabe19 on 2005-02-18
Soundjuicer: I find cuts off the beginning of each track and puts it onto the end of the previous track when ripping. i.e. if a track is 4:00 and the next track is 3:00... sound juicer would rip it as 4:02 and 2:58, it just blends it in.

But it's quick.

Grip: Slower, in my opinion, very configurable, very nice.... but has a hard time distingishing capital letters and other characters.

Goobox: very nice, rips well, great cd player, in general a very nice ripper. Downside: based off of gstreamer (yucky!)

---

### Post by MetalMusicAddict on 2005-02-18
Not that I can do better. Im really just a user, but doesnt it seem to me that there would be a really great MP3 ripper for linux? EAC and Audograbber kill anything on linux. It seems like anything it takes $ to get something done really well. Or money in it somehow.

---

### Post by ember on 2005-02-18
I would agree with you that there is no application that compares to EAC on Linux yet. I have the impression that audio under Linux is still under heavy development. Maybe it will take another year or two for it to produce applications that match their windows pendants.

Yet I'll have a look a goobox, could be at least a very cool CD Player. (note to myself: maybe I should give muine a try too)

btw: Has anybody tried running EAC in wine?

---

### Post by BWF89 on 2005-02-18
MP3 players for (non-commercial) Linux distros are illigle. I'm turning you into the athoriorties! :grin:

---

### Post by MetalMusicAddict on 2005-02-19
[QUOTE=ember]I would agree with you that there is no application that compares to EAC on Linux yet. I have the impression that audio under Linux is still under heavy development. Maybe it will take another year or two for it to produce applications that match their windows pendants.

Yet I'll have a look a goobox, could be at least a very cool CD Player. (note to myself: maybe I should give muine a try too)

btw: Has anybody tried running EAC in wine?[/QUOTE]
EAC is on the WINE page as an app that you can run. Im lookin into it.

---

### Post by br0adband on 2005-02-19
Realistically speaking, and I say this based on using EAC for almost 5 years now, it's not *that* important. Really, it's not.

I've done countless tests using EAC and several scratched/dirty/fingerprint laden CDs I have that set off the C2 error correction. I've used special CDs I purchased for calibrating CD players (I am a tech, yanno) and in the *long run*, EAC rips CDs just like the rest of them.

I used to sit there and do Secure ripping with CD after CD after CD after CD constantly, spending hours trying to create the "perfect rip" to pass to LAME to encode.

I recently decided to some down and dirty real-world testing. I used several of the damaged CDs I have (damaged to the point where playback in a normal CD player doesn't work without skipping) and fired up EAC under WinXP and let it go. I'm using a laptop CDRW/DVD combo drive that is Accurate Stream/Cached/C2 compliant.

The results weren't surprising.

With EAC Burst and EAC Secure, the checksums were always the same - every single time - in over 100 test rips I did. I would rip the data in Burst mode, eject the CD, put it back in, rerip in Secure and every single time the checksums were always verified. This happened on 40 CDs using about 105 test tracks chosen at random but they were all tracks known to *not* play correctly without skips in a normal CD player used for audio playback.

I know EAC is nice; I wouldn't have used it so long if it wasn't. But 5 years ago it was special, and a completely unique program. Nowadays, with the quality of CD and DVD drives being what they are, EAC Secure mode seems like a waste of time since it gives the same data to your MP3 encoder that Burst mode does - only much slower.

You can do these tests yourself, yanno. Just get a damaged CD with at least one track that won't play normally. Set EAC for Burst mode, then right click on the track you want to rip (the damaged one), choose Test - Uncompressed and let it rip to create a checksum. Write down the checksum since when you eject the CD EAC will clear the drive's contents.

Put that CD back in, change EAC to Secure mode and redo the Test - Uncompressed. I'm almost 100% positive the checksum will be the same as the Burst mode.

EAC is a fantastic ripper - quite possibly the best ever made, but seriously, isn't there a point of diminishing returns here? Would your ears hear a single bit or two out of place?

Another source for great information about audio encoding is:

[http://www.hydrogenaudio.org](http://www.hydrogenaudio.org)

Just my $.02.

Paul

---

### Post by MetalMusicAddict on 2005-02-19
Thanx for the reply but do you know of something as good for linux? ;)

---

### Post by br0adband on 2005-02-19
I'm still learning myself since I'm new to Ubuntu. Haven't quite gotten to the point where I'd be ripping music anymore, I have several thousand mp3 files as it is.

Take the advice of the others in this thread since they're more than likely way ahead of me using Ubuntu/Linux. I asked some friends in some tech IRC channels I live in and they said grip also, so give that a shot.

Good luck!

Paul

ps
Let us know what you chose and why, too. Might help someone else in this quest.

---

