---
title: "VLC Pulse Audio 5.1 Patch"
date: 2008-11-30
forum: Ubuntu Dev Link Forum
---

### Post by danwood76 on 2008-11-30
Hi,

Ive made a patch to the VLC pulse audio plugin that allows it to output 5.1, 4.0, 2.0 and, 1.0 based on the input streams channel count.

It works perfectly with all the audio/video files I have tested it with.

I was wondering who I need to contact to get the patch either merged or adapted to the main plugin as I have seen quite a few posts asking for this whilst I myself was looking for it.
(5.1 pulseaudio output from vlc)

The diff/patch is below, it can be patched to the main source available in intrepid (vlc-0.9.4)

thanks,
Danny

```

--- pulse.c	2008-09-18 22:03:35.000000000 +0100
+++ vlc-0.9.4/modules/audio_output/pulse.c	2008-11-28 11:39:10.000000000 +0000
@@ -114,6 +114,7 @@
     const struct pa_buffer_attr *buffer_attr;
     struct pa_buffer_attr a;
     struct pa_channel_map map;
+    int no_channels;	/* Variable to hold input stream channel count */
 
     /* Allocate structures */
     p_aout->output.p_sys = p_sys = malloc( sizeof( aout_sys_t ) );
@@ -123,12 +124,44 @@
 
     PULSE_DEBUG( "Pulse start initialization");
 
-    ss.rate = p_aout->output.output.i_rate;
-    ss.channels = 2;
+    no_channels = aout_FormatNbChannels( &p_aout->output.output );	/* Get the input stream channel count */
 
+    /* Setup the pulse audio stream based on the input stream count */
+    switch(no_channels)
+    {
+        case 6:
+        p_aout->output.output.i_physical_channels
+            = AOUT_CHAN_LEFT | AOUT_CHAN_RIGHT | AOUT_CHAN_CENTER
+               | AOUT_CHAN_REARLEFT | AOUT_CHAN_REARRIGHT
+               | AOUT_CHAN_LFE;
+        ss.channels = 6;
+	break;
+
+        case 4:
+        p_aout->output.output.i_physical_channels
+            = AOUT_CHAN_LEFT | AOUT_CHAN_RIGHT
+               | AOUT_CHAN_REARLEFT | AOUT_CHAN_REARRIGHT;
+        ss.channels = 4;
+        break;
+
+        case 2:
+        p_aout->output.output.i_physical_channels
+            = AOUT_CHAN_LEFT | AOUT_CHAN_RIGHT;
+        ss.channels = 2;
+        break;
+
+        case 1:
+        p_aout->output.output.i_physical_channels = AOUT_CHAN_CENTER;
+        ss.channels = 1;
+        break;
+    
+	default:
+        msg_Err(p_aout,"Invalid number of channels");
+	goto fail;
+    }
+
+    ss.rate = p_aout->output.output.i_rate;
     ss.format = PA_SAMPLE_S16LE;
-    p_aout->output.output.i_physical_channels =
-            AOUT_CHAN_LEFT | AOUT_CHAN_RIGHT;
     p_aout->output.output.i_format = AOUT_FMT_S16_NE;
 
     if (!pa_sample_spec_valid(&ss)) {
@@ -148,8 +181,8 @@
 
     p_sys->buffer_size = a.minreq;
 
-    pa_channel_map_init_stereo(&map);
-
+    /* Initialise the speaker map setup above */
+    pa_channel_map_init_auto(&map, ss.channels, PA_CHANNEL_MAP_ALSA);
 
     if (!(p_sys->mainloop = pa_threaded_mainloop_new())) {
         msg_Err(p_aout, "Failed to allocate main loop");

```

---

### Post by castrojo on 2008-11-30
Best way is to open a bug and attach the patch to the bug and add the "patch" tag.

---

### Post by illbashu on 2009-05-02
How do i apply this?

---

### Post by danwood76 on 2009-05-02
The patch is in the latest VLC source (from git), so if you are going to compile you mayaswell compile it from git source.

