---
title: "Stuck at grub&gt; after clean Gusty CD install on daru2. Help!"
date: 2007-11-16
forum: System76 Support
---

### Post by GregCwx1 on 2007-11-16
I thought a clean reinstall of Gusty would help clear up some lingering CD/DVD and gnome issues on my daru2. So, I backed up my home/account and decided to try a CD install of 7.10 using the alt CD. I checked both the mdsum and the CD integrity before wiping everything clean and starting again. All went well excecpt for an initial failure to detect DHCP networking (and I skipped over that to come back later). However, my real problem is that the /stage1 cannot be located and the grub bootloader fails to install! This is not good. What the heck have I done now?

It seems this may have something to do with the FS being mounted on a scsi drive /dev/sd? but I'd think that ubntu would be advanced enough to find the right place to install grub on the MBR of such a drive. I'm hoping this is something you system76 guys have seen and can provide me with an easy fix. I'm getting a little uneasy about some of the issues I've had with the Gusty upgrade on the daru2 and I'd prefer to work these issues out instead of having to ship the laptop back to you!

---

### Post by palintheus on 2007-11-16
hmm, I clean installed my laptop(daru2) without issue...did you use a livecd or an alternate?

---

### Post by thomasaaron on 2007-11-16
I've not run into that one before.
So, imagine how hard it would be to duplicate!

I'd just re-install (sorry, I know you hate to hear that). BTW: Plug in your ethernet cable BEFORE starting the computer to re-install. Then your DHCP should configure, if it doesn't, try it a couple of times.

---

### Post by theologian aaron on 2007-11-16
if it's just a grub issue, you could try installing something like[ GAG]("http://gag.sourceforge.net/").  might fix the problem, and also is pretty cool if you dual/triple/quadruple boot.


Good luck!

---

### Post by GregCwx1 on 2007-11-16
I retraced my steps and had success the 2nd time around. I think the problem the first time may have been my selection of "guided" partitioning. In the second and successful attempt I had to drop down on selection and use the full disk for the FS.

I did have a slight scare after the the software was fully installed when I got an error about that. I ran that step again without the error and then grub loaded fine. Whew! Thanks for the responses.

I have followed the system76 steps to update, wget the 76driver.deb package and restore that.

At this point I have some gtstreamer issues with sound. Upon clicking on the muted speaker icon I get this:

> "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."



Also, There is no battery/ac power icon on the task bar. I guess I have to add that from the menu,

While I'm at this very basic stage all else seems stable. I have tried the OO spreadsheet and was able to get help F1 which previously caused that app to crash. I was also able to get help/F1 from Nautilus which is also something else that was not working prior to the complete reinstall. So, by all appearances, I'm better off!

Thanks.

---

### Post by palintheus on 2007-11-16
That sound error was the same issue I was having trouble with. You may check your alsa-base file, the Sys76 driver should have added ```
options snd-hda-intel model=targa-dig
``` as the last line in the file.

---

### Post by GregCwx1 on 2007-11-16
palintheus,

That exact line *is* in this file. Did you mean another alsa-base?

/etc/modprobe.d/alsa-base

I'm still messing with other settings but it would be nice to get sound working right.

Thanks!

---

### Post by palintheus on 2007-11-16
Thats the one I meant...

I had this issue when I installed using the alternate cd, and after I ran the Sys76 driver, I didn't mess around much, I just reinstalled ubuntu and my sound worked without the Sys76 driver, although the headphone sensing did not work. I waited several days prior to running the driver, once I did though my sound continued to work and the headphone sensing started to work.

---

### Post by GregCwx1 on 2007-11-16
I just tried running the audio settings manager in the services at startup but still no sound recognized on the system.

I'm looking over the help here:

