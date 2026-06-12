---
title: "Maverick (10.10) Issues &amp; Impressions on S76 Products"
date: 2010-10-03
forum: System76 Support
---

### Post by HotShotDJ on 2010-10-03
As per usual, I've installed the RC version of the "Next Big Thing" aka Maverick Meerkat on my PanP5.  For the first time, I actually did an in-place upgrade from Lucid.  Compared to previous versions, I've had surprisingly few problems.

Here are the issues that I have encountered:
[LIST=1]
[*]Suspend/Resume is unusable.  While it will suspend, it will not resume -- only a hard reboot gets me going again.  I'm not sure what the trouble is but you can be sure I'll be researching. EDIT: There is a problem with the Kernel (I think) See [Bug #656631]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656631").  I don't expect this to be fixed by release as it hasn't even been acknowledged by Ubuntu developers as of 10/8/2010.  In the developers' defense, this is probably an upstream bug. EDIT2:  Suspend now working. However still has the cpufreq bug that existed in earlier Ubuntu releases.
[*]Plymouth splash has not been fixed for boxes with NVidia video + proprietary drivers.  Still UGLY.  I can probably use the same fix that worked in Lucid resulting in a beautiful Plymouth boot up screen, but I'm leaving it as-is for now to see if it gets fixed between now and final release.
[*]Multisync completely broken. I don't know WHAT is going on here. EDIT: Yes I do.  See my next post.
[/LIST]
Of course, this IS an RC, so we'll see what happens with the actual release.  I'll probably do a fresh install from CD to see if that fixes things if the problems persist past the release  date.

If anybody else -- especially S76 tech support folks -- have tried/tested 10.10, this would be a great thread to post your impressions.

---

### Post by gamerchick02 on 2010-10-03
I'm running 10.10 right this second on my PanP5, and I really like it.

I've written up a [couple]("http://amysramblings.wordpress.com/2010/09/30/ubuntu-maverick-meerkat-first-impressions/") [thoughts]("http://amysramblings.wordpress.com/2010/10/02/maverick-meerkat-second-impressions/") about it on my blog, but to summarize:

- Plymouth splash is worse than before.
- Loads are less (I now get an average of 0.75 system load, when under Lucid I'd easily have 1.5-2.0 system load, measured from the System Monitor applet).

I have not tried suspend/resume on this box, but Maverick on my Star1 works beautifully.

I'm unfamiliar with multisync... If it's broken, I guess I'm not using it.

I really like this release; there's been a lot of work that went into it, and the whole team has to be congratulated for doing a superb job.

Amy

---

### Post by BigDaveyL on 2010-10-04
> **HotShotDJ said:**
> As per usual, I've installed the RC version of the "Next Big Thing" aka Maverick Meerkat on my PanP5.  For the first time, I actually did an in-place upgrade from Lucid.  Compared to previous versions, I've had surprisingly few problems.

Here are the issues that I have encountered:
[LIST=1]
[*]Suspend/Resume is unusable.  While it will suspend, it will not resume -- only a hard reboot gets me going again.  I'm not sure what the trouble is but you can be sure I'll be researching.
[*]Plymouth splash has not been fixed for boxes with NVidia video + proprietary drivers.  Still UGLY.  I can probably use the same fix that worked in Lucid resulting in a beautiful Plymouth boot up screen, but I'm leaving it as-is for now to see if it gets fixed between now and final release.
[*]Multisync completely broken.  I don't know WHAT is going on here.
[/LIST]
Of course, this IS an RC, so we'll see what happens with the actual release.  I'll probably do a fresh install from CD to see if that fixes things if the problems persist past the release  date.

If anybody else -- especially S76 tech support folks -- have tried/tested 10.10, this would be a great thread to post your impressions.


One can get plymouth to work with the drivers from Nvidia.

---

### Post by gamerchick02 on 2010-10-04
> **BigDaveyL said:**
> One can get plymouth to work with the drivers from Nvidia.

Is there a way to do this without hacking anything?

Amy

---

### Post by HotShotDJ on 2010-10-08
> **HotShotDJ said:**
> 3. Multisync completely broken. I don't know WHAT is going on here.It seems that Multisync-gui is incompatible with the Opensync plugins that are used in Maverick.  As of today, it looks like developers have pulled multisync-gui from the repositories.  Unfortunately, there is no GUI alternative right now.  However, the CLI "osynctool-0.39-1" works fine.  Warning -- the configuration files have changed significantly, so you can't just copy your old configs over.  Its pretty simple to figure out (after all, I managed to get it working, so anybody can!).

---

### Post by HotShotDJ on 2010-10-08
> **BigDaveyL said:**
> One can get plymouth to work with the drivers from Nvidia.Yes, BigDavey, I know and acknowledged that fact in my original post.  The POINT is that it still doesn't work out-of-the-box with the proprietary NVidia drivers. Maybe it will by the time Maverick is released (two more days... probably not).

---

### Post by HotShotDJ on 2010-10-13
Ok... suspend works now (probably a recent kernel upgrade)... BUT the [cpu frequency]("http://ubuntuforums.org/showthread.php?t=1308828") bug persists.

---

### Post by ranjan_mg on 2010-10-17
I installed maverick on p6. While the suspend works fine, resume fails completely once in three/four times and results in a freeze. screen is blank and even the REISUB keys don't work either. I have to hard reboot. I am thinking of going back to lucid but VLC is still at 1.0.6 which does not play some of my MTS files correctly. So I am stuck.
Anyone else facing this issue ? Any workarounds ? (or getting VLC 1.14 with gpu acceleration on lucid ?)
Thanks..

---

### Post by jamiekrug on 2010-11-07
@ranjam_mg: I'm getting the failed resume occasionally on my System76 Serval Pro (SerP6). I'm pretty sure the problem has never manifested if I always suspend and resume while connected to AC power, but when on laptop battery power, it does happen every few resumes (and sometimes at suspend as well).

---

