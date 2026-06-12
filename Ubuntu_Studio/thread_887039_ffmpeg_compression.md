---
title: "ffmpeg compression"
date: 2008-08-11
forum: Ubuntu Studio
---

### Post by jfreak53 on 2008-08-11
Ok I've been trying to quite some time now to get ffmpeg to go down below 100K bitrate in wmv2 video compression.  But for some reason I cannot get it below that and the file to be smaller.  When I use -b 100k and -b 64k (why not right haha) I still get the same result:

```
Overall bit rate                 : 325 Kbps
Maximum Overall bit rate         : 96.0 Kbps
```

Somehow I have to get the overall bit rate down below 100 but I can't get it there for some reason.  Does anyone know what I'm doing wrong here?

Thanks in advance.

---

### Post by Creative2 on 2008-08-12
mm well i have used always mencoder for wmv2 
[B]
maybe this could help you , i don't know[/B]

mencoder -oac lavc -lameopts abr:br=128 -ovc lavc -vf scale -zoom -xy 720 -lavcopts vcodec=wmv2:acodec=wmav2 -o OUTPUT INPUT

---

### Post by eye208 on 2008-08-12
Get real. Video at 100kbps will not be usable anyway. 100kbps is low even for audio alone. Your video will dissolve into block noise. Even YouTube uses almost 300kbps for the video stream. And we all know how badly that sucks, don't we?

---

### Post by kostkon on 2008-08-12
> **jfreak53 said:**
> Ok I've been trying to quite some time now to get ffmpeg to go down below 100K bitrate in wmv2 video compression.  But for some reason I cannot get it below that and the file to be smaller.  When I use -b 100k and -b 64k (why not right haha) I still get the same result:

```
Overall bit rate                 : 325 Kbps
Maximum Overall bit rate         : 96.0 Kbps
```

Somehow I have to get the overall bit rate down below 100 but I can't get it there for some reason.  Does anyone know what I'm doing wrong here?

Thanks in advance.

> **eye208 said:**
> Get real. Video at 100kbps will not be usable anyway. 100kbps is low even for audio alone. Your video will dissolve into block noise. Even YouTube uses almost 300kbps for the video stream. And we all know how badly that sucks, don't we?
Indeed, 100kbs is very low. Why would you need such a low bitrate for a video.

It seems that the codec may not even allow you to use a bitrate lower than 325kbs.

---

### Post by jfreak53 on 2008-08-12
Well the whole thing is I know that 100kb is possible I use winavi flv converter in windows and it converts just fine, this is what is exported using it:

```
Overall bit rate                 : 68.5 Kbps
Maximum Overall bit rate         : 107 Kbps
```

So the whole thing is it's possible and I've been using it for some time with no problems and it looks decent for what I use it for.

---

