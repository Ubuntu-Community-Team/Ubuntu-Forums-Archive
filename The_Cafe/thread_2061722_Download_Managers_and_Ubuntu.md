---
title: "Download Managers and Ubuntu"
date: 2012-09-23
forum: The Cafe
---

### Post by t0p on 2012-09-23
I often download stuff from the internet.  My usual download solutions are: the Firefox add-on [VideoDownloadHelper]("https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/") , Firefox's own built-in downloader, and wget.  These have served me pretty well; but a video streaming site recently brought me info about [WxDownload Fast]("http://wxdownload-fast.en.uptodown.com/ubuntu"), an open-source download manager for which a .deb is available, and which offers interesting features (such as "accelerated", multi-streamed, segmented downloads which are not browser-dependant and which has a GUI - wget's nice, but I don't really understand some of its inner-workings).

I'm wondering what other forum users think about download managers, and maybe suggest some. I don't *need* a download manager, I know - but should I *want* one?  Cheers.

---

### Post by leclerc65 on 2012-09-23
For Linux ISO's I prefer Ktorrent. When not possible, I use jDownloader for off-hour downloads. My ISP doesn't like it when I
download too much during the daytime.:)

---

### Post by vexorian on 2012-09-23
I use [unity-jdownloader](http://www.webupd8.org/2011/11/jdownloader-unity-integration-speed.html). Basically, install jdownloader, that unity-jdownloader addon and I also remove the jdownlaoder tray icon extension to remove jdownloader from indicators.

Being able to monitor and control downloads by just jdownloader's launcher icon makes *a world* of difference.

---

### Post by t0p on 2012-09-23
I looked at jDownloader and decided to give it a try.  So I installed it via ppa, following the instructions [here]("https://launchpad.net/~jd-team/+archive/jdownloader"). 

But I'm having a problem.  When I try to run jDownloader it wants to do some updates.  But every time it tries to download the files, I get this error

```

Hash Failed
Error. Retry
Server Busy.  Wait 15 Seconds

```

It waits 15 secs, tries to get the updates again, and I get the same error again.

I don't know if it's a server problem or what.  The error message says "Hash failed" but I installed via ppa exactly as it says at the link via [JDownloader.org]("http://jdownloader.org/download/index").  Can anyone suggest a solution?  Forum staff: should I start a thread on this in General Help or just carry on here?

---

### Post by nothingspecial on 2012-09-23
> **t0p said:**
>   Forum staff: should I start a thread on this in General Help or just carry on here?

Support threads should be in the support areas.

---

### Post by vexorian on 2012-09-23
The PPA probably has nothing to do with it. The ppa just installs the base file that downloads the updates. If Hashes are failing, this is an issue with jdownloader.org's server, or your connection with it.

---

