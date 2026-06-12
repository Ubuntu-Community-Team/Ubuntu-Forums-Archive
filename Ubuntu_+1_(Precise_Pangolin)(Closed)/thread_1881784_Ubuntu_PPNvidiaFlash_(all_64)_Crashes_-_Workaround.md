---
title: "Ubuntu PP/Nvidia/Flash (all 64) Crashes - Workaround"
date: 2011-11-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-11-16
I have been failing to use Flash on PP (both 64-bit), any browser, for about two weeks. There are no output messages on crash, so it's hard to debug. After some digging, I found the reason why.

If I launch the browser with Mesa libGL it works. Using Nvidia 290.x libGL (which is the default for those who use Nvidia proprietary driver), I get a crash. I'm not sure how it works for people that are on 32-bit Nvidia/Ubuntu/Flash.

So I created two workaround files, to be used by the launchers/shortcuts/manually, etc.

**Firefox**
```

sudo nano /usr/local/bin/firefox.sh
#!/bin/sh
# Firefox.sh
# Workaround for nvidia vs mesa libgl issue
export LD_PRELOAD=/usr/lib/libGL.so.1
nohup /usr/bin/firefox & 

```[B]Chromium
[/B]```

sudo nano /usr/local/bin/chromium.sh
#!/bin/sh
# chromium.sh
# Workaround for nvidia vs mesa libgl  issue
export LD_PRELOAD=/usr/lib/libGL.so.1
nohup /usr/bin/chromium-browser &

``````
sudo chmod +x /usr/local/bin/firefox.sh
sudo chmod +x /usr/local/bin/chromium.sh
```Then update your launchers, shortcuts, default apps, gconf, whatever, etc.

In the case of Firefox, /usr/bin/firefox is a soft-link to /usr/lib/firefox*/firefox.sh. It is just as viable to simply add the exported libgl variable to this sh or change the soft link elsewhere.
```

$ ls -la /usr/bin/firefox 
lrwxrwxrwx 1 root root 29 Nov  7 13:59 /usr/bin/firefox -> ../lib/firefox-8.0/firefox.sh

```One can also simply add LD_PRELOAD=/usr/lib/libGL.so.1 to the default environment, avoiding all this. I'd avoid manually changing the softlinks at /usr/lib though... cause you'll have to undo the change when mesa or nvidia gets updates, etc.

---

