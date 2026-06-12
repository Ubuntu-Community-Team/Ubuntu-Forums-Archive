---
title: "how can i make my video conversions not drop frames"
date: 2012-10-08
forum: Ubuntu Studio
---

### Post by S_p_or_t_o on 2012-10-08
i'm using a dvd/divx player to feed into a menu board. i have a new video and i'm trying to convert a .mov file into a xvid .avi

the trouble is the video looks terrible after i convert it.


using winff (front end for ffmpeg), i have a preset with the following options

```
-f avi -r 29.97 -vcodec libxvid -vtag XVID -s 1280x720 -aspect 16:9 -maxrate 1800k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4m -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -ab 128k -ac 2
```
 
2 pass doesn't seem to make a difference.

using ubuntu studio 12.04 x64

any advice would be appreciated.

---

### Post by jejeman on 2012-10-09
Install mediainfo, or just use ffmpeg, and give us the properties of original video.

---

### Post by S_p_or_t_o on 2012-10-15
sorry for the lag.

ffmpeg gives the same results

media info stuff:
```
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.




original:
_____________________________
Complete name                            : x.mov
Format                                   : MPEG-4
Format profile                           : QuickTime
Codec ID                                 : qt  
File size                                : 66.0 MiB
Duration                                 : 1mn 37s
Overall bit rate                         : 5 703 Kbps
Encoded date                             : UTC 2012-10-03 03:26:38
Tagged date                              : UTC 2012-10-03 03:26:39
Writing library                          : Apple QuickTime 7.6.0

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : Main@L3.1
Format settings, CABAC                   : No
Format settings, ReFrames                : 2 frames
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 1mn 37s
Bit rate                                 : 5 565 Kbps
Width                                    : 1 280 pixels
Height                                   : 544 pixels
Display aspect ratio                     : 2.35:1
Frame rate mode                          : Constant
Frame rate                               : 23.976 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.333
Stream size                              : 64.4 MiB (98%)
Language                                 : English
Encoded date                             : UTC 2012-10-03 00:39:37
Tagged date                              : UTC 2012-10-03 03:26:39
Color primaries                          : BT.709-5, BT.1361, IEC 61966-2-4, SMPTE RP177
Transfer characteristics                 : BT.709-5, BT.1361
Matrix coefficients                      : BT.709-5, BT.1361, IEC 61966-2-4 709, SMPTE RP177

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 1mn 37s
Bit rate mode                            : Constant
Bit rate                                 : 128 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 1.53 MiB (2%)
Language                                 : English
Encoded date                             : UTC 2012-10-03 00:39:37
Tagged date                              : UTC 2012-10-03 03:26:39
Material_Duration                        : 97067
Material_StreamSize                      : 1606715

Menu
ID                                       : 3
Language                                 : English
Encoded date                             : UTC 2012-10-03 00:39:42
Tagged date                              : UTC 2012-10-03 03:26:39


from my ubuntu studio 12.04:
_____________________________
Complete name                            : x.avi
Format                                   : AVI
Format/Info                              : Audio Video Interleave
File size                                : 20.3 MiB
Duration                                 : 1mn 37s
Overall bit rate                         : 1 756 Kbps
Movie name                               : x
Writing application                      : Lavf53.21.0

Video
ID                                       : 0
Format                                   : MPEG-4 Visual
Format profile                           : Advanced Simple@L5
Format settings, BVOP                    : 2
Format settings, QPel                    : No
Format settings, GMC                     : No warppoints
Format settings, Matrix                  : Default (H.263)
Muxing mode                              : Packed bitstream
Codec ID                                 : XVID
Codec ID/Hint                            : XviD
Duration                                 : 1mn 36s
Bit rate                                 : 1 615 Kbps
Width                                    : 704 pixels
Height                                   : 384 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 29.970 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.199
Stream size                              : 18.7 MiB (92%)
Writing library                          : XviD 64

Audio
ID                                       : 1
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 3
Mode                                     : Joint stereo
Mode extension                           : MS Stereo
Codec ID                                 : 55
Codec ID/Hint                            : MP3
Duration                                 : 1mn 37s
Bit rate mode                            : Constant
Bit rate                                 : 128 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 1.48 MiB (7%)
Alignment                                : Aligned on interleaves
Interleave, duration                     : 24 ms (0.72 video frame)
Writing library                          : LAME3.99.3


from a ubuntu 10.04 box, seems to work the best:
____________________
Complete name                            : x.avi
Format                                   : AVI
Format/Info                              : Audio Video Interleave
File size                                : 20.8 MiB
Duration                                 : 1mn 37s
Overall bit rate                         : 1 796 Kbps
Writing application                      : Lavf52.31.0

Video
ID                                       : 0
Format                                   : MPEG-4 Visual
Format profile                           : Advanced Simple@L5
Format settings, BVOP                    : 2
Format settings, QPel                    : No
Format settings, GMC                     : No warppoints
Format settings, Matrix                  : Default (H.263)
Muxing mode                              : Packed bitstream
Codec ID                                 : XVID
Codec ID/Hint                            : XviD
Duration                                 : 1mn 36s
Bit rate                                 : 1 655 Kbps
Width                                    : 704 pixels
Height                                   : 384 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 29.970 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.204
Stream size                              : 19.1 MiB (92%)
Writing library                          : XviD 1.2.1 (UTC 2008-12-04)

Audio
ID                                       : 1
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 3
Mode                                     : Joint stereo
Mode extension                           : MS Stereo
Codec ID                                 : 55
Codec ID/Hint                            : MP3
Duration                                 : 1mn 37s
Bit rate mode                            : Constant
Bit rate                                 : 128 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 1.48 MiB (7%)
Alignment                                : Aligned on interleaves
Interleave, duration                     : 24 ms (0.72 video frame)
Writing library                          : LAME3.98.2


```

