---
title: "ffmpeg unknown encoder 'xvid'"
date: 2008-12-21
forum: Ubuntu Studio
---

### Post by Mahinva on 2008-12-21
EDIT: This should probably be in Multimedia & Video - ack! 

I continually get the error of "unknown encoder 'xvid'" when attempting to convert an .avi file to .mp4. I'm running Ubuntu 8.10.

I have installed, uninstalled and reinstalled ffmpeg several times to no avail.

Right now, I have medibuntu added to Synaptic and I suppose it's the medibuntu version of ffmpeg that is currently installed. Along with ffmpeg, I have also installed the following packages (which have deleted the non-unstripped versions of each lib):

libavutil-unstripped-49
libpostproc-unstripped-51
libavdevice-unstripped-52
libswscale-unstripped-0
libavcodec-unstripped-51
libavformat-unstripped-52
libavifile-0.7c2 (not sure if this one is required)

Terminal command of "ffmpeg -formats |grep aac" returns the following:

D aac ADTS AAC
EA libfaac
D A mpeg4aac

From reading elsewhere on the forums, the output stated above shows that ffmpeg is a bad install, but this output has been the same every time I uninstall/reinstall ffmpeg.

Medibuntu has been added, and Synaptic has been reloaded after the addition. Medibuntu is also checked off as well as listed under the Third-Party Software category.

How can I get xvid encoding added in - am I missing a lib?

---

### Post by FakeOutdoorsman on 2008-12-21
What is your ffmpeg command and the full ffmpeg response?  You probably need to change "xvid" to "libxvid" in your command.

---

### Post by Ng Oon-Ee on 2008-12-21
I'm pretty sure you're using Intrepid. The medibuntu repo in Intrepid does not have the unstripped version of ffmpeg, and I've heard they're not considering putting it in. You'll have to compile from source, there's a guide to that in the HOWTOs which I've used and am happy with.

---

### Post by Mahinva on 2008-12-22
> **FakeOutdoorsman said:**
> What is your ffmpeg command and the full ffmpeg response?  You probably need to change "xvid" to "libxvid" in your command.

Here is the command I've been using. I picked this up on a thread for converting videos for Sansa View.

```
ffmpeg -i /home/USER/ -r 29.97 -vcodec xvid -b 700k -acodec aac -ab 128k -bufsize 4M -qmax 51 -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -ar 44100 -g 300 -s 320x240 -aspect 4:3 -ac 2 -f mp4 -y /home/USER/
```

/home/USER/ gets filled out completely when I am trying to convert - I just have it filled by default so I don't forget my path.

I then get back the following:

```
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, avi, from '/home/USER/VIDEO.avi':
  Duration: 01:30:32.8, start: 0.000000, bitrate: 1080 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 528x288 [PAR 1:1 DAR 11:6], 23.98 tb(r)
    Stream #0.1: Audio: liba52, 48000 Hz, stereo, 192 kb/s
Unknown encoder 'xvid'

```

> **Ng Oon-Ee said:**
> I'm pretty sure you're using Intrepid. The medibuntu repo in Intrepid does not have the unstripped version of ffmpeg, and I've heard they're not considering putting it in. You'll have to compile from source, there's a guide to that in the HOWTOs which I've used and am happy with.

Yes, you're correct - I am using Intrepid. I don't know if I have followed the exact HOWTO you've used, but I did manually add medibuntu to the repository. Is simply adding medibuntu not sufficient enough - I thought that after adding medibuntu, the ffmpeg I'd install after would be the correct one? I only have 1 listing for ffmpeg in the repo.

Would you be able to provide a link to the HOWTO? This is the one I've found but am not sure whether it'll be fruitful or not:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Thanks for both of your insight!

---

### Post by FakeOutdoorsman on 2008-12-22
Try this:
```
ffmpeg -i input.avi -r 29.97 -vcodec libxvid -b 700k -acodec libfaac -ab 128k -bufsize 4M -qmax 51 -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -ar 44100 -g 300 -s 320x240 -aspect 4:3 -ac 2 -f mp4 -y output.mp4
```
I renamed "xvid" to "libxvid" and "aac" to "libfaac".  Older revisions of ffmpeg use the former names.  It should work because you have the unstripped libraries installed.  You don't need anything from Medibuntu to get this to work.

If you want the bleeding-edge, access to more codecs/encoders/decoders, or want to customize your ffmpeg install then the guide you linked to will help with that.

---

### Post by Mahinva on 2008-12-22
Thank you, FakeOutdoorsman! I am running the command you provided successfully. I'm not sure exactly how long it will take for the conversion to finish, but I'm guessing it'll be under 2 hours. I hope that I will be able to mark this thread as solved after playing the completed video on my View without any problems.

