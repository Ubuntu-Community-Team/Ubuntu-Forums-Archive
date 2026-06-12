---
title: "vlc &amp; just checking"
date: 2014-10-14
forum: Ubuntu Development Version
---

### Post by mc4man on 2014-10-14
I no longer have 14.10 but am curious if there are still issues with 14.10's vlc version with some http(s) streams. If not I'll close report, if there are will push on.
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1364186](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1364186)
4 Ex. streams in report - 2 ex.
```
vlc http://s3.amazonaws.com/akamai.netstorage/HD_downloads/Orion_SM.mp4

```
```
vlc https://www.youtube.com/watch?v=p6vq-cOAi0Y
```

---

### Post by zika on 2014-10-14
```
:~$ vlc --versionVLC media player 2.2.0-pre2 Weatherwax (revision 2.2.0-pre1-15-g5178b24)
VLC version 2.2.0-pre2 Weatherwax (2.2.0-pre1-15-g5178b24)
Compiled by buildd on kapok.buildd (Sep  5 2014 01:57:42)
Compiler: gcc version 4.9.1 (Ubuntu 4.9.1-10ubuntu2)
This program comes with NO WARRANTY, to the extent permitted by law.
You may redistribute it under the terms of the GNU General Public License;
see the file named COPYING for details.
Written by the VideoLAN team; see the AUTHORS file.
``````
:~$ vlc http://s3.amazonaws.com/akamai.netstorage/HD_downloads/Orion_SM.mp4
VLC media player 2.2.0-pre2 Weatherwax (revision 2.2.0-pre1-15-g5178b24)
[00000000009bc018] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
"sni-qt/8587" WARN  17:50:57.100 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 
[00007f9f10039ba8] avcodec decoder: Using G3DVL VDPAU Driver Shared Library version 1.0 for hardware decoding.
[00007f9f0c12f918] freetype spu text error: Breaking unbreakable line
[00007f9f10000e78] http access error: failed to read answer
[00007f9f10000e78] http access error: seek failed
``````
:~$ cvlc http://s3.amazonaws.com/akamai.netstorage/HD_downloads/Orion_SM.mp4
VLC media player 2.2.0-pre2 Weatherwax (revision 2.2.0-pre1-15-g5178b24)
[0000000000e3d288] dummy interface: using the dummy interface module...
[00007f6524c36728] avcodec decoder: Using G3DVL VDPAU Driver Shared Library version 1.0 for hardware decoding.
[00007f651812fb58] freetype spu text error: Breaking unbreakable line
^C[00007f6524000e58] http access error: cannot connect to s3.amazonaws.com:80
[00007f6524000e58] http access error: seek failed
``````
:~$ vlc https://www.youtube.com/watch?v=p6vq-cOAi0Y
VLC media player 2.2.0-pre2 Weatherwax (revision 2.2.0-pre1-15-g5178b24)
[0000000000d68018] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
"sni-qt/13674" WARN  17:52:52.991 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 
[00007f0ef4059be8] gnutls tls session error: The TLS connection was non-properly terminated.
[00007f0ef4000e98] core access error: read error: Connection reset by peer
[0000000000d7c378] core playlist: stopping playback
[00007f0ed8dab708] avcodec decoder: Using G3DVL VDPAU Driver Shared Library version 1.0 for hardware decoding.
[00007f0ed80010b8] core access error: connection failed: Network is unreachable
[00007f0ed80010b8] http access error: cannot connect to r5---sn-4g57kuel.googlevideo.com:80
[00007f0ed80010b8] http access error: seek failed
``````
:~$ cvlc https://www.youtube.com/watch?v=p6vq-cOAi0Y
VLC media player 2.2.0-pre2 Weatherwax (revision 2.2.0-pre1-15-g5178b24)
[00000000019e2288] dummy interface: using the dummy interface module...
[00007f288c059de8] gnutls tls session error: The TLS connection was non-properly terminated.
[00007f288c000e88] core access error: read error: Connection reset by peer
[00000000019c6428] core playlist: stopping playback
[00007f288c1a0e48] avcodec decoder: Using G3DVL VDPAU Driver Shared Library version 1.0 for hardware decoding.
[00007f2888006408] core input error: ES_OUT_SET_(GROUP_)PCR  is called too late (jitter of 7991 ms ignored)
[00007f288c325288] core decoder error: Could not convert timestamp 0
[00007f2888006408] core input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 1045 ms)
[00007f2888006408] core input error: ES_OUT_RESET_PCR called
[00007f288c1a0e48] avcodec decoder: Using G3DVL VDPAU Driver Shared Library version 1.0 for hardware decoding.
[00007f2888006408] core input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 3746 ms)
[00007f2888006408] core input error: ES_OUT_RESET_PCR called
[00007f288c1a0e48] avcodec decoder: Using G3DVL VDPAU Driver Shared Library version 1.0 for hardware decoding.
[h264 @ 0x7f288c20c760] Missing reference picture
[h264 @ 0x7f288c20c760] decode_slice_header error
[h264 @ 0x7f288c20d900] mmco: unref short failure
[00007f288c05c188] core access error: read error: Connection reset by peer
[00007f288c05c188] http access error: failed to read answer
[00007f288c05c188] http access error: seek failed
```

---

