---
title: "Firefox reverts to flash??"
date: 2015-11-04
forum: Ubuntu, Linux and OS Chat
---

### Post by monkeybrain20122 on 2015-11-04
I have noticed that on many sites (e.g Youtube, but not just it) instead of loading html5 player now i am shown the "activate flash" button (i set it to ask to activate) This was the old behaviour before FF 39/40. This just happened today on Firefox 41, I haven't changed anything in my settings (and tested with new profile). Just upgraded to FF42 a few minutes ago, still the same. For html5 to kick in i have to disable flash completely.

I am not complaining, as it is not as annoying as media autoplaying, just wonder what happens.

---

### Post by hey2 on 2015-11-05
Hi.

I have the same problem as you.

I was going to make a new thread, but thankfully i searched first.

I tried in two different computers, both with new profiles and different add-ons.

I'm running 42, but it was also happening on 41.

I hope they fix it, because this is not helping the "burn it down" cause... :D

---

### Post by monkeybrain20122 on 2015-11-05
So no one but the two of us experienced this?

---

### Post by ardouronerous on 2015-11-06
> **monkeybrain20122 said:**
> So no one but the two of us experienced this?

I'm also experiencing this, however, HTML5 is crashing Firefox whenever I play a Youtube video, maybe Firefox disabled it for that reason?

---

### Post by monkeybrain20122 on 2015-11-06
> **ardouronerous said:**
> I'm also experiencing this, however, HTML5 is crashing Firefox whenever I play a Youtube video, maybe Firefox disabled it for that reason?

