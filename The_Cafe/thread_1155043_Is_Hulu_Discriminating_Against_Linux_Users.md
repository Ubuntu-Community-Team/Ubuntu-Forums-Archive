---
title: "Is Hulu Discriminating Against Linux Users?"
date: 2009-05-10
forum: The Cafe
---

### Post by Darkhack on 2009-05-10
Note: If you aren't in the United States, Hulu may not work for you regardless.

I've been a big fan of Hulu and have never had problems viewing Hulu videos on Linux until just a couple days ago.  The page comes up fine but the video box (Flash based) stays stuck at the loading screen.  I tried just about everything with no success.  Then I got a hunch.  I used the "User-Agent Switcher" extension for Firefox to say that I was using IE 7 on Vista.  Sure enough Hulu started working.  I disabled/enabled the user-agent several more times just to be sure it wasn't a coincidence and every time without exception, Hulu would play when it thought I was using IE 7 and Vista, but get stuck at the loading screen with Firefox on Ubuntu.  No other settings were changed.  Is anyone else able to confirm this?  I don't want to accuse them of wrong doing just yet until others can reproduce the same behavior.

**edit:** I also wanted to add that I tested this with possible problematic extensions like Flashblock, Ad-Block, No-Script, etc, all disabled and the behavior was still the same.  Hulu would not work with Linux/Firefox but did with the IE7/Vista user-agent even when these extensions were disabled.

**update:** Approximately 5 hours after I posted this, Hulu began working on Firefox/Linux again without troubles and did so consistently.  It appears to have only been a temporary problem.  However I do find it odd that the problem could only be fixed earlier with a modified user-agent.  A few others were able to confirm this behavior.  If that was you, please post an update now to let me know if it is still happening.

**edit:** if pwnst*r replies, ignore the troll.  He's been harassing users on this thread who had the bug.

---

### Post by overdrank on 2009-05-10
I have no issues viewing Hulu. Now some others maybe :)

---

### Post by MaxIBoy on 2009-05-10
Works okay for me...

---

### Post by collinp on 2009-05-10
I can confirm. This happened when I tried both commercial settings - extended and normal. With extended, it played the commercials but then would not load the video -.-. With normal, it didnt load at all.

EDIT: Fyi, its not /visiting/ Hulu.com thats the problem, its actually playing the videos.

---

### Post by RPG Master on 2009-05-10
:o

Its doing the same thing to me :(

---

### Post by alfa16vjtd on 2009-05-10
When i install firefox under wine he does the same I can try to visit Hulu under windows :)

---

### Post by TBOL3 on 2009-05-10
Same thing here.  I can see the "This program is brought to you by", and then I see a forever lasting loading bar.  Until, I use user agent switcher.

Oh well, at least at the moment they are relying users honesty to let them know they're running windows, I hope they don't actually use some other types of implementation (requiring you to install software, etc.).

---

### Post by myusername on 2009-05-10
i watched alot of stuff yesterday and it was fine. sometimes it will give me a warning that i should turn adblock off but it just gives me a 30 second warning instead of commercials and then goes right on playing the show

---

### Post by alfa16vjtd on 2009-05-10
When I install firefox under windows, I have the same problem so it's not only a linux problem

---

### Post by Ms_Angel_D on 2009-05-10
I used to never have issues with it now It won't work unless I use Useragent switch for IE 7

---

### Post by alfa16vjtd on 2009-05-10
maybe the problem is firefox specific?

---

### Post by inobe on 2009-05-10
as of today i can't watch hulu, i am currently troubleshooting the issue.

as mentioned' the add selection seems to be the root problem.

---

### Post by swoll1980 on 2009-05-10
It's not discrimination, they just don't care. If you were in the 1% of people that used goat urine as fuel, would you expect the gas stations to set up a goat urine pump just for you?

---

### Post by inobe on 2009-05-10
it's something dealing with the add selector, if you don't make a choice' the default selection will loop forever.

if you make a selection then you get a continuous loading screen followed by an error "check your internet connection settings"

---

### Post by qiepenguin on 2009-05-10
> **alfa16vjtd said:**
> When I install firefox under windows, I have the same problem so it's not only a linux problem

Actually, Hulu works fine for me in Firefox on Windows XP.  I am seeing the problem with Firefox on Ubuntu.

Hulu is working fine in other browsers on Ubuntu (e.g. Epiphany), so it seems to me like the error is coming with the Firefox/Ubuntu combination.

---

### Post by alfa16vjtd on 2009-05-10
It's because I'm European I think,..... Can It be used outside the us?

---

### Post by inobe on 2009-05-10
who is having trouble with hulu running jaunty 64 bit ?

---

### Post by qiepenguin on 2009-05-10
I wonder if the errors have to do with Hulu's efforts to block Boxee workaround agents that pretend to be Firefox.

