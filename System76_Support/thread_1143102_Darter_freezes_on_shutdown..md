---
title: "Darter freezes on shutdown."
date: 2009-04-29
forum: System76 Support
---

### Post by riseringseeker on 2009-04-29
I have a white darter, and made a clean install of JJ on it the day it was released.  Most things went fine, and other than the notification of updates issue, I am happier with this release than most if not all I have been through.

The one thing that is a bother though is *sometimes* the darter refuses to shut down.  I click on shutdown and things seem to be going fine, then it goes to a blank screen (not even a blinking cursor) and stays there.  I have waited over 10 minutes and it does not budge.  

If I hit Ctrl-Alt-F2 it brings me to a login prompt, but will not let me log in.  Anyone else having these types of troubles?  What log entries will help solve this part-time problem?

---

### Post by thomasaaron on 2009-04-29
I've seen several cases of this with nVidia machines, but not with the DarU1.

How often does it happen?
And does it happen if desktop effects are turned off?

---

### Post by riseringseeker on 2009-04-29
> **thomasaaron said:**
> I've seen several cases of this with nVidia machines, but not with the DarU1.

How often does it happen?
And does it happen if desktop effects are turned off?

You know me, never an easy problem, Tom.  I have the effects turned on full time on both now that they work so well.  3D on the Darter works now, and now that I have added --no-start to the fusion-icon command in startup applications, it works perfectly as well.

I'll turn them off for a while and see if it reoccurs.  It is not an every time thing.  I don't suspend or hibernate the thing because the boot time is about as fast, so that's not it. I *have* turned off the warning for shutdown/restart/logout and the only other real change was to get the update notifier back, and the Ctrl-Alt-Backspace.

---

### Post by thomasaaron on 2009-04-29
Thanks, Karl. Once you figure out if it is happening with(/out) desktop effects, we should get some logs.

So to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

I'll have a look at it and see what I can figure out.

It's best to collect the logs immediately after rebooting to make it easier to find the problem area.

---

### Post by riseringseeker on 2009-05-02
> **thomasaaron said:**
> Thanks, Karl. Once you figure out if it is happening with(/out) desktop effects, we should get some logs.

So to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

I'll have a look at it and see what I can figure out.

It's best to collect the logs immediately after rebooting to make it easier to find the problem area.

Logs on the way.  Seems to occur only 1 in 10 shutdowns or so, so it took a while.  Unfortunately, when I do log in, I do quite a bit of stuff before logging out, so it's hard to pinpoint a particular app that would cause the problem.

---