But it is still mysterious for FF41, I have not made any change in the settings, it just happened out of the blue. Now again to use HTML5 on Youtube with flash enabled (even set to "ask to activate") you have to go to [https://www.youtube.com/html5](https://www.youtube.com/html5) and override Firefox's default player, which becomes flash again. But as I said this happens not just on Youtube, it seems that FF  somehow resets the default player to flash (how?) and youtube just detects the change.

---

### Post by Frogs Hair on 2015-11-06
Most Youtube videos run in html5 for me, but there are sites that use flash. Two examples are Vevo and BBC News.

---

### Post by monkeybrain20122 on 2015-11-06
> **Frogs Hair said:**
> Most Youtube videos run in html5 for me, but there are sites that use flash. Two examples are Vevo and BBC News.

Did you go to [https://www.youtube.com/html5](https://www.youtube.com/html5) and override the default player?

If override default player or disable flash then all YT videos play in html5 including Vevo.

---

### Post by mc4man on 2015-11-06
No issue here either. 
Are or have you deleted/blocked youtube cookies? (that's where pref's are saved such as player to use.

---

### Post by pqwoerituytrueiwoq on 2015-11-06
youtube defaults to flash, you have to demand html5 (see monkeybrain2012's post) or disable/remove flash

---

### Post by monkeybrain20122 on 2015-11-06
> **mc4man said:**
> No issue here either. 
Are or have you deleted/blocked youtube cookies? (that's where pref's are saved such as player to use.

No, I tested with a new profile.

---

### Post by monkeybrain20122 on 2015-11-06
> **pqwoerituytrueiwoq said:**
> youtube defaults to flash, you have to demand html5 (see monkeybrain2012's post) or disable/remove flash

Actually you don't have to since Firefox 39/40. HTML5 player has become default for FF, this apparent reversal to flash as default player happened two days ago.

---

### Post by mc4man on 2015-11-06
> **monkeybrain20122 said:**
> No, I tested with a new profile.

As mentioned above the default for firefox is flash if available. Once the html5 player is requested  it should stay on that unless you remove the cookie (youtube.com  PREF

---

### Post by monkeybrain20122 on 2015-11-06
> **mc4man said:**
> As mentioned above the default for firefox is flash if available. Once the html5 player is requested  it should stay on that unless you remove the cookie (youtube.com  PREF

Since Firefox 40 html5 has replaced flash as default even if flash is available. html5 doesn't need to be requested any more and it applies to sites other than youtube. But this has changed suddenly 2 days ago, hence the question on this thread.  [http://news.softpedia.com/news/firefox-40-for-linux-adopts-html5-player-by-default-only-720p-resolution-supported-489120.shtml](http://news.softpedia.com/news/firefox-40-for-linux-adopts-html5-player-by-default-only-720p-resolution-supported-489120.shtml)  (full hd on Youtube is not my question, I know it can be enabled manually in about:config by setting some webm string to true from one of your posts)

---

### Post by night_sky2 on 2015-11-07
I don't have this issue but then I leave Flash disabled 98% of the time in Firefox, since Youtube and Dailymotion have HMTL5 players. This solves it for me.

Also, Flash is a constant security risk, better leaving it disabled when unused.

You can install FlashDisable, which provides an easy on/off switch in the toolbar for more convenience: [https://addons.mozilla.org/fr/firefox/addon/flashdisable/](https://addons.mozilla.org/fr/firefox/addon/flashdisable/)

---

### Post by monkeybrain20122 on 2015-11-08
> **night_sky2 said:**
> I don't have this issue but then I leave Flash disabled 98% of the time in Firefox, since Youtube and Dailymotion have HMTL5 players. This solves it for me.

Also, Flash is a constant security risk, better leaving it disabled when unused.

You can install FlashDisable, which provides an easy on/off switch in the toolbar for more convenience: [https://addons.mozilla.org/fr/firefox/addon/flashdisable/](https://addons.mozilla.org/fr/firefox/addon/flashdisable/)

Yes if you disable flash all together then it won't matter of course, html5 just kick in automatically. 

For most sites I don't use flash or even html5 for that matter. I use [https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/) This isn't really a problem for me, but rather a question. I remember there was a lot of fanfare over the switch to html5 as default when FF 40 came out, I am curious why I am experiencing this apparent reversal.

---

### Post by night_sky2 on 2015-11-08
> **monkeybrain20122 said:**
> Yes if you disable flash all together then it won't matter of course, html5 just kicks in automatically.
I just don't understand people who leave flash enabled while browsing. This plugin is full of holes. Better using it ONLY when absolutely necessery.

> **monkeybrain20122 said:**
> For most sites I don't use flash or even html5 for that matter. I use [https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/) This isn't really a problem for me, but rather a question. I remember there was a lot of fanfare over the switch to html5 as default when FF 40 came out, I am curious why I am experiencing this apparent reversal.
It seems Media Source Extension (MSE) was disabled in Firefox 42 for some reason: [https://www.reddit.com/r/firefox/comments/3rmezo/html5_is_not_the_default_youtube_player_anymore/](https://www.reddit.com/r/firefox/comments/3rmezo/html5_is_not_the_default_youtube_player_anymore/)

I agree it is much better to play youtube videos in a native player like MPV or SMPlayer (SMTube)

---

### Post by monkeybrain20122 on 2015-11-08
> **night_sky2 said:**
> I just don't understand people who leave flash enabled while browsing. This plugin is full of holes. Better using it ONLY when absolutely necessery.


You can set it to 'ask to activate". This would work like having flashblock. Since FF 40 if you do this HTML5 will be used as default. But this is no longer the case now, apparently. Now in order to use html5 you have to set flash to "never activate", this was the default behaviour before FF40.

---

### Post by mc4man on 2015-11-08
> **monkeybrain20122 said:**
> You can set it to 'ask to activate". This would work like having flashblock. Since FF 40 if you do this HTML5 will be used as default. But this is no longer the case now, apparently. Now in order to use html5 you have to set flash to "never activate", this was the default behaviour before FF40.That's the part I don't see - 
On 41 (16.04) & 42 (14.04) once the html5 player is requested (PREF) then html5 is always used on youtube. (as long as cookie is not removed

The bug referenced before seems to, well I've no clue, started about mse & webm (vp9), finished for 42 in some manner - 
[https://bugzilla.mozilla.org/show_bug.cgi?id=1200834](https://bugzilla.mozilla.org/show_bug.cgi?id=1200834)

---

### Post by monkeybrain20122 on 2015-11-08
> **mc4man said:**
> That's the part I don't see - 
On 41 (16.04) & 42 (14.04) once the html5 player is requested (PREF) then html5 is always used on youtube. (as long as cookie is not removed

The bug referenced before seems to, well I've no clue, started about mse & webm (vp9), finished for 42 in some manner - 
[https://bugzilla.mozilla.org/show_bug.cgi?id=1200834](https://bugzilla.mozilla.org/show_bug.cgi?id=1200834)


As I said on this thread, this has **nothing **to do with Youtube or cookies. In FF40 HTML5 was default FF player on** all sites **where it is offered. You don't need to request HTML5 player (which is Youtube specific) Now it has gone back to giving preference to flash as long as it is not disabled. I always set flash to "ask to activate" , in FF40 (and FF41 until a few days ago) videos would just bypass flash altogether, sometimes they just autoplay (as I said it can be annoying) and if not autoplay clicking videos would result in html5 player rather than flash (if both options exist) But this changed suddenly a few days ago and flash is offered as the default again even BEFORE I upgraded to FF42. Again this is not just on Youtube.

---

### Post by mc4man on 2015-11-09
> **monkeybrain20122 said:**
> As I said on this thread, this has nothing to do with Youtube. In FF40 HTML5 was default FF player on** all sites **where it is offered. You don't need to request HTML5 player (which is Youtube specific) Now it has gone back to giving preference to flash as long as it is not disabled. I always set flash to "ask to activate" and HTML5 often just autoplay (as I said it can be annoying) and if not clicking video would result in html5 player rather than flash. But this changed suddenly a few days ago even BEFORE I upgraded to FF42.
I missed/forgot that (about other sites.
Out of curiosity what is another site that used to give html5 without  flash being disabled?

---

### Post by monkeybrain20122 on 2015-11-09
> **mc4man said:**
> I missed/forgot that (about other sites.
Out of curiosity what is another site that used to give html5 without  flash being disabled?

e.g 

[http://video.nationalgeographic.com/video/ng-live/151027-harper-technology-food-lecture-nglive-short?utm_source=Facebook&utm_medium=Social&utm_content=link_fb20151109video-revolutionizefoodvod&utm_campaign=Content&sf14986347=1](http://video.nationalgeographic.com/video/ng-live/151027-harper-technology-food-lecture-nglive-short?utm_source=Facebook&utm_medium=Social&utm_content=link_fb20151109video-revolutionizefoodvod&utm_campaign=Content&sf14986347=1)
[http://www.thestar.com/entertainment/music/newsroom-concert-series/2015/09/30/the-harpoonist-and-the-axe-murderer-perform-cry-a-little-.html](http://www.thestar.com/entertainment/music/newsroom-concert-series/2015/09/30/the-harpoonist-and-the-axe-murderer-perform-cry-a-little-.html)

---

