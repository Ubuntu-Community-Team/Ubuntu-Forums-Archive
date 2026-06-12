---
title: "devede makes iso too small"
date: 2008-07-11
forum: Ubuntu Studio
---

### Post by angryhomer17 on 2008-07-11
I've got a 5.7 gig mpeg that I originally got from using dvd::rip. My ps3 says it's a mpeg-2 file, but will not play it. Supposedly it's corrupted data. (The source is a 4 gig dvd and a 1.7 gig dvd; I merged the two mpegs later)

I'd like to get the 5.7 gig mpeg on a 4.4 gig dvd. I tried dvdauthor on the mpeg, but supposedly the mpeg isn't a good vob unit. After converting the mpeg to an iso image with genisoomage, I opened it with k9copy, which promptly crashed. dvd95 doesn't handle iso's as far as I can tell. 

I've tried mandvd and tovid before, but wasn't able to use them effectively. 

Devede works pretty well. I can get the iso it outputs to play on my ps3, which is great, but the quality sucks. There are a lot of compression artifacts. I have both quality options checked and no deinterlacing. I copied the audio and set the video bitrate to 6659 Kb/s. Devede estimates the final size to be 4400 MB, which is the size I can fit on a single layer dvd. After it does all it's stuff, I get an iso that is 2.9 gigs, nowhere close to the 4.4 gigs I wanted. 

I tried upping the bitrate to the maximum 8000 (the original is 9800) and changing the media size to 8.5 gig, but that does not produce a file much bigger. 

It appears that devede uses mencoder to convert the mpeg to a dvd compliant mpeg. 

What I want is a high quality video that can play on my ps3 that fits on a single layer dvd. 

I can use:
k9copy-- after i get an iso it can handle
mencoder-- not sure what options to use
dvdauthor--if the vob units are compatible

So any suggestions on how to get my ps3 to accept the (completely valid) mpeg, or convert the large mpeg to a 4.4 gig dvd, or make devede make a larger iso (which will hopefully reduce the visibility of artifacts) would be helpful.

Also, if anyone knows of and/or uses a standalone dvd player that can play pal, ntsc, mpeg, cd's, divx, xvid, mkv, etc. let me know.

---

### Post by angryhomer17 on 2008-07-11
Request to admin: Please move from multimedia production to multimedia & video.

---

### Post by lisati on 2008-07-11
Is K9Copy able to read the original DVD? 
I think one of the programs  you've mentioned (I can't remember which at the moment, & I don't currently have them installed on my machine to check) is able to do the equivalent of DVDshrink's ability to copy from a dual layer disk to a single layer recorable disk.

---

