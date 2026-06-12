---
title: "Totem could not get a screenshot of video and asks to open a bug"
date: 2017-10-04
forum: Ubuntu Development Version
---

### Post by corradoventu on 2017-10-04
Totem could not get a screenshot of the video and invited me to open a bug! [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1721248](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1721248) 
Is the first time I'm invited to open a bug from an application! See screenshot.

---

### Post by mc4man on 2017-10-04
Seems to work fine here, how old is your install?

Edit: have you tried with various videos?

---

### Post by corradoventu on 2017-10-04
Installed from Ubuntu 17.10 "Artful Aardvark" - Beta amd64 (20170930) but it happens also in a different install from daily dated 2170926, same PC, different partition. I just installed the 2170930 to check if problem persisted.
ctrl+alt+s gives the same problem.
My video is as from the attached screenshot, may you suggest a terminal command to get same (and may be more) info about it? 
thanks
I tried with various video all webm from cheese, different dimensions, will try to find others.

---

### Post by corradoventu on 2017-10-04
no problem with various .3gp 320x240 same problem with various.mov 1920x1080

---

### Post by mc4man on 2017-10-04
Just tried again here with a fresh install, updated. There both the menu method & the keybinding work. Image was from 9/29
As far as debugging totem - no real idea. There are --debug commands but not sure they'll help you.  see totem --help-all

---

### Post by mc4man on 2017-10-04
I tried some larger rez vids here (1080p & 4k), no issue.
One real fault with totem is that it doesn't resize to video size ( up to display size) but when you take a screenshot the image is the actual video rez.
So maybe something about your video hardware & or drivers. 
Here all was well with Intel (Haswell) & and nvidia (gt755m

---

### Post by corradoventu on 2017-10-05
Totem has no problem taking screenshot on the same PC different partition running Ubuntu 16.04, so my video hardware should be ok, but may be something wrong with drivers because cheese has problems on my 17.10 while works fine on my 16.04.
Did you have some suggestion where to look? Thanks.

---

### Post by corradoventu on 2017-10-05
Cheese seems also having problems with totem components

corrado@corrado-p5-0930:~$ cheese

(cheese:4054): Gtk-WARNING **: Theme parsing error: cheese.css:7:35: The style property GtkScrollbar:min-slider-length is deprecated and shouldn't be used anymore. It will be removed in a future version
totem-video-thumbnailer couldn't open file 'file:///home/corrado/Videos/Webcam/2017-10-05-140813.webm'

** (cheese:4054): WARNING **: could not generate thumbnail for /home/corrado/Videos/Webcam/2017-10-05-140813.webm (video/webm)

corrado@corrado-p5-0930:~$ 

corrado@corrado-p5-0930:~$ totem

(totem:4344): GLib-CRITICAL **: g_key_file_load_from_file: assertion 'file != NULL' failed

(totem:4344): Gtk-WARNING **: Drawing a gadget with negative dimensions. Did you forget to allocate a size? (node slider owner GtkScale)

** (totem:4344): WARNING **: Could not take screenshot: failed to retrieve or convert video frame
corrado@corrado-p5-0930:~$

---

### Post by mc4man on 2017-10-05
Are you getting thumbnails for the videos that don't work & thumbs for photos and or video's from cheese?
The totem warnings & the 1st cheese warning are all irrelevant to use & users.

---

### Post by corradoventu on 2017-10-06
Cheese: I record a video from webcam, when i stop recording i have the message 
** (cheese:4054): WARNING **: could not generate thumbnail for /home/corrado/Videos/Webcam/2017-10-05-140813.webm (video/webm) 
and the window appears as from the attached screenshot

---

### Post by mc4man on 2017-10-06
As mentioned in report this appears to be  from the gstreamer-vaapi plugin. While it doesn't occur in earlier versions of the plugin I guess it does now.
(- If I add it cheese reports that warning
Edit: it may not be the plugin itself, will do some tests...

---

### Post by mc4man on 2017-10-06
The gst-vaapi plugin is 100% the cause of the totem screenshot error, if you remove it then totem should start working again.
However I doubt that'll fix cheese if or when it breaks. (- on another fresh install I can't find any way to break cheese.

---

### Post by corradoventu on 2017-10-06
screenshot created ok from an MPEG-4 video created by guvcview

---

### Post by amano on 2017-10-08
> **corradoventu said:**
> Cheese: I record a video from webcam, when i stop recording i have the message 
** (cheese:4054): WARNING **: could not generate thumbnail for /home/corrado/Videos/Webcam/2017-10-05-140813.webm (video/webm) 
and the window appears as from the attached screenshot

jbcha, could that be fallout from not using Bubblewrap? That something in cheese (using gdk-pixbuf?) expects it being there?

---

### Post by corradoventu on 2017-11-28
About totem problem with screenshot I have done some more test with Ubuntu 17.10 and the last daily of Ubuntu 18.04 Bionic 
On same hardware, different partitions:
If during the installation i'm connected to internet I HAVE the problem
If during the installation i'm NOT connected to internet I DO NOT HAVE the problem
Seems crazy?

---

### Post by corradoventu on 2017-11-29
About totem problem with screenshot - see also another bug: [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1732204](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1732204)
in my bug: [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1721248](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1721248)  I added some totem debug messages

---

### Post by ventrical on 2017-11-30
No problem here on haswell but  cheese sure takes it time to load up.

---

### Post by corradoventu on 2017-11-30
Removed gstreamer1.0-vaapi plugin
Problem solved!
thanks a lot!

---

### Post by corradoventu on 2017-12-04
On same hardware, different partitions:
If during the installation I'm connected to internet I HAVE the problem
If during the installation I'm NOT connected to internet I DO NOT HAVE the problem
This is because the package gstreamer1.0-vaapi/artful,now 1.12.3-1ubuntu1 amd64 [installed,automatic]
is installed only when the installation is done CONNECTED. 
for this problem i opened another bug: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1735914](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1735914)  Installed packages missing installing Ubuntu 17.10 offline
Problem happens with Ubuntu Bionic and also with Artful

---

### Post by mc4man on 2017-12-04
> **corradoventu said:**
> On same hardware, different partitions:
If during the installation I'm connected to internet I HAVE the problem
If during the installation I'm NOT connected to internet I DO NOT HAVE the problem
This is because the package gstreamer1.0-vaapi/artful,now 1.12.3-1ubuntu1 amd64 [installed,automatic]
is installed only when the installation is done CONNECTED. 
for this problem i opened another bug: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1735914](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1735914)  Installed packages missing installing Ubuntu 17.10 offline
Problem happens with Ubuntu Bionic and also with Artful
What is the bug here?