[http://knowledge76.com/index.php/Guide_to_Sound_Problems#Using_alsa-source](http://knowledge76.com/index.php/Guide_to_Sound_Problems#Using_alsa-source)

and I can see the pci audio device detected but that's as far as I've gotten so far.

I'm currently working this issue and I know there will be others. Thanks and stay tuned!

---

### Post by GregCwx1 on 2007-11-16
Update:

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")

This was a good resource after I googled ubuntu ich8 problems.

I followed the instructions and sound worked! Only one problem...

I then encountered unexplained crashing of various python apps! Holy smokes!
I had to reinstall the add/remove gnome app, and the software sources app. I confirmed it must have been pyhton that was choaking because the system76 app even crashed with some python/gtk errors. So, I turned off the backports sources in source.list, did a sudo apt-get update (I'm not sure this did anything), and reboot. 

Upon resume my network was hosed. I turned off the laptop and went to get lunch (always a good plan). Came back, restarted, and so far, so good.

I'm glad I have the day off to do this! Anyone want to venture a guess on how the backports sources could cause problems?

Thanks for all the help. Oh, I also just confirmed that hibernate works fine.

---

### Post by thomasaaron on 2007-11-16
GregCwx1,

The sound problems are probably becuase you used update manager to update the system after installing, as opposed to the dist-update and dist-upgrade commands.

There is some problem with update manager that screws up gstreamer.

BTW: Did you run the system 76 driver (Restore tab and restore button). If you used the dist-update and dist-upgrade commands, running the driver should restore sound.

---

### Post by FuturePilot on 2007-11-16
> **GregCwx1 said:**
> Update:

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")

This was a good resource after I googled ubuntu ich8 problems.

I followed the instructions and sound worked! Only one problem...

I then encountered unexplained crashing of various python apps! Holy smokes!
I had to reinstall the add/remove gnome app, and the software sources app. I confirmed it must have been pyhton that was choaking because the system76 app even crashed with some python/gtk errors. So, I turned off the backports sources in source.list, did a sudo apt-get update (I'm not sure this did anything), and reboot. 

Upon resume my network was hosed. I turned off the laptop and went to get lunch (always a good plan). Came back, restarted, and so far, so good.

I'm glad I have the day off to do this! Anyone want to venture a guess on how the backports sources could cause problems?

Thanks for all the help. Oh, I also just confirmed that hibernate works fine.
I'm thinking the Python issues are not related. The linux-backports-modules-generic only contains kernel modules. It shouldn't have done anything to Python.

---

### Post by GregCwx1 on 2007-11-16
Here's the error message after running the add/remove app from the command line:

> myname@ubuntu:~$ /usr/bin/gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 30, in <module>
    main()
  File "/usr/lib/python2.5/site-packages/AppInstall/activation.py", line 435, in main
    from AppInstall import AppInstall
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 30, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: /var/lib/python-support/python2.5/gtk-2.0/gtk/_gtk.so: undefined symbol: gtk_tooltips_force_window


This is affecting other python-based apps too.  None of them run from the icon as they just crash in the background, I can generate the error by attempting to run from the term.

Any ideas?

---

### Post by GregCwx1 on 2007-11-17
In response to thomasarron,

I did not use update manager after the clean install. I used a failsafe terminal to run update and dist-upgrade. The sound issues resulted from a completely clean reinstall on the daru2.

Unfortunately, I am now encountering python gtk errors as noted in my previous post. Since it is not clear that these resulted from the new install, I may start a new thread related to those.

I'll try to track down the problems and post here if I can fix. If not, I'll start a new thread.

---

### Post by thomasaaron on 2007-11-19
Apparently, that sound fix you used (we have a better one in place now, by the way) broke some dependencies.

Try doing this:

sudo apt-get install -f  #May fix broken dependencies

#Update any dependencies that were added
sudo apt-get update && sudo apt-get --assume-yes dist-upgrade 

#Reload Python & GTK library
sudo apt-get --reinstall install python2.5 python-gtk2 python-pygtksourceview

sudo reboot

Let's see what errors you get after doing all of that.

---

### Post by GregCwx1 on 2007-11-20
thomasaaron!

You are the Man! I followed your apt-get instructions and it appears that the python issues are fixed! You would not believe how many google links I tried to find a solution to that. I was going down the apt-get reinstall road but was losing confidence in finding a fix. Thanks a lot! I'm sticking with gnome for now and I'm looking to get more actual work done on the laptop now that it appears that I've got a more stable platform. Thanks again! You guys at System76 are great and please keep up the good work! Happy Thanksgiving!

---

