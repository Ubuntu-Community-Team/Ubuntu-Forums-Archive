---
title: "Is Google Chrome acting up lately for anyone else?"
date: 2013-04-30
forum: The Cafe
---

### Post by DisappearingOak on 2013-04-30
After installing the latest stable Chrome (the offical Chrome, not Chromium) v26 on Raring, I keep having crashes. Sometimes it works fine for a bit, then my window suddenly disappears and I have to relaunch it and it has a message that Chrome did not shut down unexpectedly and do I want to restore my session. This happens once in a while, but that's not the only problem. I keep getting Aw, Snap every few minutes on different pages (tab has crashed). It happens every few seconds on different unrelated pages. I had Chrome v24 installed on Mint Quantal, and that was working fine till a couple days ago, I might have done a upgrade (I'm not sure) but now Chrome is crazy crashing on Mint too (I'll check if there have been version changes later). At first I thought it might be a RAM issue, but I'm not sure as everything else works fine. I have Win 7 installed, rarely use it except for Skype, but I had the stable latest Chrome set up on it and it worked perfect for twenty minutes and then Windows decided to flash a BSOD (MEMORY MANAGEMENT ERROR). I hope it's not a ram problem as I don't have time to set 8 hour tests, but I doubt it as everything else works perfectly, just Chrome. Anyway, I searched Doctor Google and there seems to be hordes of complaints since Chrome 25 about similar issues of Chrome disappearing, and aw snap crashing with some Chrome profiles. Wondered if anyone here experienced any issues?

---

### Post by jockyburns on 2013-04-30
I had problems a week ago (on 12.04) with Chrome. Youtube videos either wouldn't play or played with very jerky video. Turned out one of the updates had activated libflash or pepper flash in addition to the Chrome version. All sorted now , but,,,,,,,, I'm now having problems playing some games online. Dunno whther this is something to do with Flash or a Java issue. 
Anyway, your not alone in having problems with Chrome since the last update. I'm sure they release these updates without fully testing them on the latest versions of Ubuntu (or could be they're testing them on machines that use the latest technology, without giving a thought to those of us who use machines 5 -6yrs old  or even older)

---

