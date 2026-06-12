---
title: "How to fix this simple script?"
date: 2008-06-23
forum: The Cafe
---

### Post by Extreme Coder on 2008-06-23
Hi guys,
I made this script to convert videos to DPG format, which is a video format for my Nintendo DS, but it isn't working :/
Can anybody help?
```
!/bin/bash
ffmpeg -i $1 -s 256x192 -vcodec mpeg1video -b 512k -coder 0 -r 20 -mbd simple $1.m1v
ffmpeg -i $1 -acodec mp2 -ab 128k -ar 32000 -ac 2  out.mp2
wine dpgmux.exe out.m1v out.mp2
rm out.m1v
rm out.mp2
```
I'm sure it's something painfully obvious, but I know zilch about BASH :/

Thanks!

---

### Post by Kingsley on 2008-06-23
I know a lot less than you, but I think there's supposed to be a # in front of !/bin/bash.

---

### Post by tamoneya on 2008-06-23
also on the last line it looks like you should be changing the output destination: ```
ffmpeg -i $1 -s 256x192 -vcodec mpeg1video -b 512k -coder 0 -r 20 -mbd simple out.m1v

```

---

### Post by Extreme Coder on 2008-06-23
here's what happens when I add the # and change the output:

```
[ahmad@localhost bin]$ ./encode+mux_4_3.sh /home/ahmad/Videos/Big\ Buck\ Bunny.avi
bash: ./encode+mux_4_3.sh: /bin/bash^M: bad interpreter: No such file or directory
```

---

### Post by Extreme Coder on 2008-06-23
Hmm.. I tried also with using sh and got a different error:
```
[ahmad@localhost bin]$ sh encode+mux_4_3.sh /home/ahmad/Videos/Big\ Buck\ Bunny.avi
FFmpeg version SVN-r11599, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-shared --libdir=/usr/lib --enable-liba52 --enable-pp --enable-gpl --enable-pthreads --enable-libnut --enable-libtheora --enable-libvorbis --enable-x11grab --enable-dirac --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libx264 --enable-libxvid --enable-libamr_nb --enable-libamr_wb
  libavutil version: 49.6.0
  libavcodec version: 51.49.0
  libavformat version: 52.5.0
  libavdevice version: 52.0.0
  built on Mar 17 2008 14:46:52, gcc: 4.2.3 (4.2.3-5mnb1)
/home/ahmad/Videos/Big: no such file or directory
FFmpeg version SVN-r11599, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-shared --libdir=/usr/lib --enable-liba52 --enable-pp --enable-gpl --enable-pthreads --enable-libnut --enable-libtheora --enable-libvorbis --enable-x11grab --enable-dirac --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libx264 --enable-libxvid --enable-libamr_nb --enable-libamr_wb
  libavutil version: 49.6.0
  libavcodec version: 51.49.0
  libavformat version: 52.5.0
  libavdevice version: 52.0.0
  built on Mar 17 2008 14:46:52, gcc: 4.2.3 (4.2.3-5mnb1)
/home/ahmad/Videos/Big: no such file or directory
dpgmux v1.002
dpgmux comes with ABSOLUTELY NO WARRANTY; see 'gpl.txt'

! ERROR: Wrong parameters!

Usage:
dpgmux.exe file [file2]
  to demultiplex dpg: specify only dpg file
  to create dpg: specify m1v and mp2 file (MPEG-1 streams)
Press Return key to continue:

```

---

### Post by wootah on 2008-06-23
> **Extreme Coder said:**
> Hi guys,
I made this script to convert videos to DPG format, which is a video format for my Nintendo DS, but it isn't working :/
Can anybody help?
```
!/bin/bash
ffmpeg -i $1 -s 256x192 -vcodec mpeg1video -b 512k -coder 0 -r 20 -mbd simple $1.m1v
ffmpeg -i $1 -acodec mp2 -ab 128k -ar 32000 -ac 2  out.mp2
wine dpgmux.exe out.m1v out.mp2
rm out.m1v
rm out.mp2
```I'm sure it's something painfully obvious, but I know zilch about BASH :/

Thanks!

Should you perhaps try:
```

#!/bin/bash
thefile = $1
fmpeg -i $thefile -s 256x192 -vcodec mpeg1video -b 512k -coder 0 -r 20 -mbd simple out.m1v && ffmpeg -i $thefile -acodec mp2 -ab 128k -ar 32000 -ac 2  out.mp2 && wine dpgmux.exe out.m1v out.mp2
if [ -e out.m1v ]; then
    rm out.m1v
fi

if [ -e out.mp2 ]; then
    rm out.mp2
fi

```

PS: I'm not that good with bash scripting yet :)

---

### Post by Extreme Coder on 2008-06-23
After I fixed some spelling mistakes, I get this:
```
[ahmad@localhost bin]$ sh encode+mux_4_3.sh /home/ahmad/Videos/Big\ Buck\ Bunny.avi
encode+mux_4_3.sh: line 2: thefile: command not found
FFmpeg version SVN-r11599, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-shared --libdir=/usr/lib --enable-liba52 --enable-pp --enable-gpl --enable-pthreads --enable-libnut --enable-libtheora --enable-libvorbis --enable-x11grab --enable-dirac --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libx264 --enable-libxvid --enable-libamr_nb --enable-libamr_wb
  libavutil version: 49.6.0
  libavcodec version: 51.49.0
  libavformat version: 52.5.0
  libavdevice version: 52.0.0
  built on Mar 17 2008 14:46:52, gcc: 4.2.3 (4.2.3-5mnb1)
-s: no such file or directory
encode+mux_4_3.sh: line 11: syntax error: unexpected end of file
```

---

### Post by wootah on 2008-06-23
> **Extreme Coder said:**
> After I fixed some spelling mistakes, I get this:
```
[ahmad@localhost bin]$ sh encode+mux_4_3.sh /home/ahmad/Videos/Big\ Buck\ Bunny.avi
encode+mux_4_3.sh: line 2: thefile: command not found
FFmpeg version SVN-r11599, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-shared --libdir=/usr/lib --enable-liba52 --enable-pp --enable-gpl --enable-pthreads --enable-libnut --enable-libtheora --enable-libvorbis --enable-x11grab --enable-dirac --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libx264 --enable-libxvid --enable-libamr_nb --enable-libamr_wb
  libavutil version: 49.6.0
  libavcodec version: 51.49.0
  libavformat version: 52.5.0
  libavdevice version: 52.0.0
  built on Mar 17 2008 14:46:52, gcc: 4.2.3 (4.2.3-5mnb1)
-s: no such file or directory
encode+mux_4_3.sh: line 11: syntax error: unexpected end of file
```

Did you just try and set +777 on the script and execute it with ./script_name ?

---

### Post by Extreme Coder on 2008-06-24
> **wootah said:**
> Did you just try and set +777 on the script and execute it with ./script_name ?
Still not working :(

---

### Post by koenn on 2008-06-24
>  /bin/bash^M: bad interpreter: No such file or directory

the trailing ^M after /bin/bash makes it an unknown file(-name). 
Delete the ^M and try again. 

You can avoid this sort ot trouble easily by writing and editing your shell sccripts on Linux in stead of on Windows.

---

