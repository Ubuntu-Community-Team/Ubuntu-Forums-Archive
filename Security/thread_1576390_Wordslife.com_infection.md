---
title: "Wordslife.com infection"
date: 2010-09-17
forum: Security
---

### Post by buteo_12701 on 2010-09-17
I have recently installed ubuntu 10.04 and i somehow have gotten wordslife.com infecting my firefox browser. if anyone can give me info on the best way to get rid of it it would greatly be appreciated.

---

### Post by Soul-Sing on 2010-09-17
delete your firefox homemap/profile?

---

### Post by Rubi1200 on 2010-09-17
Are you sure?

I think this only affects Windows.

Try clearing out your browser cache and maybe consider changing to another DNS server.

---

### Post by wacky_sung on 2010-09-17
Using [urlvoid.com]("http://www.urlvoid.com/") to scan and indeed it has some hostile scripting running.

```
Report	2010-08-21 16:55:14 (GMT 1)
Website	wordslife.com
Domain Hash	3c80a656522e95fcef1481afef7316e9
IP Address	69.31.42.125 [SCAN]
IP Hostname	colo-69-31-42-125.pilosoft.com
IP Country	 US (United States)
AS Number	26627
AS Name	AS-PILOSOFT - Pilosoft, Inc.
Detections	2 / 16 (13 %)
Status	SUSPICIOUS
Scanning site with:	AMaDa 	CLEAN
Scanning site with:	BrowserDefender 	CLEAN
Scanning site with:	Google Diagnostic 	CLEAN
Scanning site with:	hpHosts 	UNRATED
Scanning site with:	Malware Patrol 	CLEAN
Scanning site with:	MalwareDomainList 	CLEAN
Scanning site with:	MyWOT 	DETECTED
Scanning site with:	Norton SafeWeb 	CLEAN
Scanning site with:	ParetoLogic URL Clearing House 	CLEAN
Scanning site with:	PhishTank 	CLEAN
Scanning site with:	SURBL 	CLEAN
Scanning site with:	Threat Log 	CLEAN
Scanning site with:	TrendMicro Web Reputation 	DETECTED
Scanning site with:	URIBL 	CLEAN
Scanning site with:	Web Security Guard 	UNRATED
Scanning site with:	ZeuS Tracker 	CLEAN

```

---

### Post by buteo_12701 on 2010-09-17
thanks for the replies....i believe i got it i deleted the profile and havent seen the problem anymore.

---

### Post by bodhi.zazen on 2010-09-17
Use NoScript =)

[How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604")

---

### Post by mr-woof on 2010-09-17
no script for the win, that url scanning website is class. I've never heard of that one before, I'll be using that again :)

---

### Post by buteo_12701 on 2010-09-17
well i came to finding i did not fix it...until i got the suggestion for no-script. seems to be functioning once again. but is this the right way of dealing with this or is this just a band aid? is my security protected ? i don't understand how this virus/spy-ware works nor do i know exactly where it came from. i get random pop ups for ridiculous websites and every now and than the wordslife.com will pop up.and at times even Google will pop up. I'm still very new to Linux but I'm learning the best i can. thanks for dealing with my newby questions.

---

### Post by bodhi.zazen on 2010-09-17
> **buteo_12701 said:**
> well i came to finding i did not fix it...until i got the suggestion for no-script. seems to be functioning once again. but is this the right way of dealing with this or is this just a band aid? is my security protected ? i don't understand how this virus/spy-ware works nor do i know exactly where it came from. i get random pop ups for ridiculous websites and every now and than the wordslife.com will pop up.and at times even Google will pop up. I'm still very new to Linux but I'm learning the best i can. thanks for dealing with my newby questions.

That is all "normal". The web runs on things such as java script and flash (and other things) and such popups and re-directs are part of the annoyances.

Nono of these things you describe are considered a security threat in the traditional sense of security as they do not change system files (only files in your home directory).

No script, and other tools in the thread I gave you are the best "defence". They are a bandaid in that they do not fix all the annoying scripts out there, they just limit what can run locally on your browser.

I also suggest you use a tool such as AdblockPlus or I prefer privoxy (ff extensions are best for single users using one browser, privoxy is better for multiple users or multiple browsers, IMHO).

---

