---
title: "FLAC to mp3 with LAME results in white noise"
date: 2008-05-04
forum: Ubuntu Studio
---

### Post by Dingbats on 2008-05-04
I have a bunch of flac files that I want to convert to mp3 with lame.  I've run lame with different quality settings (though -V 1 is what I want) and with and without -x, but all I get is white noise.  The flacs were ripped from CD with Sound Juicer on default settings.

Any ideas why this is happening?  I'm using lame 3.97, 64 bit.

---

### Post by Stochastic on 2008-05-05
I'd say the IRC channels would give you more definite answers.  Or try gnome sound converter (sudo apt-get install soundconverter), and see if a dependency is missing or maybe it'll go about it in a successful manner?  Either way I'd be interested if you find an answer.

---

### Post by Dingbats on 2008-05-06
Ok, so first off:  Apparently this applies to Lame regardless of source file format.

> **Stochastic said:**
> I'd say the IRC channels would give you more definite answers.  Or try gnome sound converter (sudo apt-get install soundconverter), and see if a dependency is missing or maybe it'll go about it in a successful manner?  Either way I'd be interested if you find an answer.
I tried on #ubuntu, but I just got repeatedly ignored.  I installed sound converter, and on startup it says:

```
'lame' element not found, disabling MP3.
```

I also installed liblame0 and lame-extras, but the problem is still there.

---

### Post by ron999 on 2008-05-06
Hi
To convert a flac file into V1 quality mp3 from the command line you may try this:-
```
flac -d foo.flac -c - | lame -V 1 - foo.mp3
```

---

### Post by Stochastic on 2008-05-06
> **Dingbats said:**
> I tried on #ubuntu, but I just got repeatedly ignored.  I installed sound converter, and on startup it says:

```
'lame' element not found, disabling MP3.
```

I also installed liblame0 and lame-extras, but the problem is still there.

Yeah, #ubuntu is pretty useless as it's too full, next time try #linux-audio (or maybe its #linuxaudio) or even #ubuntustudio as they're less crowded.

try installing the following: ```
sudo apt-get install gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```

Also, if you go into Sound Converter -> Edit -> Settings the mp3 option should be greyed out and there should be a link you can click to install the needed codec, that is if the above command doesn't work for you.

---

### Post by Dingbats on 2008-05-07
> **Stochastic said:**
> Also, if you go into Sound Converter -> Edit -> Settings the mp3 option should be greyed out and there should be a link you can click to install the needed codec, that is if the above command doesn't work for you.
That's right, I noticed that, but multiverse, doesn't that mean it's not free software?  I'd rather avoid that if at all possible.

> **ron999 said:**
> Hi
To convert a flac file into V1 quality mp3 from the command line you may try this:-
```
flac -d foo.flac -c - | lame -V 1 - foo.mp3
```
Nope, the mp3 is zero seconds long.

I'll try #linux-audio too.  EDIT:  Actually, where is #linux-audio?  Google doesn't help much because it strips '#' and '-'...

---

### Post by MetalMusicAddict on 2008-05-07
You're trying to have flac output the file as well. The 1st part before the pipe need only reference the file. The part after should have the output.

Just do:
```
flac -c -d foo.flac | lame -V 1 - foo.mp3
```

Here's a script to convert them all and keep the tags:
```
#!/bin/sh
#This script depends on the: id3v2, lame and flac packages.

   for a in *.flac
      do
         OUTF=`echo "$a" | sed s/"\.flac$"/"\.mp3"/g`

         ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
         TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
         ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
         GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
         TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
         DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

         flac -c -d "$a" | lame -V 3 --vbr-new - "$OUTF"
         id3v2 -t "$TITLE" -T "$TRACKNUMBER" -a "$ARTIST" -A "$ALBUM" -g "$GENRE" -y "$DATE" "$OUTF"
      done

   mkdir -p "$ARTIST"/"$ALBUM"
   mv *.mp3 "$ARTIST"/"$ALBUM"/.
   cp *.png "$ARTIST"/"$ALBUM"/.
```

---

### Post by Stochastic on 2008-05-07
> **Dingbats said:**
> That's right, I noticed that, but multiverse, doesn't that mean it's not free software?  I'd rather avoid that if at all possible.

mp3's aren't open source so any codecs will not be GPL, so if you'd like to use truly free (as in speech) software, try converting to ogg (it gives better audio quality at a lower file size anyway).  If you're worried about spending money, then there's no problems as the multiverse is still free (as in beer).

as for the linux audio channel, it's ##linuxaudio at irc.freenode.org
there's also #lau (linux audio users) on freenode

---

### Post by ron999 on 2008-05-07
[QUOTE=MetalMusicAddict;4904815]The 1st part before the pipe need only reference the file.

Just do:
```
flac -c -d foo.flac | lame -V 1 - foo.mp3
```
Yes, I agree.
My extra "-" is redundant.
:)

---

### Post by Dingbats on 2008-05-08
> **Stochastic said:**
> try installing the following: ```
sudo apt-get install gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```
Is there a way to install only the plugins that are relevant for making mp3s?  I don't want to install say, Flash.

I do use ogg for almost all audio, but I need to be able to distribute my own music as mp3 too, since most people don't know how to play oggs.

---

### Post by MetalMusicAddict on 2008-05-08
> **Dingbats said:**
> Is there a way to install only the plugins that are relevant for making mp3s?  I don't want to install say, Flash.

You don't want anything with gstreamer.

