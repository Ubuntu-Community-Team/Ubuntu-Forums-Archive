---
title: "Kino DV Capture"
date: 2009-11-02
forum: Ubuntu Studio
---

### Post by markosjal on 2009-11-02
I am tryiong to set up Kino With DV capture on Ubuntu 9.04, and I keep seeing n preferences that the IEE1394 subsystem is not responding. 
I followed the suggestions at
[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire) 


In my case the /devs/raw1394 does not exist. I have reinstalled raw1384 packages twice now. 

What need I do to make this work?

---

### Post by andied on 2009-11-04
I got the same "IEE1394 subsystem is not responding" error until I found this thread:

[http://ubuntuforums.org/showthread.php?t=329994](http://ubuntuforums.org/showthread.php?t=329994)

"sudo chmod 777 /dev/raw1394"     enabled my firewire in Kino; however when I tried to capture Kino crashed. I don't know why Kino crashed, I had wasted too much time already and went to XP to get my job done.

---

### Post by openzin on 2009-11-06
> **andied said:**
> I got the same "IEE1394 subsystem is not responding" error until I found this thread:

[http://ubuntuforums.org/showthread.php?t=329994](http://ubuntuforums.org/showthread.php?t=329994)

"sudo chmod 777 /dev/raw1394"     enabled my firewire in Kino; however when I tried to capture Kino crashed. I don't know why Kino crashed, I had wasted too much time already and went to XP to get my job done.

Exactly same problem happens for me (chmod gives firewire working but Kino crashed just after capturing is started). Same problem (crash on playing dv files) is with Totem, it gives the following message in terminal:

The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
(Details: serial 54 error_code 11 request_code 133 minor_code 19)
(Note to programmers: normally, X errors are reported asynchronously;
that is, you will receive the error a while after causing it.
To debug your program, run it with the --sync command line
option to change this behavior. You can then get a meaningful
backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by openzin on 2009-11-07
I had a look on "HowTo" description here [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) and found the follwoing: "Those of you who are having general issues with video playback being blank with just sound, either don't have the right codecs installed (see Part 1), or have graphics driver issues. Some of you may be able to solve it by disabling desktop effects in "System > Preferences > Appearance > Effects"."

This basically resolves my problem, i.e. advanced "Effects" are responsible for video problems. Both Totem and Kino are working with no screen effects.

---

### Post by andied on 2009-11-07
Yeah, I have read a number of suggestions to disable special effects, compiz, etc., but for me, XP works pretty much flawlessly and the main advantage I can determine to using Linux, at the present time, is for the nice "eye candy" and desktop effects.

---

### Post by openzin on 2009-11-07
Yes, I was a bit dissappointed with 9.1 (after 9.04 which worked very stable and I moved 3 my home PC from XP to ubuntu), but seems now verything is settled more or less with this new version. You, for instance, could have just one simple account for movie editing, but others with all special effects.

---

### Post by hakan26 on 2011-02-25
Have you tried "sudo kino". It works for me.

---

