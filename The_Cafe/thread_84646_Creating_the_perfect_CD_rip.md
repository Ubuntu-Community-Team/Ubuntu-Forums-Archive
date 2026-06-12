---
title: "Creating the perfect CD rip"
date: 2005-10-31
forum: The Cafe
---

### Post by jonny on 2005-10-31
I'm about to emabrk on a full re-rip of my CD collection, having mistakenly done a poor job some time ago with a crackly decoder at a low bit rate in wma format.

This is a big job, and I want to do it well.  Hopefully my grandchildren will be using the same files in the 22nd century on some awesome yet-to-be invented device.  This is a call for all you audio experts to enlighten me.

Some questions:

1. Do ripping programs differ much in quality?  For example, is Grip better then Soundjuicer.  Are there some subtle settings that I ought to know about?
2. I have some damaged CDs.  What's the best way of rescuing them.
3. Is OGG 320 kb/s a sensible choice.  I'd rather not use FLAC, as my music player doesn't understand it, and I can't tell the difference.
4. Is there any way to speed the process up, or is ripping inherently slow?
5. What software does the community love?

---

### Post by xequence on 2005-10-31
I dont think the different ripping programs are better or worse. (Unless you count features...) but it is the accual encoder they use. For example, with MP3, LAME is said to be the best, but slower.

Yes, 320 Kbps OGG is very senseable if you want perfect sound... Well, no lossless is perfect, but I doubt anyone can tell the difference between OGG 320 Kbps and lossless FLAC.

The only thing I can think of to make ripping a CD faster would be a fast CD drive and processor. This is one of those number crunching things that fast processors help alot with.

---

### Post by Malphas on 2005-10-31
[QUOTE=xequence]I dont think the different ripping programs are better or worse. (Unless you count features...) but it is the accual encoder they use.[/QUOTE]
Not quite correct, some rippers are more secure than others and the drive you have is a variable too.  [EAC]("http://www.exactaudiocopy.de/") is the most secure ripper out there, but unfortunately it's Windows only and there's not a Linux equivalent I know of that comes close.  Could give it a crack in WINE though.

Edit: [Spoke too soon perhaps?]("http://www.hydrogenaudio.org/forums/index.php?showtopic=38418")

---

### Post by mrtaber on 2005-10-31
On the Linux side, check out Grip...it uses Cdparanoia to rip...I've found it to be faster at ripping than SoundJuicer, while making pretty darned accurate rips.  You also get to choose your encoder (LAME, OggEnc, FLAC--but you'll have to install them using apt).

Mark :)

---

### Post by reedlaw on 2005-11-16
I am getting horrendous quality rips using both Sound Juicer and abcde.  I hear crackles even when I play the CD in Sound Juicer, so maybe it is a scratched disc.  Is there any way to rip a scratched disc without the terrible crackles?  I would rather there be no sound than a high-pitched crack.

Edit:
I just tried ripping an unscratched disc and the sound is hissy.  I can play the CD fine in Sound Juicer but the ripped .flac sounds terrible.

---

### Post by Carnwaj on 2005-11-18
Hi,

I've had similar experiences as you. Ripped all my music then realsied there was a much better way.

I would reccomend the hydrogen audio forums and read all you can in there.

My solution is to use EAC to rip (although I will check out grip)
Convert everything to FLAC (this is my archive)
Convert from FLAC to whatever you need at the time.

If you want your grand children to listen to your music then keep a lossless archive (FLAC or APE). Then you can convert to whatever format is flavour of the month.

It does take a ling time to RIP everything so do your homework at hydrogen audio.

Regards

Carnwaj

---

### Post by psusi on 2005-11-18
320 kbps or FLAC is overkill.  Even audiophiles with the best hearing listening to the music on the very best audio equipment can not tell the difference between the original cd and a well encoded mp3/ogg of around 160 kbps.  

Use ogg in vbr mode such that it comes out to an average of around 160-190 kbps and it should sound flawless.

---

### Post by bionnaki on 2005-11-18
If you are going to archive your music, you really should go lossless. I recommend .flac - with lossless you can convert these to whatever lossly encoding down the road (mp3, ogg, whatever) and still have the original .flac at perfect quality.

