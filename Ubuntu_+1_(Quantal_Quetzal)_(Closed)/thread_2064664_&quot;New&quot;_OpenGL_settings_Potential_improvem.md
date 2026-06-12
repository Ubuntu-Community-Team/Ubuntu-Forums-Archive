---
title: "&quot;New&quot; OpenGL settings: Potential improvement vs. performance decrease - Worth it?"
date: 2012-09-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-09-29
We had some new options showing up in CCSM / OpenGL a few updates before the latest milestone. On my hardware (all Nvidia), I see no visual improvement and a 70% cut in gtkperf results. Disabling them gets my gtkperf results back to normal, a snappier desktop, a faster Dash and a reasonably cooler GPU (and no glitches I can detect).

I'd like to know if others see improvement using these options.
(IMO, it would be wise for owners of older / less powerful GPUs) to try disabling them if they experience a significant decrease in performance, a hotter GPU, fans running more than usual, etc). 


**CCSM / OpenGL:** 

> **Sync to VBlank** (Old setting, of course, but now is enabled by default)
The switch is apparently not working here. Switching it in nvidia-settings /  OpenGL Settings works. Tested by switching in each interface and running glxgears. On or off, I get no visual improvement or problem, only a decrease of about 30% in gtkperf and a much less snappier desktop in general.

**Framebuffer Object** (Enabled by Default)
Here's the official description: "Render all frames indirectly using framebuffer objects (GL_EXT_framebuffer_object), if supported by the driver. Pros: Might be faster than the default buffer swapping method in some cases. Cons: **This will come at the cost of (1) usually reduced graphics benchmark performance; (2) increased GPU resource consumption; and (3) possibly higher visible lag.** Note: This feature is always on in OpenGL|ES builds such as ARM platforms". 

**Vertex Buffer Object** (Enabled by Default)
Official description: "Render all graphics primitives using vertex buffer objects (GL_ARB_vertex_buffer_object), if supported by the driver. Pros: This provides higher graphics performance for some drivers. Cons: This is a new feature and may cause graphical problems. Note: This feature is always on in OpenGL|ES builds such as ARM platforms."

**Always use Buffer Swapping** (Enabled by Default)
Official description: "Use glXSwapBuffers to display every frame. This eliminates visible tearing with most drivers and dramatically improves visual smoothness. Automatically enabled when framebuffer_object is on".
 
Regards,
Effenberg

**EDIT:** Just for reference, I'm not considering the impact of these options when indirect rendering via llvmpipe is used. I have tested using properly installed Nvidia drivers.

---

### Post by pqwoerituytrueiwoq on 2012-09-29
as long as it is optional it is always worth it

---

### Post by effenberg0x0 on 2012-09-29
It's not optional for ordinary users. It's a technical setting placed inside compizconfig-settings-manager and activated by default. 

It is not worth it for me: My performance is cut in half and I get a significant increase in GPU temperature in exchange for nothing.

But I'd like to know if other users can detect increase in performance or, maybe,  better visuals (eliminate tearing, better transitions, etc) by activating these.

Regards,
Effenberg

---

### Post by cariboo on 2012-09-29
I tried your suggestions, gtkperf now takes about ½ second less, 4.44 vs 3.92. I'll check out operations over the next couple of days.

---

### Post by effenberg0x0 on 2012-09-30
> **cariboo907 said:**
> I tried your suggestions, gtkperf now takes about ½ second less, 4.44 vs 3.92. I'll check out operations over the next couple of days.

I know glxgears is not a good benchmark but, anyway, enabling those options takes me from aprox. 12000.000FPS to aprox. 5000.000FPS. 

Another test: When enabled, I get a real slow Dash if playing 1080p video content. Disabling them (and restarting the session) allows me to watch HD video and use the Dash normally.

