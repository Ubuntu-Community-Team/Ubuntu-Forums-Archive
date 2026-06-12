---
title: "How much influence does Google Inc have with chromium?"
date: 2012-03-08
forum: The Cafe
---

### Post by user1397 on 2012-03-08
I'm just wondering how much Google directly influences/directs what goes on with the chromium browser.

Do they just provide financial support?  Do they pay devs to work on the project?  Do they tell them what to do?

I know chromium is open source and is different than chrome in some minor ways, such as the branding, sending usage statistics, the updater, built-in flash, etc

I guess this would also address the concern of those who are wary of Google and who would want to feel "safe" using chromium instead of chrome.

Thoughts?

---

### Post by Paqman on 2012-03-08
> **ubuntuman001 said:**
> Do they pay devs to work on the project?

Yes, most of the Chromium devs are Google employees AFAIK.

Generally the way Chrome(ium) development works is that Google works on Chromium in the open, then they periodically take a snapshot of it, bundle in the other bits and release that as Chrome. 

I don't know how receptive to patches for Chromium they are from outside Google.

---

### Post by forrestcupp on 2012-03-08
> **ubuntuman001 said:**
> 
I know chromium is open source and is different than chrome in some minor ways, such as the branding, sending usage statistics, the updater,_ built-in flash_, etc
So are you saying that when Adobe drops Flash for Linux, and it only exists for us as a plugin for Chrome, that it won't also be in Chromium?

---

### Post by BeRoot ReBoot on 2012-03-08
> **forrestcupp said:**
> So are you saying that when Adobe drops Flash for Linux, and it only exists for us as a plugin for Chrome, that it won't also be in Chromium?

Precisely. Chromium is Free Software, Adobe/Google won't bundle it with flash.

Anyway, I don't trust Google one bit. I don't have the time to go through the Chromium source code and build it myself, so I'll just have to assume it's a client to Google's botnet, like Chrome.

---

### Post by Simian Man on 2012-03-08
> **forrestcupp said:**
> So are you saying that when Adobe drops Flash for Linux, and it only exists for us as a plugin for Chrome, that it won't also be in Chromium?

It won't be included, but it would likely still work.

---

### Post by forrestcupp on 2012-03-08
> **BeRoot ReBoot said:**
> Precisely. Chromium is Free Software, Adobe/Google won't bundle it with flash.

I can see it not being bundled, but don't you think there will be some kind of installable plugin?

---

### Post by BeRoot ReBoot on 2012-03-08
> **forrestcupp said:**
> I can see it not being bundled, but don't you think there will be some kind of installable plugin?

Adobe is "planning to drop all Linux flash support, with the exception of continuing to bundle Flash player with Google Chrome."

---

### Post by Copper Bezel on 2012-03-08
Not the current Flash player as it is now. They're working with Google on a new plugin for Chrom(e/ium)'s "Pepper" PPAPI, which is apparently derived from the existing NPAPI that Firefox and everyone else uses as the API for plugins like Flash. (Though I guess Chromium actually supports PPAPI, which may or may not make it possible to trick it into using Chrome's plugin if you have both browsers installed.)

---

### Post by MisterGaribaldi on 2012-03-09
> **BeRoot ReBoot said:**
> Anyway, I don't trust Google one bit. I don't have the time to go through the Chromium source code and build it myself, so I'll just have to assume it's a client to Google's botnet, like Chrome.

Sorry, but I have to ask... do you also put your food on top of the television so the radiation kills the poisons and bacteria and other stuff that is put there by the government?

---

### Post by vasa1 on 2012-03-09
> **MisterGaribaldi said:**
> Sorry, but I have to ask... do you also put your food on top of the television so the radiation kills the poisons and bacteria and other stuff that is put there by the government?

I'm lucky I wasn't eating or drinking anything when I read your post. Hilarious!

---

### Post by Paqman on 2012-03-09
> **BeRoot ReBoot said:**
> I'll just have to assume it's a client to Google's botnet, like Chrome.

And Linux users think Microsoft is guilty of spreading FUD.

You don't have to comb the source code to find out the truth, although obviously that's the gold standard. But if you can't be bothered to even do ANY research, perhaps best not to flout your ignorance in public eh?

---

### Post by YeOK on 2012-03-09
The latest version of Chrome (Version 19.0.1061.1 dev) already has a version of the new flash plugin. 

```


Flash (2 files) - Version: 11.2.31.109
Shockwave Flash 11.2 r31
Name:	Shockwave Flash
Description:	Shockwave Flash 11.2 r31
Version:	11.2.31.109
Location:	/opt/google/chrome/PepperFlash/libpepflashplayer.so
Type:	PPAPI (out-of-process)
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl

```

---

### Post by BeRoot ReBoot on 2012-03-09
> **MisterGaribaldi said:**
> Sorry, but I have to ask... do you also put your food on top of the television so the radiation kills the poisons and bacteria and other stuff that is put there by the government?

No, that's what UV lamps and defluoridation filters are for. :D

> 
You don't have to comb the source code to find out the truth, although  obviously that's the gold standard. But if you can't be bothered to even  do ANY research, perhaps best not to flout your ignorance in public eh? 	

I'm not ignorant, and I'm not claiming to believe Chromium is a client to Google's botnet like Chrome, I'm just saying that I'll assume that's the case for practical purposes (like not turning my PC to Google) until I've taken the time and effort to assure otherwise.

---

### Post by Copper Bezel on 2012-03-09
You're all missing the obvious point here. If you're *using the internet*, you're a part of Google's botnet. Switching browsers doesn't change much. = )

[QUOTE=YeOK]The latest version of Chrome (Version 19.0.1061.1 dev) already has a version of the new flash plugin. [/QUOTE]
Oh dear. Well, that's good news and bad in equal measures. (And I say that as an exclusive Chrome user - I use Chrome on Windows more than I use anything else on Linux, and that's in ten-minute increments at work.)

---

### Post by BeRoot ReBoot on 2012-03-09
> **Copper Bezel said:**
> You're all missing the obvious point here. If you're *using the internet*, you're a part of Google's botnet. Switching browsers doesn't change much. = )

Not if you route everything google-related to 127.0.0.1.

---

### Post by MisterGaribaldi on 2012-03-10
> **BeRoot ReBoot said:**
> No, that's what UV lamps and _defluoridation filters_ are for. :D

Dang! You just made me think about that scene from Dr. Strangelove!

---

### Post by yetiman64 on 2012-03-10
> **Copper Bezel said:**
> ...which may or may not make it possible to trick it into using Chrome's plugin if you have both browsers installed.)
Yes it is possible on 32 bit  [[COLOR=Blue]--Link--[/COLOR]]("http://www.webupd8.org/2011/03/use-google-chrome-built-in-flash-in.html"), on 64 bit not sure how that will work when main flash support is dropped, as at this time to get 64 bit flash working in chrome you need to download the normal flash plugin.

I tried the instructions in the link on 64 bit, but run into no 64bit flash plugin and had to download the normal flash plugin for chrome then link it across to firefox.

I have found that the one flash installation in chrome can be shared with firefox as well.

---

