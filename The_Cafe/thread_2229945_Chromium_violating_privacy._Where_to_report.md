---
title: "Chromium violating privacy. Where to report?"
date: 2014-06-16
forum: The Cafe
---

### Post by CaRoXo on 2014-06-16
It happens some strange thing, that have no explanation out of a delivered privacy violation, and a mistake in showing it.

I explain.
Im under Lubuntu. I just come to make a fresh install of the 14.04

Im using firefox and midori as browsers, usually. Firefox i keep in another parition, with the .config/ dir linked since a time (i share the bookmarks, and the config stuff with another firefow installation in a third partition, with Voyager (XFCE))

Last day I installed chromium to see how was his perfomance, regarding cpu comsumption (sometimes pluginsn firefox uses too much cpu, and my netbook is an old one).

After on installaion, first open, I get in the "settings" side to configure the search engine chosen instead of Google, and there to my suprise was all my Historical of navigation registered from firefox. So, since last year or more, till last moment when i closed firefox before installing chromium.
(Aclaration, firefox was not runing in this moment, only chromium was)

How is this possible?
Who takes the right of doing this?, why (i can think some possibilities)? What are they doing with this information (if they copy without permission for sure sending somewhere also without... where?)? And the most important: How to prevent other people of this intrusion?

Thanx for any orientation... explanation... or redirecting...

Caroxo

---

### Post by LastDino on 2014-06-16
You probably clicked on ''import from Firefox'' while installing chromium? But I could be wrong and I doubt there is any place to complain about that, unless you go out and file a registered complaint. That would be extreme though.

Also, Chromium eats more CPU and RAM than Firefox. If you want to go lighter, stick with Midori, or go with text browser if must.

---

### Post by coffeecat on 2014-06-16
> **CaRoXo said:**
> 
How is this possible?
Who takes the right of doing this?

Most likely you. When you first open a freshly-installed chromium, there is a bar near the top that says, "For quick access, place your bookmarks here on the bookmarks bar. _Import bookmarks now..._" If you click on the underlined bit - which is a link in the browser - you get a small window which asks if you wish to import bookmarks and settings from Firefox. The pre-ticked options which you can unselect if you wish, are Browsing History, Favorites/Bookmarks, Saved passwords and Search engines, which include all the things you are complaining about. 

I guess you must have authorised all these things to be imported from Firefox yourself. All that chromium does is to import this stuff from the .mozilla folder in your home folder. 

I doubt there is any intrusion or anyone sending anything anywhere.

---

### Post by LastDino on 2014-06-16
And to add to that, you should also consider ''cleaning the browser'' once in a while.

---

### Post by monkeybrain20122 on 2014-06-16
> **LastDino said:**
> And to add to that, you should also consider ''cleaning the browser'' once in a while.

+1 :) Browser can slow down or even freeze (if ram is short) when cache grows too big.

---

### Post by CaRoXo on 2014-06-16
Hey, first thanx coffecat, lastdino and monkeybrain for your time/answer.

Yes, I know, but seems I forgot to clean cache since last year. And Yes also, Im using midori and now starting with terminal-browser. But firefox is still the one with im managing bookmarks and using like "base", even if trying to use less and less... 

Yes also, I know that you are offer to import the stuff. But, I wasnt. I never check or uncheck any pre-ticked option. So if all this options should be ticked, should have imported the other stuff also. But not. Only historical. No Bookmarks. No search engines (was this i was trying to set when i saw it). And passwords... I dont know. I just got pissed and closed chromium. But hope not. 

I was not drunk or under any effect for forgeting have done all this, or ticked or unticked... I would not submit the question if were like this. Just did it becouse i dont find logical explanation. 

And still dont find.

Ahh sorry, I forgot something maybe important. This chromium fresh installed, come also with a bug. The keyboard doesnt work with. I cant type anything, while at the same time in any other program i can.

Anyway i understand that is difficult to figure it out. And if it was a bug this of the importing, that is related somehow with this of the keyboard, have less idea still.

For me just smells strange, and I wanted to know the opinion of people with more idea that me.

Thanx again for your time.

CaRoXo

---

### Post by mastablasta on 2014-06-17
well the Chromiumk source is open and you can have a look in it for your self if you htink something is fishy. or report it and have someone else look it in for you.

---

### Post by Tar_Ni on 2014-06-18
> **CaRoXo said:**
> Hey, first thanx coffecat, lastdino and monkeybrain for your time/answer.Ahh sorry, I forgot something maybe important. This chromium fresh installed, come also with a bug. The keyboard doesnt work with. I cant type anything, while at the same time in any other program i can.

Anyway i understand that is difficult to figure it out. And if it was a bug this of the importing, that is related somehow with this of the keyboard, have less idea still.

For me just smells strange, and I wanted to know the opinion of people with more idea that me.

Thanx again for your time.

CaRoXo

There is a bug with Chromium and Ibus on Lubuntu. You just need to exit Ibus with the icon on the taskbar and all will work properly. Hopefully it will be fixed in Chromium 35.

 I will have to agree with the posts above, when installing Chromium it will ask you if you want to import all your previous browser history and bookmarks. You probably overlooked this step and ended up importing all you had accumulated in Firefox.

There is nothing fishy with Chromium, it's an open-source project that serves as a base for Google Chrome. You don't have any kind of trackers in Chromium and thanks to the Ubuntu dev you have the most stable builds made available for you as well as the latest Chrome pepperflash plugin. On Windows, it's much more complicated to get stable builds and there is no update system.

Not to mention, Chromium is a *very* fast browser, and that makes all the difference on weak hardwares. :)

---

### Post by buzzingrobot on 2014-06-21
The data Chromium imported is stored in files -- essentially text files -- on the machine in the user's home directory. It's the data -- cookies, bookmarks, cached files, etc.  -- all browsers generate in use. Offering to import it is a convenience, not a bug or a privacy threat. Chromium simply copied the Firefox files to its directory and probably massaged them a hit so Chromium can work with them.

---

### Post by kate_jakson on 2014-07-09
> **buzzingrobot said:**
> The data Chromium imported is stored in files -- essentially text files -- on the machine in the user's home directory. It's the data -- cookies, bookmarks, cached files, etc.  -- all browsers generate in use. Offering to import it is a convenience, not a bug or a privacy threat. Chromium simply copied the Firefox files to its directory and probably massaged them a hit so Chromium can work with them.
You mean that Chromium gets data from Firefox without any default values?
I heard that it can do this from Explorer, but what about Firefox.... I'm not sure....

---

### Post by buzzingrobot on 2014-07-09
> **kate_jakson said:**
> You mean that Chromium gets data from Firefox without any default values?
I heard that it can do this from Explorer, but what about Firefox.... I'm not sure....

Firefox data are stored in two locations in your /home folder:  <Home>/.cache/mozilla/firefox and <Home>/.mozilla/firefox. I haven't used Chromium in a long time, but if it imports Firefox data, that's where it finds it.

---

### Post by sam-c on 2014-07-09
> **LastDino said:**
> And to add to that, you should also consider ''cleaning the browser'' once in a while.

On my Tablet and Mobiles I have been using 360 security checkup and CM Moniter to check security:guitar::guitar:

---

### Post by kate_jakson on 2014-10-29
> **buzzingrobot said:**
> Firefox data are stored in two locations in your /home folder:  <Home>/.cache/mozilla/firefox and <Home>/.mozilla/firefox. I haven't used Chromium in a long time, but if it imports Firefox data, that's where it finds it.
Thanks for your explanation. I appreciate it.

---

