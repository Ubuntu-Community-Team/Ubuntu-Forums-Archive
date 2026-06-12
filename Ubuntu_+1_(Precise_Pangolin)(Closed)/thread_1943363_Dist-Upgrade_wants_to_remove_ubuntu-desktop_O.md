---
title: "Dist-Upgrade wants to remove ubuntu-desktop :O"
date: 2012-03-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tehowe on 2012-03-19
Dist-upgrade wants to remove ubuntu-desktop.

I think I'll wait until tomorrow to see if the upgrade queue has changed. ;)

Just a heads up to anyone who may be caught unawares.

---

### Post by bencauble on 2012-03-19
Yeah, I feel really dumb because I let it happen....And there are some broken dependencies keeping me from reinstalling it, which resolve in no installation candidates....borked.
Argh!

That's what I get for not paying attention. :-)

---

### Post by Gregory Lee on 2012-03-19
> **bencauble said:**
> That's what I get for not paying attention. :-)
Oh, I don't know about that.  We might wonder what the point is in setting this trap for the unwary.  Do you want to upgrade your system?  Sure, sounds like a good thing.  Okay, I'm upgrading, ... upgrading ..., taking away your desktop now, ...  Aha!  Gotcha!

(Well, you said you wanted to upgrade, didn't you?)

---

### Post by tehowe on 2012-03-19
You can probably get around it by hitting CTRL-ALT-F1 from the login screen, logging into the shell with your usual name and password, and installing gnome-shell.

```
sudo apt-get update && sudo apt-get install gnome-shell
```Then 

```
sudo shutdown now
```and from the lighdm login screen after you've restarted, click the little circle above your name to switch default desktop to Gnome, at least until the ubuntu-desktop package goes back in.

I've got gnome-shell and cinnamon installed as backup desktops in case Unity gets trashed again.

Good luck!

---

### Post by philinux on 2012-03-19
Repos still out of kilter.

```
Calculating upgrade... Done
The following packages will be REMOVED
  ubuntu-desktop unity-2d unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-shell unity-2d-spread
The following packages have been kept back:
  libgnome-desktop-3-2
The following packages will be upgraded:
  libunity-2d-private0

```

---

### Post by oldos2er on 2012-03-19
> **tehowe said:**
> Dist-upgrade wants to remove ubuntu-desktop.


When 'dist-upgrade' wants to be too aggressive, I use plain ol' 'upgrade' instead.

---

### Post by bencauble on 2012-03-19
> **tehowe said:**
> You can probably get around it by hitting CTRL-ALT-F1 from the login screen, logging into the shell with your usual name and password, and installing gnome-shell.

```
sudo apt-get update && sudo apt-get install gnome-shell
```Then 

```
sudo shutdown now
```and from the lighdm login screen after you've restarted, click the little circle above your name to switch default desktop to Gnome, at least until the ubuntu-desktop package goes back in.

I've got gnome-shell and cinnamon installed as backup desktops in case Unity gets trashed again.

Good luck!

Thanks for the help.  I attempted that, but I get stuck at the purple Ubuntu load screen...It's been sitting there for about 20 minutes.  The install looked to be successful at the CLI, but doesn't look it it worked. 
Thoughts? 

Thanks!

---

### Post by tehowe on 2012-03-19
> **bencauble said:**
> Thanks for the help.  I attempted that, but I get stuck at the purple Ubuntu load screen...It's been sitting there for about 20 minutes.  The install looked to be successful at the CLI, but doesn't look it it worked. 
Thoughts? 

Thanks!
I see rburkartjo over at this thread [http://ubuntuforums.org/showthread.php?t=1943105&page=2](http://ubuntuforums.org/showthread.php?t=1943105&page=2) can't get into the login screen either. 

I'm at the bleeding edge of my knowledge here, but I suspect that you can still go into the shell from there with CTRL-ALT-F1 ... in a day or so do another update/upgrade and see if things are sorted. Probably wouldn't hurt to do an 'apt-get install ubuntu-desktop' as well. Beta 2 drops March 29 so since I've only got my netbook to work with here and a big essay due, I don't think I'll be doing any more upgrades till then :S

One thing I love about Linux is even in the worst case you can always copy your home directory over to portable media, reinstall the system, then copy the home directory back and all your settings are preserved and waiting for reinstallation of your favourite applications.

---

### Post by bencauble on 2012-03-19
> **tehowe said:**
> I see rburkartjo over at this thread [http://ubuntuforums.org/showthread.php?t=1943105&page=2](http://ubuntuforums.org/showthread.php?t=1943105&page=2) can't get into the login screen either. 

I'm at the bleeding edge of my knowledge here, but I suspect that you can still go into the shell from there with CTRL-ALT-F1 ... in a day or so do another update/upgrade and see if things are sorted. Probably wouldn't hurt to do an 'apt-get install ubuntu-desktop' as well. Beta 2 drops March 29 so since I've only got my netbook to work with here and a big essay due, I don't think I'll be doing any more upgrades till then :S

One thing I love about Linux is even in the worst case you can always copy your home directory over to portable media, reinstall the system, then copy the home directory back and all your settings are preserved and waiting for reinstallation of your favourite applications.

Looks like the broken packages I was encountering with ubuntu-desktop have been fixed. All looks beautiful now...

Thanks for all your help!

---

### Post by bluenova on 2012-03-20
> **tehowe said:**
> One thing I love about Linux is even in the worst case you can always copy your home directory over to portable media, reinstall the system, then copy the home directory back and all your settings are preserved and waiting for reinstallation of your favourite applications.

You don't even need to do that if you have a separate Home partition.

---