see article: [boxees-latest-trick-to-fool-hulu-cloning-firefox-2009-3]("http://www.businessinsider.com/boxees-latest-trick-to-fool-hulu-cloning-firefox-2009-3")

---

### Post by Eviltechie on 2009-05-10
Try disabling you addons, especially addblock plus.

---

### Post by sarang on 2009-05-10
> **swoll1980 said:**
> It's not discrimination, they just don't care. If you were in the 1% of people that used goat urine as fuel, would you expect the gas stations to set up a goat urine pump just for you?

Exactly. It is for us to convince them that there is money to be made selling goat urine.

---

### Post by Ms_Angel_D on 2009-05-10
> **Eviltechie said:**
> Try disabling you addons, especially addblock plus.

I did this and still had issues. The only way I got it to work was with User Agent Switch.

---

### Post by -grubby on 2009-05-10
> **swoll1980 said:**
> It's not discrimination, they just don't care. If you were in the 1% of people that used goat urine as fuel, would you expect the gas stations to set up a goat urine pump just for you?

I don't think it's so much that they don't care if it works in Linux, but more so that they intentionally made sure it didn't.

---

### Post by LightB on 2009-05-10
It's the custom agent tags Ubuntu puts on firefox. It doesn't happen in the default Firefox user agent for linux. Try going into about:config and disabling those tags, something like "jaunty (9.04)", or something like that. Just make it ordinary firefox and hulu will work.

---

### Post by FuturePilot on 2009-05-10
> **Darkhack said:**
> Note: If you aren't in the United States, Hulu may not work for you regardless.

I've been a big fan of Hulu and have never had problems viewing Hulu videos on Linux until just a couple days ago.  The page comes up fine but the video box (Flash based) stays stuck at the loading screen.  I tried just about everything with no success.  Then I got a hunch.  I used the "User-Agent Switcher" extension for Firefox to say that I was using IE 7 on Vista.  Sure enough Hulu started working.  I disabled/enabled the user-agent several more times just to be sure it wasn't a coincidence and every time without exception, Hulu would play when it thought I was using IE 7 and Vista, but get stuck at the loading screen with Firefox on Ubuntu.  No other settings were changed.  Is anyone else able to confirm this?  I don't want to accuse them of wrong doing just yet until others can reproduce the same behavior.

edit: I also wanted to add that I tested this with possible problematic extensions like Flashblock, Ad-Block, No-Script, etc, all disabled and the behavior was still the same.  Hulu would not work with Linux/Firefox but did with the IE7/Vista user-agent even when these extensions were disabled.

I can confirm this behavior. Ubuntu 64bit

---

### Post by inobe on 2009-05-10
> **LightB said:**
> It's the custom agent tags Ubuntu puts on firefox. It doesn't happen in the default Firefox user agent for linux. Try going into about:config and disabling those tags, something like "jaunty (9.04)", or something like that. Just make it ordinary firefox and hulu will work.

```
general.useragent.extra.firefox;Firefox/3.0.10
general.useragent.locale;en-US
general.useragent.security;U
general.useragent.vendor;Ubuntu
general.useragent.vendorComment;jaunty
general.useragent.vendorSub;9.04
```

that's what it looks like, how would it be edited to.

---

### Post by ulfj on 2009-05-10
alpha wrote:

 Re: Is Hulu Discriminating Against Linux Users?
It's because I'm European I think,..... Can It be used outside the us?


I'm not sure, it doesn't work in Mexico as a client of mine misses her shows while she is at home,she cant get Fancast to work also. She wants me to make them work so she can watch "House" so I'm looking for a alternative.


As far as Hulu I can watch at work but not at home (same laptop) I think it's my ISP as I find weird things that go on with them from time to time.

---

### Post by pwnst*r on 2009-05-10
i guess i don't understand what Hulu would have to gain by purposely "discrimating" against linux users.

---

### Post by LightB on 2009-05-10
> **inobe said:**
> ```
general.useragent.extra.firefox;Firefox/3.0.10
general.useragent.locale;en-US
general.useragent.security;U
general.useragent.vendor;Ubuntu
general.useragent.vendorComment;jaunty
general.useragent.vendorSub;9.04
```

that's what it looks like, how would it be edited to.

I believe you must blank out the last 3 lines, the ones with "vendor". If you mess up you can always reset it to default. Basically, the agent has to look something like this:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.10) Gecko/2009042708 Firefox/3.0.10

---

### Post by inobe on 2009-05-10
> **LightB said:**
> I believe you must blank out the last 3 lines, the ones with "vendor". If you mess up you can always reset it to default. Basically, the agent has to look something like this:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.10) Gecko/2009042708 Firefox/3.0.10

editing jaunty to firefox on this line did the trick, thanks

```
general.useragent.vendorComment;jaunty

```

---

