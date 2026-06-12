---
title: "How to show if you are running a Wayland or X11 Session"
date: 2017-10-28
forum: Ubuntu Development Version
---

### Post by #&amp;thj^% on 2017-10-28
This seems to be very confusing for some still..so I'm going to add a few methods to show if you are running a Wayland/Gnome session or X11/Gnome session.
These I have found from other sites but work well here with Ubuntu.
1.```
$ echo $XDG_SESSION_TYPE
```
Should show either a "wayland or X11"
2.Or this even:
```
loginctl show-session $(loginctl | grep $(whoami) | awk '{print $1}') -p Type
```
And this from Fedora...Works here also:

```
loginctl show-session <YOUR_NUMBER> -p Type
```

**The number to pass in is the one you get by issuing just**

```
loginctl
```

So, for me it is:

```
loginctl show-session 2 -p Type                                                  
Type=wayland
```

Hope this is useful to someone! :)
And Happy buntuing

---

### Post by jbicha on 2017-10-28
Here are a [few more ways]("https://askubuntu.com/questions/904940/how-can-i-tell-if-i-am-running-wayland/968772").

---

### Post by VMC on 2017-10-28
> **1fallen said:**
> This seems to be very confusing for some still..so I'm going to add a few methods to show if you are running a Wayland/Gnome session or X11/Gnome session.
These I have found from other sites but work well here with Ubuntu.
1.```
$ echo $XDG_SESSION_TYPE
```
Should show either a "wayland or X11"
2.Or this even:
```
loginctl show-session $(loginctl | grep $(whoami) | awk '{print $1}') -p Type
```
And this from Fedora...Works here also:

```
loginctl show-session <YOUR_NUMBER> -p Type
```

**The number to pass in is the one you get by issuing just**

```
loginctl
```

So, for me it is:

```
loginctl show-session 2 -p Type                                                  
Type=wayland
```

Hope this is useful to someone! :)
And Happy buntuingIt was helpful to me. I installed Arch on another partition and was thinking about this.

---

### Post by ventrical on 2017-10-28
Or my favorite- less keystrokes ;)

```

inxi -Fxz

Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: wayland (X.Org 1.19.5 ) driver: i915
           Resolution: 1440x900@59.75hz
           OpenGL: renderer: Mesa DRI Intel Haswell Desktop
           version: 4.5 Mesa 17.2.2 Direct Render: Yes

```

---

