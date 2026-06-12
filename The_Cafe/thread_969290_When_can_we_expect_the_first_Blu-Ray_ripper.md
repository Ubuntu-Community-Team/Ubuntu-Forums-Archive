---
title: "When can we expect the first Blu-Ray ripper?"
date: 2008-11-03
forum: The Cafe
---

### Post by billgoldberg on 2008-11-03
Now that the way to crack the blu-ray copy protection is [public knowledge]("http://forum.doom9.org/showthread.php?t=140571&page=17"), when can we expect the first ripper for Linux?

Does anyone have any info on this?

Or will the dvd rip projects include this in future releases?

Thanks.

---

### Post by gn2 on 2008-11-03
I believe that BD+ was defeated more than six months ago?

Shouldn't be too long to wait, in the meantime there's [SlySoft]("http://www.slysoft.com/en/anydvdhd.html").

---

### Post by Polygon on 2008-11-03
i read while they did crack bd+, its still not 100% complete so maybe a little longer

---

### Post by Spr0k3t on 2008-11-03
When?  Not soon enough.  We pay for the right to use the drive, then we pay for the right to use the media, then we pay for the right to view the media on the target device, then we pay for the right if we want to view the same media on another target device.  Will this ever stop?  Probably not.

---

### Post by billgoldberg on 2008-11-03
> **gn2 said:**
> I believe that BD+ was defeated more than six months ago?

Shouldn't be too long to wait, in the meantime there's [SlySoft]("http://www.slysoft.com/en/anydvdhd.html").

It was cracked by those guys, but they've kept the method a secret.

Now it's public knowledge.

Windows software isn't an option.

---

### Post by Judo on 2008-11-03
You shouldn't expect it too soon.  Only two movies have been ripped so far following their process, to my knowledge.  Even if they manage to perfect BD+ decryption, there's still the other encryptions to worry about.  AES is something they still have problems with and AACS is set to be updated soon, iirc.  The other hurdles, like UDF and decoders for the formats used on the discs, are pretty much done with, though.

Plus, once you have the 1080p video on your computer, there's no guarantee you have the system resources to play it.  1080p h.264 (high profile) won't play on my Athlon 64 3200+, let alone 720p and very, very few drivers can do hardware decoding on Linux.

---

### Post by mips on 2008-11-03
> **Judo said:**
> 
Plus, once you have the 1080p video on your computer, there's no guarantee you have the system resources to play it.  1080p h.264 (high profile) won't play on my Athlon 64 3200+, let alone 720p and very, very few drivers can do hardware decoding on Linux.

I suspect most people will just convert it to another format.

---

### Post by handy on 2008-11-03
[***_Doom9.net The Definitive DVD Backup Resource_***]("http://www.doom9.org/"): Is a great place for those interested in this kind of subject.

---

### Post by billgoldberg on 2008-11-03
> **Judo said:**
> You shouldn't expect it too soon.  Only two movies have been ripped so far following their process, to my knowledge.  Even if they manage to perfect BD+ decryption, there's still the other encryptions to worry about.  AES is something they still have problems with and AACS is set to be updated soon, iirc.  The other hurdles, like UDF and decoders for the formats used on the discs, are pretty much done with, though.

Plus, once you have the 1080p video on your computer, there's no guarantee you have the system resources to play it.  1080p h.264 (high profile) won't play on my Athlon 64 3200+, let alone 720p and very, very few drivers can do hardware decoding on Linux.

720p plays well on Linux using my on-board ATI radeon Xpress 200.

Don't know about 1080p.

---

### Post by MaxIBoy on 2008-11-03
I know my laptop's Intel chipset sort of whimpers and cries when I try to play 1080p video.

---

### Post by handy on 2008-11-04
I just installed Slysoft's AnyDVD HD, on Arch via Wine, which went well, but it throws up an error to do with the optical drive.  Which I kind of expected. 

It was worth a try.

---

### Post by Fatboy Snarky on 2008-11-04
> Originally Posted by Judo  
Plus, once you have the 1080p video on your computer, there's no guarantee you have the system resources to play it. 1080p h.264 (high profile) won't play on my Athlon 64 3200+, let alone 720p and very, very few drivers can do hardware decoding on Linux.

