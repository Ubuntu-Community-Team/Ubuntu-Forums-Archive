---
title: "HOWTO: transfer videos from your TIVO to your Ubuntu desktop or Android using kmttg"
date: 2011-11-22
forum: Tutorials
---

### Post by michael37 on 2011-11-22
The information in this thread has been moved to [https://help.ubuntu.com/community/TransferVideosFromTIVOToUbuntuOrAndroidUsingKmttg](https://help.ubuntu.com/community/TransferVideosFromTIVOToUbuntuOrAndroidUsingKmttg)

A thread for discussion of the wiki page only can be found here 
[http://ubuntuforums.org/showthread.php?t=2012437](http://ubuntuforums.org/showthread.php?t=2012437)

Thread closed.



Based on [http://code.google.com/p/kmttg/](http://code.google.com/p/kmttg/). This tutorial uses exclusively open source software although kmttg has alternatives to use some commercial software. It takes a while to go through this tutorial, but it is well worth it at the end.

[B][SIZE="3"]INTRODUCTION
[/SIZE][/B]
**kmttg** is a Java based program I [SIZE="1"](not me the author of this tutorial, [a cool developer named Kevin Moye]("http://code.google.com/u/114749745263415438261/"))[/SIZE] wrote to facilitate TivoToGo (TTG) transfers that can download, create pyTivo metadata, decrypt, run comskip & comcut (commercial detection and removal), create closed captions files and re-encode multiple shows you select from your Tivos all automatically. The program also has the capability to transfer and process shows automatically from your Tivos based on titles and keywords you setup.

You can select one or more shows at a time and then with one click of a button the program will download all the selected items, with the options of also automatically creating a metadata file for pyTivo, decrypting .TiVo files to .mpg, running comskip (commercial detection and removal program), and automatically re-encoding to a more portable format using mencoder, ffmpeg or any other command line encoder of your choosing. The program queues up multiple jobs and displays time, size and speed statistics for ongoing jobs.

Previously I was using different point tools to accomplish this, such as Tivo Desktop or TivoPlayList for downloads, pyTivoMetaGen for generating metadata files, Tivo Decoder UI for decrypting and various GUIs built around ffmpeg for re-encoding. I did not want to pay for or be limited by Tivo Desktop Plus. This is my attempt to simplify and automate these different tasks all into 1 simple GUI.

**[SIZE="3"]INSTALLATION[/SIZE]**

1. Install [OpenJDK version of Java](https://help.ubuntu.com/community/Java).
```
sudo apt-get install openjdk-6-jre
```

2. Download kmttg installation zip file from:

[http://code.google.com/p/kmttg/downloads/list](http://code.google.com/p/kmttg/downloads/list) 

Obtain version v0p8l or later.

```

cd ~
mkdir -p kmttg
cd kmttg
wget http://kmttg.googlecode.com/files/kmttg_v0p8r.zip
unzip kmttg_v0p8r.zip

```

3. Install ProjectX video repair.

Although ProjectX exists in Ubuntu repositories, I do not recommend that particular outdated version. Instead, download a **ProjectX_0.91.0.zip** file from [http://sourceforge.net/projects/project-x/files/project-x/ProjectX_0.91.0.00/](http://sourceforge.net/projects/project-x/files/project-x/ProjectX_0.91.0.00/) and place it in /home/$USERNAME/kmttg

Afterwards, unzip downloaded file and create a link:

```
cd ~/kmttg
unzip ProjectX_0.91.0.zip
ln -s Project-X_0.91.0 ProjectX

```

4. Download and build tivodecode.

```
sudo apt-get install build-essential
cd ~/kmttg
wget http://kmttg.googlecode.com/files/tivodecode-0.3pre4.tar.gz
tar xvfz tivodecode-0.3pre4.tar.gz
cd tivodecode-0.3pre4/
./configure
make
cd ..
ln -s tivodecode-0.3pre4 tivodecode

```

5. Download comskip and wine and configure comskip to run via wine.
While comskip is open source software, folks haven't quite figured out how to build it on Linux due to a number of complexities. So, we will use a windows build instead and use wine to execute it. Don't worry, it will all be under the covers.

```
sudo apt-get install wine
cd ~/kmttg
wget http://www.kaashoek.com/files/comskip80_042.zip
mkdir -p comskip
cd comskip
unzip ../comskip80_042.zip
echo 'wine "$0".exe "$@"' > comskip
chmod +x comskip

```

6. Download HandBrake encoder.

```
sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-cli handbrake-gtk

```

7. Download Atomic Parsley metadata processor.

```

sudo apt-get install atomicparsley

```

**[SIZE="3"]CONFIGURATION[/SIZE]**

You must know your 10 digit Media Access Key (MAK) for your TIVO. PLEASE do not post your MAK in these forums! 

From [http://support.tivo.com/app/answers/detail/a_id/196](http://support.tivo.com/app/answers/detail/a_id/196), question "Unable to transfer video from TiVo DVR to PC"
>     NOTE: You can find your Media Access Key in either of these two places:

    From your TiVo DVR: Go to TiVo Central, select Messages & Settings, then Account & System Information, and then Media Access Key.
    Online: Log in to your My TiVo account.


When I say $USERNAME, I mean your actual username. 

[LIST]
[*]Run kmttg by typing ~/kmttg/kmttg
[*]Enter your MAK
[*]Configure your software by selecting File/Configure and selecting Programs tab
[*]Check that kmttg auto-detected your handbrake at /usr/bin/HandBrakeCLI
[*]Check that kmttg auto-detected your tivodecode at /home/$USERNAME/tivodecode/tivodecode
[*]Check that kmttg auto-detected your comskip at /home/$USERNAME/kmttg/comskip/comskip
[*]Check that kmttg auto-detected your ProjectX as /home/$USERNAME/kmttg/ProjectX/ProjectX.jar
[/LIST]

You are almost there!

**[SIZE="3"]USE[/SIZE]**

[LIST]
[*]Click Refresh for kmttg to update list of your TIVO programs
[*]Select checkboxes &#9745; metadata &#9745; decrypt &#9745; QS Fix &#9745; Ad Detect &#9745; Ad Cut &#9745; encode
[*]Select Encoding Profile: **hb_television**
[*]Select your favorite programs and click **[COLOR="Lime"][START JOBS][/COLOR]** on the top left.
[/LIST]

Wait, and then enjoy your videos on your computer or your mobile device.

Note that encoding profile **hb_television** is a good place to start but is not a perfect profile. There is truly no perfect encoding profile, so use HandBrake GUI to optimize your encoding experience. A file encoded using hb_television profile won't play on your Android phone or tablet (you would not use a closed source tablet, would you?), so use ff_droid or hb_iphone preset instead for taking your TIVO shows on the road.

---

### Post by nothingspecial on 2011-12-06
Nice tutorial :)

---

### Post by Iloru on 2011-12-08
Very nice tutorial, thanks for posting it!  :)

---

### Post by ba70816 on 2011-12-20
Thanks for your tutorial but being a linux moron when trying to follow the steps, I copied and pasted them into my terminal session but I got a number of errors and am not really sure how to overcome them.

First I got,  Package sun-java6-fonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Unable to locate package sun-java6-bin
E: Package 'sun-java6-fonts' has no installation candidate

Then is step 4 missing a mkdir command?

Ultimately, I got this error when I ran kmttg
ERROR: java.awt.HeadlessException
	at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:173)
	at java.awt.Window.<init>(Window.java:476)
	at java.awt.Frame.<init>(Frame.java:419)
	at java.awt.Frame.<init>(Frame.java:384)
	at javax.swing.JFrame.<init>(JFrame.java:174)
	at com.tivo.kmttg.gui.gui.getJFrame(gui.java:106)
	at com.tivo.kmttg.main.kmttg$2.run(kmttg.java:66)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
	at java.awt.EventQueue.dispatchEventImpl(EventQueue.java:647)
	at java.awt.EventQueue.access$000(EventQueue.java:96)
	at java.awt.EventQueue$1.run(EventQueue.java:608)
	at java.awt.EventQueue$1.run(EventQueue.java:606)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.security.AccessControlContext$1.doIntersectionPrivilege(AccessControlContext.java:105)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:617)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)

Any help would be so appreciated.

---

### Post by michael37 on 2011-12-20
> **ba70816 said:**
> 
E: Unable to locate package sun-java6-bin
E: Package 'sun-java6-fonts' has no installation candidate


UPD: Below is no longer a good advice. See later posts.

[s]
I suspect you may not have Partner repositories enabled.

Try clicking on this link:
[apt:sun-java6-fonts?channel=$distro-partner]("apt:sun-java6-fonts?channel=$distro-partner")
[apt:sun-java6-bin?channel=$distro-partner]("apt:sun-java6-bin?channel=$distro-partner")

If that doesn't work, read [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Canonical_Partner_Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Canonical_Partner_Repositories")
[/s]
Also, step 4 is missing an "tar" command, thank you for noticing!
I fixed step 4.

---

### Post by ba70816 on 2011-12-21
Thanks Micheal,
It seems like all the steps were installed correctly but I still have this error when I run kmttg:
ERROR: java.awt.HeadlessException
	at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:173)
	at java.awt.Window.<init>(Window.java:476)
	at java.awt.Frame.<init>(Frame.java:419)
	at java.awt.Frame.<init>(Frame.java:384)
	at javax.swing.JFrame.<init>(JFrame.java:174)
	at com.tivo.kmttg.gui.gui.getJFrame(gui.java:106)
	at com.tivo.kmttg.main.kmttg$2.run(kmttg.java:66)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
	at java.awt.EventQueue.dispatchEventImpl(EventQueue.java:647)
	at java.awt.EventQueue.access$000(EventQueue.java:96)
	at java.awt.EventQueue$1.run(EventQueue.java:608)
	at java.awt.EventQueue$1.run(EventQueue.java:606)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.security.AccessControlContext$1.doIntersectionPrivilege(AccessControlContext.java:105)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:617)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)