### Post by paddydd on 2009-05-10
I am in the US (NJ) and I just started a video on Hulu and it worked fine.
I am using Jaunty and have a 32 bit version.

Paddy

---

### Post by MikeTheC on 2009-05-10
No problems for me under any of the following:

[list][*] Firefox 3.0.x/Ubuntu 8.04 (don't remember the version any more)
[*] Firefox 3.0.x/Ubuntu 8.10 (don't remember the version any more)
[*] Firefox 3.0.10/Ubuntu 9.04
[*] Firefox 3.5b4/Mac OS X 10.5.6[/list]

---

### Post by starcannon on 2009-05-10
I use Hulu regularly on both 32bit and 64bit versions of Ubuntu 8.04+ no problems at all.

---

### Post by billmoseley on 2009-05-10
I fixed my Hulu problems by using Adobe's official Flash plugin, rather than the open source version.  Haven't had an issue since.  I'm using 32 bit though, so 64 might still not work.

---

### Post by Darkhack on 2009-05-10
Approximately 5 hours after I started this thread, Hulu began working on Firefox/Linux again without troubles and did so consistently.  It appears to have only been a temporary problem.  However I do find it odd that the problem could only be fixed earlier with a modified user-agent.  A few others were able to confirm this behavior.  If that was you, please post an update now to let me know if it is still happening.

> **swoll1980 said:**
> It's not discrimination, they just don't care. If you were in the 1% of people that used goat urine as fuel, would you expect the gas stations to set up a goat urine pump just for you?

It's not as though Hulu has to make special arrangements for Linux users.  Hulu uses Flash which works on Windows, Mac, and Linux without the developer needing to do anything special.  To use your analogy, it would be like a gas station saying that you can't fill up your minivan; only cars and trucks allowed.  It's not as though a van uses special gas or operates any differently at a gas station than the other vehicles.  This was a case of Hulu explicitly denying Linux users access even though their service works perfectly as has been demonstrated in the past and when the user-agent was manually changed.

Do you understand the difference between denying access "just because" and denying access because special accommodations would be required?

---

### Post by FuturePilot on 2009-05-10
> **Darkhack said:**
> Approximately 5 hours after I started this thread, Hulu began working on Firefox/Linux again without troubles and did so consistently.  It appears to have only been a temporary problem.  However I do find it odd that the problem could only be fixed earlier with a modified user-agent.  A few others were able to confirm this behavior.  If that was you, please post an update now to let me know if it is still happening.


It's working now without changing the user agent.

---

### Post by inobe on 2009-05-10
this means they were tinkering ?

---

### Post by pwnst*r on 2009-05-10
i think you can edit the topic title now.  a bit of an exaggeration.

---

### Post by Darkhack on 2009-05-10
> **pwnst*r said:**
> i think you can edit the topic title now.  a bit of an exaggeration.

It wasn't an exaggeration at the time.  From my experiences (and from others who confirmed similar behavior) it appeared that Hulu was only denying access based on the user-agent.  Also, I chose to write the topic title as a question instead of a statement because I wanted others to replicate my results before jumping to that conclusion.  I think my topic title was appropriate given what happened previously.  I also edited my first post so that users new to the thread would see my update about it being fixed.

---

### Post by pwnst*r on 2009-05-10
> **Darkhack said:**
> It wasn't an exaggeration at the time.  From my experiences (and from others who confirmed similar behavior) it appeared that Hulu was only denying access based on the user-agent.  Also, I chose to write the topic title as a question instead of a statement because I wanted others to replicate my results before jumping to that conclusion.  I think my topic title was appropriate given what happened previously.  I also edited my first post so that users new to the thread would see my update about it being fixed.

once you saw that some people were not having the same problem(s) as you, it should have been pretty clear there were no shenanigans going on at Hulu.

---

### Post by Darkhack on 2009-05-10
> **pwnst*r said:**
> once you saw that some people were not having the same problem(s) as you, it should have been pretty clear there were no shenanigans going on at Hulu.

But there were (past tense) shenanigans.  And other people were having the same problems as me.  I wasn't the only one with this behavior.  It appears to be fixed now, but that doesn't mean it wasn't broken before.

---

### Post by pwnst*r on 2009-05-10
again, if it was a problem with everyone, i can see your point. it wasn't - just a handful of people.  

no shenanigans, no "discrimination".

---

### Post by wolfyking2 on 2009-05-10
This happened too me to!  Good news it's working, because I gotta watch family guy :)

---

### Post by Darkhack on 2009-05-10
> **pwnst*r said:**
> again, if it was a problem with everyone, i can see your point. it wasn't - just a handful of people.  

no shenanigans, no "discrimination".

You sound like Ulrich Drepper.  If **EVERYONE** doesn't experience it, then it's not a bug.

---

### Post by SunnyRabbiera on 2009-05-10
Strange works for me just fine, no user agent needed, but I did make sure to install every codec possible

---