No problem here playing 1080p25/1080p30 on an Athlon64 4800+.

Have you tried compiling a recent MPlayer version (svn.mplayerhq.hu/mplayer/trunk)?

I'm usig the NVidia binary-only graphics driver, but it only offers the XV video output; no further hardware acceleration necessary.

---

### Post by mips on 2008-11-04
Where does one get good 1080p sample videos to test with?

---

### Post by Judo on 2008-11-04
> **Fatboy Snarky said:**
> No problem here playing 1080p25/1080p30 on an Athlon64 4800+.

Have you tried compiling a recent MPlayer version (svn.mplayerhq.hu/mplayer/trunk)?

I'm usig the NVidia binary-only graphics driver, but it only offers the XV video output; no further hardware acceleration necessary.
I've done all that I can, but there is no hope for this machine.  My 7800 GT *may* be helping through XvMC, but if it is, it's not helping much.  My machine, however, can play 1080p h.264 at main profile, but you won't see that outside of Apple's players.

I've been told that the majority of Core 2's on the market now can play any 1080p video, but I haven't tested that myself.

I guess you could say that a computer new enough to have a BD drive is also powerful enough to decode it, but there's no guarantee.

On a related note, I've done a lot of research related to drivers and accelerated playback which has brought me to the conclusion that no ATI/AMD, NVIDIA, or Intel GPU can do h.264 or VC-1 hardware decoding through X.  They are only programmed to do it through DXVA. (DirectX Video Acceleration, obviously Windows-only)

---

### Post by billgoldberg on 2008-11-04
> **mips said:**
> Where does one get good 1080p sample videos to test with?

Download a HD music video from a torrent site.

---

### Post by mips on 2008-11-04
> **billgoldberg said:**
> Download a HD music video from a torrent site.

I'm sure you mean a legit one, just to clarify.

---

### Post by Rhubarb on 2008-11-04
Just grab Big Buck Bunny here:
[http://www.bigbuckbunny.org/](http://www.bigbuckbunny.org/)

It's free, you can grab the hi-def format, and shows you just what blender can really do :D

---

### Post by Judo on 2008-11-04
> **Rhubarb said:**
> Just grab Big Buck Bunny here:
[http://www.bigbuckbunny.org/](http://www.bigbuckbunny.org/)

It's free, you can grab the hi-def format, and shows you just what blender can really do :D
Terrific film, but not a very good test.  That's the Quicktime version which doesn't use all of h.264's compression techniques.  Long story short, it requires significantly less processing power to play in comparison to a BD movie.

---

### Post by mips on 2008-11-05
> **Rhubarb said:**
> Just grab Big Buck Bunny here:
[http://www.bigbuckbunny.org/](http://www.bigbuckbunny.org/)

It's free, you can grab the hi-def format, and shows you just what blender can really do :D

Someting smaller would suite me better. I have a 3GB cap and 700MB is a big chunk of that. 50-100MB would be cool though.

---

### Post by Polygon on 2008-11-05
i have a bluray rip of a movie, i have no idea if its 1080 p though/.. I can check and then extract a 10 second clip of it and upload it somewhere for you

---

### Post by billgoldberg on 2008-11-05
> **mips said:**
> I'm sure you mean a legit one, just to clarify.

Sure I did.

:p

---

### Post by mips on 2008-11-06
> **Polygon said:**
> i have a bluray rip of a movie, i have no idea if its 1080 p though/.. I can check and then extract a 10 second clip of it and upload it somewhere for you

Thanks, but I have found something in the meantime but have not downloaded it yet.

---

### Post by davex1990 on 2009-07-08
you can just hook up  your blu ray player to a capture card and go from there
[http://www.pchdtv.com/](http://www.pchdtv.com/) <<< linux compatable capture cards
you can then install MythTV
[http://www.mythtv.org/](http://www.mythtv.org/)

---

### Post by Sub101 on 2009-07-08
> **mips said:**
> Where does one get good 1080p sample videos to test with?

Also BBC Iplayer allows you to watch programs in HD. Might not be exactly what you are looking for. Nevertheless it works without errors.

---

