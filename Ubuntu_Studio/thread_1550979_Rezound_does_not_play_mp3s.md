---
title: "Rezound does not play mp3s"
date: 2010-08-11
forum: Ubuntu Studio
---

### Post by linuxgrrl on 2010-08-11
I am using ubuntu (regular) but I think by now I have installed many studio packages.

I've seen Rezound recommended as a good mp3 editor, but when I try to open an mp3, it says it does not recognize it ... would you like to open in Raw format?  and when I click yes, all I get is static.

What am I missing?

---

### Post by maghoxfr on 2010-08-15
But you can play mp3's with other players (i.e: rhythmbox)? Have you installed the restricted-extras?

---

### Post by linuxgrrl on 2010-08-15
Yes, I can, and I have. I'm wondering if I need to compile Rezound myself, maybe Ubuntu has a "special" version of the package without the right libraries installed?

---

### Post by maghoxfr on 2010-08-15
I don't know, I'm not familiar with Rezound, does it need jack to run? The only thing I can think of is wrong conexions, or ouput configuration on the software, that's my knowledge limit, sorry.

---

### Post by linuxgrrl on 2010-08-15
Yeah, I do have jack running, and Rezound plays ogg files just fine through jack. I'm baffled b/c other posts that I've seen recommend Rezound specifically for editing mp3s. I guess I'll have to try compiling it myself and see if any better results ...

What I really need is something that will play mp3s through Jack from a playlist.  I've seen all the kludgy workarounds to get banshee, etc. playing thru jack and they are causing crashes for me.  Alsaplayer is too stripped down to use (and also crashes when I try to skip forward or back).  

Anyone have ideas?

---

### Post by AutoStatic on 2010-08-16
Aqualung, by far one of the best jackified players. Rezound should work with mp3's, did you install all the necessary packages (gstreamer-plugins0.10-bad, gstreamer0.10-plugins-bad-multiverse, gstreamer0.10-plugins-ugly and gstreamer0.10-plugins-ugly-multiverse)?

---

### Post by linuxgrrl on 2010-08-16
Thanks for the Aqualung suggestion - I will try it. For Rezound, yes, I have checked -- all those plugins are installed.  Anything else I can do?

---

### Post by maghoxfr on 2010-08-16
Maybe if you ask over [here]("http://rezound.sourceforge.net/") or you join their mailing list you'll get more luck.

---

### Post by AutoStatic on 2010-08-17
Probably not, Rezound is not being actively developed anymore afaik.

---

### Post by sgx on 2010-08-17
> **AutoStatic said:**
> Probably not, Rezound is not being actively developed anymore afaik.
Not a bad option for a 'Summer of Code' project! :-k

---

### Post by RaumTrug on 2010-08-18
too sad. I'm on 9.10, and rezound just loads any mp3 file i feed it. the interface is a bit awkward (windows style, yuck!), and has some little bugs, but apart from that it's a nice prog to cut&edit samples.

hehe I just noticed my bach mp3's sound fine backwards as well as forwards (drag the wheel at upper left corner from 1.0 to -1.0 while at some position...) - just the notes fade it instead of out, but that's of course off topic here...

as for a jack-enabled mp3-player, if you like(d) winamp, then install audacious! it looks the same, and can be made to output via jack. aqualung is better with jack, of course.

the "load as raw" thing resulting in noise is because rezound loads the .mp3 file, treating it as if it was some uncompressed .wav-file without header! as .mp3 is heavily compressed, and the individual data is spread kind of equidistributed along its range, something close to white noise (pure random data) will be the result :(

sorry, but I have no clue on how to config rezound to use the proper mp3 plugins, it just does on my pc. maybe you could try starting it from a terminal, it prints out information about the file just loaded for me...maybe it prints some error message that could be helpful!

---

### Post by AutoStatic on 2010-08-18
On 10.04 any mp3 just loads fine here. Rezound uses lame to decompress mp3's so if you don't have lame installed mp3's won't load.

---

### Post by linuxgrrl on 2010-08-19
OK, I'm pretty sure I have lame installed, but Autostatic, your comment reminds me of something.
I'm using 64 bit Lucid.  Could that be why yours works and mine doesn't?  

I vaguely recall once trying to compile some other sound-related app where the ./config kept telling me that lame was missing, when all lame-related stuff (including -dev and -lib packages) actually had been installed.  It made me wonder if 64 bit stores some needed files in the wrong place?  Anyway, if you could confirm whether you have 32 bit or 64 that would eliminate one possibility.

PS, thanks for the Aqualung suggestion, it is working perfectly for playback.

---