One other thing I noticed: Disabling those options makes the Dash blur disappear (I can't reactivate it to ON/SMART using any method). Not sure if it's a con or pro to me, I never liked the blur much, but it makes me think if maybe those settings are being used exclusively to fix Dash blur issues (I hope not). 

Here's the screenshot:
[ATTACH]224877[/ATTACH]

Regards,
Effenberg

---

### Post by VinDSL on 2012-09-30
Turned off all suggested settings.

Disabled "Sync to VBlank" in nVidia X server settings, too. Seems like it turns itself on every time I upgrade the drivers.  :-k

Everything is snappier now.  Dash is actually usable -- was horribly laggy before -- acted like I hadn't clicked the button.

Thanks!

---

### Post by effenberg0x0 on 2012-09-30
If you guys wanna try some other tweaks to chrome/chromium: 

- I'm back to using a ramdisk and --disk-cache-dir="/tmp/ram/ on /usr/share/applications/google-chrome.desktop. It seems to help a little.

- I'm also playing with settings in about:flags. Forcing GPU compositing in all pages seems to make things a little faster and lighhter on the CPU. 

Regards,
Effenberg

**EDIT:** I was also considering if it would be viable to use a bash script to scan all icon files and improve them (using ImageMagick or something). I'm under the impression the Dash is slowed down by loading these images if they are not improved in file size.

**EDIT 2:** This website slows down chrome/chromium as much as OMBUbuntu here: [http://get.webgl.org/](http://get.webgl.org/) . But it's a WebGL test, I think this is expected, to some degree.

**EDIT 3:** With VSync enabled, the Dash is always slow when glxgears is running in parallel. With VSync disabled, I see no diff in speed in the Dash with/without glxgears running in parallel.

---

### Post by VinDSL on 2012-09-30
> **effenberg0x0 said:**
> I know glxgears is not a good benchmark but, anyway, enabling those options takes me from aprox. 12000.000FPS to aprox. 5000.000FPS.
WoW!

(* Bear in mind, I'm running a GeForce 7600GT *)

Disabling those settings allowed me to go from 60 FPS => 3,000 FPS  :D

---

### Post by funicorn on 2012-09-30
Talking about profile mapping, I think profile-sync-daemon already does that. 

> **effenberg0x0 said:**
> If you guys wanna try some other tweaks to chrome/chromium: 

- I'm back to using a ramdisk and --disk-cache-dir="/tmp/ram/ on /usr/share/applications/google-chrome.desktop. It seems to help a little.

- I'm also playing with settings in about:flags. Forcing GPU compositing in all pages seems to make things a little faster and lighhter on the CPU. 

Regards,
Effenberg

**EDIT:** I was also considering if it would be viable to use a bash script to scan all icon files and improve them (using ImageMagick or something). I'm under the impression the Dash is slowed down by loading these images if they are not improved in file size.

---

### Post by effenberg0x0 on 2012-09-30
> **funicorn said:**
> Talking about profile mapping, I think profile-sync-daemon already does that.

Is it used in Ubuntu now? I was under the impression this was an Arch feature.

Regards,
Effenberg

---

### Post by dino99 on 2012-09-30
Test on a 8500gt + nouveau + default settings

gtkperf: 

GtkEntry - time:  0,02
GtkComboBox - time:  0,90
GtkComboBoxEntry - time:  0,48
GtkSpinButton - time:  0,08
GtkProgressBar - time:  0,07
GtkToggleButton - time:  0,39
GtkCheckButton - time:  0,08
GtkRadioButton - time:  0,13
GtkTextView - Add text - time:  0,38
GtkTextView - Scroll - time:  0,01
GtkDrawingArea - Lines - time:  0,72
GtkDrawingArea - Circles - time:  1,65
GtkDrawingArea - Text - time:  1,01
GtkDrawingArea - Pixbufs - time:  0,12
 --- 
Total time:  6,06

oem@dub:~$ glxgears
2185 frames in 5.0 seconds = 436.860 FPS
2288 frames in 5.0 seconds = 457.463 FPS
2280 frames in 5.0 seconds = 455.975 FPS
2255 frames in 5.0 seconds = 450.936 FPS



and with settings disabled (the 4 opengl)

GtkEntry - time:  0,03
GtkComboBox - time:  0,81
GtkComboBoxEntry - time:  0,51
GtkSpinButton - time:  0,09
GtkProgressBar - time:  0,07
GtkToggleButton - time:  0,39
GtkCheckButton - time:  0,08
GtkRadioButton - time:  0,13
GtkTextView - Add text - time:  0,34
GtkTextView - Scroll - time:  0,32
GtkDrawingArea - Lines - time:  0,66
GtkDrawingArea - Circles - time:  1,24
GtkDrawingArea - Text - time:  0,68
GtkDrawingArea - Pixbufs - time:  0,09
 --- 
Total time:  5,46


oem@dub:~$ glxgears
2007 frames in 5.0 seconds = 401.290 FPS
2269 frames in 5.0 seconds = 453.718 FPS
2253 frames in 5.0 seconds = 450.431 FPS
2276 frames in 5.0 seconds = 455.136 FPS
2286 frames in 5.0 seconds = 457.113 FPS
2296 frames in 5.0 seconds = 459.112 FPS

That is gtkperf is worst when settings are enabled

---

### Post by funicorn on 2012-09-30
Not exactly. PSD is a universal bash daemon to map navigator profile into memory and sync it back to hard disk. It sure woks in Ubuntu.
> **effenberg0x0 said:**
> Is it used in Ubuntu now? I was under the impression this was an Arch feature.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-09-30
> **dino99 said:**
> Test on a 8500gt + nouveau + default settings

gtkperf: 

GtkEntry - time:  0,02
GtkComboBox - time:  0,90
GtkComboBoxEntry - time:  0,48
GtkSpinButton - time:  0,08
GtkProgressBar - time:  0,07
GtkToggleButton - time:  0,39
GtkCheckButton - time:  0,08
GtkRadioButton - time:  0,13
GtkTextView - Add text - time:  0,38
GtkTextView - Scroll - time:  0,01
GtkDrawingArea - Lines - time:  0,72
GtkDrawingArea - Circles - time:  1,65
GtkDrawingArea - Text - time:  1,01
GtkDrawingArea - Pixbufs - time:  0,12
 --- 
Total time:  6,06

oem@dub:~$ glxgears
2185 frames in 5.0 seconds = 436.860 FPS
2288 frames in 5.0 seconds = 457.463 FPS
2280 frames in 5.0 seconds = 455.975 FPS
2255 frames in 5.0 seconds = 450.936 FPS



and with settings disabled (the 4 opengl)

GtkEntry - time:  0,03
GtkComboBox - time:  0,81
GtkComboBoxEntry - time:  0,51
GtkSpinButton - time:  0,09
GtkProgressBar - time:  0,07
GtkToggleButton - time:  0,39
GtkCheckButton - time:  0,08
GtkRadioButton - time:  0,13
GtkTextView - Add text - time:  0,34
GtkTextView - Scroll - time:  0,32
GtkDrawingArea - Lines - time:  0,66
GtkDrawingArea - Circles - time:  1,24
GtkDrawingArea - Text - time:  0,68
GtkDrawingArea - Pixbufs - time:  0,09
 --- 
Total time:  5,46


oem@dub:~$ glxgears
2007 frames in 5.0 seconds = 401.290 FPS
2269 frames in 5.0 seconds = 453.718 FPS
2253 frames in 5.0 seconds = 450.431 FPS
2276 frames in 5.0 seconds = 455.136 FPS
2286 frames in 5.0 seconds = 457.113 FPS
2296 frames in 5.0 seconds = 459.112 FPS

That is gtkperf is worst when settings are enabled

dino99, thanks for helping test this. I just wanted to point out that for gtkperf, less is better. Therefore your results show a &#8771; 10% improvement in gtkperf when the settings are disabled. 

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-09-30
> **funicorn said:**
> Not exactly. PSD is a universal bash daemon to map navigator profile into memory and sync it back to hard disk. It sure woks in Ubuntu.

I'll give it a try. I checked git and an update to make it independent of arch init scripts was pushed some months ago, I couldn't find a package in Ubuntu repos though. If it doesn't have any significant downside it should be considered as a package for Ubuntu.

Regards,
Effenberg

---

### Post by jerrylamos on 2012-09-30
How are these OpenGL settings done?  What keystrokes are required?  I looked in Dash and System Settings and couldn't see what to do.  apt-get install ccsm package not found.

Thanks.

---

### Post by effenberg0x0 on 2012-09-30
> **jerrylamos said:**
> How are these OpenGL settings done?  What keystrokes are required?  I looked in Dash and System Settings and couldn't see what to do.  apt-get install ccsm package not found.

Thanks.

Hi Jerry, ccsm is in package "compizconfig-settings-daemon"
```
sudo apt-get install compizconfig-settings-manager
```
Then at Dash / ccsm, Go to the "OpenGL" Plugin and you'll find them.

I think once you change any of them you gotta restart to see any effect in benchmarks.

Regards,
Effenberg

**EDIT:** Except for VSync which, at least when using Nvidia hw and drivers, can't be disabled in CCSM anymore according to my tests. You gotta go to Dash / nvidia-settings / OpenGL Settings to enable / disable it (and there's no need to restart after changing this one).

---

### Post by x-shaney-x on 2012-09-30
Using Intel gfx (on Core i5) I don't see any difference whatsoever performance-wise (unity 12.10 runs like a pig regardless), just the opaque dash background as mentioned before.

---

### Post by effenberg0x0 on 2012-09-30
> **x-shaney-x said:**
> Using Intel gfx (on Core i5) I don't see any difference whatsoever performance-wise (unity 12.10 runs like a pig regardless), just the opaque dash background as mentioned before.

I'm not sure how those settings work on other GPU then Nvidia. I think Intel runs with VSync enabled by default unless you launch programs with an env var to disable it if I'm not mistaken. 

The Dash/Desktop is currently faster here on a Intel i5 laptop with Intel GPU and PP then on a AMD Phenom II desktop with a NVidia GPU and QQ (with or without the tweaks mentioned in this thread). 

But, anyway, disabling those settings really makes my desktop normal and usable on QQ+Nvidia. I think there's something wrong with them right now and they are enabled by default for all users.  That's bad.

Regards,
Effenberg

---

### Post by VinDSL on 2012-10-02
_UPDATE_

After 2 days of running "disabled", I noted some occasional smearing & artifacts hanging around... under certain conditions.

As a lark, I "enabled" buffer swapping in CCSM.

No more strange behavior, and everything is more responsive than before!


Here are some test results.  Not bad for a GeForce 7600GT...
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-2-oct-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-2-oct-2012-1.png")[/INDENT]


And, here are the CCSM settings...
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-2-oct-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-2-oct-2012-2.png")[/INDENT]


These changes made a huge difference in performance!  Thanks!

---

### Post by effenberg0x0 on 2012-10-03
> **VinDSL said:**
> _UPDATE_

After 2 days of running "disabled", I noted some occasional smearing & artifacts hanging around... under certain conditions.

As a lark, I "enabled" buffer swapping in CCSM.

No more strange behavior, and everything is more responsive than before!


Here are some test results.  Not bad for a GeForce 7600GT...
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-2-oct-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-2-oct-2012-1.png")[/INDENT]

And, here are the CCSM settings...
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-2-oct-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-2-oct-2012-2.png")[/INDENT]


These changes made a huge difference in performance!  Thanks!

Hey Vin, I'm using "Vertex Buffer Object" and "Use Buffer Swapping" but Vsync and "Frame Buffer object" are disabled. These last two cut my gtkperf/glxgears performance by half and provide me no noticeable improvement. The first two compromise performance slightly smoother (although slower) transition and a tearing/artifact free experience.

OBS: Do you notice any screen corruption when loading lightdm and right after you fill in  your password and press enter (before the Unity desktop loads)? I'm seeing complete art-deco screens for 2 to 5 seconds before the desktop shows normally with these settings (not all the times I login though, It's erratic - hard to debug or report).

Regards,
Effenberg

---

### Post by cariboo on 2012-10-03
I've been running with effenberg0x0's suggestions, and the only thing I've noticed is some weirdness in chromium,, where the previous page partially shows, after going back to an index page. Of course if I take a screenshot, everything looks as it should. :)

---

### Post by effenberg0x0 on 2012-10-03
> **cariboo907 said:**
> I've been running with effenberg0x0's suggestions, and the only thing I've noticed is some weirdness in chromium,, where the previous page partially shows, after going back to an index page. Of course if I take a screenshot, everything looks as it should. :)

Cariboo, is the Dash just as responsive with or without those settings enabled for you? I can see a very noticeable improvement when I disable them, or at least VSync and "Framebuffer Object". 

By the way, I'm not sure yet but there seems to be some problem with dual monitors and NVidia's Dynamic Twinview (which is applied by default when you have more than one monitor) and those settings, that causes some lag in OpenGL, including the Dash.

Regards,
Effenberg

---

### Post by P-I H on 2012-10-03
I removed all settings. 
Performance got a lot better, but I got a lot of tearing in XBMC. That disappeared when I set "sync to vblank".
When I move around windows, some parts remains on the display for a very short period.

---

### Post by VinDSL on 2012-10-03
> **cariboo907 said:**
> I've been running with effenberg0x0's suggestions, and the only thing I've noticed is some weirdness in chromium,, where the **[COLOR="DarkRed"]previous page partially shows[/COLOR]**, after going back to an index page.[...]
Yes, exactly!  Thank you!

I was struggling to find the right words to describe the situation, and "artifacts" popped into my head.  :D

I've also noticed "artifacts" in things other than Chromium.  For instance, when I'm banging out code...

I might have 2-3 instances of the file manager running, 5-6 instances of the text editor (some with root auth), 4-5 terminals open, blah, blah, blah, all in the same user workspace, e.g. same desktop.  

As I switch back n' forth between all of these windows, sometimes they don't totally disappear into the background.  Some of the time, "artifacts" of the inactive windows are still visible in the active window.

I haven't had this reoccur, since I enabled "Always use buffer swapping" in CCSM. Dittos for Chromium...  ;)

---

### Post by VinDSL on 2012-10-03
> **P-I H said:**
> I removed all settings.
 
Performance got a lot better, but I got a lot of **[COLOR="DarkRed"]tearing[/COLOR]** in XBMC.[...]

When I move around windows, some **[COLOR="DarkRed"]parts remains on the display[/COLOR]** for a very short period.
Again... I used the words "smearing" & "artifacts" to describe these situations.

All of us are experiencing the same problem(s), eh what? We're just using different terms of art.

Interesting!

**EDIT**

In case you didn't read the above reply...  ;)

I haven't had these reoccur, since I enabled "Always use buffer swapping" in CCSM.


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-2-oct-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-2-oct-2012-2.png")[/INDENT]

---

### Post by VinDSL on 2012-10-03
> **effenberg0x0 said:**
> OBS: Do you notice any screen corruption when loading lightdm and right after you fill in  your password and press enter (before the Unity desktop loads)?

I'm seeing complete art-deco screens for 2 to 5 seconds before the desktop shows normally with these settings (not all the times I login though, It's erratic - hard to debug or report).
Yes n' no!  LoL!  :D

