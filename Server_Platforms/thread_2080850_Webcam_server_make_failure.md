---
title: "Webcam server make failure"
date: 2012-11-05
forum: Server Platforms
---

### Post by UltraG33k on 2012-11-05
Hello!


I'm trying to install webcam-server on my server at home.
I got it configured but when I type "make" I get this:
```

Making all in src
make[1]: Entering directory `/home/metal/webcam_server-0.50/src'
gcc -DPACKAGE=\"webcam_server\" -DVERSION=\"0.50\" -DHAVE_FTIME=1 -DHAVE_INET_NTOA=1 -DHAVE_MALLOC=1 -DHAVE_MEMSET=1 -DHAVE_MUNMAP=1 -DHAVE_SELECT=1 -DHAVE_SOCKET=1 -DHAVE_STRCHR=1 -DHAVE_STRSTR=1 -DHAVE_UNISTD_H=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MMAP=1 -DHAVE_STRFTIME=1 -DHAVE_LIBPTHREAD=1 -DHAVE_ARPA_INET_H=1 -DHAVE_FCNTL_H=1 -DHAVE_NETINET_IN_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_SYS_IOCTL_H=1 -DHAVE_SYS_SOCKET_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_SYS_TIMEB_H=1 -DHAVE_UNISTD_H=1 -DSTDC_HEADERS=1 -DTIME_WITH_SYS_TIME=1 -DRETSIGTYPE=void  -I. -I.      -g -O2 -c camera.c
In file included from camera.c:26:0:
webcam_server.h:89:26: error: field 'vid_caps' has incomplete type
webcam_server.h:90:22: error: field 'vid_win' has incomplete type
webcam_server.h:91:23: error: field 'vid_pic' has incomplete type
webcam_server.h:92:20: error: field 'vid_mbuf' has incomplete type
webcam_server.h:93:20: error: field 'vid_v4lmmap' has incomplete type
webcam_server.h:99:6: warning: conflicting types for built-in function 'log' [enabled by default]
camera.c: In function 'set_cam_info':
camera.c:60:23: error: 'VIDIOCSPICT' undeclared (first use in this function)
camera.c:60:23: note: each undeclared identifier is reported only once for each function it appears in
camera.c:64:23: error: 'VIDIOCSWIN' undeclared (first use in this function)
camera.c: In function 'get_cam_info':
camera.c:73:21: error: 'VIDIOCGCAP' undeclared (first use in this function)
camera.c:78:21: error: 'VIDIOCGWIN' undeclared (first use in this function)
camera.c:83:21: error: 'VIDIOCGPICT' undeclared (first use in this function)
camera.c:88:21: error: 'VIDIOCGMBUF' undeclared (first use in this function)
camera.c: In function 'get_cam_image':
camera.c:148:25: error: 'VIDIOCMCAPTURE' undeclared (first use in this function)
camera.c:152:25: error: 'VIDIOCSYNC' undeclared (first use in this function)
make[1]: *** [camera.o] Error 1
make[1]: Leaving directory `/home/metal/webcam_server-0.50/src'
make: *** [all-recursive] Error 1

```

Anyone have an idea on what to fix this?

---

### Post by SeijiSensei on 2012-11-06
Just curious, but did you try the [package]("http://packages.ubuntu.com/lucid/webcam-server") in the Lucid repositories? It might work even though it appears that webcam-server itself is no longer being maintained.  Also, on that page it says webcam-server depends on libjpeg62.  You might need to install both that and the development package libjpeg62-dev.

---

### Post by SlugSlug on 2012-11-06
there is also a program called motion thats in the repo's 

You can use it as a webcam stream via webpage and it can also start to record if it detects motion

---

### Post by UltraG33k on 2012-11-06
> **SeijiSensei said:**
> Just curious, but did you try the [package]("http://packages.ubuntu.com/lucid/webcam-server") in the Lucid repositories? It might work even though it appears that webcam-server itself is no longer being maintained.  Also, on that page it says webcam-server depends on libjpeg62.  You might need to install both that and the development package libjpeg62-dev.

I did try that one. But even though I installed the dependencies it failed to install for some reason.

> **SlugSlug said:**
> there is also a program called motion thats in the repo's 

 You can use it as a webcam stream via webpage and it can also start to record if it detects motion

I will try that, thanks :)

---

### Post by SeijiSensei on 2012-11-06
Did you have libjpeg62-dev installed before you tried compiling? If not, try it again.

---

