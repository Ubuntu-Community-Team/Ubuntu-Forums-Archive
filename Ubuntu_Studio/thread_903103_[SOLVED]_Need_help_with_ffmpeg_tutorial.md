---
title: "[SOLVED] Need help with ffmpeg tutorial"
date: 2008-08-27
forum: Ubuntu Studio
---

### Post by Meph1st0 on 2008-08-27
I am trying to follow the tutorial found [here]("https://wiki.ubuntu.com/ffmpeg").  I'm able to get the svn copy of ffmpeg and run Make to compile it.  When I enter "sudo make install"  I get the follow errors:

```
install -d "/usr/local/lib"
install -m 644 libpostproc/libpostproc.a "/usr/local/lib"
ranlib "/usr/local/lib/libpostproc.a"
install -d "/usr/local/lib"
install -m 755 libpostproc/libpostproc.so "/usr/local/lib/libpostproc.so.51.1.0"
strip "/usr/local/lib/libpostproc.so.51.1.0"
cd "/usr/local/lib" && ln -sf libpostproc.so.51.1.0 libpostproc.so.51
cd "/usr/local/lib" && ln -sf libpostproc.so.51.1.0 libpostproc.so
install -d "/usr/local/lib"
install -m 644 libswscale/libswscale.a "/usr/local/lib"
ranlib "/usr/local/lib/libswscale.a"
install -d "/usr/local/lib"
install -m 755 libswscale/libswscale.so "/usr/local/lib/libswscale.so.0.5.1"
strip "/usr/local/lib/libswscale.so.0.5.1"
cd "/usr/local/lib" && ln -sf libswscale.so.0.5.1 libswscale.so.0
cd "/usr/local/lib" && ln -sf libswscale.so.0.5.1 libswscale.so
install -d "/usr/local/lib"
install -m 644 libavdevice/libavdevice.a "/usr/local/lib"
ranlib "/usr/local/lib/libavdevice.a"
install -d "/usr/local/lib"
install -m 755 libavdevice/libavdevice.so "/usr/local/lib/libavdevice.so.52.1.0"
strip "/usr/local/lib/libavdevice.so.52.1.0"
cd "/usr/local/lib" && ln -sf libavdevice.so.52.1.0 libavdevice.so.52
cd "/usr/local/lib" && ln -sf libavdevice.so.52.1.0 libavdevice.so
install -d "/usr/local/lib"
install -m 644 libavformat/libavformat.a "/usr/local/lib"
ranlib "/usr/local/lib/libavformat.a"
install -d "/usr/local/lib"
install -m 755 libavformat/libavformat.so "/usr/local/lib/libavformat.so.52.21.0"
strip "/usr/local/lib/libavformat.so.52.21.0"
cd "/usr/local/lib" && ln -sf libavformat.so.52.21.0 libavformat.so.52
cd "/usr/local/lib" && ln -sf libavformat.so.52.21.0 libavformat.so
install -d "/usr/local/lib"
install -m 644 libavcodec/libavcodec.a "/usr/local/lib"
ranlib "/usr/local/lib/libavcodec.a"
install -d "/usr/local/lib"
install -m 755 libavcodec/libavcodec.so "/usr/local/lib/libavcodec.so.51.69.0"
strip "/usr/local/lib/libavcodec.so.51.69.0"
cd "/usr/local/lib" && ln -sf libavcodec.so.51.69.0 libavcodec.so.51
cd "/usr/local/lib" && ln -sf libavcodec.so.51.69.0 libavcodec.so
install -d "/usr/local/lib"
install -m 644 libavutil/libavutil.a "/usr/local/lib"
ranlib "/usr/local/lib/libavutil.a"
install -d "/usr/local/lib"
install -m 755 libavutil/libavutil.so "/usr/local/lib/libavutil.so.49.10.0"
strip "/usr/local/lib/libavutil.so.49.10.0"
cd "/usr/local/lib" && ln -sf libavutil.so.49.10.0 libavutil.so.49
cd "/usr/local/lib" && ln -sf libavutil.so.49.10.0 libavutil.so
install -d "/usr/local/include/libpostproc"
install -d "/usr/local/lib/pkgconfig"
install -m 644 "/home/jbrown/ffmpeg/libpostproc"/postprocess.h "/usr/local/include/libpostproc"
install -m 644 "/home/jbrown/ffmpeg"/libpostproc/libpostproc.pc "/usr/local/lib/pkgconfig"
install -d "/usr/local/include/libswscale"
install -d "/usr/local/lib/pkgconfig"
install -m 644 "/home/jbrown/ffmpeg/libswscale"/swscale.h "/home/jbrown/ffmpeg/libswscale"/rgb2rgb.h "/usr/local/include/libswscale"
install -m 644 "/home/jbrown/ffmpeg"/libswscale/libswscale.pc "/usr/local/lib/pkgconfig"
install -d "/usr/local/include/libavdevice"
install -d "/usr/local/lib/pkgconfig"
install -m 644 "/home/jbrown/ffmpeg/libavdevice"/avdevice.h "/usr/local/include/libavdevice"
install -m 644 "/home/jbrown/ffmpeg"/libavdevice/libavdevice.pc "/usr/local/lib/pkgconfig"
install -d "/usr/local/include/libavformat"
install -d "/usr/local/lib/pkgconfig"
install -m 644 "/home/jbrown/ffmpeg/libavformat"/avformat.h "/home/jbrown/ffmpeg/libavformat"/avio.h "/home/jbrown/ffmpeg/libavformat"/rtsp.h "/home/jbrown/ffmpeg/libavformat"/rtspcodes.h "/usr/local/include/libavformat"
install -m 644 "/home/jbrown/ffmpeg"/libavformat/libavformat.pc "/usr/local/lib/pkgconfig"
install -d "/usr/local/include/libavcodec"
install -d "/usr/local/lib/pkgconfig"
install -m 644 "/home/jbrown/ffmpeg/libavcodec"/avcodec.h "/home/jbrown/ffmpeg/libavcodec"/opt.h "/usr/local/include/libavcodec"
install -m 644 "/home/jbrown/ffmpeg"/libavcodec/libavcodec.pc "/usr/local/lib/pkgconfig"
install -d "/usr/local/include/libavutil"
install -d "/usr/local/lib/pkgconfig"
install -m 644 "/home/jbrown/ffmpeg/libavutil"/adler32.h "/home/jbrown/ffmpeg/libavutil"/avstring.h "/home/jbrown/ffmpeg/libavutil"/avutil.h "/home/jbrown/ffmpeg/libavutil"/base64.h "/home/jbrown/ffmpeg/libavutil"/common.h "/home/jbrown/ffmpeg/libavutil"/crc.h "/home/jbrown/ffmpeg/libavutil"/fifo.h "/home/jbrown/ffmpeg/libavutil"/intfloat_readwrite.h "/home/jbrown/ffmpeg/libavutil"/log.h "/home/jbrown/ffmpeg/libavutil"/lzo.h "/home/jbrown/ffmpeg/libavutil"/mathematics.h "/home/jbrown/ffmpeg/libavutil"/md5.h "/home/jbrown/ffmpeg/libavutil"/mem.h "/home/jbrown/ffmpeg/libavutil"/random.h "/home/jbrown/ffmpeg/libavutil"/rational.h "/home/jbrown/ffmpeg/libavutil"/sha1.h "/usr/local/include/libavutil"
install -m 644 "/home/jbrown/ffmpeg"/libavutil/libavutil.pc "/usr/local/lib/pkgconfig"
install -d "/usr/local/lib/vhook"
install -m 755 vhook/fish.so vhook/null.so vhook/watermark.so vhook/ppm.so vhook/imlib2.so vhook/drawtext.so "/usr/local/lib/vhook"
install -d "/usr/local/bin"
install -c -m 755 ffmpeg ffplay ffserver "/usr/local/bin"
install -d "/usr/local/share/man/man1"
install -m 644 doc/ffmpeg.1 doc/ffplay.1 doc/ffserver.1 "/usr/local/share/man/man1"

```

