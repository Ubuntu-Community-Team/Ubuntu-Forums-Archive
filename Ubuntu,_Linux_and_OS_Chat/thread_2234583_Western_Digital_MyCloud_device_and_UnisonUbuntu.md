---
title: "Western Digital MyCloud device and Unison/Ubuntu"
date: 2014-07-15
forum: Ubuntu, Linux and OS Chat
---

### Post by mikecole on 2014-07-15
I had Unison all setup on my MyCloud device, but there were enough issues that when the firmware update came out, I was silly enough to upgrade to the 4.x version.  Now, having had to reinstall unison (and ensuring that I grabbed the EXACT version to match my unison install on the Ubuntu 14.04 machines I'm syncing this drive with), I find that I'm constantly getting a "Fatal error: Lost connection with the server" when I try to connect.  

SSH'ed into the MyCloud device, and found that when I simply type "unison" or "unison -version", I get "Killed" returned to me.  My only guess is that the update has something in place to kill random apps that it doesn't like.  I don't know how to track down WHAT is killing the app, or make it run in a way that won't allow it to be killed.  

Has anyone experienced something similar, or maybe had better luck getting everything setup with a MyCloud and Unison (or even some other synchronization software that may work better in this situation) that might be able to help point me in the right direction?  I'm lost and rather annoyed by this.  I know better than to update firmware, but the last version was so darned buggy I was willing to risk it. I'm not necessarily looking for tech support on this, but I'm looking for suggestions of things that may have worked for others in the past, or that may work better than what I have.  MyCloud, for being on Linux, is sure trying their best to be a pain in the rump about it.  

The good news is that this new firmware does seem to address some of the issues I had in the old.  The bad news is, it broke my synchronization, and is running VERY slowly right now since one of the things I had disabled previously (due to it being broken) was the file scanning functionality.  That appears to still stop occasionally, but it recovers itself now instead of just breaking.  I'm debating on disabling that AGAIN, just to speed things up to a usable point without having to wait until it's scanned tens of thousands of files.  

Sigh..... for a "easy cloud solution", this thing sure is a pain in the rump.

---