I *think* they added the "art-deco" effect, a day or two ago.  However, on my machine, the "art-deco" effect stays inside the login box after you press [Enter].

From your description, it sounds like this effect is mirgrating outside the boundaries of the login box, and corrupting the whole screen.

If this is the case, then yes, a bug report would be warranted...  ;)

---

### Post by Milos_SD on 2012-10-03
@VinDSL: I see that you have 7600GT card like I do. Do you have problems with black windows, frozen video when you go fullscreen or enlarge a video window? I had that problem back in beta of 12.04, and then, few days after final release, it was fixed with some update. Now on 12.10 beta, I have it again. :( Back in 12.04 beta, it started to do that when I changed monitors, from 17" 1280x1024 to 23" 1920x1080. So I guess there is some video memory leak or some debuging thing going on.

---

### Post by mgmiller on 2012-10-03
> **VinDSL said:**
> WoW!

(* Bear in mind, I'm running a GeForce 7600GT *)

Disabling those settings allowed me to go from 60 FPS => 3,000 FPS  :D

That was because you disabled sync to v blank.  That setting forces the system to run at the monitor refresh rate.

If you re-enable the other settings, but leave sync to v blank disabled, you should still see the higher frame rates.

I prefer to leave it on as it eliminates tearing in videos and other full screen windows.  I only disable it when playing games like UT2K4.

Although supposedly, the tearing is now controlled by enabling the vertex buffer and always use buffer swapping.

In fact, it is only the sync to v blank setting in the nvidia driver that effects this.  I just tried turning it off in the driver, but leaving it on in the ccsm settings and my glx gears went from 60 fps to 14,500.

By leaving it on in ccsm and off in the driver, I can get my nice smooth full screen video with no tearing and I get good frame rates in the game.  Sweet!

---

### Post by cariboo on 2012-10-03
> **effenberg0x0 said:**
> Cariboo, is the Dash just as responsive with or without those settings enabled for you? I can see a very noticeable improvement when I disable them, or at least VSync and "Framebuffer Object". 

By the way, I'm not sure yet but there seems to be some problem with dual monitors and NVidia's Dynamic Twinview (which is applied by default when you have more than one monitor) and those settings, that causes some lag in OpenGL, including the Dash.

Regards,
Effenberg

The dash, and everything else are definitely faster, than before the changes.

```
cariboo@alexis:~$ glxgears
4426 frames in 5.0 seconds = 885.042 FPS
4753 frames in 5.0 seconds = 950.431 FPS
4756 frames in 5.0 seconds = 951.048 FPS
4767 frames in 5.0 seconds = 953.287 FPS
4756 frames in 5.0 seconds = 951.180 FPS
4726 frames in 5.0 seconds = 945.179 FPS
```

the above resiult is with sync to Vblank turned off, and this is the result with it turned on:

```
cariboo@alexis:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
294 frames in 5.0 seconds = 58.784 FPS
300 frames in 5.0 seconds = 59.949 FPS
300 frames in 5.0 seconds = 59.949 FPS
300 frames in 5.0 seconds = 59.932 FPS
300 frames in 5.0 seconds = 59.965 FPS
300 frames in 5.0 seconds = 59.949 FPS
299 frames in 5.0 seconds = 59.733 FPS
```

---

### Post by dino99 on 2012-10-03
That is a huge difference ;)

As some tweakings have been made, a report should be usefull to reset some options instead of turning them all on. Seems we have made all the same conclusion about disabling these options and looks not affecting recent hardware but all the oldies.

---

### Post by jfernyhough on 2012-10-03
Uh, if you have sync to VBLANK turned on then the frame rate will match your monitor refresh rate. That's what it's supposed to do. ;)