---

### Post by corradoventu on 2017-12-04
I think installation should not give different results when done online or offline.

---

### Post by mc4man on 2017-12-04
> **corradoventu said:**
> I think installation should not give different results when done online or offline.

I don't see 18.04 currently installing the vaapi plugin with internet enabled for install. There are some differences, likely concerning language-packs. (- on  one week old image, online - 1539 installed, 97 to update, offline - 1535 installed, 122 to update.

As far as bug report - pretty much useless, really just an opinion & as far as 17.10 it's a moot point..

Regarding the vaapi plugin, if it's fixed then it seems a decent idea to install during install (if that was the orig. idea..

---

### Post by corradoventu on 2017-12-05
In 18.04 daily 1127 I found automatically installed gstreamer1.0-vaapi/bionic,now 1.12.3-2ubuntu2 amd64 [installed,automatic]

corrado@corrado-p8-bb-1127:~$ apt list --installed | grep  gstreamer 
WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

gir1.2-gstreamer-1.0/bionic,now 1.12.3-1 amd64 [installed]
gstreamer1.0-alsa/bionic,now 1.12.3-1 amd64 [installed]
gstreamer1.0-clutter-3.0/bionic,now 3.0.24-1 amd64 [installed]
gstreamer1.0-fluendo-mp3/bionic,now 0.10.32.debian-1 amd64 [installed,automatic]
gstreamer1.0-libav/bionic,now 1.12.3-1 amd64 [installed,automatic]
gstreamer1.0-packagekit/bionic,now 1.1.7-1 amd64 [installed]
gstreamer1.0-plugins-base/bionic,now 1.12.3-1 amd64 [installed]
gstreamer1.0-plugins-base-apps/bionic,now 1.12.3-1 amd64 [installed]
gstreamer1.0-plugins-good/bionic,now 1.12.3-1ubuntu1 amd64 [installed]
gstreamer1.0-plugins-ugly/bionic,now 1.12.3-1build1 amd64 [installed,automatic]
gstreamer1.0-pulseaudio/bionic,now 1.12.3-1ubuntu1 amd64 [installed]
gstreamer1.0-tools/bionic,now 1.12.3-1 amd64 [installed]
gstreamer1.0-vaapi/bionic,now 1.12.3-2ubuntu2 amd64 [installed,automatic]
gstreamer1.0-x/bionic,now 1.12.3-1 amd64 [installed]
libgstreamer-plugins-bad1.0-0/bionic,now 1.12.3-1ubuntu2 amd64 [installed,automatic]
libgstreamer-plugins-base1.0-0/bionic,now 1.12.3-1 amd64 [installed]
libgstreamer-plugins-good1.0-0/bionic,now 1.12.3-1ubuntu1 amd64 [installed]
libgstreamer1.0-0/bionic,now 1.12.3-1 amd64 [installed]
libreoffice-avmedia-backend-gstreamer/bionic,now 1:5.4.3-0ubuntu1 amd64 [installed]
corrado@corrado-p8-bb-1127:~$

