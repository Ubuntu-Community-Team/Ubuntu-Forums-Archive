---
title: "Google Calendar doesn't like Linux"
date: 2008-11-30
forum: The Cafe
---

### Post by Dragonbite on 2008-11-30
I don't know if it is just me or not, but Google calendar doesn't like Firefox in Linux, but it works 100% fine on Firefox in Windows!

I have multiple calendars set up; one for my activites, one for my wife's, one for each kids, one for the entire family, etc.

Attaching the calendars to Evolution/Thunderbird isn't a solution because it is one-way only (unless there is something nobody is telling me).

When I go into my Google Calendar in Firefox in Linux I get : [LIST]
[*]Only a couple of my calendars are displayed. I have to click on all of my calendars one-by-one (click once to deactivate it and another to activate it again)
[*]Just tonight I find no entries what-so-ever for a couple of my calendars that I know have a number of recurring and non-recurring activities.
[*]When I go into it in Windows, it works perfectly fine.
[*]It hasn't made any difference what version of Firefox I am using.
[*]Many times it will not save or double-saves new events.
[/LIST]

I use Gmail and a number of google apps. I would rather not return/switch to Yahoo! until I know the future fate of it and MSN is not very linux friendly.

My ultimate desire is to have a MS-Exchange like system for Linux with web accessibility without having to host and run myself (Zimbria?)

---

### Post by qamelian on 2008-11-30
Odd, I don't experience any of those problems with Google Calendar and I exclusively use Firefox and Linux.

---

### Post by bruce89 on 2008-11-30
> **Dragonbite said:**
> Attaching the calendars to Evolution/Thunderbird isn't a solution because it is one-way only (unless there is something nobody is telling me).

In Evolution, the "Google" calendar type is two-way.

---

### Post by OrangeCrate on 2008-11-30
> **qamelian said:**
> Odd, I don't experience any of those problems with Google Calendar and I exclusively use Firefox and Linux.

+1

I have five separate calendars in Google Calendar, and I haven't had a problem at all with Firefox on Linux. Strange.

---

### Post by cybergalvez on 2008-11-30
> **bruce89 said:**
> In Evolution, the "Google" calendar type is two-way.

I use google calendar in thunderbird all the time and its two-way, you just need the right plugins.  You need lightning and one other extension to make it work.  (search the plugin site, I don't have it open at the moment and don't remember the name of the extensions)  

As for google cal in fireforx I've not had any issues.  I remeber having some strange stuff with firefox a while back that didn't make sense, try making a new profile, and see if google cal work better in the new profile.  If so then your current profile is messed up.

---

### Post by Dragonbite on 2008-11-30
All of my systems at home run through an IPCop proxy server running DansGuardian content filter system.

I had the issue before that DansGuardian was blocking some Ubuntu repositories and I had to enter them into the exclude list so my growing guess is something similar happening here.

2-way works in Evolution and Thunderbird? What versions are you running? Currently I'm running Ubuntu 7.10 and 8.04.  I may upgrade to 8.10 on one of my systems but the desktops are having problems with their video cards in 8.10 (but shows up in hardware drivers in 8.04).

---

### Post by aeacides on 2008-12-01
Yup, works in both directions ! :

[http://bfish.xaedalus.net/?p=239](http://bfish.xaedalus.net/?p=239)

:)


> **Dragonbite said:**
> All of my systems at home run through an IPCop proxy server running DansGuardian content filter system.

I had the issue before that DansGuardian was blocking some Ubuntu repositories and I had to enter them into the exclude list so my growing guess is something similar happening here.

2-way works in Evolution and Thunderbird? What versions are you running? Currently I'm running Ubuntu 7.10 and 8.04.  I may upgrade to 8.10 on one of my systems but the desktops are having problems with their video cards in 8.10 (but shows up in hardware drivers in 8.04).

---

### Post by Dragonbite on 2008-12-01
Partial success (better than none).  I added group.calendar.google.com to my exceptions list from my content filter.

Now when I first go into Google calendar on the web, most of them are still not selected but when I go through and click 2x for each calendar the each come up.

So now it is just the initial view that is not working, which is very annoying but not a killer.  At least Calendar is fully functioning.

Thanks for the link. I have 1/2 installed so I'm going to give the second half a go when I get a chance.

What do I need to get Evolution working?

---

### Post by Yownanymous on 2008-12-01
> **Dragonbite said:**
> MSN is not very linux friendly.
Well I wouldn't have thought that at all... :twisted:

---

### Post by Enigmatic on 2008-12-01
I have Thunderbird working both ways with Gcal in 8.10, but no luck with Evo. It doesn't even read properly :(

---

### Post by ooolongT on 2009-01-05
As someone stated before, all you need are the right extensions.  Lightning and the "Provider" pluug-in will do the trick.  There seems to be something of a lag, but Provider will definitely give you two way access to your Gcal.

---

### Post by Dragonbite on 2009-01-05
Ok, I think I've fixed my problems (well, mostly).

I added the google calendar URL to the whitelist for DansGuardian to allow. This helped some.

I also realized that I was using the Public calendar link, not the Private (writable) version. :oops:

I did remove the Lightening that came from the Ubuntu repositories and instead added it through Thunderbird's Add-On site plus updated the Google pieces.

Now it works like a charm!  I haven't tried going to it via Firefox (or Opera) but Thunderbird is running it beautifully.

I also included the Google Contacts so my Thunderbird is really very Exchange like (for better or worse) with contacts, email (imap) and calendar!

Next step will be to setting up my calendars on my wife's login Thunderbird so she can updates/change as things come up! I had set up a calendar for each of our kids, my wife, myself and everybody as a family so I can keep track of who is doing what which may be overkill, but she's the one who knows their current schedules so it makes sense for her to keep them up-to-date.

---

