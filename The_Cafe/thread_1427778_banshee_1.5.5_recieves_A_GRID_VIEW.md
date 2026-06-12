---
title: "banshee 1.5.5 recieves A GRID VIEW"
date: 2010-03-11
forum: The Cafe
---

### Post by ctrlmd on 2010-03-11
Hi,
i've just received an banshee update to 1.5.5 and i noticed that banshee now have 
a great new view option which is grid view :) 

thx banshee team

---

### Post by Jesus_Valdez on 2010-03-11
What's a grid view?

---

### Post by Enigmapond on 2010-03-11
That's really good however after MY last update...banshee doesn't even start...attempting to rectify this problem...:((

---

### Post by bedhead75 on 2010-03-12
Is anyone having a problem with grid view, in that it sometimes doesn't update to the proper album covers when you click through different artists?  Sometimes the covers from a previous artist are still being displayed, but clicking on the "wrong" cover will properly list the songs that belong to the currently selected artist.

---

### Post by vishy1618 on 2010-03-12
Same here people, banshee doesn't even start after updating...looked through the logs and it complains about some exception in System.Reflection.Whatever..

Upgraded through banshee PPA, any others who have this problem?

---

### Post by bedhead75 on 2010-03-12
I upgraded through the Banshee PPA as well, but I don't have that problem.  I'm running Ubuntu 9.10 64-bit here.  The Youtube extension doesn't seem to work even though I've selected it in the preferences.  Is it actually working for anyone?

---

### Post by mykrob on 2010-03-12
I have a lot of the same problems. To test, i uninstalled the app including config files using

sudo aptitude remove --purge banshee


then reinstalled it. Problems persisted, although it at least populate the cover art this time.
The grid view does not properly track album covers, though. It doesnt change properly when I change artists. I'm sure they'll get it fixed, though. Looks like it'll be pretty nice once its working.

---

### Post by bedhead75 on 2010-03-12
Re-sizing the grid view window when wrong artist covers are shown causes it to show the properly updated artist.  I filed a bug report.

---

### Post by jpeddicord on 2010-03-12
> **Enigmapond said:**
> That's really good however after MY last update...banshee doesn't even start...attempting to rectify this problem...:((

Had the same problem, so I removed the mirage plugin that was installed from the repositories and it seems to launch fine now.

---

### Post by Zoot7 on 2010-03-12
I quite like Banshee, it's the only player I've found for Linux that's actually comparable to Winamp (my choice in Windows).

The only problem at the moment for me is that I can't build debs from the 1.5.5 source code at the minute. Oh well, I'll wait for it to hit the repos.

---

### Post by jpeddicord on 2010-03-12
> **Zoot7 said:**
> I quite like Banshee, it's the only player I've found for Linux that's actually comparable to Winamp (my choice in Windows).

The only problem at the moment for me is that I can't build debs from the 1.5.5 source code at the minute. Oh well, I'll wait for it to hit the repos.

[https://launchpad.net/~banshee-team/+archive/banshee-daily](https://launchpad.net/~banshee-team/+archive/banshee-daily)

might satisfy the urge. Use with caution, some days it may work and others it may not.

---

### Post by Enigmapond on 2010-03-12
> **jpeddicord said:**
> Had the same problem, so I removed the mirage plugin that was installed from the repositories and it seems to launch fine now.

That's not even installed I never installed that plugin. The only one I did install was the alarm, so I purged that and still nothing...I'm sick to death as that was really the only media management programme I was really happy with...

---

### Post by Zoot7 on 2010-03-12
> **jpeddicord said:**
> [https://launchpad.net/~banshee-team/+archive/banshee-daily](https://launchpad.net/~banshee-team/+archive/banshee-daily)

might satisfy the urge. Use with caution, some days it may work and others it may not.
Thanks but I'm actually using Debian. The "debianized" source isn't yet in the Sid repo but I'm sure it'll be there soon enough.

---

### Post by jpeddicord on 2010-03-12
> **Zoot7 said:**
> Thanks but I'm actually using Debian. The "debianized" source isn't yet in the Sid repo but I'm sure it'll be there soon enough.

Ah, fair enough. :)

> **Enigmapond said:**
> That's not even installed I never installed that plugin. The only one I did install was the alarm, so I purged that and still nothing...I'm sick to death as that was really the only media management programme I was really happy with...

Try running `banshee --debug` in a terminal and see what you get. If there's a C stacktrace, look for the last few errors that had color text in them and that might give you a hint.

---

### Post by Enigmapond on 2010-03-12
> **jpeddicord said:**
> Ah, fair enough. :)



Try running `banshee --debug` in a terminal and see what you get. If there's a C stacktrace, look for the last few errors that had color text in them and that might give you a hint.

Thank you for the suggestion however this did not reveal much at all...at least not to my eyes. I have attached the result.

---

### Post by jpeddicord on 2010-03-12
> **Enigmapond said:**
> Thank you for the suggestion however this did not reveal much at all...at least not to my eyes. I have attached the result.

Hmm I'm not sure about it either at the moment; maybe Banshee needs a newer Gtk# or something (relevant error is likely "Exception in Gtk# callback delegate")

---

### Post by Noah0504 on 2010-03-21
> **bedhead75 said:**
> Is anyone having a problem with grid view, in that it sometimes doesn't update to the proper album covers when you click through different artists?  Sometimes the covers from a previous artist are still being displayed, but clicking on the "wrong" cover will properly list the songs that belong to the currently selected artist.

I am having this exact same problem.  So annoying.  I am hoping it will be fixed with 1.6.

Also, do you know the number of the bug report you filed?

---