Is there something I'm missing? A dependency?

---

### Post by Meph1st0 on 2008-08-27
I am also getting the following error message now when I type ffmpeg --help

jbrown@mythbuntu:/usr/local/lib$ ffmpeg --help
ffmpeg: error while loading shared libraries: libavdevice.so.52: cannot open shared object file: No such file or directory

doing a google search I'm finding that there's a quite a few people who've had this error message.  All of their solutions look extremely complicated.  Could someone help me figure this out?

---

### Post by puurokauha on 2008-08-28
Im not running mythbuntu, but I had similar problem
```
ffmpeg: error while loading shared libraries: libswscale.so.0: cannot open shared object file: No such file or directory
```
this fixed it, ```
export LD_LIBRARY_PATH=/usr/local/lib/
```

---

### Post by Meph1st0 on 2008-08-28
Nice!  That did fix it.  What does that command do?

---

### Post by verysimple on 2008-11-06
2 other solutions. Begin by making sure that you indeed have the libraries installed. Run the command **locate libavdevice.so.52** and you should have the specific file path showing up in the list.

I will assume that the location of these libraries is **/usr/local/lib/** such as /usr/local/lib/libavdevice.so.52 . 

- Now that we know that the libraries are there, The first solution to fix this problem is to create symlinks of the missing libraries from /usr/lib to /usr/local/lib

**ln -s /usr/local/lib/libavdevice.so.52 /usr/lib/libavdevice.so.52**
ln -s /usr/local/lib/libavformat.so.52 /usr/lib/libavformat.so.52
etc ...

Not a very elegant solution.

- My preferred solution: there's a file called **/etc/ld.so.conf**. In my ubuntu install it contains a single line that includes the content of the directory **/etc/ld.so.conf.d/**

That directory in turn should normally have a couple of files. One of them should be /etc/ld.so.conf.d/**libc.conf**, which contains the line /usr/local/lib . If this is the case, then simply run the command **sudo ldconfig -v** to reload the libraries cache and your problem should be fixed. 

If the file doesn't exist you could create one called /etc/ld.so.conf.d/**ffmpeg.conf** (or even libc.conf) and add the line /usr/local/lib in it, then run **sudo ldconfig -v**.

---

### Post by phlipdascrip on 2010-03-10
> **verysimple said:**
> - My preferred solution: there's a file called **/etc/ld.so.conf**. In my ubuntu install it contains a single line that includes the content of the directory **/etc/ld.so.conf.d/**

That directory in turn should normally have a couple of files. One of them should be /etc/ld.so.conf.d/**libc.conf**, which contains the line /usr/local/lib . If this is the case, then simply run the command **sudo ldconfig -v** to reload the libraries cache and your problem should be fixed.

thanks a bunch, that did the trick! i was already digging around this stuff but since it all looked ok to me i didn't think there was something else to do, i.e. refresh a lib cache - who would have known.
i've read lots of "solutions" that said "just run export LD_LIBRARY_PATH=/usr/local/lib/" but this is the only thread that shows the right way to do it. appreciated!

---

