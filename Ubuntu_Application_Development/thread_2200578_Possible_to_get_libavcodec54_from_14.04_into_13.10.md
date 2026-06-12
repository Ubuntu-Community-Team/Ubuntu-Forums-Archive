---
title: "Possible to get libavcodec54 from 14.04 into 13.10?"
date: 2014-01-20
forum: Ubuntu Application Development
---

### Post by PeterTaps on 2014-01-20
Folks,

My development environment is Ubuntu 13.10. I am compiling VLC with support for vdpau. This library is dependent upon libavcodec.so.54, among other things. However, Ubuntu 13.10 repositories contain libavcodec53. I see that libavcodec54 is available under 14.04 (trusty) builds. I am wondering if there is a way to backport this to 13.10? Perhaps I can just add trusty universal repository to 13.10.

Thank you in advance for your help.

Regards,
Peter

---

### Post by monkeybrain20122 on 2014-01-20
Hi

To get the latest ffmpeg 2.1.2 install ffmpeg from [https://launchpad.net/~samrog131/+archive/ppa](https://launchpad.net/~samrog131/+archive/ppa)
Install all the -dev files and ffmpeg-set-alternatives, then 

```
sudo update-alternatives --config ffmpeg
```
and pick /opt/ffmpeg as the default. 

To check run ffmpeg in the terminal and you should see

```
ffmpeg version 2.1.2 Copyright (c) 2000-2013 the FFmpeg developers
  built on Jan 15 2014 00:48:16 with gcc 4.8 (Ubuntu/Linaro 4.8.1-10ubuntu9)
  configuration: --prefix=/opt/ffmpeg --libdir=/opt/ffmpeg/lib/ --enable-shared --disable-stripping --enable-gpl --enable-version3 --enable-runtime-cpudetect --enable-postproc --enable-x11grab --enable-libcdio --enable-vaapi --enable-vdpau --enable-bzlib --enable-gnutls --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-libfaac --enable-libvo-aacenc --enable-nonfree --enable-libmp3lame --enable-libx264 --enable-libxvid --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libfdk_aac --enable-libopus --enable-pthreads --enable-zlib --enable-libvpx --enable-libfreetype --enable-libpulse
  libavutil      52. 48.101 / 52. 48.101
  libavcodec     55. 39.101 / 55. 39.101
  libavformat    55. 19.104 / 55. 19.104
  libavdevice    55.  5.100 / 55.  5.100
  libavfilter     3. 90.100 /  3. 90.100
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

```
See this thread for some small additional points about getting the vlc dependencies [http://ubuntuforums.org/showthread.php?t=2188965](http://ubuntuforums.org/showthread.php?t=2188965) (basically if you run apt-get build-dep vlc do it before you add the ppa because it will want to install the libav -dev files from the repo and that would defeat the purpose, but after installing all the dependencies you can install the ppa's dev files and it will remove the default ones)

There is no need for adjusting CPPFLAGS LDFLAGS and PKG_CONFIG_PATH as in my thread if you have set ffmpeg from the ppa as the default. I also did it in a sort of clumsy way because I need to keep phonon-backend-vlc, but if you don't then it would be straight forward.

---

### Post by deadflowr on 2014-01-20
[This]("http://packages.ubuntu.com/trusty/libavcodec54")
you can get it from here, if you like.
Note the needed depends it needs(?).

You could build it from source or try grabbing the .deb package.

I wouldn't recommend adding  a repo, too many changes and you might end up with a mixed/mucked up machine.
Also here's this
[http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949)

---

### Post by monkeybrain20122 on 2014-01-20
> **deadflowr said:**
> [This]("http://packages.ubuntu.com/trusty/libavcodec54")
you can get it from here, if you like.
Note the needed depends it needs(?).

You could build it from source or try grabbing the .deb package.

I wouldn't recommend adding  a repo, too many changes and you might end up with a mixed/mucked up machine.
Also here's this
[http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949)
Installing those debs WILL break the system (and a small point, it is not real ffmpeg, but a Debian/Ubuntu fork called avconv which cannot handle some formats that ffmpeg has no problem playing. e.g some .flv files) Adding the ppa is ok because it is installed in /opt and you can use update-alternatives to pick your version as default.

Yes, OP can also use Andrew's tutorial and compile a local version of ffmpeg first, that was my first attempt (and instead of cloning the beta from git just get the tarball for vlc-2.1.2). But then it is simpler just to add a ppa and switch it to default. It can also be used as standalone ffmpeg.

---

### Post by PeterTaps on 2014-01-20
Thank you very much for your help.

Regards,
Peter

---