The patch will be in the version 1.0 release (which is coming soon ;))

---

### Post by illbashu on 2009-05-03
can you give to the link to the git vlc source?

---

### Post by danwood76 on 2009-05-04
You need to install git-core from the repos.
Also you'll need to get all the vlc depends:
```

sudo apt-get build-dep vlc

```
Then get the source by following this section of the git guide:
[http://wiki.videolan.org/Git#Getting_VLC_or_x264_source_code_via_Git](http://wiki.videolan.org/Git#Getting_VLC_or_x264_source_code_via_Git)

And compile by using the following commands in the source directory:
```

./bootstrap
./configure --prefix=/usr
make
sudo make install

```
The build will take a while, if the bootstrap complains about autoconf install it from synaptic and you should be fine.

---

### Post by illbashu on 2009-05-04
```
bash@bash-desktop:~$ sudo apt-get build-dep vlc
[sudo] password for bash: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for vlc could not be satisfied.

```
I'm running Ubuntu 9.04

---

### Post by danwood76 on 2009-05-05
thats odd, I built it on 9.04 the other day!

Make sure all the repos are enabled in the software sources, and then do:
```

sudo apt-get update

```
and try the commands above again.

---

### Post by illbashu on 2009-05-06
I am running 64bit could that be the problem?

---

### Post by danwood76 on 2009-05-06
No I'm running 64-bit and it works fine.
Make sure you have all the repositories in the list enabled and make sure you run 'sudo apt-get update' it should find the dependencies no problem.

---

### Post by illbashu on 2009-05-07
i have everything checked. Do you have any extra repos installed?

---

### Post by danwood76 on 2009-05-07
No, the alternative is to install the dependencies themselves.
But there are quite a few.

You could install a nightly build from here:
[http://nightlies.videolan.org/](http://nightlies.videolan.org/)
(The ubuntu packages will work on jaunty I'm sure)

---

### Post by illbashu on 2009-05-07
This is my source list

```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gulus.usherbrooke.ca/ubuntu/ jaunty main restricted
deb-src http://gulus.usherbrooke.ca/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gulus.usherbrooke.ca/ubuntu/ jaunty-updates main restricted
deb-src http://gulus.usherbrooke.ca/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gulus.usherbrooke.ca/ubuntu/ jaunty universe
deb-src http://gulus.usherbrooke.ca/ubuntu/ jaunty universe
deb http://gulus.usherbrooke.ca/ubuntu/ jaunty-updates universe
deb-src http://gulus.usherbrooke.ca/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gulus.usherbrooke.ca/ubuntu/ jaunty multiverse
deb-src http://gulus.usherbrooke.ca/ubuntu/ jaunty multiverse
deb http://gulus.usherbrooke.ca/ubuntu/ jaunty-updates multiverse
deb-src http://gulus.usherbrooke.ca/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
 deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://gulus.usherbrooke.ca/ubuntu/ jaunty-security main restricted
deb-src http://gulus.usherbrooke.ca/ubuntu/ jaunty-security main restricted
deb http://gulus.usherbrooke.ca/ubuntu/ jaunty-security universe
deb-src http://gulus.usherbrooke.ca/ubuntu/ jaunty-security universe
deb http://gulus.usherbrooke.ca/ubuntu/ jaunty-security multiverse
deb-src http://gulus.usherbrooke.ca/ubuntu/ jaunty-security multiverse
deb http://ppa.launchpad.net/transmissionbt/ubuntu jaunty main
deb-src http://ppa.launchpad.net/transmissionbt/ubuntu jaunty main
deb http://ppa.launchpad.net/transmissionbt-beta/ubuntu jaunty main
deb-src http://ppa.launchpad.net/transmissionbt-beta/ubuntu jaunty main
deb http://gulus.usherbrooke.ca/ubuntu/ jaunty-proposed restricted main multiverse universe
deb http://gulus.usherbrooke.ca/ubuntu/ jaunty-backports restricted main multiverse universe
deb http://apt.boxee.tv jaunty main

```

For the nightly build do I install 8.10 repo?

edit....

```

W: Failed to fetch http://nightlies.videolan.org/build/intrepid-amd64/arch/./Packages  404 Not Found

``` -_- am i doomed to not get any use out of my system or something?, i guess ill there source code... none of there f*cking folder have anything in them.. The ones that you get linked to if you click on tar >:(

edit... i finally found one in the trunk folder.. maybe i should of read the thing first -_-

Edit: This is the part i am stuck on in compiling it. 

```
configure: WARNING: Could not find img_resample in libavcodec.
configure: error: in `/home/bash/Desktop/vlc-1.0.0-pre1':
configure: error: swscale (and its fallback module imgresample) support will be missing. Use --disable-swscale to ignore this error. (This basically means that you will be missing any good software scaling module and some video chroma converters.)
See `config.log' for more details.


```

Edit i figured it out i needed libswscale-dev

---

### Post by illbashu on 2009-05-07
I manged to get get it compiled but now i am getting this error:
```

bash@bash-desktop:~$ '/usr/local/bin/vlc' 
/usr/local/bin/vlc: error while loading shared libraries: libvlccore.so.2: cannot open shared object file: No such file or directory

```

i cant even run the regular VLC now it gives the same error. I tried removing it and it still gave that error :/

---

### Post by danwood76 on 2009-05-08
Oh dear. This is probably an issue because you now have 2 versions of VLC installed.

The thing to do is remove VLC from your machine and try to recompile.
First remove the one from the repos, and then run 'sudo make uninstall' in the vlc source dir.

When you recompile run the commands I said above, so first bootstrap then recompile configured with --prefix=/usr then make and sudo make install.

You should then be able to run vlc by just typing vlc into the terminal.

---

### Post by illbashu on 2009-05-08
its working know that i ran 
```
 echo export LD_LIBRARY_PATH=\${LD_LIBRARY_PATH}:/usr/local/lib >>~/.bash_profile
```
 but i cant run 5.1 as there is no option for it now and .mkv files are really choppy(they are so choppy that its pretty much unwatchable.

The guy on linux forums helped me out 

[http://www.linuxforums.org/forum/ubuntu-help/146113-libvlccore-so-2-problem.html#post694300](http://www.linuxforums.org/forum/ubuntu-help/146113-libvlccore-so-2-problem.html#post694300)

---

### Post by danwood76 on 2009-05-08
The choppyness is probably caused by Ubuntus new pulseaudio.
I have made a patch that pretty much fixes this by enabling a newer pulse output mode which will be in VLC git soon.

The 5.1 is automatic in pulse output (as long as you have that enabled) as pulse takes care of everything, you may need to adjust your pulse config to allow the 5.1 surround also.

---

### Post by illbashu on 2009-05-08
the audio isn't choppy the video is.

btw how do i set it to 5.1 it is detecting my speakers as Mono :/

Where is the pulse config file?

---

### Post by danwood76 on 2009-05-08
The file is:
/etc/pulse/daemon.conf

change the line:
```

; default-sample-channels = 2

```
to:
```

default-sample-channels = 6

```
You should then have 5.1, I dont use analogue I have a strange alsa setup with it encoding to dolby digital and outputting through spdif.

The mkv shouldnt stutter, if it does it could be related to your graphics drivers or some ofther video reason.
Does the video play smoothly in totem (Movie Player)?

---

### Post by illbashu on 2009-05-08
> **danwood76 said:**
> The file is:
/etc/pulse/daemon.conf

change the line:
```

; default-sample-channels = 2

```
to:
```

default-sample-channels = 6

```
You should then have 5.1, I dont use analogue I have a strange alsa setup with it encoding to dolby digital and outputting through spdif.

The mkv shouldnt stutter, if it does it could be related to your graphics drivers or some ofther video reason.
Does the video play smoothly in totem (Movie Player)?

the regular VLC used to run great... and no it doesn't lag in totem.

---

### Post by danwood76 on 2009-05-08
well the git version of VLC is very different to the one in the repos.
You can compile the pulse patch into the version from the repos just fine.

First dowbload the ubuntu source:
```

apt-get source vlc

```
then replace the pulse audio source file located:
```

modules/audio_output/pulse.c

```
Then compile the older version, the pulse audio module will run fine in the older version as I wrote the patch for 8.4 and the file hasn't changed since then.

---

### Post by illbashu on 2009-05-08
> **danwood76 said:**
> well the git version of VLC is very different to the one in the repos.
You can compile the pulse patch into the version from the repos just fine.

First dowbload the ubuntu source:
```

apt-get source vlc

```
then replace the pulse audio source file located:
```

modules/audio_output/pulse.c

```
Then compile the older version, the pulse audio module will run fine in the older version as I wrote the patch for 8.4 and the file hasn't changed since then.

is the GIT version different from the night version? and is there any special things i should put after ./compile? 

This is how i compile...
```
./configure --prefix=/usr/local

```

how do i install the pulse audio thing?

---

### Post by danwood76 on 2009-05-08
The nightly build is just a snapshot of the git source.
It ranges from being highly unstable to being stable so some builds will be quite poor and some good. Th souce from the repos will be stable though.

You dont have to configure /usr/local as the prefix as that is ubuntus default anyway, you only need to change the prefix if you want to install where the repo versions install. So a plain ./configure is fine.

I would try and completely remove the vlc you have installed at the moment as the librarys between the two versions might conflict if you dont remove the newer version. I'm pretty sure make uninstall works with ubuntu just fine so run that on the nightly build source first.

---

### Post by illbashu on 2009-05-08
i removed the old VLC... so there shouldn't be any conflict.

---

### Post by illbashu on 2009-05-09
this is the Terminal output when i run the file...

```
bash@bash-desktop:~$ vlc
VLC media player 1.0.0-pre1 Goldeneye
[0xdb3888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x1efc828] main demux error: no meta reader module matched "any"
[0x7f9848046328] a52 decoder: A/52 channels:7 samplerate:48000 bitrate:448000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x7f984804af28] alsa audio output error: audio device: surround51 is already in use
Qt: Dead lock detected while activating a BlockingQueuedConnection: Sender is QVLCVariable(0x10cd088), receiver is DialogHandler(0x10cd070)
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
[????????] x11 video output error: X11 request 142.3 failed with error code 9:
 BadDrawable (invalid Pixmap or Window parameter)
[????????] x11 video output notice: buggy X11 server claims shared memory
[????????] x11 video output notice: support though it does not work (OpenSSH?)
[????????] x11 video output error: X11 request 142.3 failed with error code 9:
 BadDrawable (invalid Pixmap or Window parameter)
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  142 (MIT-SHM)
  Minor opcode of failed request:  3 (X_ShmPutImage)
  Resource id in failed request:  0x4e00006
  Serial number of failed request:  1386
  Current serial number in output stream:  1387

```

---

### Post by danwood76 on 2009-05-10
You need to enable the pulseaudio plugin for it to work.
From that output I can see you are still using the alsa plugin:
> 
[0x7f984804af28] alsa audio output error: audio device: surround51 is already in use

The alsa plugin is much slower than the pulseaudio, btw which version of Ubuntu are you on?

---

### Post by illbashu on 2009-05-10
> **danwood76 said:**
> You need to enable the pulseaudio plugin for it to work.
From that output I can see you are still using the alsa plugin:

The alsa plugin is much slower than the pulseaudio, btw which version of Ubuntu are you on?

how do i enable it? i am on ubuntu 9.04 64bit.

---

### Post by danwood76 on 2009-05-10
If you open up the VLC preferences click audio and select the pulseaudio output type.

Choppy video can be caused by the audio modules but it can also be caused by the video output module. Make sure the video output is set to XVideo mode.
If XVideo doesnt work you can try X11, OpenGL whatever to see if it gets better.

I have just compiled the latest VLC on my old laptop (P4 2.66 GHz 512MB RAM) and playing a .mkv is just fine with the default settings and pulseaudio enabled.

---

### Post by illbashu on 2009-05-10
> **danwood76 said:**
> If you open up the VLC preferences click audio and select the pulseaudio output type.

Choppy video can be caused by the audio modules but it can also be caused by the video output module. Make sure the video output is set to XVideo mode.
If XVideo doesnt work you can try X11, OpenGL whatever to see if it gets better.

I have just compiled the latest VLC on my old laptop (P4 2.66 GHz 512MB RAM) and playing a .mkv is just fine with the default settings and pulseaudio enabled.

there is no pulse audio in there :/

i checked audio output module and installed (went into audio_output in modules and run make install) it and its still not there...

---

### Post by illbashu on 2009-05-10
These are the outputs i have.

Defult 
Dummy audio output
Simple DirectMedia layer 
File audio output 
Unix oss
ALSA

---

### Post by danwood76 on 2009-05-11
This means you havent compiled the plugin or installed it.
Make sure you also have the libpulse-dev package installed from synaptic so that the module can be compiled.
If you havent got this lib installed its also possible that you are missing some other libs forcing vlc to use the wrong video driver.
The vlc build-dep requires the universe repo I have discovered so make sure that is turned on and try the build-dep to install the dependencies.

The latest git source has my new patch in it which fixes some of the pulseaudio latency issues also so it might be worth you donwnloading the latest git to test also.

---

### Post by illbashu on 2009-05-11
I desided to give it another go and it worked now.. idk why it didn't before. I haven't changed anything the software sources. its installing right know. I'll post if i get any more probs.

---

### Post by illbashu on 2009-05-11
It works! Thank you!!!!!!!

---

### Post by danwood76 on 2009-05-11
You're welcome!

---

### Post by illbashu on 2009-05-11
More problems.... MP3s wont work....

```
bash@bash-desktop:~$ vlc '/home/bash/Music/Alexisonfire - Rough Hands.mp3' 
VLC media player 1.0.0-pre1 Goldeneye
[0xddd888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
TagLib: ID3v2.4 no longer supports the frame type TDAT.  It will be discarded from the tag.
[0x1d8bcd8] pulse audio output: No. of Audio Channels: 2
[0x1d8bcd8] pulse audio output error: Failed to connect to server: Invalid argument
[0x1d8bcd8] pulse audio output error: Pulse initialization failed
ALSA lib pcm_pulse.c:626:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

ALSA lib pcm_pulse.c:626:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

[0x1d8bcd8] alsa audio output error: unable to commit hardware configuration (Input/output error)
[0x1d8bcd8] oss audio output error: cannot open audio device (/dev/dsp)
ALSA lib pcm_pulse.c:626:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

E: stream.c: Assertion 's' failed at pulse/stream.c:1224, function pa_stream_drain(). Aborting.
Aborted

```
Edit... i fixed it... Changed the default server to default. Was set to other for some reason.

---

### Post by blacksm1th on 2009-06-11
@danwood76
Thank you.

---

### Post by danwood76 on 2009-06-11
Just as a note vesion 1.0 of VLC (of which rc3 is the latest release) has this patch and another fix included so it will be better and more stable to use that as opposed to the daily builds.

---

### Post by Clockware on 2009-06-17
@danwood76

I'm trying to fix this 5.1 problem, under Jaunty 9.04 (x86_64), but I have some errors.

"sudo apt-get build-dep vlc" doesn't work even if i have all the repos enabled, below the /etc/apt/source.list file:

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://it.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://it.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://it.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://it.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://it.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe #Added by software-properties

```So I downloaded the source tarball of the 1.0.0-rc3 version and I used the hints from the VideoLan Developer Wiki, to be more precise: [http://wiki.videolan.org/UnixCompile](http://wiki.videolan.org/UnixCompile) :popcorn:

```

** Get'em**

 There are a few ways to get those libs. You should use only one method at a time: 
 
[LIST]
[*] **The preferred way**: Using your distribution or portage system, in order to get all the needed libs.
[/LIST]
 For example on Debian or Ubuntu: 
 # sudo apt-get build-dep vlc

[LIST]
[*] If your distro is really bad and doesn't provide the libs, no -dev or -devel packages: Using the contribs system in VLC's sources
[/LIST]
  % cd extras/contrib;
 % ./bootstrap;
 % make;
This should download and build a lot of those libs for you. 


```So I used the contribs systems but the scripts fail when it try to download the ffmpeg tarball, printing some errors about the need to use the subversion version of that lib!

How can i fix these issues!? :(

Thank you,
Clockware

---

### Post by danwood76 on 2009-06-17
You do not need the contribs in Ubuntu. They are mainly from Windows and OSX.

I have just managed to install the depends on a fresh install of ubuntu Jaunty using:
```

sudo apt-get build-dep vlc

```
This is with the default repository setup.
What errors do you get from apt-get?

---

### Post by danwood76 on 2009-06-17
Oh and this is my sources.list:
```

#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

```

Have you done a 'sudo apt-get update' top retrieve the full online file lists?

---

### Post by Clockware on 2009-06-18
Yes, I do. But I get the same error:

```

xxx@xxx:~/software$ sudo apt-get build-dep vlc
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Lettura informazioni sullo stato... Fatto        
E: Non è stato possibile soddisfare le dipendenze di costruzione per vlc.

```It's mean that apt cannot retrieve the build dependencies for vlc. I also tried to rewrite the /etc/apt/source.list with the default (the one below) and I tried your source.list, the one with the GB repos! But I get the same error!

I have the same error with any package (ie. cheese):
sudo apt-get build-dep cheese
[...]
E: Non è stato possibile soddisfare le dipendenze di costruzione per cheese.

Something does not work as it should, but what?!

```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted

deb http://it.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty main restricted

deb http://it.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

deb http://it.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty universe

deb http://it.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-updates universe

deb http://it.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty multiverse

deb http://it.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

# deb http://it.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted

deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe

deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

## OTHERS ##
deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu jaunty main

deb http://download.virtualbox.org/virtualbox/debian jaunty non-free

```Any ideas?!

Thank you so much,
Clockware

---

### Post by danwood76 on 2009-06-18
I just used apt-cache to get the buil-dep list.

Here are the build depends:
```

Build-Depends: debhelper (>= 7), dh-buildinfo, gettext, quilt, nasm, yasm [amd64 kfreebsd-amd64], libass-dev (>= 0.9.5-2), libxul-dev, liba52-0.7.4-dev, libaa1-dev, libasound2-dev (>= 0.9.0beta10a) [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386], libaudiofile-dev, libavahi-client-dev, libavcodec-dev (>= 0.cvs20060823), libavformat-dev (>= 0.cvs20060823), libcaca-dev (>= 0.99.beta4), libcdio-dev, libdca-dev, libdvbpsi4-dev, libdvdnav-dev, libdvdread-dev (>= 0.9.5), libesd0-dev, libfaad-dev, libflac-dev (>= 1.1.2-3), libfreetype6-dev, libfribidi-dev, libggi2-dev, libgl1-mesa-dev, libglib2.0-0, libgnutls-dev (>= 1.2.8), libhal-dev (>= 0.5.5.1-3) [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386], libid3tag0-dev, libidl0, libimlib2-dev, libjack-dev, liblircclient-dev, liblivemedia-dev (>= 2008.07.24), liblua5.1-0-dev, libmad0-dev, libmatroska-dev (>= 0.8.0), libmodplug-dev, libmpcdec-dev, libmpeg2-4-dev, libncursesw5-dev, libnotify-dev, libogg-dev, libpng12-dev, libpostproc-dev (>= 0.cvs20060823), libpulse-dev, libqt4-dev, libschroedinger-dev, libsdl-image1.2-dev, libsdl1.2-dev (>= 1.2.7+1.2.8cvs20041007-5.3), libshout3-dev, libsmbclient-dev, libspeex-dev, libsvga1-dev [amd64 i386], libswscale-dev, libsysfs-dev, libtag1-dev, libtar-dev, libtheora-dev, libtwolame-dev (>= 0.3.8), libv4l-dev [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386], libvcdinfo-dev, libvorbis-dev, libx11-dev, libx264-dev, libxext-dev, libxml2-dev, libxpm-dev, libxt-dev, libxv-dev, pkg-config, qt4-dev-tools, zlib1g-dev

```

and here is a nice apt-get line to install them:
```

sudo apt-get install autoconf debhelper dh-buildinfo gettext quilt nasm yasm libass-dev libxul-dev liba52-0.7.4-dev libaa1-dev libasound2-dev libaudiofile-dev libavahi-client-dev libavcodec-dev libavformat-dev libcaca-dev libcdio-dev libdca-dev libdvbpsi4-dev libdvdnav-dev libdvdread-dev libesd0-dev libfaad-dev libflac-dev libfreetype6-dev libfribidi-dev libggi2-dev libgl1-mesa-dev libglib2.0-0 libgnutls-dev libhal-dev libid3tag0-dev libidl0 libimlib2-dev libjack-dev liblircclient-dev liblivemedia-dev liblua5.1-0-dev libmad0-dev libmatroska-dev libmodplug-dev libmpcdec-dev libmpeg2-4-dev libncursesw5-dev libnotify-dev libogg-dev libpng12-dev libpostproc-dev libpulse-dev libqt4-dev libschroedinger-dev libsdl-image1.2-dev libsdl1.2-dev libshout3-dev libsmbclient-dev libspeex-dev libsvga1-dev libswscale-dev libsysfs-dev libtag1-dev libtar-dev libtheora-dev libtwolame-dev libv4l-dev libvcdinfo-dev libvorbis-dev libx11-dev libx264-dev libxext-dev libxml2-dev libxpm-dev libxt-dev libxv-dev pkg-config qt4-dev-tools zlib1g-dev

```
Post any errors.
I think that if you install ubuntu-restricted-extras it removes the ffmpeg libs and adds an unstripped version which is incompatible with the dev libs. This could be an issue.
Post any errors you get when executing that apt line.

---

### Post by Clockware on 2009-06-18
Very good! It's work!

I get the dependencies with the sudo line, and built the vlc-1.0.0-rc3 version. 
The 5.1 audio works very fine, now this audio output configuration is chosen by default.

I also modified the /etc/pulse/pulse.conf with the suggestion you provided some posts ago and I set the default-channel to 6.

Very nice. However I configured with the previous configuration for the ubuntu vlc version:

```

'--build=x86_64-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2

```(i just removed the '--enable-maintainer-mode' '--enable-release' because i wasn't sure about them)

And i get this non-fatal error (the player just work fine):

```

VLC media player 1.0.0-rc3 Goldeneye
[0x1c3e0c8] main interface error: no interface module matched "globalhotkeys,none"
[0x1c3e0c8] main interface error: no suitable interface module
[0x1b0a888] main libvlc error: interface "globalhotkeys,none" initialization failed

```So I have two question:
1) I need to improve this ./configure command-line?
2) How can fix the problem with not loaded modules?!

Thank you,
Clockware

---

### Post by danwood76 on 2009-06-19
The reason is that the new vlc version has additional modules.
I would just compile without choosing the various modules and let vlc decide the default modules and compiler settings.

```

./configure --prefix=/usr
make
sudo make install

```

Also you might want to update to rc4 as there is a pulseaudio patch which should improve performance slightly on some systems.

---

