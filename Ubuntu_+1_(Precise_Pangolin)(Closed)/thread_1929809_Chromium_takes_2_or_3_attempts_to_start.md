---
title: "Chromium takes 2 or 3 attempts to start"
date: 2012-02-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by x-shaney-x on 2012-02-22
At the start of a session, chromium browser never starts at the first attempt.
If I click the launcher I added then it flashes a few times and then nothing happens.
Sometimes it will start at the second attempt, others it just flashes again and nothing.  It never takes more than 3 attempts.

If I ignore the launcher and click on something that opens in the browser (such as email count in gm-notify) then again, chromium will not start at the first attempt.

If I close chromium and try launching it again later in the session then once again it fails to launch at the first attempt.

Strangely enough, if I launch it from the terminal, it starts first time, every time.

Anyone else get this?

---

### Post by jfernyhough on 2012-02-22
Yes. It seems to run fine from the terminal, and last time I tried right-clicking the launcher and selecting Open New Window instead of just left-clicking.

I'm not sure it's only Chromium that does this...

---

### Post by Stinger on 2012-02-22
Google-chrome does it too, but they are closely related.

There is a bug about it on launchpad:
[Bug #918474]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/918474")
A fix is released, it is targeted for Unity 5.6.0

---

### Post by x-shaney-x on 2012-03-06
This seems to be a different problem as according to the reporter, chromium does launch but the icon continues pulsing.

My problem is that the icon starts pulsing but chromium doesn't start.

Since I first posted this I have done a fresh install from beta 1 and the problem is still there.
I have also tried adding the chromium-daily PPA and the problem still persists.
Seems to be other problems in chromium.  Right-click menus often don't appear first time either, it will just be the drop shadow with no menu content.

---

### Post by rburkartjo on 2012-03-07
loads okay on my end but when i try to open up my bookmarks from the toolbar chromium freezes for awhile. however i have an extension installed that lets me open my bookmarks from the contextual menu and if i use that no problem.

---

### Post by sonicb00m on 2012-03-07
I have this problem with chromium and sometimes filezilla.

Also Geany is maximising over the launcher and top panel.

I think it must be some bugs in compiz.

---

### Post by x-shaney-x on 2012-03-07
It would seem so.
I have been using Unity 2D today and noticed chromium started up first time, EVERY time.
Not only that, it has no problems with the menus.

---

### Post by cwhebert on 2012-03-07
I am having the same problem with Chrome as mentioned by other.  To open the browser I need to click on it twice.  I can hear the HD spin a bit when I fist click on the Chrome icon, however, nothing happens.  I then click on the icon a second time and Chome opens.  It does seem to be a problem with Compiz.

---

### Post by snkiz on 2012-03-07
I've been getting this with the 2d launcher as well (still with compiz). And I have compiz from the unity testing ppa

---

### Post by sonicb00m on 2012-03-30
Anyone have a fix for this? It is still taking time to launch chromium even with all the latest updates installed.

---

### Post by jasonsmith01 on 2012-03-30
> **jfernyhough said:**
> Yes. It seems to run fine from the terminal, and last time I tried right-clicking the launcher and selecting Open New Window instead of just left-clicking.

I'm not sure it's only Chromium that does this...

Same here, right click new window always works. I've noticed that my icons are no longer pulsing after todays updates. Checked compiz and the settings are good.

---

### Post by x-shaney-x on 2012-03-30
I've also tried google chrome today and again, I have this problem.

---

### Post by lucazade on 2012-03-31
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/965314](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/965314)

---

### Post by Abandon on 2012-04-04
It often takes more than one mouseclick to open Chromium webbrowser or Google Chrome. Is this an known issue and if so..is there a solution?

---

### Post by zika on 2012-04-04
> **Abandon said:**
> It often takes more than one mouseclick to open Chromium webbrowser or Google Chrome. Is this an known issue and if so..is there a solution?[http://ubuntuforums.org/showthread.php?t=1929809&highlight=chromium](http://ubuntuforums.org/showthread.php?t=1929809&highlight=chromium)
(Threads were (obviously) merged. Thank You...)

---