---

### Post by jejeman on 2012-10-15
Original

1280x544 23.976 AVC 48k AAC

other ones

704x384 29.970 XVID 48K mp3


In what format do you need transcoded file to be?

command you gave sets size to 1280x720, but you have 704x384?

Also you changed framerate.

Try to keep the same everything you can, sepcialy the framerate. Also you changed aspect ratio of the picture in the command. And in presented files.
Aspect ratio of 1280x544 is not the same as 704x384 nor 1280x720.

---

### Post by S_p_or_t_o on 2012-10-15
it needs to be xvid/mp3 for the dvd player (coby dvd298 ) i have to read it as a divx file. i'll play with some settings and see if the original framerate will work.



update: i tried with switches -sameq and then with -r 23.976 -s 1280x720, the dvd player refuses to play them.

---

### Post by FakeOutdoorsman on 2012-10-16
ffmpeg will simply either drop or duplicate frames, as in your case, to achieve the desired output frame rate. Do not use *-sameq*: [sameq does not mean "same quality"](http://superuser.com/a/478550/110524).

---

### Post by jejeman on 2012-10-16
Okay, so, if you play back on DVD player, then it is best you convert it to the DVD standard of your player. What is it NTSC or PAL?

---

### Post by S_p_or_t_o on 2012-10-16
the ones i've made in openshot all have been NTSC, actually more like .avi xvid/mp3. i'm using a 2gb thumb drive instead of burning discs (doing it on the cheap).
 
it's a coby dvd-298. the manual says:
Color System: PAL/NTSC
Video Output:1Vpp (at 75ohm
Audio Output: (stereo): 2Vrms (1KHz, 0db
 
the box says:
Plays all versions of DivX video (including DivX 6) with standard playback of DivX media files
 
i was just using openshot to make videos, but the export feature for .avi's changed in 10.10 from xvid encoding to mp4. 
 
the videos that skip also do so on my pc, so i don't belive it's the flashdrive.
 
what works on it for the other content i've made has been 720p @29.97. I'm not sure what else the player can handle, appearently not 23.976.
 
i'm starting to believe it's the shift in framerates. (i'm putting a lot of work into this for a video I only mildly care about, i guess i'm more into learning the how & why than successfully converting this one video lol).

---

### Post by jejeman on 2012-10-17
If your player can playback 720p then keep the image size, change only framerate.
If you have HDD space, the best way to preserve the quality is to make PNG image sequence from the original and then from the sequence make the 29fps version.

If the motion of the video is jerky then the framerate's change is the cause. Framerate change doesn't influence image quality.

---

### Post by FakeOutdoorsman on 2012-10-17
> **S_p_or_t_o said:**
> i'm starting to believe it's the shift in framerates
Seems likely to me.

> **jejeman said:**
> If you have HDD space, the best way to preserve the quality is to make PNG image sequence from the original and then from the sequence make the 29fps version.

You can do this with pipes instead of making thousands of files. Going from NTSC Film to NTSC Video, and using all of the frames, would simply cause the video to speed up and the audio would be out of sync.

---

