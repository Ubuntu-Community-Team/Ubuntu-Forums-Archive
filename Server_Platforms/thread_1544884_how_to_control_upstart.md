---
title: "how to control upstart?"
date: 2010-08-03
forum: Server Platforms
---

### Post by Duckslammer on 2010-08-03
Is there any script or application that will tell me what services will start on boot and change them?

I can find very little documentation about this and what I can find doesn't make a lot of sense to me.

I have asked this question a dozen times on the irc channel and every time someone tells me to rtfm - and there is no "fm" to read.

There are still runlevels though ubuntu doesn't use them, and there is still /etc/init.d but also /etc/init - what is the intersection, why are some services started by the old sysv but not upstart and vice versa and what happens if I change something?

---

### Post by gobbledigook on 2010-08-03
here is the [**_manual_**](http://upstart.ubuntu.com/getting-started.html)

if you want to be sure you are not going to mess things up you could practice in a virtual machine or back-up the /etc/init folders. I personally haven't read the manual, just skimmed the first page.. but it tells you how to manage jobs and set your own up. i think that not all programs have been/at present can be set up to use upstart... hence the two options runnign side by side

---