When I encode, I use crip - its a commandline ripper - works great. just modify the /usr/bin/crip with gedit for whatever preferences you prefer (location of cd drive, for example).

some might say flac is overkill in audio quality - they might be correct, but they are missing the point of lossless. Lossless is perfect for archiving an exact copy of a cd - you can encoding to whatever lossy format later down the road without losing the archive. If you were to rip everything to some extreme bitrate .ogg file, what happens in 3 years when you are no longer pleased with .ogg for whatever reason? you'll have to re-rip your collection yet again.

---

### Post by Lovechild on 2005-11-18
1. not really, but use sound-juicer it's much simpler and cleaner
2. yes, set /apps/sound-juicer/paranoia to 255
like this:
gconftool -s /apps/sound-juicer/paranoia 255
this greatly increases the chances of ripping correctly - also you might want to try cleaning your cds well before ripping them.
3.  Ogg Vorbis at 320Kbit is likely to be overkill, I personally use the default settings and can't tell the difference, another maximum quality choice would be ripping to flac and since that's loseless audio you can reencode the flac file if you want to use the song on your player.
4. Ripping is slow and in my experience it causes some io load problems under Ubuntu (seems much better in Fedora). but again for prestine cds set paranoia to 0 and you'll save some time.
5. GStreamer, rhythmbox  and Sound-juicer are my big audio loves right now.

---

### Post by raublekick on 2005-11-18
I never really liked OGG much. I've heard it takes out some of the bassiness of songs, but I can't really confirm it myself. I always use 192kbps mp3, which sounds just fine for all of my CDs. 

How good is the compression for .flac? And how is it really lossless? 

If only I could afford a few terrabytes of hard drive space and just rip the wavs from CDs...

---

### Post by mcduck on 2005-11-18
For scratched CD's, I recommend Grip, as it can actually fix some errors. If you still hear cracks, you'll have to fix those CD's. There are some nice CD-repair-kits available, usually with a bottle of polishing liquid and a piece of cloth. You put some drops of liquid on CD and then polish the disk with some force for couple of minutes. This way you can get rid of all big scratches on CD's.. It work's great, I've even managed to fix a DVD that had spent couple of months without a case in car's trunk.

---

### Post by bionnaki on 2005-11-18
[QUOTE=raublekick]I never really liked OGG much. I've heard it takes out some of the bassiness of songs, but I can't really confirm it myself. I always use 192kbps mp3, which sounds just fine for all of my CDs. 

How good is the compression for .flac? And how is it really lossless? 

If only I could afford a few terrabytes of hard drive space and just rip the wavs from CDs...[/QUOTE]

192kbps mp3 sounds swishy to me, personally. High-hats are swishy and bass is flat. My ears can generally hear the dataloss. But quality of lossy encodings is really up to your ears - if you cannot tell the difference, then go for it.

as for flac, you might want to visit [http://flac.sourceforge.net](http://flac.sourceforge.net)
flac works like a .zip or .tar file - you can compress and decompress without losing any data.

---

### Post by xequence on 2005-11-18
[QUOTE=raublekick]I never really liked OGG much. I've heard it takes out some of the bassiness of songs, but I can't really confirm it myself. I always use 192kbps mp3, which sounds just fine for all of my CDs. 

How good is the compression for .flac? And how is it really lossless? 

If only I could afford a few terrabytes of hard drive space and just rip the wavs from CDs...[/QUOTE]

It is lossless because while mp3 takes out information that we cant here, and compresses it, flac just compresses it. It compresses a WAV file in half, or so ive heard.

Now me personally, I like alt preset standard, which is as far as I know the same file size as 192 KBPS but better quality, and its VBR also. I havnt found out how to encode to it yet, but the albums I download that are encoded in it are good.

Dont even get me started at how annoyed I am with all the 128 Kbps MP3 crap on non-bittorent P2P networks...

---

### Post by makeyre on 2005-11-18
Does anyone know a cdparanoia-based ripper that can write log files?  Grip would be perfect for my needs but it only keeps a log file in the interface, and doesn't seem to have any option to write it to disk automatically when it rips.

---