### Post by angryhomer17 on 2008-07-11
I just finished watching the chumscrubber [http://www.imdb.com/title/tt0406650/](http://www.imdb.com/title/tt0406650/) (which btw is a great movie, though not everyone will find it appealing). It was encoded with xvid (xvid.hls, i think, not sure what the hls is for), and I was very impressed with the quality. Especially since I had it burned on a 700 MB cd. 

I figure if I can deal with an xvid compressed from possibly 6000 MB to 700 MB (almost 9 times smaller), then surely I will be more than happy from 6000 MB to 4400 MB. 

Xvid avi's seem to play well on the ps3, at least this last one did. I don't know if I'd want to do that for all my large mpeg movies, because of compatibility with standalone dvd players. 

So is xvid just really good at compression or was it because of a high quality source or something else? I've read that some dvd's are highly compressed to begin with, while others are much higher quality for their size. Does anyone know if that is true?

I'm testing an mpeg to xvid copy using transcode, so we'll see if that works well.

---

### Post by angryhomer17 on 2008-07-11
> **lisati said:**
>  Is K9Copy able to read the original DVD? 

Unfortunately, I do not have the original dvd. I ripped it from my roommate's collection last year. And at the time, I was just using my computer to watch movies, so I went for the full quality instead of compatibility. Now I know to use something like k9copy over dvd::rip if I want to play it on something other than a PC. 

You mention copying from a dual layer to a single layer. Yes, that is what I want to do, but I think I failed to mention that I only have the mpeg rips from dvd:rip. The issue is that I don't have the needed? ifo's and bup's for a dvd. 

I've tried recreating them with ifo edit under wine and in xp (running under virtualbox). Neither instance turned out successful.

---

### Post by aeiah on 2008-07-11
you could try it on the command line with these to make a 5.7gb dvd without reconverting anything (just build the structure) and then use k9copy to make it smaller or something.

```

dvdauthor -o /tmp/dvdparts/DVD/ -t /path/to/video.mpg
dvdauthor -o /tmp/dvdparts/DVD/ -T
mkisofs -dvd-video -v -o /whereyouwant/your/DVD.iso /tmp/dvdparts/DVD


```

and yea, xvid is ok. its very popular and has good support but its not the best. as it stands, x264 is the best but i think it can get complicated when using ps3s etc. on the piracy scene most movies are either converted to xvid 700mb or if over a certain length, 2x700mb


oh, and what program did you use to merge your two mpegs together with? because this seems to be whats causing you problems.

---

### Post by angryhomer17 on 2008-07-11
> **angryhomer17 said:**
> I'm testing an mpeg to xvid copy using transcode, so we'll see if that works well.

Well, it worked, but not well. I ended up with what appears to be a "good" avi (it plays), but the video is scrambled (like when you try to watch a blocked cable channel)

I used: ```
 transcode -A -y xvid -w 7000 -i serenity_full.mpg -o serenity.avi
```

From what I read on the man page this should have transcoded the mpeg to an avi using xvid compression, AC3 passthrough, at 7000 KB/s. Guess I'll have to try again.

---

### Post by angryhomer17 on 2008-07-11
> **aeiah said:**
> ...
```

dvdauthor -o /tmp/dvdparts/DVD/ -t /path/to/video.mpg

```...


I tried the above code and got 
```
WARN: Skipping sector, waiting for first VOBU...
```
as a result. Like I said in my earlier post, this has happened before with dvdauthor. Supposedly, it can't find a valid vob unit.

> **aeiah said:**
> oh, and what program did you use to merge your two mpegs together with? because this seems to be whats causing you problems.

I used cat.

```
cat serenity_disc1.mpg serenity disc2.mpg > serenity_full.mpg
```

---

### Post by angryhomer17 on 2008-07-11
Got some more programs.

Avidemux- Audio/video sync off. Xvid encoding was horrible, extreme pixelation. Compressed to 700 MB.

Mandvd- Guess this wasn't what I thought it was. Turns out that it's pretty decent. Pretty fast, say 40 mins? But I still have the problem of not using an entire single layer dvd. I ended up with a 3.6 gig iso, which doesn't make sense. 

I choose the maximum 7000 KB/s quality. The original video is encoded at 9800 KB/s. That means I should get a 4.07 gig iso. Why couldn't it use another half gig? I'd like to use the full capacity of the dvd or get a decent 700 meg file.

I am going to try some stuff on this page: 
[http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide#XviD_One-Pass_Encoding](http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide#XviD_One-Pass_Encoding)

---

### Post by RainmanATX on 2009-01-07
I have been having this problem for quite awhile now. From what I have found via good'ol google, is that mencoder seems to be ignoring bitrate settings passed to it by DEVEDE. I recall that there was a thread on Mplayer's forum (I do believe the user with the issue was using a different 'frontend' for mencoder though) where a moderator addressed the issue as thus; "...if the source file being converted does not have enough inherent quality to achieve the bitrate set by the user, it will not 'pad' the file with zeros, it will simply encode at the highest possible bitrate for the given source material." Personally, I have tried stepping the DEVEDE versions back to 3.6, the last version I remember working properly, it was a no go. So, either mencoder is 'fixed', where it will 'pad' the file, or someone lets us know how to load an older version of mencoder. I will post if I find anything else, good luck. :confused:

From what I can tell, no matter what I set the bitrate, mencoder seems to choose VBR of around 2000.

---

