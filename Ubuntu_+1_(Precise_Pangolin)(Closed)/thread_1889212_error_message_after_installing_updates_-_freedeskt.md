---
title: "error message after installing updates - freedesktop"
date: 2011-11-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by doctordruidphd on 2011-11-30
Whenever I install updates or packages, after the "trigger" items run, the update hangs for a minute, then I get the following message:

> Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

It appears that the update/install is actually working properly.

This is 64-bit kubuntu.

---

### Post by bluexrider on 2011-11-30
where are these updates coming from?

synaptic

software manager

apt-get

did you look at your source file to determine if the address was correct ie: org.freedesktop


I sure wouldn't get a hit on that from my browser.

---

### Post by doctordruidphd on 2011-11-30
This is coming from apt-get run in a terminal window.  I notice that if I run synaptic, it also gives this error in the "detail" window. 

The message is cut-and-pasted from the terminal window, and is correct as posted.

Edit: this is an error coming from apt, or something related to it. It is not specific to any package -- everything does it.

Edit further: for a while I was getting error messages about not being able to update the gtk icon cache. Those errors have now stopped, I believe after installing an updated libgtk-something-or-other a couple of days ago. But now this error is coming up.  Might be a bug in whatever does the icon cache updating. (just a guess)

---

### Post by bluexrider on 2011-12-01
have you done 

sudo apt-get update

and 

sudo apt-get upgrade

you might also need to do 

sudo apt-get clean 

and 

sudo apt-get autoremove


sounds like from the posted information that you have a corrupted source file

---

### Post by ventrical on 2011-12-01
I just got done going through the same thing  (64bit) and opted for a fresh install. I tried everything.  The error that I commited was that I installed the 3.2.n-n kernel before I had properly set up the sources.list and then update and upgrade them. Theortically it should be capable of being repaired but the down time is greater than that of  a fresh install to the affected partition.

---

### Post by doctordruidphd on 2011-12-01
> have you done 
sudo apt-get update
and
sudo apt-get upgrade
you might also need to do
sudo apt-get clean 

Yes, of course, normal update procedure.

> sudo apt-get autoremove
bad idea for a development release. But I have manually removed everything autoremove suggests removing.

> sounds like from the posted information that you have a corrupted source file 

What do you mean by "source file"? From the error message I suspect a dbus problem.

Further info: I just tried installing a small package while chrooted into the system, and it installed without the error message.

---

### Post by doctordruidphd on 2011-12-01
> The error that I commited was that I installed the 3.2.n-n kernel before I had properly set up the sources.list

That could be, the problem seems to have appeared with the 3.2 kernel.  What did you do to your sources.list to correct this?

Edit: As far as I can tell, sources.list is correct. This is a system upgraded from oneiric, and has been running fine with kernel upgrades until now. So it's had whatever kernel dist-upgrade has installed all along the way, didn't go from 3.0 directly to 3.2.

Edit further: Problem exists with both 3.2.0-1 and 3.2.0-2. Wouldn't you know it, I had just cleared out the 3.1 and 3.0 kernels, and they have disappeared from the repositories. Will try to find a 3.1.x and do the experiment.

---

### Post by seeker5528 on 2011-12-01
I already posted this in another thread, but since this thread is longer......

```
sudo dpkg --purge gstreamer0.10-packagekit packagekit
```

Seems to take care of it.

Later, Seeker

---

### Post by doctordruidphd on 2011-12-01
> sudo dpkg --purge gstreamer0.10-packagekit packagekit

Worked. Problem solved, thanks.

---

