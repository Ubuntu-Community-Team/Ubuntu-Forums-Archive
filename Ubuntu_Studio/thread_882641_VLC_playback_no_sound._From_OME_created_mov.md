---
title: "VLC playback no sound. From OME created mov"
date: 2008-08-07
forum: Ubuntu Studio
---

### Post by vector on 2008-08-07
Hi all
Big help needed. (running hardy)
Im using VLC as my main playback utill for an OME produced slideshow movie with music backing.
Totem will play the rendered OME file ( a mov quicktime) fine with sound but VLC only produces video with no sound. Yet If I use VLC to play something else I got off the net,its plays sound fine.

I converted the mov into an flv using
```
ffmpeg -i my_vid.mov -s 320x240 myvid.flv
```
Great video but no sound from VLC.. But the last lines almost indicate there is no sound? So VLC is reporting correctly
```
frame= 5620 q=2.0 Lsize=    5893kB time=224.8 bitrate= 214.8kbits/s    
video:5805kB audio:0kB global headers:0kB muxing overhead 1.515736%
```

then I tired converting to avi
```
 ffmpeg -i wep08_5_vid.mov -s 320x240 wepdvd5.avi
```

```
frame= 5620 q=2.0 Lsize=    7903kB time=224.6 bitrate= 288.3kbits/s    
video:5785kB audio:1754kB global headers:0kB muxing overhead 4.828910%
```

ahh look we have audio and VLC correctly displays audio.


so why cant I produce an audio/vid flv(which Im lead to believe is what youtube etc require.

and why does VLC not play the audio in the original mov?

thanks heaps gents.

---

