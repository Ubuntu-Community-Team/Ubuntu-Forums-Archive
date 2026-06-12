---
title: "Reauthoring DVD - Add/change audio track"
date: 2010-02-03
forum: Ubuntu Studio
---

### Post by cmfarley19 on 2010-02-03
I received a DVD of my son playing hockey at the Verizon Center in DC.  The accompanying audio only comes out of the right channel.  I would like to modify it so the same audio comes out of both channels.  I have already done some reauthoring (changed the aspect ratio from 4:3 to 16:9).  I guess what I am really asking is how to modify/edit an AVI to fix my audio issue.

Any suggestions?

Here is a copy of the video on youtube:
[http://www.youtube.com/watch?v=3QtOVA8F0pc](http://www.youtube.com/watch?v=3QtOVA8F0pc)

Thanks,

Chris

---

### Post by hemimaniac on 2010-02-03
I know in Avidemux there is an option in the audio output to "force stereo" or "dual mono" ( i believe), can't exactly remember, been awhile since i had to do it. :(

---

### Post by ron999 on 2010-02-04
Hi Chris
I downloaded your video from YouTube.
The sound can be corrected using ffmpeg.
This is the command that I used:-

```
ffmpeg -i Noah_playing_in_the_Mites_on_Ice_Caps_Video_Feed-3QtOVA8F0pc.mp4 -vcodec copy -acodec libfaac -ab 128kb -ar 48000 -ac 1 result.mp4

```
**-vcodec copy** means leave the video alone.
**-acodec libfaac -ab 128kb -ar 48000 -ac 1** means use aac encoder at bitrate 128Kbps sample rate 48000Hz.

The important bit is _**-ac 1**_. This means just one audio channel, but it comes out of both speakers.
The downloaded file from YouTube is mp4. I expect the same method may be used with avi and other types of files. Use the appropriate audio codec. Use the appropriate suffix for the result file instead of mp4.

Edit
I downloaded your video using this command:-
```
youtube-dl -i -t -f 18 http://www.youtube.com/watch?v=3QtOVA8F0pc
```

---

### Post by cmfarley19 on 2010-02-10
Sorry... I was without power for about 36 hours.
I too figured it out.  Similar approach...
```
ffmpeg -i VTS_01_1.VOB -target ntsc-dvd -aspect 16:9 -acodec ac3 -ab 192K -ac 1 final_2.mpg
```

Thanks for the help.  Also... thanks for the tip on youtube-dl.

Chris

---