---

### Post by mc4man on 2017-12-05
> **corradoventu said:**
> In 18.04 daily 1127 I found automatically installed gstreamer1.0-vaapi/bionic,now 1.12.3-2ubuntu2 amd64 [installed,automatic]

corrado@corrado-p8-bb-1127:~$ apt list --installed | grep  gstreamer 
WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

gir1.2-gstreamer-1.0/bionic,now 1.12.3-1 amd64 [installed]
gstreamer1.0-alsa/bionic,now 1.12.3-1 amd64 [installed]
gstreamer1.0-clutter-3.0/bionic,now 3.0.24-1 amd64 [installed]
gstreamer1.0-fluendo-mp3/bionic,now 0.10.32.debian-1 amd64 [installed,automatic]
gstreamer1.0-libav/bionic,now 1.12.3-1 amd64 [installed,automatic]
gstreamer1.0-packagekit/bionic,now 1.1.7-1 amd64 [installed]
gstreamer1.0-plugins-base/bionic,now 1.12.3-1 amd64 [installed]
gstreamer1.0-plugins-base-apps/bionic,now 1.12.3-1 amd64 [installed]
gstreamer1.0-plugins-good/bionic,now 1.12.3-1ubuntu1 amd64 [installed]
gstreamer1.0-plugins-ugly/bionic,now 1.12.3-1build1 amd64 [installed,automatic]
gstreamer1.0-pulseaudio/bionic,now 1.12.3-1ubuntu1 amd64 [installed]
gstreamer1.0-tools/bionic,now 1.12.3-1 amd64 [installed]
gstreamer1.0-vaapi/bionic,now 1.12.3-2ubuntu2 amd64 [installed,automatic]
gstreamer1.0-x/bionic,now 1.12.3-1 amd64 [installed]
libgstreamer-plugins-bad1.0-0/bionic,now 1.12.3-1ubuntu2 amd64 [installed,automatic]
libgstreamer-plugins-base1.0-0/bionic,now 1.12.3-1 amd64 [installed]
libgstreamer-plugins-good1.0-0/bionic,now 1.12.3-1ubuntu1 amd64 [installed]
libgstreamer1.0-0/bionic,now 1.12.3-1 amd64 [installed]
libreoffice-avmedia-backend-gstreamer/bionic,now 1:5.4.3-0ubuntu1 amd64 [installed]
corrado@corrado-p8-bb-1127:~$
Sorry, don't see this at all. Based on a dev's comment to me in a bug I thought they had decided to auto enable hwdec, maybe for mpv but certainly not for gstreamer/totem.
Are you checking the option to add media packages during the install as that's the only way I'd think all those gstreamer packages would be included. Note that you also show the bad, ugly & fluendo plugins. You should mark your bug as invalid if that's the case. (100% sure it is..

What's default installed (online or offline, both the same
```
gir1.2-gstreamer-1.0/bionic,now 1.12.3-1 amd64 [installed]
gstreamer1.0-alsa/bionic,now 1.12.3-1 amd64 [installed]
gstreamer1.0-clutter-3.0/bionic,now 3.0.24-1 amd64 [installed]
gstreamer1.0-packagekit/bionic,now 1.1.7-1 amd64 [installed]
gstreamer1.0-plugins-base/bionic,now 1.12.3-1 amd64 [installed]
gstreamer1.0-plugins-base-apps/bionic,now 1.12.3-1 amd64 [installed]
gstreamer1.0-plugins-good/bionic,now 1.12.3-1ubuntu1 amd64 [installed]
gstreamer1.0-pulseaudio/bionic,now 1.12.3-1ubuntu1 amd64 [installed]
gstreamer1.0-tools/bionic,now 1.12.3-1 amd64 [installed]
gstreamer1.0-x/bionic,now 1.12.3-1 amd64 [installed]
libgstreamer-plugins-base1.0-0/bionic,now 1.12.3-1 amd64 [installed]
libgstreamer-plugins-good1.0-0/bionic,now 1.12.3-1ubuntu1 amd64 [installed]
libgstreamer1.0-0/bionic,now 1.12.3-1 amd64 [installed]
libreoffice-avmedia-backend-gstreamer/bionic,now 1:5.4.3-0ubuntu1 amd64 [installed]
```

---

