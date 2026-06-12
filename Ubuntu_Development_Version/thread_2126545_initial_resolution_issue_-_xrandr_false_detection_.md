---
title: "initial resolution issue - xrandr false detection of second monitor"
date: 2013-03-17
forum: Ubuntu Development Version
---

### Post by cprofitt on 2013-03-17
I updated 13.04 today and ended up with two issues:

1.  On reboot two monitors were 'detected' though I only have one. 

2.  The initial resolution was improperly detected.

----

1.  I was able to 'deactivate' the second monitor

2.  After disabling the second monitor I was able to set the proper resolution -- however each boot results in the wrong resolution at the login screen... after login I get the proper resolution.

----
I searched launchpad and did not find any related bugs so I thought perhaps I was the only one to have experienced this issue -- anyone else? If yes, can someone point me to the bug report.

---- update ----
I did some more digging myself and I am seeing the following results:

```

Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 32767 x 32767
LVDS1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1680x1050      60.0*+   60.0     59.9     50.0  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected (normal left inverted right x axis y axis)
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DP1 disconnected (normal left inverted right x axis y axis)

```

There is no second monitor attached.

reported a [bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1156310") on this.

Thanks

---

### Post by deltasync on 2013-03-17
I have the same problem after last update ( mar 17 2013 ) in Ubuntu 13.04.

kernel details: Linux LnxServer 3.8.0-13-generic #22-Ubuntu SMP Fri Mar 15 17:51:30 UTC 2013 i686 i686 i686 GNU/Linux

---

### Post by laborg on 2013-03-18
Count me in. Looks like we have the same hardware T500 (using integrated intel card)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1156310](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1156310)

---

### Post by deltasync on 2013-03-20
> **laborg said:**
> Count me in. Looks like we have the same hardware T500 (using integrated intel card)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1156310](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1156310)

Yes, that seems to be the problem that we have ( i solved temporarily, returning to: Linux LnxServer 3.8.0-11-generic #20-Ubuntu SMP Tue Mar 5 20:33:22 UTC 2013 i686 i686 i686 GNU/Linux )

---

