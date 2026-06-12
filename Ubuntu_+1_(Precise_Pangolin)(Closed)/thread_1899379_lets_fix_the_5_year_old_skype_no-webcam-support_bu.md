---
title: "lets fix the 5 year old skype no-webcam-support bug for good."
date: 2011-12-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by madjr on 2011-12-23
skype is mainly used for **VIDEO to VIDEO** calls, this works great on every OS, but this Doesnt work in ubuntu.... a 5 year old silly bug that can be fixed in one command (but this command can be hard to find sometimes), usually changes from release to release and is not accesible to non-techies.

this mainly makes ubuntu (and YOU) look bad when you give it to a friend...

vote to solve this bug once and for all.
[https://bugs.launchpad.net/ubuntu/+source/skype/+bug/908174](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/908174)

---

### Post by hakermania on 2011-12-23
Did so, although I know that many could have Skype working without any command or such.

---

### Post by rajeev1204 on 2011-12-23
Skype works fine on Ubuntu. Iam not sure if you talk of a specific bug.

64 bit users have to use the ld_preload command to get video, otherwise the 32 bit version works fine without any commands on systems i have tested it with. AFAIK skype has been working fine on most standard webcams for some time now.

---

### Post by madjr on 2011-12-23
> **rajeev1204 said:**
> Skype works fine on Ubuntu. Iam not sure if you talk of a specific bug.

64 bit users have to use the ld_preload command to get video, otherwise the 32 bit version works fine without any commands on systems i have tested it with. AFAIK skype has been working fine on most standard webcams for some time now.

weird because skype webcam support was not working this morning in 11.10 (32bit), nor any release prior to that (which i also keep a few installed). Till i used the command on the bug report.

webcam has always worked fine with cheese out of the box , but not with skype as many users in many threads complain about.

not to mention the next LTS will be 64bit by default, so everyone will have the problem now if they dont resolve it.

---

### Post by rajeev1204 on 2011-12-23
> **madjr said:**
> weird because skype webcam support was not working this morning in 11.10 (32bit), nor any release prior to that (which i also keep a few installed). Till i used the command on the bug report.

webcam has always worked fine with cheese out of the box , but not with skype as many users in many threads complain about.

not to mention the next LTS will be 64bit by default, so everyone will have the problem now if they dont resolve it.


Maybe its a problem with your webcam?  As far as the 64 bit version is concerned, the version from the ubuntu repositories was patched to run fine on a 64 bit OS. A later update broke it though. 

Well, i have read about the problem you mention, but from your post it seems webcams dont work with skype at all. Which is not exactly right.

---

### Post by rtalcott on 2011-12-23
I have never had problems with Skype video (or Skype) for the last 2-3 years and I have been using both the 32 and 64 bit OS...have not tried 12.04 yet...but that should happen soon.
rt

---

### Post by madjr on 2011-12-23
> **rajeev1204 said:**
> Maybe its a problem with your webcam?  As far as the 64 bit version is concerned, the version from the ubuntu repositories was patched to run fine on a 64 bit OS. A later update broke it though. 

Well, i have read about the problem you mention, but from your post it seems webcams dont work with skype at all. Which is not exactly right.

Ok, I have tested 3 or 4 cams in different computers and always had the same problem. So I thought it was a problem with all/most webcams. Maybe only a limited number of cams work by default with skype on linux?

All the ones i tested work fine in cheese and not in skype, which am not sure why. I think they need to find out why this is not consistent. I believe that any webcam that works well with cheese should work equally well with any other app that would make use of it. else is frustrating for the user and faults ubuntu for it. Skype being under developed on linux also amplifies this misconception.

Some time ago my brother stopped booting into ubuntu because of this. Am trying to convince him again... ;/

---

### Post by rtalcott on 2011-12-23
Which cameras have your tried?  I have 2 Logitech webcams...and neither has given me any problems...
rt

---

### Post by cecilpierce on 2011-12-24
Skype has not worked for me since 10.10 without adding libs to the skype loader, Im using a Logitech cam and it worked in 10.10 and windoz but not in the newer Ubuntu's, so all you other people are just lucky  :P

---

### Post by jockyburns on 2011-12-24
Never had a problem with Skype (running 11.04 Natty) Worked from day one, although I did have to set it to use my usb webcam, as it defaulted to my Asus TV Card.

---

### Post by sammiev on 2011-12-24
Had to add the libs for the 64bit version only. Will try it today again to see if I still need to. There was a few threads on this about 6 months back.

---

### Post by Merk42 on 2011-12-24
Anecdotal: I have a logitech QuickCam Communicate STX and while it worked fine in cheese*. It wouldn't work in Skype without the LD_PRELOAD thing.


*Cheese doesn't work at all right now, but I think that may be more UNity 2D than 11.10
```
Xlib:  extension "GLX" missing on display ":0".

(cheese:4293): Clutter-CRITICAL **: Unable to initialize Clutter: The OpenGL version could not be determined

```

---

### Post by madjr on 2011-12-24
> **rtalcott said:**
> Which cameras have your tried?  I have 2 Logitech webcams...and neither has given me any problems...
rt

@rtalcott

I would like to test if the "preload" command affects working webcams.

can you (or someone with a webcam skype auto detects) drag a shortcut to your desktop, add the "preload" command and see if the cams keep working as usual ?

commands are here:
[http://ubuntuforums.org/showthread.php?t=1860519](http://ubuntuforums.org/showthread.php?t=1860519)
[http://community.skype.com/t5/Linux/video-is-not-working-on-Ubuntu-11-10/td-p/216792](http://community.skype.com/t5/Linux/video-is-not-working-on-Ubuntu-11-10/td-p/216792)

---

### Post by sammiev on 2011-12-24
Unloaded the 32 bit version on my system and tried to replace it with the 64 bit system which my computer is set up for and I get this error which is the same error I got many months back. Error: Cannot install 'ia32-libs'. There is a fix for this but as I reload my computer all the time, I just use the 32 bit version for now. :)

---

### Post by rtalcott on 2011-12-24
@ madjr:

I'm probably doing something wrong...on a 64 bit system...getting this:  ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

but then Skype starts up and works...Beta 2.2.0.35
rt

---

### Post by madjr on 2011-12-25
> **rtalcott said:**
> @ madjr:

I'm probably doing something wrong...on a 64 bit system...getting this:  ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

but then Skype starts up and works...Beta 2.2.0.35
rt

Ok, thanks for taking the time to test it. some of the posts mention installing the 32bit version of the package for 64 bit systems.
```
sudo apt-get install libv4l-0:i386
```

then one of these commands:

```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

or 

```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

or 

```
env LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

note "env" at the start.

---

### Post by rtalcott on 2011-12-25
@ madjr:  i believe I have been using the 64 bit "beta" from Skype on 64 bit 10.10...11.04 $ 11.10....have not put a camera on my 12.04 machines yet...
rt

---

