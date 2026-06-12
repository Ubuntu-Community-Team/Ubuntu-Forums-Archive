---
title: "Help expand my knowledge about lossless, WAV and Mp3"
date: 2011-08-24
forum: The Cafe
---

### Post by KUU on 2011-08-24
Something I never understood.

:) I know lossless is the original raw audio source, then this can be compressed to small size (mp3) but loses quality, 
now if we have an MP3 that's been converted from WAV and convert it back to WAV does the audio regain the quality
 of it's original state or just make the file bigger with benificial reason for changing back to WAV?

---

### Post by Ozor Mox on 2011-08-24
No the quality won't come back. Once converted to a lossy format, the quality is lost for good. You'd need to rip from the original source to get it back into a lossless format.

---

### Post by lykwydchykyn on 2011-08-24
It does not regain any quality.

That's what's meant by "lossy" -- the extra information is lost.

---

### Post by YesWeCan on 2011-08-24
Hi and welcome to the Ubuntu forums.
I believe a loss-less .wav file can typically be compressed by roughly 50% using flac format or similar. Lossy MP3 will reduce it by roughly 90%. So I suppose one could, very broady, say that lossy compression removes roughly 80% of the original music information. You can never get it back just like you cannot reduce the pixel size of an image and then reconstruct the original afterwards (in spite of what they do on CSI TV shows).
It is astonishing that this loss of information is not more noticeable. On ordinary music systems it is tolerable but on good hifi the difference is obvious.

---

### Post by forrestcupp on 2011-08-24
> **Ozor Mox said:**
> No the quality won't come back. Once converted to a lossy format, the quality is lost for good. You'd need to rip from the original source to get it back into a lossless format.

Right. That's the difference between lossy compression and lossless compression. It's like the difference between cutting a sponge in half to get it part of it to fit into a small ziplock bag and squeezing it into a small ball to get the whole thing to fit.

It's possible to compress audio without losing information. I don't think it's possible to do that with an mp3, though. Also, wav files can be compressed or raw. But the compression isn't nearly as extreme as an mp3, hence the larger file sizes.

---

### Post by Ranko Kohime on 2011-08-24
> **KUU said:**
> Something I never understood.

:) I know lossless is the original raw audio source, then this can be compressed to small size (mp3) but loses quality, 
now if we have an MP3 that's been converted from WAV and convert it back to WAV does the audio regain the quality
 of it's original state or just make the file bigger with benificial reason for changing back to WAV?
To expound somewhat on what the two previous posters said, MP3 compression makes substantial, (though some say undetectable to the ear) changes to the audio signal in order to achieve the compression that it does.  The resulting WAV from converting an MP3 is going to retain those changes to the audio signal.  Worse, compressing an original WAV to MP3, then back to WAV, then into MP3 again will result in more, DIFFERENT changes to the audio signal, as compared to the first compression.

Continued ad infinitum, the audio would degrade into an unrecognizable mess after a few hundred generations.

---

### Post by mips on 2011-08-24
> **forrestcupp said:**
> 
It's possible to compress audio without losing information. 

I don't think it's possible to do that with an mp3, though.

[FLAC]("http://en.wikipedia.org/wiki/Free_Lossless_Audio_Codec") being one example but you won't get file sizes approaching that of mp3 ones.

Correct, mp3 is lossy, end of story.

---

### Post by thatguruguy on 2011-08-24
> **Ranko Kohime said:**
> To expound somewhat on what the two previous posters said, MP3 compression makes substantial, (though some say undetectable to the ear) changes to the audio signal in order to achieve the compression that it does.  The resulting WAV from converting an MP3 is going to retain those changes to the audio signal.  Worse, compressing an original WAV to MP3, then back to WAV, then into MP3 again will result in more, DIFFERENT changes to the audio signal, as compared to the first compression.

Continued ad infinitum, the audio would degrade into an unrecognizable mess after a few hundred generations.

Specifically, the process of converting a .wav file into an .mp3 file clips the top and bottom frequencies.  These frequencies are above and below the range that a typical person can hear.  This clipping is responsible for why the bass line in an .mp3 doesn't produce the same amount of vibrations in your furniture that an uncompressed file can produce (assuming you speakers that can handle it).  This is why the procedure is "lossy"; you've lost some of the dynamic range of frequencies.  Since there is less to compress after the top and bottom ranges have been stripped out, an .mp3 can be much smaller than a .flac file, which compresses the entire original range.

---

