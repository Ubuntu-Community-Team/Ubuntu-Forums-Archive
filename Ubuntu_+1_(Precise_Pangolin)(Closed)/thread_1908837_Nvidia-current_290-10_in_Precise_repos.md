---
title: "Nvidia-current 290-10 in Precise repos"
date: 2012-01-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2012-01-14
Nvidia-current_290.10 proprietary driver package is in the Precise repos now.

Note, that you should install it only if you use the xserver 1.10 (like the one in Precise repos).

However, if you have enabled additional PPA's and you have xserver 1.11 or xserver 1.12rc1, you should not install this nvidia-current. It would break the xserver.

If you have xserver 1.11, use the nvidia-current from xorg-edgers PPA and
if you have xserver 1.12rc1, use nvidia-current from Ricotz Unstable PPA.

---

### Post by shuttleworthwannabe on 2012-01-14
Harry, can you show me how to check what version of xserver and nvidia I am currently using--I saw this update while I was update/upgrade -ing this morning; so want o check if I will be affected?

Thanks

---

### Post by paul_in_london on 2012-01-14
> **shuttleworthwannabe said:**
> Harry, can you show me how to check what version of xserver and nvidia I am currently using--I saw this update while I was update/upgrade -ing this morning; so want o check if I will be affected?

Thanks

```
paul@precise-64:~$ less /var/log/Xorg.0.log
[   130.584] 
X.Org X Server 1.10.4
Release Date: 2011-08-19

```

```
paul@precise-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 290.10-0ubuntu1
  Candidate: 290.10-0ubuntu1
  Version table:
 *** 290.10-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
        100 /var/lib/dpkg/status
     290.10-0ubuntu1~xedgers~precise1 0
```

