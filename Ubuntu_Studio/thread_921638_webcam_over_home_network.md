---
title: "webcam over home network"
date: 2008-09-16
forum: Ubuntu Studio
---

### Post by nbo10 on 2008-09-16
Hi All,

I have a room with my pets and I want to be able to monitor them while I'm in my office, in home. I have a old laptop and webcam I can put in the room and connect to my wireless network. But how could I view the cam on other computers that are on the same network. I don't need to the cam to go to the outside internet. Thanks

---

### Post by prshah on 2008-09-16
> **nbo10 said:**
>  But how could I view the cam on other computers that are on the same network.

You can do this using vlc. First, install vlc```
sudo apt-get install vlc
```

Then start vlc (Applications-Sound and Video-VLC Media Player". Then click on File-Open Capture Device and select your webcam device (usually /dev/video0). Near the bottom, click stream / save, then click settings and choose a protocol and port (usually UDP for video streaming).

Now go to your other computer and open VLC, then click File-Open network stream and give the same information as you have given earlier. VLC should now stream the video to your computer.

---

