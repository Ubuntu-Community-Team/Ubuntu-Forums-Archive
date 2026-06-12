---
title: "Installing Ubuntu touch/wily/snappy development on 7&quot; tablet"
date: 2015-09-17
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-09-17
Opening this this thread as a spin off of another thread that was current with the vivid cycle. Working with RCA Voyager 7" tablets but other tablet discussion as well.

Also using the reference thread as a valuable resource to get started as those of us who tried to crack it were not successful at that point , but , perhaps things have changed as new tools come down the line.

Regards..

ref: [http://ubuntuforums.org/showthread.php?t=2254725](http://ubuntuforums.org/showthread.php?t=2254725)

---

### Post by ventrical on 2015-09-17
Finally got successful #root#  on RCA Voyager 7" tablet with Kingo Root from the Google App Store.

Regards

---

### Post by cariboo on 2015-09-17
The image I used to get my tablet usable again is already rooted, but I have a feeling that the image may be the wrong one for the tablet, as I keep getting a notification that I need to allow root for something, but haven't been able to do anything about it. To use the flash tool linked to int the thread, you need a scatter file, which is included with the downloaded image. I haven't had time to look at it, but it may be useful in getting some version of Ubuntu on the tablet.

---

### Post by QDR06VV9 on 2015-09-17
> **cariboo said:**
> The image I used to get my tablet usable again is already rooted, but I have a feeling that the image may be the wrong one for the tablet, as I keep getting a notification that I need to allow root for something, but haven't been able to do anything about it. To use the flash tool linked to int the thread, you need a scatter file, which is included with the downloaded image. I haven't had time to look at it, but it may be useful in getting some version of Ubuntu on the tablet.
Is there anything like SuperSU that you can find?
> SuperSU is the Superuser access management tool of the future ;) SuperSU allows for advanced management of Superuser access rights for all the apps on your device that need root. SuperSU has been built from the ground up to counter a number of problems with other Superuser access management tools.

---

### Post by ventrical on 2015-09-18
I am able to use an app called Linux Deploy that downloads and installs ubuntu wily LDXE 15.10. You also have to install VNC Viewer.

There are other options for Kylin , Precise, Debian etc.. but we are in current development versions. I can't seem to get wily  to load in VNC viewer but Linux  Deploy does download and install a 4GB image that is supposed to run parallel  with android . .etc.. Not what I wanted to do but thought it might be good practice.

 The Kingo Root app - cannot get rid of it .. even after hard reset. The google app store and the way that android works is not my idea of a secure  and stable system. Hopefully snappy may provide more continuity... hmmm that would be a good name for a desktop environment .. continutity.

If I do not get this linux install to work on slate I'll do what Cariboo has suggested and take a chance to  brick my tablet because anything is better than this..

---

### Post by ventrical on 2015-09-18
Seding this msg via lubuntu 15.10 through ff on rca voyager 7 inch tab
regards.

```

android@localhost:~$ uname -a
Linux localhost 3.4.67 #1 SMP PREEMPT Fri Jan 9 13:41:06 CST 2015 arm7l arm7l arm7l GNU/Linux


below  hand typed on another terminal because slate is so small :))
lsb_release -a
Distributor ID: Ubuntu
Description      Ubuntu Wily Werewolf (development branch)
Release          15.10
Codename:     wily

```

Will try to

```

sudo apt-get dist-upgrade

```

edit: No upgrades..

---

### Post by ventrical on 2015-09-18
I have two slates so I am going to try the other process as I know now I can get ubuntu development version to work through a vnc, Perhaps even snappy:)

regards..

Just a side note- Installing wily 15.10 on  an android slate using Linux Deploy and VNC Viewer gave me some good practice and insight and a better understanding at how android is setup and working.  Perhaps a slate can be (probably has been ) set up to dual boot an image. One on the internal storage and one on the external ssd card. That would save a lot of time with adb splicing and hacking. And of course for run of the mill/average tablets and external ssds being able to reach as high as 32GB to 64GB on these lower-end slates then it would be the practical process to follow.

---

### Post by ventrical on 2015-09-27
Pic of xubuntu desktop (wily) on RCA 7" Voyager. Awesome speed on arm Quad.

edit:

Lots of bugs though .. ie; when you try to take a screenshot it will just white out but other programs work ok.

---

