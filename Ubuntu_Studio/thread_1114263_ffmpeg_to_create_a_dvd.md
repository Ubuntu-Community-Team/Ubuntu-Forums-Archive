---
title: "ffmpeg to create a dvd"
date: 2009-04-02
forum: Ubuntu Studio
---

### Post by cdmike2k8 on 2009-04-02
I am using ffmpeg to create a dvd from command line because I am doing the dvd creating from a server environment.  I use the following code to convert the video:```
ffmpeg -i infile.mkv -target ntsc-dvd outfile.mpg
```  This generates a mpg file that I can use with dvdauthor to create a dvd.  The problem is that ffmpeg is not adjusting the size of the file so that it fits on a standard dvd.  I decided that I would try to adjust the bitrates of the output file as to make the file smaller.  When using the flags for bitrate ```
-ab 400k -b 5500k
```, I get the error message ```
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height
```
Here is an output of the terminal when using ffmpeg to encode the video.```
$ ffmpeg -i input.mkv -target ntsc-dvd -ab 400k -b 5500k output.mpg
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
[matroska @ 0xb7f72388]Ignoring seekhead entry for ID=0x1549a966
[matroska @ 0xb7f72388]Ignoring seekhead entry for ID=0x1654ae6b
[matroska @ 0xb7f72388]Ignoring seekhead entry for ID=0x114d9b74
[matroska @ 0xb7f72388]Unknown entry 0x73a4 in info header
[matroska @ 0xb7f72388]Unknown track header entry 0x55aa - ignoring
[matroska @ 0xb7f72388]Unknown track header entry 0x23314f - ignoring
[matroska @ 0xb7f72388]Unknown track header entry 0x55ee - ignoring
[matroska @ 0xb7f72388]Unknown track header entry 0xaa - ignoring
[matroska @ 0xb7f72388]Unknown track header entry 0x55aa - ignoring
[matroska @ 0xb7f72388]Unknown track header entry 0x23314f - ignoring
[matroska @ 0xb7f72388]Unknown track header entry 0x55ee - ignoring
[matroska @ 0xb7f72388]Unknown track header entry 0xaa - ignoring
Input #0, matroska, from 'input.mkv':
  Duration: 02:01:50.3, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: h264, yuv420p, 1280x536 [PAR 1:1 DAR 160:67], 23.98 tb(r)
    Stream #0.1(eng): Audio: dca, 48000 Hz, 5:1
Output #0, dvd, to 'output.mpg':
    Stream #0.0(eng): Video: mpeg2video, yuv420p, 720x480 [PAR 199:125 DAR 597:250], q=2-31, 5500 kb/s, 29.97 tb(c)
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 5:1, 400 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

```Is it possible that I don't have the right codecs?  If anyone knows of an easier way to author a dvd from an mkv at command line, their feedback would be much appreciated.  Thanks in advance for all your help.

---

### Post by cdmike2k8 on 2009-04-02
I just realized that if I don't try to control the audio bitrate, it appears to encode.  I will try to see if this will be enough to get the disk to fit on a dvd.

---

