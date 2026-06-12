---
title: "Why does Amazon Instant Video work all the sudden in 14.04"
date: 2014-02-17
forum: Ubuntu Development Version
---

### Post by estamets on 2014-02-17
Not complaining, I just need educated.

I first installed xubuntu 14.04, Amazon Instant Video didn't work. I used my Mac for that. All the sudden, I install playonlinux and ever since, it's been working like a charm. What changed? What package did playonlinux/wine install to enable this to work.

No buffering, no crashing.. Working like a dream in Google Chrome as evidenced by the pic below.

---

### Post by wildmanne39 on 2014-02-17
*Thread moved to **Ubuntu +1**.*

---

### Post by monkeybrain20122 on 2014-02-17
Amazon video doesn't work with Linux flash (including Chrome's pepper flash) because of drm. For it to work you need to install hal. [https://launchpad.net/~mjblenner/+archive/ppa-hal](https://launchpad.net/~mjblenner/+archive/ppa-hal)

Alternatively install Windows' flash with pipelight [http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)
(and setup a switch mechanism between native flash by installing galternative, open it, go to Mozilla flash something and add piplight flash's path to it and choose whichever one you want. Native flash is usually smoother when it works as wine has its limitations, Need to restart FF every time you make a switch)

The first solution works with system flash (11.2) on Firefox (and all browsers that use Mozilla plugins) but not Chrome's pepper flash. The second solution works for both at the moment but will not work for Chromium based browsers (Chrome/Chromium) after April when google bans all NNAPI plugins. So I would stick to Firefox for this.

Edited: You may also need a user-agent-overrider addon to disguise your browser as Windows Firefox for some streaming sites. Though I heard it is not necessary for amazon video, I don't use it so I have no idea, I mention this just in case you may need it.

---

### Post by estamets on 2014-02-17
I understand that.. I was well aware that HAL was not in the 14.04 repo's anymore. However, I am using Pepper flash ON CHROME build 32. something something.. I am very very confused by the fact that it is working. I didn't do anything with regard to the hack required to make it work.. Nothing at all. 

I didn't install HAL or HAL-INFO nor did I upgrade from 12.04 to 14.04. This is a fresh clean ISO image from Sunday. I only installed wine/playonlinux. So, why does it work? 

I must've done something..

---

### Post by monkeybrain20122 on 2014-02-17
Sorry, misunderstood your post.

Can you go to [http://helpx.adobe.com/flash-player/kb/protected-video-content-play.html](http://helpx.adobe.com/flash-player/kb/protected-video-content-play.html) and scroll to the bottom to do test and see if it works?

---

### Post by estamets on 2014-02-17
I appreciate the link. I'm still confused though. I have been to all my video accounts and I can play them all all of the sudden. ALL OF THEM. I went to the website mentioned and followed the instructions, I honestly didn't get anything, I 'll upload screenshots of what I did see. AZ video running and the Adobe link

Amazon is a HUGE one for me, considering I have much in my library. 

If you all don't believe me, I have proof.

---

### Post by kostkon on 2014-02-17
> **estamets said:**
> I understand that.. I was well aware that HAL was not in the 14.04 repo's anymore. However, I am using Pepper flash ON CHROME build 32. something something.. I am very very confused by the fact that it is working. I didn't do anything with regard to the hack required to make it work.. Nothing at all. 
It could be that the latest version of pepper flash doesn't require hal to be present anymore. Would be possible to test it in Firefox?

---

### Post by monkeybrain20122 on 2014-02-17
Maybe Amazon has changed something? I doubt that it has anything to do with Chrome or Pepper flash because drm is still disabled, otherwise you would have seen a running train in Adobe's test (see screenshot) I am able to play this only with pipelight flash, it doesn't work with pepper flash. I used to be able to play it with flash 11.2 + hal on Firefox but it has apparently stopped working (perhaps I am booting off a different machine, not sure why) I am on 13.10 BTW.  Don't think anything has changed re flash or amazon video in 14.04 that is specific to 14.04. You may check whether your video accounts work in 12.04 or 13.10 if you still have those in different partitions.

Maybe someone can test Adobe's site with hal and see if it works.

(aside: pepper flash never worked with hal so testing hal has to be done on Firefox or Chrome with pepper flash disabled)

---

### Post by sdowney717 on 2014-02-18
I can watch my amazon prime with 12.04 and firefox or chrome.
It works well, you should support the effort, become a member. Hopefully Netflix will quickly move on HTML5

Playing with an nvidia gefore 8400 gs 256mb works full screened with the nvidia driver.
Old nvidia cards work, not so old AMD cards, wont for me.
Regarding Linux and AMD, I hate it, windows and AMD are great. Nvidia has always been just fine, but people rag on them, but they just work for what I want to do in Linux.

---

### Post by sdowney717 on 2014-02-18
plays fine in firefox with 11.2 version, always post link, I had to figure yours from a screen shot.
[http://drmtest2.adobe.com:8080/SVP/SampleVideoPlayer_FP.html#](http://drmtest2.adobe.com:8080/SVP/SampleVideoPlayer_FP.html#)
play file link
[http://drmtest2.adobe.com:8080/Content/anonymous.f4v](http://drmtest2.adobe.com:8080/Content/anonymous.f4v)

---

### Post by vpiercy on 2014-04-11
It had been working on 12.04 LTS, but not after updating today:

"Updating player..."

"An error occurred and your player could not be updated.This is likely because your Flash Player or Browser needs to be updated.This update is required to play back this video."

"Click here to learn more about updating your player."

[http://www.amazon.com/gp/help/customer/display.html/ref=atv_drm_flash_help?nodeId=200256920#flash](http://www.amazon.com/gp/help/customer/display.html/ref=atv_drm_flash_help?nodeId=200256920#flash)

Which goes to a dead page.

**We're Sorry.**

  [IMG]http://g-ecx.images-amazon.com/images/G/01/x-locale/cs/help/customer/background/louis_french_bulldog._V192250726_.gif[/IMG] 
                  We can't find the page you were trying to reach.  We apologize for the inconvenience.
                 We keep an eye on pages that cannot be displayed, and we work to resolve any issues as quickly as possible.
                 The [Help homepage]("http://www.amazon.com/gp/help/customer/display.html") may be able to help you find the information you're looking for.

---

### Post by SeijiSensei on 2014-04-11
I've been using the "[pipelight]("http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html")" solution for Amazon Instant and Netflix.  I haven't watched anything on Amazon Instant for a while, so I thought I'd give it a try.  However even with pipelight installed, Amazon now complains about my Flash version and won't play the video.

However you can also use pipelight to install and run the Windows version of Flash.  I hadn't done that up until now because it wasn't needed.  I tried following the simple instructions on the webupd8 site, but that didn't work because there are now multiple versions of Flash on my machine.  The instructions for fixing that are [here](http://fds-team.de/cms/pipelight-installation.html#section_2_3), but from reading that page it sounds like Chrome/Chromium might be a better choice.  Anyway I'd need to invest more time than I have right now to test this all out, but if you get it to work, please post a follow-up about what you did.

Update: I tried using the update-alternatives method described in the link above and now Netflix is broken.  Amazon seems to think I have too many clients viewing at the moment.  It's possible one of them is my daughter at college, but it may also be because I tried and failed to watch a film multiple times and Amazon is confused.  I'll give it another try tomorrow with Firefox and then try Chromium.

I usually rely on my PS3 for streaming video so this isn't a deal-breaker for me.

---

### Post by monkeybrain20122 on 2014-04-12
> **SeijiSensei said:**
> 
Update: I tried using the update-alternatives method described in the link above and now Netflix is broken.  Amazon seems to think I have too many clients viewing at the moment.  It's possible one of them is my daughter at college, but it may also be because I tried and failed to watch a film multiple times and Amazon is confused.  I'll give it another try tomorrow with Firefox and then try Chromium.
.

Sorry to hear that. I don't have an account on Amazon and never watch any videos from there so I have no idea about it. But you maybe able to fix your pipelight as follows:

Close all browsers,
 then

1) in the terminal disable all your pipelight plugin
 ```
pipelight-plugin --disable flash
 pipelight-plugin --disable silverlight
```
use sudo if you enabled them with sudo

2) remove the folder ~/.wine-pipelight

3) uninstall pipelight and then reinstall it and update the plugins.
```
sudo apt-get update
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin --update
``` 

4) re-enable plugins
```
pipelight-plugin --enable flash
 pipelight-plugin --enable silverlight
```

5)Open a browser and let the pipelight installers do their work.

There is a very convenient way to switch between pipelight and system flash for firefox.
```
sudo apt-get install galternatives
```

Now open galternatives' gui and on the left pane find mozilla-flashplugin and enter pipelight-flash's path (/usr/lib/pipelight/libpipelight-flash.so), you can switch between versions of flash by choosing the version and restart Firefix

(On KDE you may want to install kalternatives instead of galternatives, I suppose it works similarly but I have never used it)

Edited: Google will ban all NPAPI plugins for Chromium/Chrome soon (May) and that include pipelight, so I would just focus on Firefox.

---

### Post by vpiercy on 2014-04-13
So many options with Linux. Even if Hal is deprecated, it works. This easy fix at Amazon.com's forum worked like a charm for 12.04 LTS:

[COLOR=#000000][FONT=verdana]> 
[DB]("http://www.amazon.com/gp/pdp/profile/A1JYV24QKC67AD/ref=cm_cd_et_pdp") says: [/FONT][/COLOR][COLOR=#000000][FONT=verdana]Thank you.... Here is what I did on ubuntu 13.10 64 bit 

sudo add-apt-repository ppa:mjblenner/ppa-hal
sudo apt-get update
sudo apt-get install hal
rm -rf ~/.adobe
restart firefox[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]
[/FONT][/COLOR]
[http://www.amazon.com/forum/amazon%20video%20on%20demand?_encoding=UTF8&cdForum=Fx3EQAX98ED5WQ3&cdPage=1&cdSort=newest&cdThread=Tx167YET6CH0PQI](http://www.amazon.com/forum/amazon%20video%20on%20demand?_encoding=UTF8&cdForum=Fx3EQAX98ED5WQ3&cdPage=1&cdSort=newest&cdThread=Tx167YET6CH0PQI)

---

