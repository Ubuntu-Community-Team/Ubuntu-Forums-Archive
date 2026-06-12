---
title: "Video Encoding for PSP: How to do it fullscreen (480x272) in h.264"
date: 2009-04-19
forum: Ubuntu Studio
---

### Post by Achlervor on 2009-04-19
I just bought my PSP yesterday, primarily to carry videos with me. It took me half a day to get video encoding to work properly on Ubuntu. As good sources on this problem are rare on the internet and there are plenty of outdated instructions that rather confuse than help, I decided to quickly write down what I found out. There is still room for improvement here and there, but basically it works well.

In general the PSP is very picky when it comes to playing videos. You need to have files with extension .MP4, you can only use certain video resolutions and only mpeg4 and h264 as codecs.

**1. Connecting the PSP**

In Ubuntu 8.10 usually you just have to connect the PSP and set it to USB mode. It will show up as a usual storage device.

If this should not work (happened to me once, I don't know why), just use the manual procedure: *tail /var/log/messages* gives you the device name (i.e. /dev/sdd1), then *sudo mount -t auto /dev/sdd1 /somewhere*.

**2. How not to do video encoding (a.k.a. the old way)**

There are plenty of instructions on the internet that tell you to encode videos MPEG4 and place them in the folder /MP_ROOT/100MNV01 on the memory stick. This procedure has drawbacks:
- it is limited to mpeg4 (no h264)
- there are strict limitations on the video size (no fullscreen)
- you have to use a silly naming convention for your files (M4V00001.MP4)

**3. How to do it correctly**

**a.** Update your PSP firmware to at least 3.30. Actually I have only tested 5.03. You can find the firmware version in the system settings menu of the PSP. Updating is easy and painless. If you have WLAN (802.11b) you can just tell the PSP to automatically download an update from the internet.

**b.** Format your memory stick **with the updated PSP**. Only after formating you will have /VIDEO and /MUSIC folders in the root folder of the stick.

**c. **Encoding

For this I only use stuff from the Ubuntu repositories (8.10), no external tools, nothing to compile. Unfortunately I am not really sure which packages are needed for this (during my experiments I installed almost anything that looked related to video, including many -dev packages).

```
mencoder <INPUT> -sws 9 -vf scale=-3:272,expand=480:272 -lavcopts aspect=16/9 -oac faac -faacopts br=128:mpeg=4:object=2:raw -ovc x264 -x264encopts bitrate=650:global_header:partitions=all:trellis=1:vbv_maxrate=768:vbv_bufsize=2000:level_idc=30 -of lavf -af lavcresample=48000,channels=2 -lavfopts format=psp -o <OUTPUT>
```

If you encode DVDs etc, try to remove the part "*-af lavcresample=48000,channels=2*", as this re-samples the audio. I only added it since I want to encode videos from my digital cameras and sometimes the AAC codec complained about the audio format.

In general the PSP can play videos with 16:9 format (480x272) in fullscreen. The largest working 4:3 resolution appears to be 320x240. As this looks signifficantly worse than a full resolution video, the above line takes 4:3 videos, scales them to 272 pixels hight and then adds black bars on the left and right. This is not a nice solution but it appears to be the best way to handle 4:3 videos. 

The line above also works with 16:9 videos without problems. I tested this with MJPG-MOVs, H.264-MOVs (from different digicams), MPEG4-AVIs, FLVs, and MP4-Files (from my Nokia Mobile).

The output file needs to have the extension .MP4, but the actual name can be chosen freely. Copy the video to the /VIDEO directory on the card. You can also create one layer of subdirectories to organize your files.

**d. **Thumbnails

For each "videofile.MP4", the PSP looks for a "videofile.THM", which is just a renamed JPG. The best resolution for this appears to be 160x120 (yes, its 4:3).

If you search for instructions on the internet, you will always find this command using ffmpeg:

```
ffmpeg -i <INFILE> -f image2 -ss 5 -vframes 1 -r 1 -s 160x120 -an <OUTFILE>.THM

```

I did not like this, as ffmpeg has no easy way of handling automatic resizing (you have to give pixel offsets). So I prefer this:

```
mplayer -vo jpeg -frames 1 -ss 00:00:05 -vf scale=-3:120,crop=160:120 <INFILE>
```

This creates a file named 00000001.jpg which you can rename afterwards.

**4. Doing it semi-automatic**

I did not write real scripts yet, just copy-paste one-liners to save some work.

**a. **Encode all videos in a directory and place the encoded videos in a subdirectory "psp"
```

mkdir psp
for e in mov MOV avi AVI MP4 mp4 flv FLV; do for f in $(ls *.$e); do mencoder $f -sws 9 -vf scale=-3:272,expand=480:272 -lavcopts aspect=16/9 -oac faac -faacopts br=128:mpeg=4:object=2:raw -ovc x264 -x264encopts bitrate=650:global_header:partitions=all:trellis=1:vbv_maxrate=768:vbv_bufsize=2000:level_idc=30 -of lavf -af lavcresample=48000,channels=2 -lavfopts format=psp -o psp/${f%$e}MP4; done; done
```

**b. **Collect all files from the "psp" subdirs in a whole directory tree

```
find . -name "psp" -type d | while read f; do mkdir -p somepath/${f%psp}; cp $f/* somepath/${f%psp}; done
```

**c. **Generate the thumbnails

```
find . -name "*.MP4" | while read f; do mplayer -noconsolecontrols -vo jpeg -frames 1 -ss 00:00:05 -vf scale=-3:120,crop=160:120 $f ; mv 00000001.jpg ${f%MP4}THM ; done;
```

"-noconsolecontrols" is necessary here as mplayer will otherwise read the next commands from the console.

---

### Post by MartyBuntu on 2009-04-19
Nice, but I have no problems with encoding video using **Winff**.

I'm sure your way works too, although I haven't tried it.

---

### Post by Arsic on 2010-08-28
I get this error:
```
MEncoder 1.0rc3-4.4.3 (C) 2000-2009 MPlayer Team
-x264encopts is not an MEncoder option

Exiting... (error parsing command line)

```

I tried reinstalling x264 and mencoder, but I think I might have to recompile mencoder too. No idea how. Any help?

Edit: Woohoo fixed it. I reinstalled mplayer, then had to reinstall mencoder. I got an error saying:
```
MPlayer was compiled without libfaac. See README or DOCS.
MPlayer was compiled without libfaac. See README or DOCS.
```
Then uninstalled mplayer (which also uninstalls mencoder). Added and updated the repository for Medibuntu by running the first two commands from [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"). Reinstalled both mplayer and mencoder after that and it works.

---

