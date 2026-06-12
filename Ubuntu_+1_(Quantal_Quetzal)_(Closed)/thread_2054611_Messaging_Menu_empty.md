---
title: "Messaging Menu empty"
date: 2012-09-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Aenima99x on 2012-09-07
Not sure when it happened, but my Messaging menu is now completely empty. I've tried to reinstall the indicator-messages and related packages, but still the same. Anyone else seeing this?

[IMG]http://i.imgur.com/XqsBb.png[/IMG]

---

### Post by victor9098 on 2012-09-07
Yes, I noticed it too. Empathy seems to start at login for me so that is listed in the menu with the new icons. Then as I turn apps on (like Thunderbird) they appear in there then leave when you shut them down. Did the same as you, reinstalled to see if broken :D

EDIT: Looks like this is the intended behaviour for the messaging menu, just read [System status menu refinements in Ubuntu 12.10]("http://design.canonical.com/2012/04/status-menus/") on the Canonical Design blog.

---

### Post by kuvanito on 2012-09-08
something is seriously wrong with online accounts/empathy/thunderbird
if you set up thunderbird with your hotmail account this will cause empathy to logout from your hotmail account also setting up automatic login in empathy will gives you login errors with your gmail account,facebook account also disconnets in empathy once you open thunderbird,go figure....

---

### Post by victor9098 on 2012-09-08
> **kuvanito said:**
> something is seriously wrong with online accounts/empathy/thunderbird
if you set up thunderbird with your hotmail account this will cause empathy to logout from your hotmail account also setting up automatic login in empathy will gives you login errors with your gmail account,facebook account also disconnets in empathy once you open thunderbird,go figure....

I agree, the handling of the online accounts is a mess. I am getting connections errors at the start of each session and during the day I will get several. Mostly having to grant access to Google at the start of most sessions. Can not connect to Foursquare at all. I keep getting taken to an authentication page at [www.mardy.it](www.mardy.it) too!? When I try to report bugs against the telepathy errors I get told the bugs are not valid as my system is not up to date.

---

### Post by Aenima99x on 2012-09-08
I don't use Empathy or Thunderbird, so that was the problem. I installed Empathy to test and sure enough it showed up. I use Pidgin & GM-Notify and it looks like both are still in the process of getting updated to work with the new messaging menu.

---

### Post by Aenima99x on 2012-09-08
> **victor9098 said:**
> I agree, the handling of the online accounts is a mess. I am getting connections errors at the start of each session and during the day I will get several. Mostly having to grant access to Google at the start of most sessions. Can not connect to Foursquare at all. I keep getting taken to an authentication page at [www.mardy.it](www.mardy.it) too!? When I try to report bugs against the telepathy errors I get told the bugs are not valid as my system is not up to date.

Yeah I was getting those authentication pages to mardy.it too.....very strange. I've disabled online accounts until this mess gets sorted out.

---

### Post by greenwapiti on 2012-09-12
My Google account access disconnects regularly and can't reconnect at boot up, either.  

More disturbing, though, is the [www.mardy.it](www.mardy.it) tabs popping up after login that say:

Authentication completed.
Please close this window.

in the browser window.  I hadn't ever been to this site and am not aware of any of my online accounts needing to authenticate against this site!  The first time this occurred, I got a slew of tabs opening at the same site and with the same message.  

There isn't anything installed on my system that wasn't preinstalled or from the Ubuntu Software Center, so I'm really at  a loss to understand what this is about.  Anyone got a clue?

---

### Post by victor9098 on 2012-09-12
The Mardy issue is down to Shotwell, check out  [Bug #1047588]("https://bugs.launchpad.net/ubuntu/+source/shotwell/+bug/1047588") for more details.

As for the Google accounts, I am experiencing the exact same behaviour. Also I can not connect to the IRC via 'Online Accounts' using my username/password, have to do manually via nickserv.

---

