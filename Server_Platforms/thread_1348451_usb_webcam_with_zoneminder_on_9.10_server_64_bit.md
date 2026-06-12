---
title: "usb webcam with zoneminder on 9.10 server 64 bit"
date: 2009-12-07
forum: Server Platforms
---

### Post by juanbill on 2009-12-07
usb webcam with zoneminder on 9.10 server 64 bit
 

Hi:

I followed this instruction to install zoneminder 
[http://www.zoneminder.com/forums/viewtopic.php?t=14819](http://www.zoneminder.com/forums/viewtopic.php?t=14819)

The problem is i am unable to view any video.

I have difficult to fix the problem as I'm using a server 
edition and alot of recommendations require gui programs. 

I wanted to know if the server edition have 
v4l1/v4l2 drivers installed by default? 

Are there command line ways to query the camera. 

I have used zmu from zoneminder to query the camera 
and my errors 

are

:/usr/lib# zmu -d /dev/video0 -q -v
12/08/09 00:21:40.104844 zmu[-1].INF-zm_debug.c/224 [Debug Level = 9, Debug Log = <none>]
12/08/09 00:21:40.112627 zmu[-1].ERR-zm_local_camera.cpp/913 [Failed to query crop: Invalid argument]
Error, failed to query crop /dev/video0: Invalid argument

any help is greatly appreciated. 

here is printout of syslog:

Dec  8 00:07:29 zeus zmc_dvideo0[2384]: INF [Debug Level = 0, Debug Log = <none>]
Dec  8 00:07:29 zeus zmc_dvideo0[2384]: INF [Starting Capture]
Dec  8 00:07:29 zeus zmc_dvideo0[2384]: ERR [Failed to set picture attributes: Invalid argument]
Dec  8 00:07:29 zeus zmdc[1380]: ERR ['zmc -d /dev/video0' exited abnormally, exit status 255]


thanks

---

### Post by alexthunder on 2010-05-03
see 
[http://stream-recorder.com/forum/zmu-d-dev-video0-q-v-error-t6516.html](http://stream-recorder.com/forum/zmu-d-dev-video0-q-v-error-t6516.html)
(usb webcam with zoneminder on ubuntu 10.04)

haven't tried to change the source code... and it doesn't seem to work in some cases

---

