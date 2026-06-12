---
title: "Play Video on LTSP thin client"
date: 2010-08-03
forum: Server Platforms
---

### Post by pravindra.kumar on 2010-08-03
Dear,
I am unable to play some video files on LTSP thin client, when i play through VLC then it get closed. So now i opened VLC from terminal and clicked on play then it gave me following errors:-

[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[????????] x11 video output error: X11 request 143.1 failed with error code 10:
 BadAccess (attempt to access private resource denied)
[????????] x11 video output notice: buggy X11 server claims shared memory
[????????] x11 video output notice: support though it does not work (OpenSSH?)
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused

[00000381] oss audio output error: cannot open audio device (/dev/dsp)
[????????] x11 video output error: X11 request 143.1 failed with error code 10:
 BadAccess (attempt to access private resource denied)
[????????] x11 video output notice: buggy X11 server claims shared memory
[????????] x11 video output notice: support though it does not work (OpenSSH?)
[????????] x11 video output error: X11 request 143.1 failed with error code 10:
 BadAccess (attempt to access private resource denied)
[????????] x11 video output notice: buggy X11 server claims shared memory
[????????] x11 video output notice: support though it does not work (OpenSSH?)
[????????] x11 video output error: X11 request 143.1 failed with error code 10:
 BadAccess (attempt to access private resource denied)
[????????] x11 video output notice: buggy X11 server claims shared memory
[????????] x11 video output notice: support though it does not work (OpenSSH?)
[????????] x11 video output error: X11 request 143.1 failed with error code 10:
 BadAccess (attempt to access private resource denied)
[????????] x11 video output notice: buggy X11 server claims shared memory
[????????] x11 video output notice: support though it does not work (OpenSSH?)
[????????] x11 video output error: X11 request 132.19 failed with error code 160:
 BadShmSeg (invalid shared segment parameter)
X Error of failed request:  BadShmSeg (invalid shared segment parameter)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Segment id in failed request:  0x460000b
  Serial number of failed request:  83
  Current serial number in output stream:  84

But on standalone system the video files are playing fine.

Thanks

---

### Post by pravindra.kumar on 2010-08-05
Hi,
It's solved by installing "gxine"

Code :
$sudo apt-get install gxine

---

