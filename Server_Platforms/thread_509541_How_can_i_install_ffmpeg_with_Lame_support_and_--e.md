---
title: "How can i install ffmpeg with Lame support and --enable-shared (for ffmpeg-php)?"
date: 2007-07-25
forum: Server Platforms
---

### Post by envis on 2007-07-25
ffmpeg-php tells me that i need to have configured ffmpeg with "--enable-shared" to work

ffmpeg does not work properly (no sound on flv, ect..) if installed with a simple "apt-get install ffmpeg"

by following this guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_lame_for_FFMPEG_.28needed_to_encode_FLV_with_sound.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_lame_for_FFMPEG_.28needed_to_encode_FLV_with_sound.29)
i was able to have ffmpeg do everything i needed

this guide tells me to "./configure" ffmpeg like this:
sudo ./configure --enable-gpl --enable-pp --enable-vorbis --enable-libogg \
--enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug \
--enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-pthreads \
--enable-x264

which works but sadly does not include "--enable-shared"... if i add "--enable-shared" to this like that:
sudo ./configure --enable-gpl --enable-pp --enable-vorbis --enable-libogg \
--enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug \
--enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-pthreads \
--enable-x264 --enable-shared

then i get this error:
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/libdts.a(parse.o): relocation R_X86_64_32S against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/libdts.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [libavcodec.so.51] Error 1
make[1]: Leaving directory `/usr/local/src/ffmpeg-0.cvs20060823/libavcodec'
make: *** [lib] Error 2

interesting thing is that if i do
sudo ./configure --enable-shared
the make functions. but i didnt try the ffmpeg in those condition cos i need my ffmpeg to support lame anyways...

so.. i tried this just for fun:
sudo ./configure --enable-shared --enable-mp3lame
this way also the make worked.. no errors. but when i tried to use it it didnt work.. gave me an error about "libavcodec"....

so im just posting this here in hope that anyone has any hint to help me figure this one out...

How can i install ffmpeg with Lame support and --enable-shared (for ffmpeg-php)?

---