BTW - the smiley faces are supposed to be the number 8.

I've searched the problem but can't find the fix, I'm sure it's got to be something simple. I'm running Ubuntu 11.1.

Any ideas?
Thanks

---

### Post by ba70816 on 2011-12-21
I finally got it... I had to run  
sudo apt-get install openjdk-6-jre

Thanks again so much

---

### Post by michael37 on 2011-12-23
> **ba70816 said:**
> I finally got it... I had to run  
sudo apt-get install openjdk-6-jre

Thanks again so much

Amazing, I just discovered this java problem (it occurred on December 15th): 
[https://lists.ubuntu.com/archives/ubuntu-security-announce/2011-December/001528.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2011-December/001528.html)

I will update my instructions with OpenJDK.

---

### Post by michael37 on 2012-01-07
Updated instructions with latest version of kmttg and added Atomic Parsley section. I guess I forgot about that tool earlier.

---

### Post by Robertjm on 2012-03-10
Thanks for the easy instructions to follow. I've installed it on Precise and it seems to be running.

However, I just downloaded a program and it seems to is stuck in the remux stage. It got up to 86%, and has been sitting there for a good 10 minutes.

Does it usually take that long in this step, or did something happen? 

Robert

---

### Post by madscientist on 2012-05-08
I'm downloading a file right now--very nice!!

FYI, for a fresh install of Ubuntu 12.04 I needed the following extra/different steps:

First, you need to:

```
sudo apt-get install curl mencode
```

because those aren't installed by default.

Second, the handbrake release area doesn't support 12.04 so you have to use the snapshot area; change the add-apt-repository to:

```
sudo add-apt-repository ppa:stebbins/handbrake-snapshots
```

Then it all worked for me!

---

### Post by madscientist on 2012-05-08
Oh and a slight improvement on your comskip shell script, which avoids customization for the current directory:

```
echo 'wine "$0".exe "$@"' > comskip
```

---

### Post by madscientist on 2012-05-08
Something else: I have a 64bit Ubuntu install and comskip is a 32bit app; when I run it under wine I get a warning:

```
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
```

This requires a 32bit version of gnome-keyring installed but there's a missing dependency so it doesn't work.  I've asked about this and I'll update here if/when I figure it out.  It's possible that comskip will still run: if I run "comskip --help" it gives that error but still runs (and shows some help).  I'm still downloading my first show so we'll see what happens after it's done.

---

### Post by Robertjm on 2012-05-08
Definitely keep us informed madscientist. Whiel the program seemed to run on my Ubuntu 12.94 64bit system, it always seemed to blow up at the end, so I'm intrigued to see if anything changed since I tried it.

Fingers crossed,

Robert

---

### Post by madscientist on 2012-05-08
I had to go to work while the show was still downloading.  When I got home I discovered it failed in the HandBrakeCLI step; as above I have to use the snapshot PPA because there's no release PPA for Ubuntu 12.04.  When I use this (version 4650svnppa1~precise1) I get this error from kmttg:

```
encoding failed (exit code: 1 ) - check command: /usr/bin/HandBrakeCLI -i "/home/me/TVShows/MyShow_cut.mpg" --cpu 4 -t 1 -c 1 -f mkv --large-file --decomb --detelecine -e x264 -b 1300 -2 -T -a 1 -E faac -B 160 -6 dpl2 -D 1 -x ref=3:mixed-refs=1:bframes=6:weightb=1:direct=auto:b-pyramid=1:me=umh:subq=9:analyse=all:8x8dct=1:trellis=1:nr=150:no-fast-pskip=1:psy-rd=1,1 -v -o "/home/me/TVShows/MyShow.mkv" 
/usr/bin/HandBrakeCLI: unrecognized option '--cpu'
unknown option (--cpu)
```

I've edited the .enc files to remove the --cpu flag and its argument and I'm trying again.

---

### Post by michael37 on 2012-05-08
> **madscientist said:**
> Something else: I have a 64bit Ubuntu install and comskip is a 32bit app; when I run it under wine I get a warning:

```
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
```

This requires a 32bit version of gnome-keyring installed but there's a missing dependency so it doesn't work.  I've asked about this and I'll update here if/when I figure it out.  It's possible that comskip will still run: if I run "comskip --help" it gives that error but still runs (and shows some help).  I'm still downloading my first show so we'll see what happens after it's done.

I also have 32-bit comskip.exe and 64-bit ubuntu. Wine is supposed to take care of the conversion, I have no idea where this error is coming from. Perhaps from your wine config?

Besides, my file /usr/lib/gnome-keyring/gnome-keyring-pkcs11.so is 64-bit:
```

$ file /usr/lib/gnome-keyring/gnome-keyring-pkcs11.so
/usr/lib/gnome-keyring/gnome-keyring-pkcs11.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

```

---

### Post by madscientist on 2012-05-09
Michael: the issue with wine is a known bug; see [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/885492](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/885492)

---

### Post by madscientist on 2012-05-09
Hrm.  On this second attempt I tried to choose a smaller file (The Simpsons episode) to avoid longer download times.  While the first file worked all the way up to the HandBrakeCLI step, on this second attempt I ran into the same problem Robertjm hit.  The ffmpeg remux step got to 44% and hung.  I left it running overnight but no change.

strace shows that it's simply mmap()ing memory, then munmapping it, then mmapping more memory, then munmapping it, continuously.  I thought I'd leave it overnight to see what happened when it ran out but even after 10 hours or so it's still running:

```
mmap(NULL, 1292320768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f84be747000
munmap(0x7f850b7bb000, 1292304384)      = 0
mmap(NULL, 1292374016, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f84716c6000
munmap(0x7f84be747000, 1292320768)      = 0
mmap(NULL, 1292386304, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f850b7a7000
munmap(0x7f84716c6000, 1292374016)      = 0
mmap(NULL, 1292414976, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f84be71c000
munmap(0x7f850b7a7000, 1292386304)      = 0
```

I tried attaching with the debugger but the stack trace is not too interesting:

```
#0  0x00007f855d435897 in munmap () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007f855dc250ba in av_fifo_realloc2 ()
   from /usr/lib/x86_64-linux-gnu/libavutil.so.51
#2  0x00007f855f11ee93 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libavformat.so.53
#3  0x00007f855f168559 in av_write_trailer ()
   from /usr/lib/x86_64-linux-gnu/libavformat.so.53
#4  0x000000000040c5ba in ?? ()
#5  0x0000000000407904 in ?? ()
#6  0x00007f855d36876d in __libc_start_main ()
   from /lib/x86_64-linux-gnu/libc.so.6
#7  0x0000000000407a71 in ?? ()
#8  0x00007fff538af158 in ?? ()
#9  0x000000000000001c in ?? ()
#10 0x000000000000000f in ?? ()
#11 0x00007fff538b1363 in ?? ()
#12 0x00007fff538b1373 in ?? ()
#13 0x00007fff538b1376 in ?? ()
#14 0x00007fff538b137e in ?? ()
#15 0x00007fff538b1385 in ?? ()
#16 0x00007fff538b1388 in ?? ()
#17 0x00007fff538b13d3 in ?? ()
#18 0x00007fff538b13d6 in ?? ()
#19 0x00007fff538b1421 in ?? ()
#20 0x00007fff538b1429 in ?? ()
#21 0x00007fff538b142e in ?? ()
#22 0x00007fff538b1436 in ?? ()
#23 0x00007fff538b143b in ?? ()
#24 0x00007fff538b143e in ?? ()
#25 0x00007fff538b1442 in ?? ()
#26 0x0000000000000000 in ?? ()
```

It seems to be the av_write_trailer() function that's causing this; if I step through with GDB that seems to be the one it never returns from.  If I set a breakpoint in mmap() I get this backtrace:

```
#0  0x00007f855d435860 in mmap64 () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007f855d3c7f5d in ?? () from /lib/x86_64-linux-gnu/libc.so.6
#2  0x00007f855d3c8291 in ?? () from /lib/x86_64-linux-gnu/libc.so.6
#3  0x00007f855d3ca556 in memalign () from /lib/x86_64-linux-gnu/libc.so.6
#4  0x00007f855d3cb799 in posix_memalign ()
   from /lib/x86_64-linux-gnu/libc.so.6
#5  0x00007f855dc282ab in av_malloc ()
   from /usr/lib/x86_64-linux-gnu/libavutil.so.51
#6  0x00007f855dc24df9 in av_fifo_alloc ()
   from /usr/lib/x86_64-linux-gnu/libavutil.so.51
#7  0x00007f855dc2508f in av_fifo_realloc2 ()
   from /usr/lib/x86_64-linux-gnu/libavutil.so.51
#8  0x00007f855f11ee93 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libavformat.so.53
#9  0x00007f855f168559 in av_write_trailer ()
   from /usr/lib/x86_64-linux-gnu/libavformat.so.53
#10 0x000000000040c5ba in ?? ()
#11 0x0000000000407904 in ?? ()
#12 0x00007f855d36876d in __libc_start_main ()
   from /lib/x86_64-linux-gnu/libc.so.6
#13 0x0000000000407a71 in ?? ()
#14 0x00007fff538af158 in ?? ()
#15 0x000000000000001c in ?? ()
#16 0x000000000000000f in ?? ()
#17 0x00007fff538b1363 in ?? ()
#18 0x00007fff538b1373 in ?? ()
#19 0x00007fff538b1376 in ?? ()
#20 0x00007fff538b137e in ?? ()
#21 0x00007fff538b1385 in ?? ()
#22 0x00007fff538b1388 in ?? ()
#23 0x00007fff538b13d3 in ?? ()
#24 0x00007fff538b13d6 in ?? ()
#25 0x00007fff538b1421 in ?? ()
#26 0x00007fff538b1429 in ?? ()
#27 0x00007fff538b142e in ?? ()
#28 0x00007fff538b1436 in ?? ()
#29 0x00007fff538b143b in ?? ()
#30 0x00007fff538b143e in ?? ()
#31 0x00007fff538b1442 in ?? ()
#32 0x0000000000000000 in ?? ()
```

---

### Post by madscientist on 2012-05-09
Hm.  I killed this ffmpeg to let the process continue, then it hung again in the same place (again at 44% done) in the same way during the ffmpeg remux step.  I killed that too and it's proceeding to the encode step (most likely the result will be corrupted but I wanted to see what happened).

One interesting thing I noticed in the kmttg log panel after I kill ffmpeg was this:

```
>> Running ffmpeg remux to generate /home/me/MyTv/The Simpsons.mpg.qsfix ...
/usr/bin/ffmpeg -y -fflags genpts -i "/home/me/MyTvThe Simpsons.m2v" -i "/home/me/MyTv/The Simpsons.ac3" -acodec copy -vcodec copy -f dvd "/home/me/MyTv/The Simpsons.mpg.qsfix" 
remux failed (exit code: 143 ) - check command: /usr/bin/ffmpeg -y -fflags genpts -i "/home/me/MyTv/The Simpsons.m2v" -i "/home/me/MyTv/The Simpsons.ac3" -acodec copy -vcodec copy -f dvd "/home/me/MyTv/The Simpsons.mpg.qsfix" 
ffmpeg version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Mar 22 2012 05:09:06 with gcc 4.6.3
This program is not developed anymore and is only provided for compatibility. Use avconv instead (see Changelog for the list of incompatible changes).
```

Note the comment at the end... maybe kmttg should be changed to use avconv instead?

---

### Post by DrewLGT on 2012-05-09
can i transfer video TO my tivo with this?

---

### Post by madscientist on 2012-05-09
> **DrewLGT said:**
> can i transfer video TO my tivo with this?

Transferring TO your TiVo is ***much*** simpler.  Go get [pyTivo from here]("http://pytivo.sourceforge.net/wiki/index.php/Linux_Install") and that's all you need to do.  It's very simple, very easy.  You may need to install "ffmpeg" (you can find it by searching Add/Remove Sources) if you don't have it already.

Other than that you just have to edit the pyTivo config file to tell it where on your Linux system you keep your videos, then start it up.

Now on your TiVo, go to Now Playing and scroll to the bottom and you'll see a new folder there with the name you used in the pyTivo config file; enter it and select the items you want to play.

---

### Post by madscientist on 2012-05-09
FYI I filed [a bug in Launchpad here]("https://bugs.launchpad.net/ubuntu/+source/libav/+bug/997360") about the "hang" during ffmpeg.  If you see this problem and have a Launchpad account you should go mark that bug as affecting you: the more people that it impacts the more likely someone will look at it.

What does the "QS Fix" step do in kmttg, anyway?  I haven't been able to figure it out.  That appears to be the step that's hanging.

---

### Post by DrewLGT on 2012-05-09
> **madscientist said:**
> Transferring TO your TiVo is ***much*** simpler.  Go get [pyTivo from here]("http://pytivo.sourceforge.net/wiki/index.php/Linux_Install") and that's all you need to do.  It's very simple, very easy.  You may need to install "ffmpeg" (you can find it by searching Add/Remove Sources) if you don't have it already.

Other than that you just have to edit the pyTivo config file to tell it where on your Linux system you keep your videos, then start it up.

Now on your TiVo, go to Now Playing and scroll to the bottom and you'll see a new folder there with the name you used in the pyTivo config file; enter it and select the items you want to play.



thank you for that!


Im a total linux newb. can you point me towards a guide to install this?

i see this in the wiki:
unzip pyTivo-nnn.zip cd pyTivo vi pyTivo.conf /path/to/python pyTivo.py

i know these are commands to be used in terminal, but as is, they dont do anything

---

### Post by Elfy on 2012-06-29
This thread is closed. 
 
The information is now held on the community wiki at  [https://help.ubuntu.com/community/TransferVideosFromTIVOToUbuntuOrAndroidUsingKmttg](https://help.ubuntu.com/community/TransferVideosFromTIVOToUbuntuOrAndroidUsingKmttg)
 
Thank you for your thread and the work you have done in keeping it current and of use to the community. 
 
A thread for discussion of the wiki can be found at  [http://ubuntuforums.org/showthread.php?t=2012437](http://ubuntuforums.org/showthread.php?t=2012437)
 
 
Support threads regarding the wiki and it's content should be created in a suitable forum.

---