### Post by OpSecShellshock on 2010-09-17
If you frequently view Flash content, it would be a good idea to also install the add-on called [BetterPrivacy]("https://addons.mozilla.org/en-US/firefox/addon/6623/"). It can get rid of persistent stored objects that are not contained in the Firefox profile folder and as such are not removed when clearing private data. It's entirely possible that if you've viewed any Flash content that there's something tucked away in the ~/.macromedia folder.

---

### Post by bodhi.zazen on 2010-09-17
> **bodhi.zazen said:**
> That is all "normal". The web runs on things such as java script and flash (and other things) and such popups and re-directs are part of the annoyances.

Nono of these things you describe are considered a security threat in the traditional sense of security as they do not change system files (only files in your home directory).

No script, and other tools in the thread I gave you are the best "defence". They are a bandaid in that they do not fix all the annoying scripts out there, they just limit what can run locally on your browser.

I also suggest you use a tool such as AdblockPlus or I prefer privoxy (ff extensions are best for single users using one browser, privoxy is better for multiple users or multiple browsers, IMHO).

I should add, some of these flash or java script things can, rarely, be potentially problematic.

---

### Post by wacky_sung on 2010-09-17
> **OpSecShellshock said:**
> If you frequently view Flash content, it would be a good idea to also install the add-on called [BetterPrivacy]("https://addons.mozilla.org/en-US/firefox/addon/6623/"). It can get rid of persistent stored objects that are not contained in the Firefox profile folder and as such are not removed when clearing private data. It's entirely possible that if you've viewed any Flash content that there's something tucked away in the ~/.macromedia folder.

I will suggest to use [bleachbit]("http://bleachbit.sourceforge.net/") which is much better.
[IMG]http://lh6.ggpht.com/_1XYQfEGGEIw/Sq-U8kbsLDI/AAAAAAAACc0/TYOtViwcFPo/s800/BleachBit-064-Firefox-Fedora11-English.png[/IMG]

---

### Post by bodhi.zazen on 2010-09-18
Careful with bleachbit =)

Does it handle flash cookies (which are separate from cookies cookies).

---

### Post by slooksterpsv on 2010-09-18
Another protection element is AdBlock plus addon for Firefox.

---

### Post by buteo_12701 on 2010-09-18
wow thanks for all the great information i really appreciate it. no script is working amazingly actually and haven't had any problems since i installed it. You guys are definitely a big help...its kinda tough switching from windows to a Linux OS but I'm enjoying it . Ill try downloading more off the list and see how it goes. I'm always using flash so I'm sure ill run in to problems again. thanks again :)

---

### Post by wacky_sung on 2010-09-18
> **bodhi.zazen said:**
> Careful with bleachbit =)

Does it handle flash cookies (which are separate from cookies cookies).

Yes it does.See below. :)
[IMG]http://img59.imageshack.us/img59/7685/screenshotbleachbit.png[/IMG]

---

### Post by bodhi.zazen on 2010-09-18
> **wacky_sung said:**
> Yes it does.See below. :)

Thanks for the screen shot.

---

### Post by Rubi1200 on 2010-09-19
> **OpSecShellshock said:**
> If you frequently view Flash content, it would be a good idea to also install the add-on called [BetterPrivacy]("https://addons.mozilla.org/en-US/firefox/addon/6623/"). It can get rid of persistent stored objects that are not contained in the Firefox profile folder and as such are not removed when clearing private data. It's entirely possible that if you've viewed any Flash content that there's something tucked away in the ~/.macromedia folder.
+1 to using BetterPrivacy

In combination with NoScript and Adblock Plus, a pretty decent start at protecting one's browser.

---

### Post by HousieMousie2 on 2010-09-29
I have to say it...

This is just another fine example of why I love the Ubuntu Forums and the Linux community.

Thanks again!

---

### Post by Sage_Reimer on 2010-10-14
> **buteo_12701 said:**
> I have recently installed ubuntu 10.04 and i somehow have gotten wordslife.com infecting my firefox browser. if anyone can give me info on the best way to get rid of it it would greatly be appreciated.

Hello, I was also infected with the wordslife malware and I think I've gotten rid of it.  

I'm running Mac OSX and was getting redirected on Safari and Firefox.   All scans I was doing were coming back clean.  NoScript seems to be a good stop-gap, but resetting my Router to its factory settings seems to have worked.   I'm using a linksys ADSLME1.  

Good luck!  :)

---

