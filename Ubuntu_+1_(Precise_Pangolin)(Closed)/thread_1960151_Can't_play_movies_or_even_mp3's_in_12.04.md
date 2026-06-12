---
title: "Can't play movies or even mp3's in 12.04"
date: 2012-04-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by More or Less on 2012-04-16
When I go to the Ubuntu program download area, a few media players are listed and only Amarok downloads.  However, the default media player and Amarok won't play media files.

It gives an error with the word "python" in it.  Is there a way I can update Mr. Python?

When I try to download other programs, it wants to go to the "universe" source.  After about 5 seconds it stalls and won't download.  How do I get at least 1 media player to successfully play mp3's and movie files like .mp4, .avi, .wmv, and .flv in 12.04? Also, I would like one to play .rmvb files.

By the way, I was able to get flash files to load on the internet (.swf), so the computer sound and video is working.

---

### Post by mikewhatever on 2012-04-16
Was 'python' the only word in the error? Can you copy/paste the error as is, or post a screenshot. I suspect the problem is not with the number of media player; no need to download new ones.

PS: Are you aware that 12.04 is still in testing?

---

### Post by More or Less on 2012-04-16
The error message reads, "Python (v2.7) requires to install plugins to play media files of the following type: Advanced Streaming Format (ASF) demuxer"  I found something in the download area to get mp3s to work.  I can't get Ubuntu 11 (any version) to work properly.  Right now, the only thing I am having a problem with is video not displaying.  If it worked in 10, I am surprised 12 can't use the same VLC source.

---

### Post by oldfred on 2012-04-17
Moved to Ubuntu +1.

Did you install the restricted extras as part of the install?

---

### Post by More or Less on 2012-04-17
In the Ubuntu Software Center, there was something I tried that sounded like what you described.  However, it wouldn't download.  I would click "install" and then it would flicker for a second and stop as if nothing happened.  Is this what you mean?  Please give the EXACT location of where I should be getting files, thanks.

---

### Post by zombifier25 on 2012-04-17
Try again using the terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by More or Less on 2012-04-17
Looks like that part is already installed.  I think maybe the internet connection isn't working for the location of the files.  Is there another location I can install vlc from?

---

### Post by More or Less on 2012-04-17
I decided to try 11.10 one more time.  There was definitely a problem with the connection.  Maybe being connected to Pidgin was enough to prevent the downloads from even starting.  I had to try 3 times before the GStreamer would finish.  VLC wouldn't download at first, but after GStreamer finally downloaded, I tried VLC again and it worked.

---

