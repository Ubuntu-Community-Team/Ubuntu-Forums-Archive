---
title: "WWW-Login not working"
date: 2010-04-09
forum: Ubuntu One (CLOSED)
---

### Post by Regel on 2010-04-09
I can't seem to be able to log in to Ubuntu One. The Single Logon says:

```


Oops!

Sorry, something just went wrong in Ubuntu Single Sign On.

We&#8217;ve recorded what happened, and we&#8217;ll fix it as soon as possible. Apologies for the inconvenience.

(Error ID: 1560carambola6)

```

It's been like this since yesterday (when I created my account and could login for a few hours).

Any ideas? Is it just me or is someone else having problems too?

---

### Post by joshuahoover on 2010-04-12
> **Regel said:**
> I can't seem to be able to log in to Ubuntu One. The Single Logon says:

```


Oops!

Sorry, something just went wrong in Ubuntu Single Sign On.

We’ve recorded what happened, and we’ll fix it as soon as possible. Apologies for the inconvenience.

(Error ID: 1560carambola6)

```It's been like this since yesterday (when I created my account and could login for a few hours).

Any ideas? Is it just me or is someone else having problems too?

I haven't seen any complaints of this nor experienced it myself. Are you still having problems logging in?

Thank you,

Joshua

---

### Post by kolinab on 2010-04-18
I am having a similar problem. Posted a new thread but should have posted to this one. Sorry!

The thread I just started: [http://ubuntuforums.org/showthread.php?t=1457178](http://ubuntuforums.org/showthread.php?t=1457178)

[edit] . . . a few hours later and now I'm able to log in again. Everything seems back to normal.

---

### Post by cprofitt on 2010-04-18
I can confirm this issue -- it started for my yesterday on my desktop. I filed a bug report. ([https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/565941](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/565941)) Though perhaps this is more of a service level issue.

Upon boot my CPU usage is between 50-100% on both cores. If I click the Ubuntu One notification icon it errors out instantly.

I have deleted the keys, .cache and .config folders for Ubuntu One and CouchDB and then going to web to re-establish the computer account results in the error in this thread.

I went to the IRC channel, but it appears no one is awake currently.

---

### Post by joshuahoover on 2010-04-19
> **cprofitt said:**
> I can confirm this issue -- it started for my yesterday on my desktop. I filed a bug report. ([https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/565941](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/565941)) Though perhaps this is more of a service level issue.

Upon boot my CPU usage is between 50-100% on both cores. If I click the Ubuntu One notification icon it errors out instantly.

I have deleted the keys, .cache and .config folders for Ubuntu One and CouchDB and then going to web to re-establish the computer account results in the error in this thread.

I went to the IRC channel, but it appears no one is awake currently.

Sorry I missed your ping on IRC. It was Sunday where I am so I wasn't actually online. :) I'm normally on Monday-Friday, 13:00 - 21:00 UTC. I'm in the Central Daylight time zone in the US.

So you're still seeing a similar OOPs error when you attempt to login to Ubuntu One from your web browser? Can you try deleting the cookies for one.ubuntu.com and login.ubuntu.com in your web browser and then attempt to login?

Also, the CPU usage and crash should not be related to this. If you haven't already, can you please file a bug report describing the problem you're seeing? You can file a bug report by right-clicking on the Ubuntu One client applet and selecting "Report a Problem". This will include some debug log files that we can use to see what might be causing the crash and possibly the high CPU usage.

Thank you,

Joshua

---

