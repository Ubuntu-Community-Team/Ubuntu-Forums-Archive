---
title: "Video step in Hardware Testing crashes computer, hard"
date: 2008-09-06
forum: System76 Support
---

### Post by phyzome on 2008-09-06
When I run the Hardware Testing command in the System -> Administration menu, the Video step blanks the screen and the computer becomes completely unresponsive. I have to press and hold the power button for 8 seconds to turn the computer off.

---

### Post by thomasaaron on 2008-09-08
Hello, phyzome.

Whenever you request help in forums, it is a good idea to include as much information about your system as you can (particularly your System76 model number) so that we can try to reproduce the problem in our shop.

---

### Post by phyzome on 2008-09-08
Ah, sorry about that. I've got a Pangolin Performance (panp4i), which is 64-bit Ubuntu Hardy Heron.

This problem also occurs when I try to use Cheese (a webcam package) or when I try to play a video.

The video may actually be a different problem, since the screen recovered somewhat after a few seconds of blackness. (I've attached a photo of the screen.) However, the system is still locked up pretty bad.

Things to note about the attached photo: Text near the bottom of the screen is choppy, the desktop background is pretty wedged, and some of the file thumbnails display random splotches of color. I suppose this is a corruption of the video data.

---

### Post by thomasaaron on 2008-09-08
Let's forget about the hardware testing utility for a moment. Let's get your webcam working in cheese.

First, go to System > Admin > System76 Driver > Install (tab) > Install (button).

Then reboot your computer.

Now start cheese. You should either see yourself (after several seconds) or multi-colored bars and static.

If you see the bars and static, turn cheese off. Press Fn-F10 (to turn on the camera) and restart cheese.

Now, you should definitely see yourself (after several seconds).

Once you get that far, you might try running Hardware Detection. But, I'm not too concerned about that particular app not working right. It may not be up to speed with the X4500 chips yet. We can try to duplicate it on a shop machine, though.

---

### Post by phyzome on 2008-09-08
> **thomasaaron said:**
> First, go to System > Admin > System76 Driver > Install (tab) > Install (button).

Then reboot your computer.

Yeah, that was one of the first things I did after receiving the computer.

> **thomasaaron said:**
> Now start cheese. You should either see yourself (after several seconds) or multi-colored bars and static.

When I start Cheese, there's a little animation in the viewport for a few seconds (presumably the webcam is being initialized) and then the crash happens. Instant blackout, though the hard drive LED blinks some.

---

### Post by thomasaaron on 2008-09-08
Go to a terminal and enter this command:
gstreamer-properties

Go to the 'Video' tab.

What is the default Output plugin set to?
What is the default Input plugin set to?

---

### Post by phyzome on 2008-09-08
Default output: Autodetect
Default input: Video for Linux 2 (v4l2)

Would it be safe to just try different Inputs and Output settings?

---

### Post by thomasaaron on 2008-09-08
Well, the input plugin is correct.

The output should be fine too. You might want to try setting it to X11/XShm/Xv and see what happens. If it doesn't help set it back to Autodetect.

Have you downloaded any codecs or anything? Any gstreamer stuff? It's sounding like a hosed config somewhere.

Our stock install with the System76 driver should work great with the webcam. There is a bug in cheese that causes freezing if the webcam driver isn't compiled (...by the Sytsem76 driver).

What driver version do you have installed? (...System76 Driver > About).

---

### Post by phyzome on 2008-09-08
I played around a bit with different settings. It seems that using an output of "X Window System (No Xv)" in combination with "Test Input" will avoid the crash in Cheese -- and cheese then works! Using Xv or either Video 4 Linux option will make the crash return.

However, this does not solve the crash that occurs with playing AVI files or for that matter the Hardware Testing tool. :-/

---

### Post by phyzome on 2008-09-08
> **thomasaaron said:**
> Have you downloaded any codecs or anything? Any gstreamer stuff? It's sounding like a hosed config somewhere.

I installed gstreamer0.10-plugins-ugly sometime yesterday, but I /think/ the bug was already present. Here's a list of all package changes since I received the laptop:

```
aircrack-ng
apache2.2-common
apache2
apache2-mpm-prefork
apache2-utils
cheese
gparted
gstreamer0.10-plugins-ugly
gthumb
kdelibs4c2a
kdelibs-data
kismet
kphotoalbum
liba52-0.7.4
libadns1
libapache2-mod-php5
libapr1
libaprutil1
libarts1c2a
libartsc0
libaudio2
libavahi-qt3-1
libavcodec1d
libavformat1d
libavutil1d
libdbd-mysql-perl
libdbi-perl
libdc1394-13
libdvbpsi4
libdvdnav4
libdvdread3
libebml0
libexiv2-2
libfreebob0
libgmp3c2
libgsm1
libid3tag0
libiso9660-5
libjack0
libkdcraw3
libkipi0
liblua50
liblua5.1-0
liblualib50
libmad0
libmatroska0
libmcrypt4
libmodplug0c2
libmpcdec3
libmpeg2-4
libmysqlclient15off
libnet-daemon-perl
libnss3-0d
libplrpc-perl
libpostproc1d
libpq5
libqt3-mt
libqt3-mt-sqlite
libqt4-core
libqt4-gui
libsdl-image1.2
libsidplay1
libtar
libvcdinfo0
libvlc0
libwxbase2.6-0
libwxgtk2.6-0
libxalan110
libxerces27
libxosd2
liferea
mysql-client-5.0
mysql-common
mysql-server-5.0
mysql-server
nmap
php5-common
php5-imagick
php5
php5-mcrypt
php5-mysql
phpmyadmin
pidgin-encryption
pidgin-extprefs
pidgin-guifications
pidgin-plugin-pack
thunderbird-gnome-support
thunderbird
ttf-dejavu-extra
ttf-dejavu
virtualbox-2.0
vlc
vlc-nox
vlc-plugin-pulse
weplab
wireshark-common
```

In addition, I've enabled Hardy-proposed, and uninstalled libmagick 9.

> **thomasaaron said:**
> What driver version do you have installed? (...System76 Driver > About).

I show version 2.2.3.

I should probably disable all video plugins in Firefox so that I don't crash every time I hit a web page with an embedded WMV. :-/

---

### Post by gaussian on 2008-09-08
Just a suggestion: Try things with Compiz disabled (Desktop Effects).

---

### Post by thebinaryblob on 2008-09-08
I get problems like this alot as well, especially when using xine or mplayer to play video, and when trying to play certain games, such as torus-trooper. I have tried turning compiz off, but it didn't help.

Is this just a problem with the drivers for the X4500 (or is it X4500HD?)? and if so, do you know if they will be fixed, or at least less catastophic, in Intrepid?

---

### Post by thomasaaron on 2008-09-08
I'm betting it is VLC related. There are a ton of posts and bug reports on VLC crashing stuff.

It's difficult to tell for sure though, as I don't know which package introduced the problem.

---

### Post by phyzome on 2008-09-08
> **thomasaaron said:**
> I'm betting it is VLC related. There are a ton of posts and bug reports on VLC crashing stuff.

I don't think it is VLC. I installed that on Sep 6, and I believe I had already encountered the crash. I think.

> **thomasaaron said:**
> It's difficult to tell for sure though, as I don't know which package introduced the problem.

Is there a way I can quickly test it here? I'm willing to back up the machine to an external drive and return the configuration to its original state, if that's possible.

---

### Post by phyzome on 2008-09-21
I installed the 2.2.5 system76-driver package (from the [sound-gone-after-suspend bug]("https://bugs.launchpad.net/system76/+bug/264516")), and that seems to have solved the video crash (and the sound problem).

Caveat: I am still using the no-XV setting. I have not tested any other settings.

The Hardware Testing app still crashes, but it may be trying to display video in a way that normal apps do not.

---

