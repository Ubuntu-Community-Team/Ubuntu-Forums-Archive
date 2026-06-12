---
title: "Cross platform Flash vulnerabilty, Ubuntu is affected too"
date: 2008-08-19
forum: Security
---

### Post by balaknair on 2008-08-19
Apparently there's a new flash based attack out there now which hijacks your clipboard(it loads a url on the systemwide clipboard which can be reset only by restarting the system). It uses Adobe flash-based banner ads (even on major websites like digg and newsweek)to affect your system.
All major platforms- Windows, Mac OSX *and Linux*- and browsers- IE, *Firefox, Opera, Konqueror* and Safari)are affected.
Apparently someone has already run into this problem first hand and posted about it here on ubuntuforums 
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=886905](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=886905)

More info here:
[http://blogs.zdnet.com/security/?p=1733&tag=nl.e539](http://blogs.zdnet.com/security/?p=1733&tag=nl.e539)

and here:
[http://www.heise-online.co.uk/security/Flash-banners-manipulate-the-clipboard--/news/111353](http://www.heise-online.co.uk/security/Flash-banners-manipulate-the-clipboard--/news/111353)

(thanks to elwillow for the second link)


A demo page for the vulnerability is here:
[http://raffon.net/research/flash/cb/test.html](http://raffon.net/research/flash/cb/test.html)

Note: [I]If you click on the demo link, your clipboard is automatically hijacked and will only be released if the browser window is closed
[/I]

The solution(at least at until Adobe releases a security patch, don't count on that happening anytime soon):
**1)** Use the latest version of Firefox(preferably 3.0.1+, but use the latest version in the repos for your version of Ubuntu) with all patches applied, and use NoScript and AdBlockPlus addons
NoScript blocks the demo page I linked to above(see screenshot)

NoScript:  [https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)

AdBlock Plus:  [https://addons.mozilla.org/en-US/firefox/addon/1865](https://addons.mozilla.org/en-US/firefox/addon/1865)

If you use an earlier version of Ubuntu than Hardy, use this guide to get Firefox 3
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)


**2)**  Use your judgment, don't click on links you get in those emails from people you don't know, don't allow html in your email and don't click on suspicious looking links(even from people you know).
And yes, it's probably safer to avoid those Cracks and Warez sites (and those shady porn sites too ;) )

Browse safely.

---

### Post by balaknair on 2008-08-19
Tried going to the spam site that gets linked from MSNBC(after completely backing up my drive)
see screenshots:
1- NoScript blocks the site(trying to redirect with js?) from loading at all
2- Allowing the script by clicking on it led to this page, but NoScript still blocks the site
3- Allowing the site(temporarily of course) starts a 'scan' which finds so many Windows virii on the 'C:\' Drive of my Ubuntu PC. It even 'fixes' some of them, leaving only a few critical ones behind.
4- I'm asked if I want to fix these critical errors on my PC
5- Clicking 'Remove All' leads to asking to download an .exe file(wanna bet it's malicious) to my drive. No, I didn't risk downloading the file(I may be on Ubuntu but I dual boot with WinXP, don't want to risk it).

---

