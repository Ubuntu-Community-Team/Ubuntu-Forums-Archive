---
title: "Creating CBR 320kb/s MP3 with Sound-Juicer in Ubuntu17.10"
date: 2018-03-10
forum: Tutorials
---

### Post by koshka--ru on 2018-03-10
By default Sound-Juicer create mp3 with 128kb/s VBR only and there is no control to change it.
To create CBR highbitrate mp3's with Sound-Juicer in Ubuntu 17.10 I make:

1) Edit /usr/share/sound-juicer/rhythmbox.gep
> 
[GStreamer Encoding Target]
name = rhythmbox
category = muh
description = Common encoding profiles for Rhythmbox

[profile-mp3-Ubuntu]                                               #profile-format-presetname (see GstLameMP3Enc.prs for mp3 - sapienti sat)
name = mp3-Ubuntu                                                 #format-presetname
description = MPEG Layer 3 Audio (HQ)                       #this is profile name for Output Format Control
format = application/x-id3
type = container

[streamprofile-mp3-1]
parent = mp3-Ubuntu                                               #format-presetname
type = audio
format = audio/mpeg, mpegversion=1, layer=3
presence = 1
preset=Ubuntu

[profile-oggvorbis-Ubuntu]
name = oggvorbis-Ubuntu
description = Ogg Vorbis
format = application/ogg
type = container

[streamprofile-oggvorbis-1]
parent = oggvorbis-Ubuntu
type = audio
format = audio/x-vorbis
presence = 1
preset = Ubuntu

[profile-oggopus]
name = oggopus
description = Ogg Opus
format = application/ogg
type = container

[streamprofile-oggopus-1]
parent = oggopus
type = audio
format = audio/x-opus
presence = 1

[profile-flac]
name = flac
description = FLAC
format = audio/x-flac
type = audio

[profile-m4a]
name = m4a
description = MPEG 4 Audio
format = video/quicktime, variant=iso
type = container

[streamprofile-m4a-1]
parent = m4a
type = audio
format = audio/mpeg, mpegversion=4, stream-format=raw
presence = 1

     
 
2) My /usr/share/gstreamer-1.0/presets/GstLameMP3Enc.prs 
 > 
[_presets_]
element-name=GstLameMP3Enc
version=0.10.36

[Ubuntu]
name=lamemp3enc
perfect-timestamp=false
hard-resync=false
tolerance=40000000
target=Bitrate
quality=0
cbr=true
bitrate=320
encoding-engine-quality=high
mono=false                      
     
 
3) My /usr/share/gstreamer-1.0/presets/GstVorbisEnc.prs
 >                                                         [_presets_]
element-name=GstVorbisEnc
version=0.10.36

[Ubuntu]
name=vorbisenc
perfect-timestamp=true
hard-resync=false
tolerance=40000000
quality=0.6
managed=false                      
     
 
Then I start ripping and...It works! 
Now I can use SJ for ripping my CDs to <320 or wht u want> CBR mp3 and high bitrate OGG.

Sadly, I can't use more than only one preset for format.
 I hope it helps you.
Sorry my bad english..

---

### Post by conny-x on 2018-03-22
Thank you so much!!! It works wonderfully.:guitar:

---

### Post by benzu on 2018-03-23
Thank you for your tutorial!

---