I inadvertently downgraded my xserver version last night. :(

---

### Post by shuttleworthwannabe on 2012-01-14
Thanks Paul--I have the same config as you do. I am safe.

Aside: in xserver, I want to set my scrolling speed using external USB mouse to 'slow'; at the moment the wheel scrolls more than I would estimate 6 clicks--I want it to scroll at 1 click at a time. Do you how to do this? Or have I missed the plot here?

SwB

---

### Post by paul_in_london on 2012-01-14
> **shuttleworthwannabe said:**
> Thanks Paul--I have the same config as you do. I am safe.

Aside: in xserver, I want to set my scrolling speed using external USB mouse to 'slow'; at the moment the wheel scrolls more than I would estimate 6 clicks--I want it to scroll at 1 click at a time. Do you how to do this? Or have I missed the plot here?

SwB

More recent xserver versions don't need an **/etc/X11/xorg.conf** file, but I think you should be able to do what you want by creating **/etc/X11/xorg.conf** if you don't already have one and then add (or edit) the **"InputDevice"** section. This may help get you started (not a definitive answer and I haven't done this myself, just the 1st link I went to):

[http://humanreadable.nfshost.com/sdeg/scroll-wheel-mouse.htm](http://humanreadable.nfshost.com/sdeg/scroll-wheel-mouse.htm)

EDIT: My wireless mouse has a scroll wheel, but I very rarely use it. :lolflag:

---

### Post by dino99 on 2012-01-14
Look at menu: System Settings Mouse

---

### Post by lucazade on 2012-01-14
I'm wondering if this 290 release will bring back the wayland hook (disabled in the past) and the giant memory leak.. anyone know about this?

---

### Post by mc4man on 2012-01-14
> **lucazade said:**
> I'm wondering if this 290 release will bring back the wayland hook (disabled in the past) and the giant memory leak.. anyone know about this?

If you are referring to the issues caused by [a gl enabled cairo ]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434")then it doesn't seem that will happen in 12.04 but would expect 12.10 to use & then either nvidia fixes or it doesn't but either way gl in cairo likely will remain

(though have seen mentioned that a gl enabled cairo wasn't totally necessary

---

### Post by lucazade on 2012-01-14
> **mc4man said:**
> If you are referring to the issues caused by [a gl enabled cairo ]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434")then it doesn't seem that will happen in 12.04 but would expect 12.10 to use & then either nvidia fixes or it doesn't but either way gl in cairo likely will remain

(though have seen mentioned that a gl enabled cairo wasn't totally necessary

exactly.. I was referring to that one.
good to know and thanks for the info :)

---

### Post by mc4man on 2012-01-14
While for the last 8 years or so have only used nvidia, much of that period was Xp, if I get something new may have to take a look at ati, or at least research specific nvidia. There are some things that just don't seem as good as previously here.
(though my current laptop has an admittedly crappy 8400m adapter.

For instance - after being online for several hours now I see this, vsync is enabled  - 
> :~$ /opt/VirtualGL/bin/glxspheres
Polygons in scene: 62464
Visual ID of window: 0x27
Context is Direct
OpenGL Renderer: GeForce 8400M GS/PCI/SSE2
20.242410 frames/sec - 22.590529 Mpixels/sec
18.313068 frames/sec - 20.437384 Mpixels/sec
17.967602 frames/sec - 20.051844 Mpixels/sec
19.790192 frames/sec - 22.085854 Mpixels/sec
19.144172 frames/sec - 21.364895 Mpixels/sec
20.653172 frames/sec - 22.867900 Mpixels/sec
16.476993 frames/sec - 16.366267 Mpixels/sec
14.468549 frames/sec - 14.371321 Mpixels/sec
17.677676 frames/sec - 18.555635 Mpixels/sec
11.882012 frames/sec - 13.260325 Mpixels/sec

After a log out/in back to expected - 
> 
:~$ /opt/VirtualGL/bin/glxspheres
Polygons in scene: 62464
Visual ID of window: 0x27
Context is Direct
OpenGL Renderer: GeForce 8400M GS/PCI/SSE2
56.300657 frames/sec - 62.831534 Mpixels/sec
59.893747 frames/sec - 66.841421 Mpixels/sec
59.868335 frames/sec - 66.813062 Mpixels/sec
58.413319 frames/sec - 61.145504 Mpixels/sec
59.883897 frames/sec - 59.481477 Mpixels/sec


Additionally - as far as h tearing in some videos which developed here in 11.10 
Using a small tear test video what I find interesting is - 
win7 - no tearing at all, ever
gnome-fallback, no effects - no tearing at all, ever
gnome-fallback with compiz - a very minor amount, likely not noticeable in actual playback
unity-3d - more than gnome-fallback/compiz, noticeable in some video scenes
unity-2d - awful

---

### Post by shuttleworthwannabe on 2012-01-14
> **dino99 said:**
> Look at menu: System Settings Mouse
Yup, I played around with the settings here--and also installed "Pointing devices"--it seemed to have set the right scrolling speed for the wheel.

Thanks

---

### Post by lucazade on 2012-01-14
Personally I would avoid both Intel and Ati.. Support and drivers are usually awful compared to Nvidia. 
I don't know what VirtualGL is and if that performance degradation is present only with a 8400 board but it is probably worth reporting it in the nvidia forum. They are usually proactive in listening this stuff.

---

### Post by paul_in_london on 2012-01-14
Yes, the thing that messed things up was that the updated version of nvidia-current superseded the xorg-edgers version and reintroduced a dependency on **[COLOR="Red"]xorg-video-abi-10[/COLOR]**: 

```
paul@precise-64:~$ apt-cache show nvidia-current | egrep -i "(xorg-video-abi|version)"
**[COLOR="Red"]Version: 290.10-0ubuntu1[/COLOR]**
Depends: x11-common (>= 1:7.0.0), make, sed (>> 3.0), dkms, linux-libc-dev, libc6-dev, linux-headers-generic | linux-headers, patch, acpid, libc6 (>= 2.2.5), libgcc1 (>= 1:4.1.1), libx11-6, libxext6, libxv1, libxvmc1, zlib1g (>= 1:1.1.4), **[COLOR="Red"]xorg-video-abi-10[/COLOR]**, xserver-xorg-core (>= 2:1.10.0-0ubuntu1~)
**[COLOR="Red"]Version: 290.10-0ubuntu1~xedgers~precise1[/COLOR]**
Depends: x11-common (>= 1:7.0.0), make, sed (>> 3.0), dkms, linux-libc-dev, libc6-dev, linux-headers-generic | linux-headers, patch, acpid, libc6 (>= 2.2.5), libgcc1 (>= 1:4.1.1), libx11-6, libxext6, libxv1, libxvmc1, zlib1g (>= 1:1.1.4), **[COLOR="Red"]xorg-video-abi-11[/COLOR]**, xserver-xorg-core (>= 2:1.10.99.901)
paul@precise-64:~$
```

What I ended up doing was purging xorg-edgers again (temporarily), removing nvidia-current and installing nvidia-current-updates from this ppa:

```
https://launchpad.net/~portis25/+archive/cnav
```

```
paul@precise-64:~$ apt-cache policy nvidia-current-updates
nvidia-current-updates:
  **[COLOR="Red"]Installed: 295.09-0[/COLOR]**
  Candidate: 295.09-0
  Version table:
 *** 295.09-0 0
        500 http://ppa.launchpad.net/portis25/cnav/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     290.10-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
```

The downside is that the xorg-video-abi dependencies are the same at the moment:

```
paul@precise-64:~$ apt-cache show nvidia-current-updates | egrep -i "(xorg-video-abi|version)"
**[COLOR="Red"]Version: 290.10-0ubuntu1[/COLOR]**
Depends: x11-common (>= 1:7.0.0), make, sed (>> 3.0), dkms, linux-libc-dev, libc6-dev, linux-headers-generic | linux-headers, patch, acpid, libc6 (>= 2.2.5), libgcc1 (>= 1:4.1.1), libx11-6, libxext6, libxv1, libxvmc1, zlib1g (>= 1:1.1.4), **[COLOR="Red"]xorg-video-abi-10[/COLOR]**, xserver-xorg-core (>= 2:1.10.0-0ubuntu1~)
**[COLOR="Red"]Version: 295.09-0[/COLOR]**
Depends: x11-common (>= 1:7.0.0), make, sed (>> 3.0), dkms, linux-libc-dev, libc6-dev, linux-headers-generic | linux-headers, patch, acpid, libc6 (>= 2.2.5), libgcc1 (>= 1:4.1.1), libx11-6, libxext6, libxv1, libxvmc1, zlib1g (>= 1:1.1.4), **[COLOR="Red"]xorg-video-abi-10[/COLOR]**, xserver-xorg-core (>= 2:1.10.0-0ubuntu1~)
paul@precise-64:~$
```

and

```
paul@precise-64:~$ apt-cache show xserver-xorg-core | egrep -i "(xorg-video-abi|version)"
**[COLOR="Red"]Version: 2:1.10.4-1ubuntu6[/COLOR]**
**[COLOR="Red"]Provides: xorg-input-abi-12, xorg-video-abi-10[/COLOR]**
**[COLOR="Red"]Version: 2:1.11.2.902+git20111209+server-1.11-branch.0ca8869e-0ubuntu0sarvatt[/COLOR]**
**[COLOR="Red"]Provides: xorg-input-abi-13, xorg-video-abi-11[/COLOR]**
paul@precise-64:~$
```

so after re-enabling xorg-edgers I'm stuck with:

```
paul@precise-64:~$ sudo aptitude full-upgrade                                   
The following packages will be upgraded: 
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse 
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse 
  xserver-xorg-video-ati xserver-xorg-video-fbdev xserver-xorg-video-intel 
  xserver-xorg-video-mach64 xserver-xorg-video-neomagic 
  xserver-xorg-video-nouveau xserver-xorg-video-r128 
  xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage 
  xserver-xorg-video-siliconmotion xserver-xorg-video-sisusb 
  xserver-xorg-video-tdfx xserver-xorg-video-trident 
  xserver-xorg-video-vesa xserver-xorg-video-vmware 
21 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/3,454 kB of archives. After unpacking 343 kB will be freed.
The following packages have unmet dependencies:
  nvidia-current-updates: Depends: xorg-video-abi-10 which is a virtual package.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     nvidia-current-updates      



Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
paul@precise-64:~$
```

because the candidate version of xserver-xorg-core from xorg-edgers "only" provides xorg-input-abi-11 and xorg-video-abi-13.

---

### Post by Harry33 on 2012-01-15
Xserver 1.10 series provides xorg-video-abi-10 and xorg-input-abi12
   so you need to have a nvidia-current that depends on xorg-video-abi-10

Xserver 1.11 series provides xorg-video-abi-11 and xorg-input-abi13
   so you need to have a nvidia-current that depends on xorg-video-abi-11

Xserver 1.12 branch provides xorg-video-abi-12 and xorg-input-abi16
   so you need to have a nvidia-current that depends on xorg-video-abi-12



The nvidia-graphics-drivers-updates (295.09) from the Mingmin Ren PPA only works with xserver 1.10 series.
For xserver 1.11 series, use Xorg-edgers PPA version.
For xserver 1.12 branch, use Ricotz Unstable PPA version.

Note, that also all input drivers must be installed accordingly.

---

### Post by paul_in_london on 2012-01-15
> **Harry33 said:**
> Xserver 1.10 series provides xorg-video-abi-10 and xorg-input-abi12
   so you need to have a nvidia-current that depends on xorg-video-abi-10

Xserver 1.11 series provides xorg-video-abi-11 and xorg-input-abi13
   so you need to have a nvidia-current that depends on xorg-video-abi-11

Xserver 1.12 branch provides xorg-video-abi-12 and xorg-input-abi16
   so you need to have a nvidia-current that depends on xorg-video-abi-12



The nvidia-graphics-drivers-updates (295.09) from the Mingmin Ren PPA only works with xserver 1.10 series.
For xserver 1.11 series, use Xorg-edgers PPA version.
For xserver 1.12 branch, use Ricotz Unstable PPA version.

Note, that also all input drivers must be installed accordingly.

Thanks Harry.

I haven't been using the Ricotz Unstable PPA, but I've added it now and disabled xorg-edgers for the moment.

I also removed nvidia-current-updates and installed nvidia-current:

```
paul@precise-64:~$ apt-cache policy nvidia-current
nvidia-current:
  **[COLOR="Red"]Installed: 290.10-0ubuntu1[/COLOR]**
  Candidate: 290.10-0ubuntu1
  Version table:
 *** 290.10-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
        100 /var/lib/dpkg/status
     290.10-0ubuntu1~xedgers~precise1 0
        500 http://ppa.launchpad.net/ricotz/unstable/ubuntu/ precise/main amd64 Packages
```

so as you say I'll need to wait for an nvidia-current that depends on xorg-video-abi-12.

I see that Ricotz Unstable is using the xorg-edgers version of nvidia-current and right now this is older than the version in the main repos.

---

### Post by Harry33 on 2012-01-15
> **paul_in_london said:**
> Thanks Harry.

I haven't been using the Ricotz Unstable PPA, but I've added it now and disabled xorg-edgers for the moment.

I also removed nvidia-current-updates and installed nvidia-current:

```
paul@precise-64:~$ apt-cache policy nvidia-current
nvidia-current:
  **[COLOR=Red]Installed: 290.10-0ubuntu1[/COLOR]**
  Candidate: 290.10-0ubuntu1
  Version table:
 *** 290.10-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
        100 /var/lib/dpkg/status
     290.10-0ubuntu1~xedgers~precise1 0
        500 http://ppa.launchpad.net/ricotz/unstable/ubuntu/ precise/main amd64 Packages
```so as you say I'll need to wait for an nvidia-current that depends on xorg-video-abi-12.

I see that Ricotz Unstable is using the xorg-edgers version of nvidia-current and right now this is older than the version in the main repos.

The nvidia-current in Ricotz Unstable PPA is not the same as in xorg-edgers.
It is not older than in Precise repos. It only has a longer name. Thus it is ranked lower.
It has been built against new video-abi-12. It is the only version that works with xserver 1.12 branch.
You just need to put this in your /etc/X11/xorg.conf file:

```

Section "ServerFlags"
    Option         "IgnoreABI" "True"
EndSection

```

---

### Post by paul_in_london on 2012-01-15
> **Harry33 said:**
> The nvidia-current in Ricotz Unstable PPA is not the same as in xorg-edgers.
It is not older than in Precise repos. It only has a longer name. Thus it is ranked lower.
It has been built against new video-abi-12. It is the only version that works with xserver 1.12 branch.
You just need to put this in your /etc/X11/xorg.conf file:

```

Section "ServerFlags"
    Option         "IgnoreABI" "True"
EndSection

```

Hi Harry,

On [this page](https://launchpad.net/~ricotz/+archive/unstable/+packages ) the following entry is listed:

```
nvidia-graphics-drivers - 290.10-0ubuntu1~xedgers~precise1 (Newer version available):

Publishing details

    Published on 2011-11-22
    Copied from ubuntu precise in xorg-edgers fresh X crack
```

Maybe nvidia-current in this ppa doesn't always track the xorg-edgers version, but that's what it seems to be using at the moment.

The problem is the main repo version of nvidia-current (290.10-0ubuntu1) is being "treated" as newer so the ppa version isn't installable at the moment.

I do have the "IgnoreABI" "True" option ready in xorg.conf btw when the time comes.

Regards,

Paul

EDIT: the "Newer version available" link on that page points to the main repo version even though it's not really newer.

---

### Post by Harry33 on 2012-01-15
> **paul_in_london said:**
> Hi Harry,

On [this page]("https://launchpad.net/%7Ericotz/+archive/unstable/+packages") the following entry is listed:

```
nvidia-graphics-drivers - 290.10-0ubuntu1~xedgers~precise1 (Newer version available):

Publishing details

    Published on 2011-11-22
    Copied from ubuntu precise in xorg-edgers fresh X crack
```Maybe nvidia-current in this ppa doesn't always track the xorg-edgers version, but that's what it seems to be using at the moment.

The problem is the main repo version of nvidia-current (290.10-0ubuntu1) is being "treated" as newer so the ppa version isn't installable at the moment.

I do have the "IgnoreABI" "True" option ready in xorg.conf btw when the time comes.

Regards,

Paul

EDIT: the "Newer version available" link on that page points to the main repo version even though it's not really newer.


Like I said, because of the longer name of the package, it is treated as lower.
That is only repo technical issue. The driver is exactly the same. Only Nvidia Corporation is able to change that.

In a PPA, what is copied, is the source, not the built deb package.
Then the source has been rebuilt.

Then, a totally different question is building the deb package.
In Precise repos this was built with dependency of video-abi-10,
in Xorg-edgers PPA this was built with dependency of video-abi-11, and
in Unstable PPA with video-abi-12.

If you try installing with Synaptic, you can force any package.
Just choose "Package - Force Version".
Or you can install it manually with dpkg.

---

### Post by paul_in_london on 2012-01-15
> **Harry33 said:**
> Like I said, because of the longer name of the package, it is treated as lower.
That is only repo technical issue. The driver is exactly the same. Only Nvidia Corporation is able to change that.

In a PPA, what is copied, is the source, not the built deb package.
Then the source has been rebuilt.

Then, a totally different question is building the deb package.
In Precise repos this was built with dependency of video-abi-10,
in Xorg-edgers PPA this was built with dependency of video-abi-11, and
in Unstable PPA with video-abi-12.

If you try installing with Synaptic, you can force any package.
Just choose "Package - Force Version".
Or you can install it manually with dpkg.

Thanks Harry. I appreciate what you're saying about the respective nvidia-current versions in those ppas having different build dependencies.

So as you suggested I "downgraded" nvidia-current to:

```
nvidia-current:
  Installed: 290.10-0ubuntu1~xedgers~precise1
  Candidate: 290.10-0ubuntu1
  Version table:
     290.10-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
 *** 290.10-0ubuntu1~xedgers~precise1 0
        500 http://ppa.launchpad.net/ricotz/unstable/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status

```

and that allowed me yo upgrade the xserver stuff from Ricotz Unstable that was held back and now I have:

```
paul@precise-64:~$ less /var/log/Xorg.0.log
[   135.970] 
X.Org X Server 1.11.99.901 (1.12.0 RC 1)
Release Date: 2011-12-27
```

---

### Post by Harry33 on 2012-01-15
Right Paul, now you have the latest xserver, and working.

---

### Post by paul_in_london on 2012-01-15
> **Harry33 said:**
> Right Paul, now you have the latest xserver, and working.

Thanks again Harry - all seems to be fine now apart from the ridiculously long boot times I started getting a few days ago. Haven't worked that one out yet. ;)

---

### Post by Harry33 on 2012-01-15
> **paul_in_london said:**
> Thanks again Harry - all seems to be fine now apart from the ridiculously long boot times I started getting a few days ago. Haven't worked that one out yet. ;)

Sorry Paul, I do not have such issues.
Nothing wrong with boot times here.

---

### Post by paul_in_london on 2012-01-15
> **Harry33 said:**
> Sorry Paul, I do not have such issues.
Nothing wrong with boot times here.

That's ok Harry, thanks for letting me know. I'll keep googling! :)

---

