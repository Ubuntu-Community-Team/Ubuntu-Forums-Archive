---
title: "Check exact frame rate"
date: 2013-01-16
forum: Ubuntu Studio
---

### Post by cub on 2013-01-16
I record small music videos with my iPhone4 and create the video in Ubuntu Studio 12.10 and Kdenlive. However, the iPhone decides automatically which frame rate to use and I can't figure out if it's 24 and 30 fps or 23.99 and 29.97 fps.

When I check the clips in Ubuntu Studio it tells me the files are 24 and 30 fps. When I check the same files on my MacBook it says they are 23.99 and 29.97 fps. Since Kdenlive have different project settings for 29.97 and 30 fps project I suppose it would make a difference depending on what I choose. I would like to avoid any sync issues with the actual music file when syncing the video clips to the musical score.

How can I check the movie clips to be sure of the exact fps of the file?

---

### Post by jejeman on 2013-01-16
Use mediainfo.

---

### Post by cub on 2013-01-16
mediainfo seems not to be installed on a vanilla Ubuntu Studio..? I got other tips about ffplay and ffprobe which agree with my MacBook on the 23.99 fps and 29.97 fps.

---

### Post by jejeman on 2013-01-16
Yes it is not installed by default.
Or you can use ffmpeg, as you already did.

---