I've got fingers crossed. :)

My encoding needs are very simple right now; I just want to convert files to mp4 and have them play without lagging fps on my Sansa View. I will keep that HOWTO in mind in case things change. Thanks. :)

---

### Post by FakeOutdoorsman on 2008-12-22
You can encode a specific number of frames for a test encode by using the -vframes option.  For example, to encode the first 300 frames use "-vframes 300".

---

### Post by Mahinva on 2008-12-22
Wonderful - this worked! Sound and video are perfect. Thank you so much!

---

### Post by jacob01 on 2008-12-28
im having the same problem but when i try and switch xvid with libxvid it still doesn't work

i get this error: ```
Unknown encoder 'libxvid'
```

---

### Post by FakeOutdoorsman on 2008-12-28
> **jacob01 said:**
> im having the same problem but when i try and switch xvid with libxvid it still doesn't work

i get this error: ```
Unknown encoder 'libxvid'
```

I'm assuming you're using Ubuntu 8.10.  You probably need to install the ffmpeg unstripped libraries:
```
sudo apt-get install libavcodec-unstripped-51
```

---

### Post by jacob01 on 2008-12-29
yes i am running 8.10


it works!!

thank you!

---

### Post by Tuxi on 2008-12-30
Thanks a bunch for the pointer that I needed the "unstripped" versions of these packages.  I had a hard time figuring out why Kino couldn't encode using ffmpeg, and this fixes that problem.  (I could have looked at the scripts in /usr/share/kino/scripts/exports and try the script manually.)

---

### Post by in_rainbow on 2009-03-05
> **FakeOutdoorsman said:**
> I'm assuming you're using Ubuntu 8.10.  You probably need to install the ffmpeg unstripped libraries:
```
sudo apt-get install libavcodec-unstripped-51
```

this worked for me, thanks a million

---

### Post by AintJoe on 2009-05-11
For those running Jaunty, I had to run
```
sudo apt-get install libavcodec-unstripped-52
```
to get xvid conversion to work in ffmpeg.

---

### Post by m3alnemer on 2009-05-15
> **AintJoe said:**
> For those running Jaunty, I had to run
```
sudo apt-get install libavcodec-unstripped-52
```
to get xvid conversion to work in ffmpeg.

This works Great in Jaunty :D

Thanks):P

---

### Post by jdavilape on 2009-11-07
> **m3alnemer said:**
> This works Great in Jaunty :D

Thanks):P

Works in karmic too, thanks a lot

---

### Post by AlexanderDGreat on 2010-01-20
I also found the answer to this page:

If you want a more comprehensive approach: HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg

[http://ubuntuforums.org/showthread.php?p=8298012#post8298012]("http://ubuntuforums.org/showthread.php?p=8298012#post8298012")

Thanks.

---

### Post by wkulecz on 2010-01-21
My question is: Why are there stripped and unstripped versions?  Isn't Linux saddled with enough arcane knowledge requirements already?

--wally.

---

### Post by andrew.46 on 2010-01-21
Hi Wally,

> **wkulecz said:**
> My question is: Why are there stripped and unstripped versions?  Isn't Linux saddled with enough arcane knowledge requirements already?

This is not a 'Linux' issue as such, more a result of packaging decisions made by Debian and Ubuntu. It is designed so that users in various countries will not inadvertently break patent laws by using Ubuntu 'off the shelf'. The original source code comes with no such restrictions and in the case of FFmpeg compiling from source is the *best* way to get the full product (as long as this breaks no patent laws in your country).

All the best,

Andrew

---

### Post by cwhisperer on 2010-12-14
> **FakeOutdoorsman said:**
> I'm assuming you're using Ubuntu 8.10.  You probably need to install the ffmpeg unstripped libraries:
```
sudo apt-get install libavcodec-unstripped-51
```

this worked for me too ;) good job

---

### Post by Argard on 2011-05-07
> **FakeOutdoorsman said:**
> I'm assuming you're using Ubuntu 8.10.  You probably need to install the ffmpeg unstripped libraries:
```
sudo apt-get install libavcodec-unstripped-51
```

thanks!

---

### Post by raghuchandra on 2013-01-29
here is the solution for unrecognised codec libxvid just search "ubuntu restricted extras" in ubuntu software center and install them thats all its done.

---

### Post by codemaniac on 2013-01-29
Old thread is closed now.

---

### Post by sandyd on 2013-01-29
**Necromancing - thread closed**
As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.

Thanks!

edit: ninja'd!

---

