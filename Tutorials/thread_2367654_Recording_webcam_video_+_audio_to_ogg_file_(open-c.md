---
title: "Recording webcam video + audio to ogg file (open-container format)"
date: 2017-08-01
forum: Tutorials
---

### Post by openlaptop on 2017-08-01
[COLOR=#242729][FONT=Arial]Hi all,

I saw a[/FONT][/COLOR]desperate[COLOR=#242729][FONT=Arial] need of this information. So hopefully somebody finds this informative. It uses the open-source Ogg container format as encoder for video and audio.

First, get an overview of all devices (in this example: /dev/video0):[/FONT][/COLOR]
```
v4l2-ctl --list-devices
```

[COLOR=#242729][FONT=Arial]Check the availible formats:
[/FONT][/COLOR]```
v4l2-ctl --list-formats-ext -d /dev/video0
```

[COLOR=#242729][FONT=Arial]Determ sound source (card: **0** ..., device: **1**... is equal to hw:**0,1**. In this example hw:0,0):[/FONT][/COLOR]
```
arecord -l
```

[COLOR=#242729][FONT=Arial]Record video + audio, directly to file:[/FONT][/COLOR]
```
cvlc v4l2:///dev/video0:width=640:height=480 :input-slave=alsa://hw:0,0 --sout="#transcode{vcodec=theo,vb=2000,fps=20,scale=1.0,acodec=vorb,ab=90,channels=1,samplerate=44100}:standard{access=file,mux=ogg,dst=output.ogg}"

```
[COLOR=#242729][FONT=Arial]
Same but with live video:[/FONT][/COLOR]
```
cvlc v4l2:///dev/video0:width=640:height=480 :input-slave=alsa://hw:0,0 --sout="#transcode{vcodec=theo,vb=2000,fps=20,scale=1.0,acodec=vorb,ab=90,channels=1,samplerate=44100}:duplicate{dst=display,dst=standard{access=file,mux=ogg,dst=output.ogg}}" 

```
[COLOR=#242729][FONT=Arial]
You could change [FONT=lucida console]cvlc[/FONT] back to [FONT=lucida console]vlc[/FONT] if you want to have controls + menu.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][More options with the v4l2 module in VLC.]("https://wiki.videolan.org/Documentation:Modules/v4l2/")

[/FONT][/COLOR]

---

