---
title: "Fedora on Pangolin?"
date: 2011-06-24
forum: System76 Support
---

### Post by rgheck on 2011-06-24
I'd like to try to get Fedora running on my new Pangolin. Are the people at System 76 interested in helping me do this? or no? I.e., is it worth posting things here, or should I just use the Fedora lists?

---

### Post by DanneStrat on 2011-06-24
> **rgheck said:**
> I'd like to try to get Fedora running on my new Pangolin. Are the people at System 76 interested in helping me do this? or no? I.e., is it worth posting things here, or should I just use the Fedora lists?

Do you plan on dual-booting with ubuntu?
Here you have an installation guide:
[http://docs.fedoraproject.org/en-US/Fedora/15/html/Installation_Guide/index.html](http://docs.fedoraproject.org/en-US/Fedora/15/html/Installation_Guide/index.html)
I don't know if system76 will be able to help you with fedora.
I would try the mailing lists for help.
Good luck.

---

### Post by Grelf on 2011-06-24
Either way, could you keep this thread updated with how it went? I installed Debian for a bit, but it couldn't find the video driver, and I just went back to Ubuntu, (mostly out of laziness).

I like Ubuntu, but I'd much rather be running straight Debian.

---

### Post by rgheck on 2011-06-24
For the moment, yes, I'll dual boot with Ubuntu.  I will post here about how it goes.

---

### Post by snowpine on 2011-06-24
What hardware problems have you encountered so far?

---

### Post by rgheck on 2011-06-24
The first one was the wireless, but this was just a matter of installing the RPM for the firmware.  The second concerns the touchpad, which seems to be misdetected as a PS2 mouse. Looking at the S76 driver files, they seem deal with this by installing a kernel module psmouse.ko that they build with dkms. I'm working on getting it to install on F15. I can compile it, partly, but the module itself doesn't build. That one I will ask about on the Fedora list, I think.  The third seems to have to do with the KDM login manager. I had some very weird video behavior with it, but that seems to have been resolved by switching to GDM.  Sound seems to work. I haven't tested the camera yet.  Most of the function keys seem to work, but not brightness. This may have to do with the other change the S76 driver makes, but which I haven't made yet myself. We'll see.

---

### Post by isantop on 2011-06-24
We can try to offer help where we can, but there are a lot of differences between Fedora and Ubuntu, and no one in the office is familiar with Fedora at all.

---

### Post by mchauber on 2011-06-28
> **rgheck said:**
> ...wireless...touchpad...*some function keys*...
 
These are common issues (in my experience) when buying laptops. So long as the important stuff is seen and utilized by the kernel, the rest of it is just a matter of tweaking (but it's gotten a lot better over the last few years).
 
I'm looking at buying the Bonobo Pro because I need the performance (and I'm sick of both Dell and HP). Being that I'd like to be running Fedora as well, can you tell us whether there is any kind of performance hit? 
 
Also, if somone out there has a Bonobo Pro, can you send me a dmesg output from a Fedora live CD?
 
Id appreciate it much (and If I do get it, I'll do what I can to help).
 
mc

---

### Post by HotShotDJ on 2011-06-28
Just to let you know, I, too, have abandoned Ubuntu (I won't go into the why's in this context).  In my case, I've gone to OpenSuSE (11.4).

Everything has mostly worked.  I had a little trouble with my Intel 5300 wifi, but a Kernel upgrade took care of that.  Of course, I had to "re-learn" some things, but it has been worth the effort!

I hope you have a similar experience with Fedora.  I too will be watching this thread to see how you've made out.

---

