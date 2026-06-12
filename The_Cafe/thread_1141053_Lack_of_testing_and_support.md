---
title: "Lack of testing and support?"
date: 2009-04-28
forum: The Cafe
---

### Post by Athropos on 2009-04-28
Hi all,

I installed the latest Ubuntu last week, and overall I don't see much difference with the previous version (yeah I know under the hood bla bla...). That's not really a problem, but what is slowly becoming difficult to accept for me is the lack of testing and support.

In older versions of Ubuntu, the printer icon in the systray used to stay there forever, and I had to right-click on it to hide it. This has been fixed some time ago, and guess what? This bug is back in Jaunty (#151360). Why is that? How could nobody notice that the icon never disappear? The best is that now, the "hide" option does absolutely nothing!

The new notification system is nice, but why integrate it now while it's not yet finished? Popups are always black, how is it supposed to integrate with non-dark themes? There are way too small, most of the time the text doesn't fit (e.g., Foo Bar has signed in). They stay for a too short time (I think it's something like 5-6 seconds). By the time I stop reading/writing something, it's already gone and I couldn't read it completely. Most icons are blurry in these popups, even the "system" ones (e.g., you are now connected to...).

The media keys of my laptop (volume up/down) no longer work. Why? They have been working from the beginning, so what happened?

The tooltips of the workspace switcher never disappear when I use my mouse to switch of workspace (#356702), I must click on them *each time* to remove them. Why isn't there any reply from someone capable of fixing this? At least patching the applet to remove the tooltips should take no more than 5 minutes to the guy managing the package. Now I think that chances are that this thing will never be fixed until the next Ubuntu release, and one of these days there will be a reply like "do you still face this bug?".

As you see I've been using the new release for so little time that I don't understand how I can face so many irritating things that will most likely never be fixed. Am I the only one thinking this?

Don't get me wrong, I like Ubuntu (I've been using it full-time since Hoary), but I see it more and more like a big assembly of thousands of components and no real integration.

---

### Post by billgoldberg on 2009-04-28
> **Athropos said:**
> Hi all,

I installed the latest Ubuntu last week, and overall I don't see much difference with the previous version (yeah I know under the hood bla bla...). That's not really a problem, but what is slowly becoming difficult to accept for me is the lack of testing and support.

In older versions of Ubuntu, the printer icon in the systray used to stay there forever, and I had to right-click on it to hide it. This has been fixed some time ago, and guess what? This bug is back in Jaunty (#151360). Why is that? How could nobody notice that the icon never disappear? The best is that now, the "hide" option does absolutely nothing!

The new notification system is nice, but why integrate it now while it's not yet finished? Popups are always black, how is it supposed to integrate with non-dark themes? There are way too small, most of the time the text doesn't fit (e.g., Foo Bar has signed in). They stay for a too short time (I think it's something like 5-6 seconds). By the time I stop reading/writing something, it's already gone and I couldn't read it completely. Most icons are blurry in these popups, even the "system" ones (e.g., you are now connected to...).

The media keys of my laptop (volume up/down) no longer work. Why? They have been working from the beginning, so what happened?

**The tooltips of the workspace switcher never disappear when I use my mouse to switch of workspace (#356702), I must click on them *each time* to remove them. Why isn't there any reply from someone capable of fixing this? At least patching the applet to remove the tooltips should take no more than 5 minutes to the guy managing the package. Now I think that chances are that this thing will never be fixed until the next Ubuntu release, and one of these days there will be a reply like "do you still face this bug?".**

As you see I've been using the new release for so little time that I don't understand how I can face so many irritating things that will most likely never be fixed. Am I the only one thinking this?

Don't get me wrong, I like Ubuntu (I've been using it full-time since Hoary), but I see it more and more like a big assembly of thousands of components and no real integration.

Most of these things will most likely be fixed in the next few weeks.

Either way, the tooltip problem (had the same) can be fixed in gconf-editor.

Press "alt+f2" and enter gconf-editor.

Then go to apps -> panel -> global and untag the box next to "Tooltips_enabled"

---

### Post by Athropos on 2009-04-28
> **billgoldberg said:**
> Most of these things will most likely be fixed in the next few weeks.


Well, we'll see, but I'm rather skeptical about this. 

> 
Either way, the tooltip problem (had the same) can be fixed in gconf-editor.

Press "alt+f2" and enter gconf-editor.

Then go to apps -> panel -> global and untag the box next to "Tooltips_enabled"

I unchecked the box and killed gnome-panel, but (all) tooltips are still there. I'll try to restart Gnome to make sure.

/EDIT

No luck, tooltips aren't disabled.

---

### Post by insane_alien on 2009-04-28
there's only so much testing that can be done in a beta, even an open one so of course there are going to be bugs and regressions missed. And yes they will be spotted when the new version undergoes final release. this ALWAYS happens and there is always a period of mass bug reports and mass bug fixing after the realease. 

you've been a member since 2005, you should know this by now. same thing happens every 6 months and it is not just limited to ubuntu, every other distro and every other bit of software ever produced undergoes this cycle.

---

### Post by Athropos on 2009-04-28
> **insane_alien said:**
> 
you've been a member since 2005, you should know this by now. same thing happens every 6 months and it is not just limited to ubuntu, every other distro and every other bit of software ever produced undergoes this cycle.

I know that, but still I feel like a few people are missing on the integration side. There are so many bugs opened on Launchpad about these integration issues, and that do not depend on a particular software.

It's very frustrating when a bug stays opened for a long time with absolutely no reply (except from other users facing the same problem) and that after more than a year you get a reply asking you whether you're still seeing the bug (which you had to live with for 6 months, until the new Ubuntu release).

And most of the time these bugs could be very easily fixed by people with the right knowledge (e.g., the hide command that does nothing on the print icon)...

---

### Post by billgoldberg on 2009-04-28
> **Athropos said:**
> 
No luck, tooltips aren't disabled.

They won't be disabled, but they will not stay there forever now when switching desktops.

---

### Post by Athropos on 2009-04-28
> **billgoldberg said:**
> They won't be disabled, but they will not stay there forever now when switching desktops.

I just tried: They still appear after my mouse left the applet, and they stay there forever.

---

### Post by skymera on 2009-04-28
People want a 6 month release cycle.
Everyone gets all hyped up.

What can be new and TESTED to be perfect AND stable in 6 months? About jack diddly.

The only realy way to get stable new features it to only release them on LTS or extend the general release cycle.

---

### Post by insane_alien on 2009-04-28
if it frustrates you then get in on the bugfixing loop. you don't need any programming skills to help speed up the bugfixing process, by providing logs of the errors and helping to pinpoint the cause of a bug you'll help developers fix it quicker.

if you have some programming knowledge then have a go at fixing some bugs yourself.

myself i try to help pinpoint the causes but i don't actually come across many bugs that aren't caused by me messing with a config file.

---

### Post by Skripka on 2009-04-28
There are a few reasons that cause users to start with Ubuntu...and a larger number of reasons that they move on to other linux distros after a while.  If you no longer like the Ubuntu way, with all the goods and bads thereof-try something else.  Lots of users do, in fact.

---

### Post by ddrichardson on 2009-04-28
> **Athropos said:**
> It's very frustrating when a bug stays opened for a long time with absolutely no reply (except from other users facing the same problem) and that after more than a year you get a reply asking you whether you're still seeing the bug (which you had to live with for 6 months, until the new Ubuntu release).
I appreciate that its frustrating but as a user you need to appreciate that while you're focused on one or two bugs that you're subscribed to, as a developer we're subscribed to hundreds.

Bug triaging is incredibly important because no-one wants to lose you as a user but unfortunately, the majority of bugs reported in Launchpad are in completely the wrong project. Unless a triager or team member sees them, they never get to the right people and unfortunately there are teams that don't utilize the bug tracking service.

A year seems like a long time, but its only two development cycles and you're talking about a wish list bug really - even if it is a good idea.

---

### Post by mihai.ile on 2009-04-28
well I really think that would help much if there were more guidelines for normal users that have interest on how to help Ubuntu.
And more important is givinf feedback that what the user did actually was worth the time spent so maybe will help again instead of creating threads about "how bad ubuntu is :D and why I leaved... lol".

For example: does the reviews given by users on the wiki under laptop testing team helped in something? so much work and I think it could helped a lot in improving Ubuntu.

Also I think more time should be invested in polishing the "final release". (for example +1 month on the release cycle just for making sure everything is as is expected would be great and I know in the case of Dapper was a huge success in my opinion)

---

### Post by LowSky on 2009-04-28
I just want to say that it took Microsoft  8 years to release Windows Vista, and look how bad it is.

worse comes to worse use an older version that is still supported, like 8.10 or 8.04

---

### Post by Athropos on 2009-04-28
> **ddrichardson said:**
> 
Bug triaging is incredibly important because no-one wants to lose you as a user but unfortunately, the majority of bugs reported in Launchpad are in completely the wrong project. Unless a triager or team member sees them, they never get to the right people and unfortunately there are teams that don't utilize the bug tracking service.


If this is really important to get bugs fixed, then maybe the current system in Launchpad should be improved. When reporting a bug and trying to choose the right package, any search terms bring so many results that it's most likely that the user will select the wrong one or will not select any at all. That's also my case, and I'm not a novice Linux user.

> **mihai007 said:**
> 
Also I think more time should be invested in polishing the "final release". (for example +1 month on the release cycle just for making sure everything is as is expected would be great and I know in the case of Dapper was a huge success in my opinion)

That could be a very good idea. I myself never install any release prior RCs, because I use only one computer and I need it to work correctly, and I'm sure many users do the same. A "final but not-yet-polished release" would attract more people and thus more testers (including me). Then some time could be dedicated to polish the release, and with more users this could be really efficient.

And if choosing the right package is the most important thing in this process, this forum could be used to list the issues found, so that someone with the right knowledge could report the bug to Launchpad with the right tags attached to it.

---

### Post by ddrichardson on 2009-04-28
> **Athropos said:**
> If this is really important to get bugs fixed, then maybe the current system in Launchpad should be improved. When reporting a bug and trying to choose the right package, any search terms bring so many results that it's most likely that the user will select the wrong one or will not select any at all. That's also my case, and I'm not a novice Linux user.No your absolutely right, its a nightmare trying to find the right package, you'd be amazed how often bugs are put against the doc team regardless of what they are.

> **Athropos said:**
> And if choosing the right package is the most important thing in this process, this forum could be used to list the issues found, so that someone with the right knowledge could report the bug to Launchpad with the right tags attached to it.
I'm not so sure about that but it might work - I think a concerted effort to list the most common teams to report certain types of bug to might work.The problem with the forum is that devs dip in and out but its not somewhere that's checked that often.

---

### Post by ddrichardson on 2009-04-28
> **mihai007 said:**
> well I really think that would help much if there were more guidelines for normal users that have interest on how to help Ubuntu.You realise [OpenWeek]("https://wiki.ubuntu.com/UbuntuOpenWeek") is on this week?!
> **mihai007 said:**
> And more important is givinf feedback that what the user did actually was worth the time spent so maybe will help again instead of creating threads about "how bad ubuntu is :D and why I leaved... lol".Of course you need feedback and we'd love to give it fo everything we do but if you look at it from the other side, most people don't bother and then complain about people who are giving up their time!

> **mihai007 said:**
> For example: does the reviews given by users on the wiki under laptop testing team helped in something? so much work and I think it could helped a lot in improving Ubuntu.You wouldn't get feedback here. Laptop testing is designed to let people know about what works and what doesn't because laptops are traditionally a little problematic in Linux. I've completed several of these for laptops I've owned and you'd be surprised, I've had emails asking how I overcame certain issues years later.

> **mihai007 said:**
> Also I think more time should be invested in polishing the "final release". (for example +1 month on the release cycle just for making sure everything is as is expected would be great and I know in the case of Dapper was a huge success in my opinion)
Yes that would be great - it'd make my life a lot easier but there isn't enough time, consider the doc team where I work, we freeze string near the end of the release cycle (because new stuff is being added) then the translations begin. When Hardy was released there was a change to networking under Gnome at the last minute that completely invalidated all my work!

That said, all it takes is more testing volunteers reporting problems and we can fix more stuff for release.

---

### Post by deew on 2009-07-16
Don't mean to hijack the thread, I just want to post this here because it was one of the top places google sent me on this tooltip bug.

I ran across something on another forum that seems to take care of this.  Seems to kill all tool tips in general - personally, I deem that to be an added bonus.

Go to /usr/share/themes/Human/gtk-2.0 and edit gtkrc  (if using another theme then substitute for Human)
go right after the line that says "widget "gtk-tooltip*" style "murrine-tooltips"
and add a line that says "gtk-enable-tooltips = 0"

---

