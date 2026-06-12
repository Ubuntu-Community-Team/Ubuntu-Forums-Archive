---
title: "Trouble muxing h264 vid, dts audio, and subtitle tracks with ffmpeg."
date: 2008-09-12
forum: Ubuntu Studio
---

### Post by banhbau01 on 2008-09-12
If there are some users out there competent in using command lines I would greatly appreciate your input on this matter.

So first, I downloaded a movie as a mkv file and used devede to convert into a DVD player compatible format, which it did in flying colors with great quality sound and video. The only problem was that the film is a Japanese film and when it was being converted by devede it lost all the subtitle files. So now I'm left wondering what everyone is saying.

So next, I extracted the mkv file into several files: an h264 video, dts audio, 2 *** files, 1 srt file, several idx files, and several sub files. Then I tried to mux the audio and video files using ffmpeg with the command line:

ffmpeg -r 23.976 -f h264 -i video.h264 -f dts -i audio.dts -vcodec copy -acodec copy -f vob output.vob 

The resulting vob file only had audio. I'm not sure what went wrong, if anyone has ideas please let me know. Also if there is a command line that could account for the subtitle tracks, I would be much obliged. It also just struck me that perhaps a vob file is the wrong thing to try to convert it into, but once again I'm at a loss as to what would be a good format which I could play on a DVD player.

---

### Post by Maybelline on 2008-09-17
> **banhbau01 said:**
> Then I tried to mux the audio and video files using ffmpeg with the command line:

ffmpeg -r 23.976 -f h264 -i video.h264 -f dts -i audio.dts -vcodec copy -acodec copy -f vob output.vob 

The resulting vob file only had audio.

I do think a VOB is what you'd want.  Did you try it w/o the -f h264 and -f dts (in other words, let ffmpeg figure out the format of each file?)

---