---

### Post by VinDSL on 2012-10-03
> **Milos_SD said:**
> @VinDSL: I see that you have 7600GT card like I do. 

Do you have problems with black windows, frozen video when you go fullscreen or enlarge a video window? [...]
No, sorry!  None of the above.  Working fine here...  ;)

Here's my setup, as of Sunday (I'm on the trot today).

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.9.30 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Installed PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo  && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 12.9.30 (vindsl.com) ~
Current Date/Time: Sun Sep 30 08:54:32 MST 2012
Distro Release: Ubuntu quantal (development branch)
Kernel Release: Linux 3.6.0-030600rc7-generic
Unity Release: unity 6.6.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.51

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch
  Installed: 2:1.13.0+git20120920.70e57668-0ubuntu0ricotz

Installed PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 
```


Here's the little monster, in action...  LoL!  :D

The heat pipes (and 80mm case fan) make it run a LOT cooler than the OEM reference fan.  

Maybe that's the difference!?!? 

I live in Arizona -- need all the cooling I can get!


[IMG]http://vindsl.com/images/nmb-case-fan.png[/IMG]

---

### Post by effenberg0x0 on 2012-10-03
Just to clarify things, I mentioned disabling "Sync to VBlank"   because:

- With Sync to VBlank enabled, glxgears will always report the monitor refresh rate (&#8771;60). Disabling it naturally provides a higher FPS, which is a normal and expected result. 

- Therefore it would be impossible to see any increase/decrease in the results of glxgears when enabling/disabling the *new* options in CCSM without first disabling Sync to VBlank.

- Disabling Sync caused some tearing and artifacts in the past for some users / cards. It seems like we can disable it now and still have a better and probably tearing free experience, if some of the other options are enabled. Right now, I don't see a need to enable VSync when playing HD content via 3 simultaneous instances of xbmc (using Buffer Swapping). 

- But, on the other hand, enabling all the mentioned options (as is the default when Ubuntu is installed) creates a significant impact in performance (responsiveness of the Dash and desktop windows, glxgears, gtkperf) and provides no benefits I could notice. 

Considering these settings are not accessible by ordinary users and are enabled by default (so far in the development process): Does it really make sense to have them all enabled in Quantal Release?

Right now it doesn't look like that to me. Let's take under consideration that many early adopters already complain about the Unity DE and Dash being heavy on resources and slow. We will see that multiply after release. Whatever we can do to improve that experience should be considered now.

Regards,
Effenberg

---

### Post by mc4man on 2012-10-03
> **dino99 said:**
>  Seems we have made all the same conclusion about disabling these options and looks not affecting recent hardware but all the oldies.
Those options do seem to have different results if disabled, in whole or part depending on hardware & possibly driver in use. 
(at least here vsync option in compiz is irrelevant, have absolutely no tearing here with vsync enabled in driver & the 'Always use buffer swapping' in a Unity session

So on a 8400m, nouveau, any Actual gain in use by disabling those options is far out weighed by video display issues inc. mentioned window deco remaining on screen for a moment when moving window quickly & other possible bad behavior, alot related to Dash & blur options
(currently all 3 blur options have faults, active blur is the least affected

---

### Post by effenberg0x0 on 2012-10-03
Maybe having those options enabled as a default is necessary because of llvmpipe?

Regards,
Effenberg

---

### Post by mc4man on 2012-10-03
> **effenberg0x0 said:**
> Maybe having those options enabled as a default is necessary because of llvmpipe?

Regards,
Effenberg
Not 100% sure but at least here the 1st.indication of slightly reduced overall perf (in actual use), came after the GLES branch merge in compiz, seen here (note the extensive changes
[http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/quantal/compiz/quantal/revision/3277](http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/quantal/compiz/quantal/revision/3277)

Taking a look at one file you can see those 3 added
[http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/quantal/compiz/quantal/revision/3277#plugins/opengl/opengl.xml.in](http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/quantal/compiz/quantal/revision/3277#plugins/opengl/opengl.xml.in)

Again here there has been some improvement from before with the most recent compiz upgrade (on a fresh daily from post beta2

---

### Post by VinDSL on 2012-10-03
> **effenberg0x0 said:**
> Considering these settings are not accessible by ordinary users and are enabled by default (so far in the development process): Does it really make sense to have them all enabled in Quantal Release?

Right now it doesn't look like that to me.
Agreed!

Look, I consider myself to be an "ordinary user", in a lot of ways.

Right now, I'm watching...
[LIST]
[*]The "First Presidential Debate" live, so called
[*]Playing a Deadmau5 video, on my YouTube channel
[*]Listening to an Alex Jones Podcast in Banshee
[/LIST]
Just "ordinary" activities...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-3-oct-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-oct-2012-1.png")[/INDENT]


I don't have any tearing, artifacts, lagginess... nothing.  No audio/video display issues. Everything is working like a charm!

IMO, it's a big mistake having all that stuff enabled! In order to what?!?!? Have a transparent Dash? A paisley password box?

It pulls the whole system down...

---

### Post by funicorn on 2012-10-04
@VinDSL, what icon theme are you using ? That seems cool.

---

### Post by VinDSL on 2012-10-04
> **funicorn said:**
> @VinDSL, what icon theme are you using ? That seems cool.
Any Color You Like 0.9.4 (aka ACYL)

---

### Post by balloons on 2012-10-16
I'll note performance is a funny thing -- sometimes changing options to have something feel faster actually makes it slower (but what do you care, it feels faster right?). The sync to vblank is an obvious one for any gamer. Turn it off first thing.. If your a hardcore gamer though, instead you buy a nice card, 120hz monitor, and turn it on. It's critical for proper gameplay :-)

The unity team described the changes as a meeting in the middle. For some performance would be worse, others it would be better. But overall, it would be predictable and "correct". And they valued that over any small performance loss.

---

### Post by effenberg0x0 on 2012-10-16
> **guitara said:**
> I'll note performance is a funny thing -- sometimes changing options to have something feel faster actually makes it slower (but what do you care, it feels faster right?). The sync to vblank is an obvious one for any gamer. Turn it off first thing.. If your a hardcore gamer though, instead you buy a nice card, 120hz monitor, and turn it on. It's critical for proper gameplay :-)

The unity team described the changes as a meeting in the middle. For some performance would be worse, others it would be better. But overall, it would be predictable and "correct". And they valued that over any small performance loss.

Disregarding Sync to VBlank, which is known to all of us, the other settings cut my performance in more than half and produce more artifacts and graphics errors (that do not occur when they are disabled). I have now tested with GTS450, GT9500, GT9800. The Dash is unusable in high-end hardware with these cards and these options enabled. 

I can understand their long-term goals, but IMO these options are not ready for 12.10 and should be disabled by default. That would be the safest strategy, which we know will not be the one chosen. Instead we will see Ubuntu once again burn it's branding in release week and before with all support forums, blogs, etc globally complaining about the drop in graphics performance and suggesting workarounds.

That's just the way it is and has been for the last releases. No change in that.

Regards,
Effenberg

---

### Post by mc4man on 2012-10-17
> **effenberg0x0 said:**
> . 

I can understand their long-term goals, but IMO these options are not ready for 12.10 and should be disabled by default. 
Part of an issue there may be those settings, all or most, may provide better performance when using open source drivers, I certainly can see that here.
With nouveau -  disabling them causes noticeably  poorer performance and much greater chance of various artifacts, ect.
With them enabled  for the most part things run smoothly  - I can cause issues with the Dash thru certain actions & overall 12.10 is 'slower' than 12.04 with or without those options, nouveau or nvidia
(but then compiz 0.9.x is slower than 0.8 in many areas

I think they need to base their defaults on what's best for the open source drivers, whether my experience is widespread or an 'exception' no clue though I'm also not sure of the testing base hardware wise for those making these decisions..

---

### Post by effenberg0x0 on 2012-10-17
> **mc4man said:**
> Part of an issue there may be those settings, all or most, may provide better performance when using open source drivers, I certainly can see that here.
With nouveau -  disabling them causes noticeably  poorer performance and much greater chance of various artifacts, ect.
With them enabled  for the most part things run smoothly  - I can cause issues with the Dash thru certain actions & overall 12.10 is 'slower' than 12.04 with or without those options, nouveau or nvidia
(but then compiz 0.9.x is slower than 0.8 in many areas

I think they need to base their defaults on what's best for the open source drivers, whether my experience is widespread or an 'exception' no clue though I'm also not sure of the testing base hardware wise for those making these decisions..

You have a good point. I have never adopted Nouveau as default in my installs, maybe it makes sense for Nouveau users. I have tested these options a lot when using the proprietary driver in some different cards and IMO it doesn't look good so far. I'm willing to bet we will have problems in release week and after that. The impact on the Dash responsiveness is really noticeable. 

Maybe these options should be enabled if Nouveau is loaded and disabled if nvidia-proprietary is loaded. Not hard at all programatically.

Regards,
Effenberg

---

### Post by mc4man on 2012-10-17
I've only gone to nouveau on this older (4yr.) laptop, 8400m, because the nvidia drivers in conjunction with compiz-0.9.x have just continued to get worse & worse while nouveau has gone from unusable to very good in 12.10 though it is not without some issues.

Whether this is due to nvidia drivers, compiz-0.9, or both is quite hard to tell as I can't test older nvidia in newer X though in past Windows days I never assumed newer nvidia releases were a given to be better for hardware in hand.
(and to some extent in Windows one has a bit more choice as to driver to use & as I remember on laptops I just stuck to vendor supplied nvidia drivers/updates

If I was to get a new laptop, (not currently possible), I'd have to take a hard look at Not getting nvidia where as in the past it was a no-brainer (as far as linux/Ubuntu.

If I was to get a new desktop then probably would still stick with nvidia & adjust as needed as you've done.
I'd guess that there wouldn't be much interest in changing compiz options based on driver even if it made complete sense
(is there actually any way to alter those options except initially  thru ccsm??
Maybe an override?

---

