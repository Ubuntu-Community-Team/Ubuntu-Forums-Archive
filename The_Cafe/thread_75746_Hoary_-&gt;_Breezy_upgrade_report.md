---
title: "Hoary -&gt; Breezy upgrade report"
date: 2005-10-14
forum: The Cafe
---

### Post by agger on 2005-10-14
A friend of mine upgraded to Breezy last night, and today he blogged his experience for future reference.

The blog entry is here:

[http://www.midtimod.dk/blog/index.php?/archives/322-Ubuntu-News-Upgrade-Edition.html](http://www.midtimod.dk/blog/index.php?/archives/322-Ubuntu-News-Upgrade-Edition.html)

but since it's in Danish, I'll give a (rought) translation here:

> I started upgrading my own machine last night, and of course I encountered the problem you always get when you want upgrades right away - getting the files took a long time. But OK - the machine was allowed to continue downloading overnight; at some point, it lost the connection to the Ubuntu server, and when I got up this morning, I could simply continue where it had left off. Half an hour late the upgrade was complete.

I must say I'm actually quite impressed at the smoothness of the upgrade process. You were able to work normally on the machine throughout the process, and the few times, where the upgrade process encountered changed configuration files, you were given a manageable display of the difference between your current file and the one Ubuntu proposed to replace it with, and this actually made it quite easy to decide which version to choose.

Just to make sure, I wanted to reboot the machine after the upgrade was finished. Here I encoutered the only actual error message - stating that Gnome had crashed. This is probably because Gnome had been upgraded, while it was running, so it hadn't been able tu shut down properly. This is not actually a problem, just thought I'd mention it so others will know what to expect.

A few cosmetic changes have been made in the desktop theme, but nothing serious (and yes, I still use Ubuntu's standard theme - the brown colours are realy delightful).

There are a few remarkable innovations in this version, and in the time to come, I'll attempt to have a closer look at some of them and write a bit about it - if I get the time.

---

### Post by agger on 2005-10-14
Well, i just changed all "hoary" to "breezy" in my /etc/apt/sources.list, and typed  

apt-get install dist-upgrade.

So help me God ... :-)

---