### Post by flemur13013 on 2011-08-24
> **YesWeCan said:**
> On ordinary music systems it is tolerable but on good hifi the difference is obvious.

Unless you're doing [ABX tests]("http://wiki.hydrogenaudio.org/index.php?title=ABX"), or using a lot of compression (very low kbps), it's probably your imagination - like the people who hear the superior transparency and clarity of their new $5,000 molecularly aligned solid gold connectors ... until they ABX them with [Radio Shack]("http://home.provide.net/%7Edjcarlst/abx_wire.htm") cables and [can't tell the difference]("http://www.hometheaterhifi.com/volume_11_4/feature-article-blind-test-power-cords-12-2004.html"). [Also here.]("http://www.hometheaterfocus.com/accessories/transparent-audio-cables.aspx")

[http://www.hydrogenaudio.org](http://www.hydrogenaudio.org) has more information than you'll ever need or want to know about audio quality and digital file compression, although you have to dig a bit.

---

### Post by YesWeCan on 2011-08-24
> **flemur13013 said:**
> Unless you're doing [ABX tests]("http://wiki.hydrogenaudio.org/index.php?title=ABX"), or using a lot of compression (very low kbps), it's probably your imagination - like the people who hear the superior transparency and clarity of their new $5,000 molecularly aligned solid gold connectors ... until they ABX them with [Radio Shack]("http://home.provide.net/%7Edjcarlst/abx_wire.htm") cables and [can't tell the difference]("http://www.hometheaterhifi.com/volume_11_4/feature-article-blind-test-power-cords-12-2004.html"). [Also here.]("http://www.hometheaterfocus.com/accessories/transparent-audio-cables.aspx")

[http://www.hydrogenaudio.org](http://www.hydrogenaudio.org) has more information than you'll ever need or want to know about audio quality and digital file compression, although you have to dig a bit.
Actually, I did about 20, random, double-blind tests and my ability to recognize the MP3 was 100% accurate and furthermore I was able to tell within just the first few notes. So my experience is that it is obvious.

---

### Post by forrestcupp on 2011-08-24
> **YesWeCan said:**
> Actually, I did about 20, random, double-blind tests and my ability to recognize the MP3 was 100% accurate and furthermore I was able to tell within just the first few notes. So my experience is that it is obvious.

What kbps were the mp3s? If you're talking about 128 kbps, then yes, but after a certain level, it becomes less obvious.

---

### Post by blueturtl on 2011-08-24
> **thatguruguy said:**
> Specifically, the process of converting a .wav file into an .mp3 file clips the top and bottom frequencies.  These frequencies are above and below the range that a typical person can hear.  This clipping is responsible for why the bass line in an .mp3 doesn't produce the same amount of vibrations in your furniture that an uncompressed file can produce (assuming you speakers that can handle it).  This is why the procedure is "lossy"; you've lost some of the dynamic range of frequencies.  Since there is less to compress after the top and bottom ranges have been stripped out, an .mp3 can be much smaller than a .flac file, which compresses the entire original range.

I thought the MP3 algorithm worked by removing sounds that would be audible to the human ear, but masked by other sounds. I also thought dynamic range referred to the differences of quiet and loud parts in a recording (ie. a recording with low dynamic range wouldn't have very big differences between the quiet and loud parts of the recording when it comes to the volume level).

How far out in the woods am I?

---

### Post by David Andersson on 2011-08-24
> **blueturtl said:**
> > 
Originally Posted by thatguruguy View Post
Specifically, the process of converting a .wav file into an .mp3 file clips the top and bottom frequencies. These frequencies are above and below the range that a typical person can hear...

I thought the MP3 algorithm worked by removing sounds that would be audible to the human ear, but masked by other sounds. I also thought dynamic range referred to the differences of quiet and loud parts in a recording ...

How far out in the woods am I?
You are basically right and the post you are quoting is an over-simplification. (Cutting hi and low frequencies only saves a few percent.)

---

### Post by David Andersson on 2011-08-24
> **KUU said:**
> 
now if we have an MP3 that's been converted from WAV and convert it back to WAV does the audio regain the quality of it's original state or just make the file bigger with benificial reason for changing back to WAV?

I like the photo copier analogy. You have a sharp photo. Copy it in a bad copier and you get a blurry photo. You can not take the blurred photo, copy it in a good copier and expect a sharp photo to come out.

Same with: color photo -> black/white copier -> black/white photo -> color copier -> still black/white photo.

---

### Post by KUU on 2011-08-24
Thanks for the feedback all,  :P

---