### Post by vasa1 on 2013-04-30
> **DisappearingOak said:**
> ... **hordes of complaints** since Chrome 25 about similar issues of Chrome disappearing, and aw snap crashing with some Chrome profiles. Wondered if anyone here experienced any issues?
Hmmm .... 
[http://askubuntu.com/a/286081/25656](http://askubuntu.com/a/286081/25656)

---

### Post by dandroid13 on 2013-04-30
I think he's talking about crashing, not issues with installing.

---

### Post by codingman on 2013-04-30
Err... Yes. I can tell you that it is not an Ubuntu problem. I made the switch to FF months ago, and forgot to remove Chrome.

---

### Post by vasa1 on 2013-04-30
> **dandroid13 said:**
> I think he's talking about crashing, not issues with installing.

The point is that Chrome stable isn't yet available for 13.04. If someone does something to install it despite, then crashes may be expected.

---

### Post by monkeybrain2012 on 2013-04-30
> **vasa1 said:**
> The point is that Chrome stable isn't yet available for 13.04. If someone does something to install it despite, then crashes may be expected.

Why not? Just download the .deb from google and there you have it. The issue is that ATM to install it you need to grab some libraries from quantal's repo and the fix has not yet filtered down to the stable channel, but doesn't mean you cannot install stable Chrome if you get those libraries.

I have Chrome (stable) in 13.04 and it doesn't seem to have any problem so far, but maybe I don't notice it since I mainly use Firefox.

EDITED: Booted up my 13.04 install and surfed the web a bit with Chrome, watched some short videos on Youtube and Vimeo, didn't have any problem. It was fast and smooth.

---

### Post by Max Blyss on 2013-05-01
Had an odd freeze - bug with Chrome Stable on 12.04...  It would freeze if I minimized a non-fullscreen window, esp. when watching video.  Cleared up after a week or so.

---

### Post by ikt on 2013-05-01
Currently have a problem on 12.04 where it seems to not close properly and I have to kill it via system monitor else it opens with profile problems.

---

### Post by castrojo on 2013-05-01
I get this weird thing where it'll freeze, but if I resize it the window and back all the tabs look weird and break.

---

### Post by Mikeb85 on 2013-05-01
I've found Chrome Beta works better all around.  Strangely enough even seems more stable than Stable...

---

### Post by DisappearingOak on 2013-05-01
Hi, After writing that post, it seems I did experience instability with other system components too so I've cleaned out and reseated the RAM stick in another slot. Will buy a new stick if problem persists. So, in this particular case, I think there was a problem with the RAM. But, yeah, Google Chrome has been a little unstable in some versions before also, especially with the new Pepper Flash and all. Thanks for the replies, everyone.

Btw, I'm really disappointed to see that Opera browser doesn't support many Facebook games. I love Opera otherwise, but my mother plays those games often so can't use it as primary browser. On the other hand, Chrome does get some small details right. For example, If I'm reading a page and I want to open a link, if I want to open it in the same tab, OF COURSE I'll just click it and not open the context menu. If I'm opening the context menu, then obviously I don't want to interrupt my reading and want to open link in new tab. Chrome rightly puts the options then on top of the context menu. That's something I can't get used to in other browsers, not putting new tab options on top of their context menus. It's also a problem when I want to search a piece of text without interrupting my reading. It's things like this where Chrome excels.

---

### Post by vdubeau on 2013-05-01
I was having the same problem with it crashing all of the time.

In above question on AskUbuntu (answer by vasa1) it was suggested to use the unstable branch to fix the problem. I just dl'd the deb and installed it with gdebi. I'll report back in a day or on the results. If you want to try it yourself you can get it from Softpedia: [http://linux.softpedia.com/progDownload/Google-Chrome-Download-48046.html](http://linux.softpedia.com/progDownload/Google-Chrome-Download-48046.html). Just scroll down for the version you need. I use version 28.

---

### Post by DisappearingOak on 2013-05-02
Hi, vdubeau, in my case it was the ram. However, this crash problem does exist for many users. You may want to search the Chrome developer support group to see if there have been any fix or anything for such issue. What I gathered, it's a problem with some variables in certain user's Chrome user profiles causing Chrome to become unstable and crash all the time. So you may try purging your Chrome user profile. Not sure if the issue has been resolved by the developers, but purging helps some users. Also, some people have issues because of faulty extensions or plugins. So, can try disabling extensions and/or stuff like Flash to see if that resolves the problem.

I've hit these problems before but the new stable has been running smoothly (stable gets updated frequently also), except for the hardware issue I had. I refuse to use an unstable development branch, that's likely to have more issues. So if people are having problems, try the newest stable (there are updates often) from the Chrome website first.

---

### Post by vdubeau on 2013-05-02
I had already purged my profile and deleted my extensions and Chrome was still crashing. The unstable was working OK (no crashing) but the longer I used it the slower it went and it seemed that it was also slowing down the system. I stick with Firefox for the time being until Chrome 28 becomes stable.

---

### Post by DisappearingOak on 2013-05-02
Stable latest [COLOR=#303942][FONT=Cantarell]26.0.1410.63 is working for me here great now that my RAM issue is fixed. The devs do need to get their act up though, one user even had his browser crash everytime he wrote a letter in the address bar because of a broken autocomplete. I hear you about the unstable having problems though like memory leaks like they happen to you. That's why I try avoid unstable software.[/FONT][/COLOR]

---

### Post by mreq on 2013-05-03
Why would you ever use Google's instead of Chromium? I had absolutely **no problems** over X years using it. I even copied the PDF plugin from Google's deb ;)

---

### Post by DisappearingOak on 2013-05-03
Chrome has more multimedia plugins I believe so all your videos and stuff work properly. But, anyway, I'd expect any issue in Chrome to be present in Chromium. Google is the one who develops Chromium, they just repackage the builds with a couple extra plugins and branding. So it doesn't really matter what you are using.

---

### Post by monkeybrain2012 on 2013-05-03
> **DisappearingOak said:**
> Chrome has more multimedia plugins I believe so all your videos and stuff work properly..

Actually Firefox has the most except for updated flash. Gecko-mediaplayer is the most useful multimedia plugin for Linux but unfortunately it somehow doesn't load on Chrome or Chromium. 

If I need updated flash I use Chrome, otherwise I use Firefox. Not sure about the point of Chromium and it is quite out of date.

---

### Post by Paqman on 2013-05-03
> **mreq said:**
> Why would you ever use Google's instead of Chromium? I had absolutely **no problems** over X years using it. I even copied the PDF plugin from Google's deb ;)

See now I see it the other way: why would you use Chromium over Chrome? Chrome is the same browser with more features.

---

### Post by tjeremiah on 2013-05-03
> **monkeybrain2012 said:**
> Gecko-mediaplayer is the most useful multimedia plugin for Linux 

thanks for the heads up.

---

### Post by tjeremiah on 2013-05-03
> **monkeybrain2012 said:**
> Gecko-mediaplayer is the most useful multimedia plugin for Linux

thanks for the heads up.

---

### Post by deadflowr on 2013-05-04
> **mreq said:**
> Why would you ever use Google's instead of Chromium? I had absolutely **no problems** over X years using it. I even copied the PDF plugin from Google's deb ;)

Can you even call that chromium anymore?

---

### Post by codingman on 2013-05-04
I think Chrome and Chromium are in the middle. I use w3m for browsing when I don't want plugins, and I use Firefox which has plenty more plugins when I want them.

---

### Post by DisappearingOak on 2013-05-04
OK, after using Firefox a bit, I've changed my mind about it being inferior to Chrome. At first, what I saw was a very fat and ugly layout. Then after customizing it, I see it has potential, Untick show menu bar, to get a Chrome gears like button saying 'Firefox' in your tab bar. Cool. That alone is a massive reduction of screen space. Then I searched for themes but what they call themes these days, useless travel photos, ain't my idea of themes, and the old themes section were mostly outdated for new version of FF, but fortunately I found the Gnome 3 integration extension and that beautified things immensely (Shell users, take note). Then I found one of my favourite ever extensions, Tab Mix Plus, I missed you! Then the usual productivity enhancers, FastestFox, CoolPreviews (shows you preview of any website or photo or content via a button near your links on mouseover), and AdBlock, etc. That was fine, but I found an extension that has made me a real fan, it's named 'Location Bar Enhancer' and it turns your address bar into a breadcrumbs like layout that you can interact with and do all sorts of funny and useful things with. Layout is looking much nicer - beautiful - on my desktop after customizing, and I think I can use this as a replacement for Chrome after all, if it turns out to be more stable.

---

### Post by Sam Mills on 2013-05-04
I use chromium with no issues at all.

---

