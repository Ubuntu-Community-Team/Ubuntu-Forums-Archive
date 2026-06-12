---
title: "App to capture from webcam"
date: 2008-06-25
forum: Ubuntu Studio
---

### Post by bermuda345 on 2008-06-25
Anyone know of a good app to capture video from my built in webcam?

---

### Post by bermuda345 on 2008-06-25
bump

---

### Post by Stochastic on 2008-06-25
Try using Cheese (it's in the repos: apt-get install cheese).

---

### Post by Samhain13 on 2008-06-25
With VLC:

1. File > Open
2. Under the Video4Linux tab, select your video device (for example, mine would be /dev/video0

3a. Hit OK and wait for VLC to show you what it's getting from the webcam or 
3b. To save the stream...

4. Tick "Stream/Save" in Advanced Options section and click Settings
5. Tick "Play Locally" to view the captured images, tick "file" and provide a file name with the appropriate extension (see next item)
6. Select an "Encapsulation Method", say "MP4"
7. Select the appropriate video codec under "Transcoding Options", say "mp4v"
8. Hit OK and wait for VLC to show you what it's getting from the webcam

Hit stop when done and check the file in your Home directory, if you didn't instruct VLC to save in another location.

---

### Post by jakupl on 2008-06-26
> **Samhain13 said:**
> With VLC:

1. File > Open
2. Under the Video4Linux tab, select your video device (for example, mine would be /dev/video0

3a. Hit OK and wait for VLC to show you what it's getting from the webcam 

when i do this, i get 
```
Unable to open 'v4l://'
```

what am I doing wrong?

maybe I am not writing the correct video device. I have an asus A6Rp with an integrated webcam.

EDIT: i can't use cheese, because it crashes on me. It gets video input though. I also have Camorama webcam viewer and it works beautifully.. but it can only take pictures... aarh

---

### Post by nalmeth on 2008-06-26
Lots of good info here:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by jakupl on 2008-06-27
> **nalmeth said:**
> Lots of good info here:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)


nope. i have no driver issues. i only want vlc to work

---

### Post by Windsurfer619 on 2008-06-27
I'd like to hear about a nice video capture program as well.

---

### Post by Samhain13 on 2008-06-27
> **jakupl said:**
> maybe I am not writing the correct video device. I have an asus A6Rp with an integrated webcam.

It must just be the address to the device. I'm sorry but I can't help you any further with that problem. :(

---

### Post by nalmeth on 2008-06-27
The link I gave you shows how to capture video using mencoder via the command line. I know, everyone loves GUI's but you should at least try it - you can just copy&paste the commands.

[Recording to an AVI File]("https://help.ubuntu.com/community/Webcam#Recording%20to%20an%20AVI%20file")
It has worked beautifully for me

BTW, I'm sure v4l must stand for video4linux. Perhaps your camera isn't supported by v4l, or additional setup may be required. 
If you really want VLC to do the job, check if your cam is supported by v4l.

---

### Post by Orlsend on 2008-06-28
Cheese is One of the best ones around,

I try several other but thye are not as good as Cheese.

---

### Post by Windsurfer619 on 2008-06-28
> **Orlsend said:**
> Cheese is One of the best ones around,

I try several other but thye are not as good as Cheese.

Unfortunately, cheese seems to almost freeze when it captures video, and the resulting video is "sped up" and lacks sound.

---

### Post by wolffangalchemist on 2008-09-22
> **Windsurfer619 said:**
> Unfortunately, cheese seems to almost freeze when it captures video, and the resulting video is "sped up" and lacks sound.

i had the same problem only fix i know of is to put the mic right up to your face and convert the video to mpg with ffmpeg.

in terminal type "sudo apt-get install ffmpeg" without "quotes" if you haven't already
then once installed cd to the directory with the .ogg file and type
"ffmpeg -i yourvideo.ogg yourvideo.mpg" without "quotes" this works nicely for uploading to youtube and such. 
oddly enough only media player the original .ogg files play fine in for me is vlc.

p.s a good simple video editor would be kdenlive it is slightly similar to wmm.

---

### Post by crazyfuturamanoob on 2008-09-22
XSane! Works for me.

[SIZE="1"]You may have to reboot your computer if xsane doesn't find your webcam.[/SIZE]

---