[LIST]
[*]**Mp3** = lame (and id3v2 for tagging if you want)
[*]**Ogg-Vorbis** = vorbis-tools
[*]**FLAC** = flac
[*]**FAAC** = faac
[*]**Musepack** = mppenc
[*]**Wavpack** = wavpack
[/LIST]

I have 2 threads [HERE]("http://ubuntuforums.org/showthread.php?t=785675") and [HERE]("http://ubuntuforums.org/showthread.php?t=183125") you might be interested in.

> I do use ogg for almost all audio, but I need to be able to distribute my own music as mp3 too, since most people don't know how to play oggs.

I think post software players will do vorbis now.

---

### Post by Dingbats on 2008-05-10
> **MetalMusicAddict said:**
> You don't want anything with gstreamer.

[LIST]
[*]**Mp3** = lame (and id3v2 for tagging if you want)
[*]**Ogg-Vorbis** = vorbis-tools
[*]**FLAC** = flac
[*]**FAAC** = faac
[*]**Musepack** = mppenc
[*]**Wavpack** = wavpack
[/LIST]
Ok... but lame apparently doesn't work.

> I think post software players will do vorbis now.
Not iTunes, Windows Media Player, iPods, etc...

---

### Post by Stochastic on 2008-05-10
> **Dingbats said:**
> Not iTunes, Windows Media Player, iPods, etc...

iTunes works but you need to download the plugin, WMP should be the same.  iPods are silly.

Lame SHOULD work, but you seem to be having some troubles with it; that's why I suggested attempting the Gstreamer plugins.  Did you try that route or are you on some hypocritical stance about "free as in speech" (hypocritical because mp3s are closed-source)?

---

### Post by Dingbats on 2008-05-11
> **Stochastic said:**
> iTunes works but you need to download the plugin, WMP should be the same.  iPods are silly.
I agree, but lots of people just want it to work, and oggs won't in many cases.

> Lame SHOULD work, but you seem to be having some troubles with it; that's why I suggested attempting the Gstreamer plugins.  Did you try that route or are you on some hypocritical stance about "free as in speech" (hypocritical because mp3s are closed-source)?
I know that mp3s are closed-source, but I don't want to install a whole bunch of proprietary plugins just because I need one of them.  So is there a way to install only the ones needed for mp3 encoding and not others like Flash and whatnot?

---

### Post by MetalMusicAddict on 2008-05-12
> **Dingbats said:**
> Ok... but lame apparently doesn't work.
It does. The example I gave will work. If it doesn't, you have something wrong on your end
> Not iTunes, Windows Media Player, iPods, etc...
I said software players. Like was already mentioned, iTunes, WMP both do. As well a Winamp, FooBar2000, VLC, Quintessential player... I could go on. (and on)
> **Dingbats said:**
> I agree, but lots of people just want it to work, and oggs won't in many cases.
More cases than not, they work. So now, your iPod is the only thing stopping. Which can most likely run RockBox and then just about any format you can think of.
> I know that mp3s are closed-source, but I don't want to install a whole bunch of proprietary plugins just because I need one of them.  So is there a way to install only the ones needed for mp3 encoding and not others like Flash and whatnot?

LAME is all you need.

---

### Post by Dingbats on 2008-05-14
> **MetalMusicAddict said:**
> It does. The example I gave will work. If it doesn't, you have something wrong on your end
Apparently I do, because it doesn't work here.

> I said software players. Like was already mentioned, iTunes, WMP both do. As well a Winamp, FooBar2000, VLC, Quintessential player... I could go on. (and on)

More cases than not, they work. So now, your iPod is the only thing stopping. Which can most likely run RockBox and then just about any format you can think of.
I do have Rockbox on by iPod.  Don't get me wrong, I love ogg, I use it for almost all my audio, it's just that most people will look confused when faced with an ogg file.  Everyone knows what an mp3 is and how to play it.  This is my own produced music intended to be distributed to lots of people, so I'll need it in mp3 format (as well as ogg and flac).

> LAME is all you need.
I guess it's unfixable on my system then.  I'll just have to convert them with lame on another box.

Well, you can't expect everything to work all the time, can you?  ;)

---

### Post by ron999 on 2008-05-14
..

---

### Post by Stochastic on 2008-05-14
> **Dingbats said:**
> I guess it's unfixable on my system then.  I'll just have to convert them with lame on another box.

Well, you can't expect everything to work all the time, can you?  ;)

One useful tool I've found for situations like this is Synaptic Package Manager's "mark for re-installation" option.  I've had it fix busted packages on previous systems.  Also, do an apt-get update before hand just to be safe.

---

### Post by Dingbats on 2008-05-15
> **Stochastic said:**
> One useful tool I've found for situations like this is Synaptic Package Manager's "mark for re-installation" option.  I've had it fix busted packages on previous systems.  Also, do an apt-get update before hand just to be safe.
Thanks for the tip!  Didn't work though.

---

### Post by ghindo on 2008-05-21
I've been having the exact same problem.  What version of Ubuntu are you running?  What hardware do you have?

I'm running Ubuntu 8.04 on an Dell Inspiron laptop.

**EDIT:**  Nevermind, found the problem.

You need to decompress the FLAC file into a WAV file.  Do this by typing```
flac -d EXAMPLE.flac -o EXAMPLE.wav
```Then, from there, you can decode the WAV file into mp3.

**EDIT NUMBER 2:**  I also found a simple bash script if you don't want to do it all by hand.  See the attached file.

---

### Post by Dingbats on 2008-05-21
That works!  Thanks a lot, ghindo!  :)

---

### Post by bonobo78 on 2009-09-15
@ghindo
Thanks for the script it works great !

Bonobo

---

