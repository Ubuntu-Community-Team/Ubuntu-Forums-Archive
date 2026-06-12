---
title: "Suggestion on BUG sticky - Organizing our work as PP testers"
date: 2011-11-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-11-26
Last development cycle (OO) we all ran into a bunch of bugs and discussed workarounds to them. We also opened bug reports about them, but it was hard to keep track of bug reports created by other testers. 

I'd like to suggest that we have a **sticky** here to which **testers** would post:

> **1. Bug _Short_ Description: **(as succinct as possible);
**2. ****How to Reproduce the bug: **(as succinct as possible);
**3. Expected behavior: **(as succinct as possible);
**4. Current behavior: **(as succinct as possible);
**5. Attachments: **Image, code, files that can contribute to understanding the bug (if any)[B];
6. Platform tested (if relevant): [/B]Software / package versions, hardware involved.[B] 
7. Workaround (if any): [/B]Full workaround in CODE (for code) or QUOTE (for other procedures) tags. Not a long tutorial for beginners. A working/usable fix. No external link to workaround unless really needed (download of package, etc), so one can rapidly learn how to solve the problem when reading this sticky;
**8. Link to Discussion Thread (if any): **(full U+1 link, so we can easily click it to open);
**9. Link to Bug Report: **(full launchpad link, so we can easily click it to open)[B];
10. Bug Report Status: [/B](will fix, will not fix);
**11. Bug status: **(Fixed, Not Fixed).[B]
Why?[/B]
- We have a higher density of power-users here than in other forum sections. The content we create is not being properly organized / used;
- Reading all posts in all our threads is not viable for users, testers, helpers or developers.

**Working like this, we can:**
- Keep track of bugs, workarounds and reports of all testers; 
- Test and try to reproduce behavior;
- Try to find cause and workarounds to support developers and helpers;
- Participate and reinforce bug reports;
- Organize information that helpers can use when PP is released (they can read this thread to see if the behavior they are trying to help a user with is a reported bug. If there's a workaround, they can advise it instead of trying non-sense procedures);
- Organize information in a format developers can use to fix bugs.

**The only rules would be:**
- One bug report per post, so the original bug reporter can edit it when the status changes;
- All fields must be respected, even if blank, in the exact same order. Formatting must be respected (Numbering, bold on section title, normal on following text, no empty/space lines between items). 
- Partial, confusing reports, will be checked by us, and re-reported in proper way if valid;
- Descriptions as succinct, technical and direct as possible. Keep any sort of discussion on the bug discussion thread;
- No unrelated, "me too", newbie postings**(¹)** or any type of comment. All these can be done in the bug discussion thread;
- No political, anti-ubuntu, anti-unity, pro-any-distro, rant content of any kind. All these can be done in the bug discussion thread;
- If a bug report is posted by someone (tester or not) and no one can reproduce the bug (e.g. the report is wrong) the bug report will be deleted.

**(¹)** **Newbie postings** are those that: Are not bugs, do not relate to PP, are of no use to us, to helpers, to developers. Should be in "General Help".
e.g.: "Ubuntu doesn't work", "I can't print", "I can't move the launcher", "I can't customize Unity", "I see a black screen", "I get a 404 error when I run apt", "Flash won't work", "I did something, installed a thing and now I can't xyz", "Ubuntu is slow", "I can't start Unity in my HP-12C".

**Creating this structure / organization method:**
- Is easy;
- Make us more productive / professional as testers;
- Increases chances of helpers providing more effective support at General Help (considering they use this tool);
- Increases chances of bugs getting fixed, as we can provide technical info to developers and all sign to the same bugs;
- Makes it clearer for the community what our work here is. Brings value to our work.
[B]
About the sticky:
[/B]- The first post will contain the aforementioned rules;
- The first post will identify which testers are involved in testing what (general testing, (x)buntu, ISO Testing, UI Only, laptops, Unity, etc) in the following format:
<tester handle><space><(link to launchpad if any)>:<Succinct list of test areas, comma separated>;
- Having the list of testers / areas of interest / contact info in the first post allows us to be easily contacted by helpers/developers of specific areas that may need us to provide additional information. It's all about making things agile and productive.
 
**We can start right now with the bugs we already know.**

Your opinions, please?

---

### Post by ventrical on 2011-11-26
Aye aye Captain. ! :)

 Great idea. Lets do it.

 Last session with OO I got so busy with other projects that I  de-documented a lot of important items.

Not a tidy way to beta test at all.

+1

---

### Post by ventrical on 2011-11-26
> **effenberg0x0 said:**
> 
- No unrelated, "me too", newbie postings or any type of comment. All these can be done in the bug discussion thread;



  You got to loosen up a bit about newbies. Remember, you were a newbie once too :)

just a suggestion.

:)

---

### Post by effenberg0x0 on 2011-11-26
> **ventrical said:**
> Aye aye Captain. ! :)

 Great idea. Lets do it.

 Last session with OO I got so busy with other projects that I  de-documented a lot of important items.

Not a tidy way to beta test at all.

+1

Me too Ventrical... Once hell break loose in OO release day, and we needed to point users/helpers in the right direction, I was searching my own threads to try to find the workarounds I had done months earlier, trying to search the archived U+1 forum section to find workarounds by others, etc. Not the best way to do things.

---

### Post by effenberg0x0 on 2011-11-26
> **ventrical said:**
> You got to loosen up a bit about newbies. Remember, you were a newbie once too :)

just a suggestion.

:)

I think it's more of a language limitation for me in trying to communicate what I want. I don't have any prejudice at all against newbies. They pay my salary :) 

What I meant to say by **"newbie posting" **(let me see if I can say it without sounding "tight" with them): Posts like this should be immediately deleted:

- I can't print
- I can't move the launcher
- I can't customize Unity
- I see a black screen
- I get a 404 error when I run apt
- Flash won't work

This is useless, not a bug, not related to PP and should be in General Help.

**EDIT: **I added a note to the original text properly explaining what I call a newbie post. Hopefully I can sound less hard on them.

---

### Post by ventrical on 2011-11-26
> **effenberg0x0 said:**
> Me too Ventrical... Once hell break loose in OO release day, and we needed to point users/helpers in the right direction, I was searching my own threads to try to find the workarounds I had done months earlier, trying to search the archived U+1 forum section to find workarounds by others, etc. Not the best way to do things.


 While you're at this project (not trying to hijack the forum here) but another good add-on would be (Popularly used sudo code commands) .. a sort of list. I am sure they have one somewhere .. but .. somthing specific to Unity/Precise beta testing .. like Cariboo has in the sticky on how to change over the repos from Oneiric to Precise.

 A  Most Commonly used Sudo Commands- sticky would be great I think. Winter setting in here in Canada and so I'll have lots of indoor time, Jan/Feb, to burn the midnight oil.

You got my vote on this.

 Regards..

---

### Post by ventrical on 2011-11-26
> **effenberg0x0 said:**
> I think it's more of a language limitation for me in trying to communicate what I want. I don't have any prejudice at all against newbies. They pay my salary :) 

What I meant to say by **"newbie posting" **(let me see if I can say it without sounding "tight" with them): Posts like this should be immediately deleted:

- I can't print
- I can't move the launcher
- I can't customize Unity
- I see a black screen
- I get a 404 error when I run apt
- Flash won't work

This is useless, not a bug, not related to PP and should be in General Help.

 Yes.. I see your point now. Perhaps a reminder or so for a once or two time infraction because  even advanced users have a tendency to lead in with nomenclature. ya know .. we' re on the fly eh :)

---

### Post by effenberg0x0 on 2011-11-26
> **ventrical said:**
> Yes.. I see your point now. Perhaps a reminder or so for a once or two time infraction because  even advanced users have a tendency to lead in with nomenclature. ya know .. we' re on the fly eh :)

My idea is that this sticky should be completely focused, technical, organized and "politics-agnostic" (no DE discussion, etc). All bugs should in fact be bugs. It's a tool, it has a purpose, it should stick to it. Which is why I think that, only in this sticky, unrelated / wrong content would have to be addressed a little more tightly. 

Nothing stops people from starting any other thread saying whatever they want outside the sticky, as it already happens. I'm sure the mods can properly move unrelated content out of the sticky to general help.  

I think that bug discussions will likely start in a thread, be tested by everyone, and only if confirmed will be posted at the sticky (that has an item for the link to the discussion thread).

It's just a suggestion anyway :-) Let's see how mods feel about it.

---

### Post by effenberg0x0 on 2011-11-26
> **ventrical said:**
> While you're at this project (not trying to hijack the forum here) but another good add-on would be (Popularly used sudo code commands) .. a sort of list. I am sure they have one somewhere .. but .. somthing specific to Unity/Precise beta testing .. like Cariboo has in the sticky on how to change over the repos from Oneiric to Precise.

 A  Most Commonly used Sudo Commands- sticky would be great I think. Winter setting in here in Canada and so I'll have lots of indoor time, Jan/Feb, to burn the midnight oil.

You got my vote on this.

 Regards..

When we are talking about cli commands to fix a bug, I think the bugs sticky can provide for that in item [B]7. Workaround (if any):.

But there are things that are not properly bugs[/B], that users may want/need to do in their systems. A similarly well-organized sticky, would act as a good "library" **for users and helpers. **Things like how to fix sources.list and APT, code t o auto fix/purge ppas, etc, could be provided/explained there. Once PP is released, it should look good, organized and clean enough to be automatically moved to General Help as a sticky. We have a couple months to work on that. It's a good idea and you got my vote on that :)

**EDIT:** Suggestion: If its organized enough, it could also be easily ported to a wiki page on PP too. I like the idea. If you put together the model, requirements, organization of the thing, I'll contribute. You know how much I love those crazy while|for|if|cat|grep|awk|sed|tee pipes :P

---

### Post by ronacc on 2011-11-27
I like the idea of an organized bug thread , we will need some help from the mods keeping it "pure" by removing posts that belong elsewhere . And I think it will take awhile to get everyone upto speed on a standard form for reporting, I know that I for one tend to wander around a bit . the worst that can happen is that it not be used but if we don,t try we won,t know so go for it.

---

### Post by cariboo on 2011-11-27
> **ronacc said:**
> I like the idea of an organized bug thread , we will need some help from the mods keeping it "pure" by removing posts that belong elsewhere . And I think it will take awhile to get everyone upto speed on a standard form for reporting, I know that I for one tend to wander around a bit . the worst that can happen is that it not be used but if we don,t try we won,t know so go for it.

I'm willing to remove posts that don't belong, and even sticky the thread if it isn't busy enough.

---

### Post by VinDSL on 2011-11-27
> **effenberg0x0 said:**
> 
Your opinions, please?

Great idea!

> **cariboo907 said:**
> I'm willing to remove posts that don't belong, and even sticky the thread if it isn't busy enough.
Green light!

You dah men... ;)

---

### Post by ventrical on 2011-11-27
> **effenberg0x0 said:**
> When we are talking about cli commands to fix a bug, I think the bugs sticky can provide for that in item [B]7. Workaround (if any):.

But there are things that are not properly bugs[/B], that users may want/need to do in their systems. A similarly well-organized sticky, would act as a good "library" **for users and helpers. **Things like how to fix sources.list and APT, code t o auto fix/purge ppas, etc, could be provided/explained there. Once PP is released, it should look good, organized and clean enough to be automatically moved to General Help as a sticky. We have a couple months to work on that. It's a good idea and you got my vote on that :)

**EDIT:** Suggestion: If its organized enough, it could also be easily ported to a wiki page on PP too. I like the idea. If you put together the model, requirements, organization of the thing, I'll contribute. You know how much I love those crazy while|for|if|cat|grep|awk|sed|tee pipes :P


 I'll write up a template page on this sometime early next week and see what the mods say.

!hey! Congrads.. looks like you got your sticky! :)

---

### Post by ventrical on 2011-11-27
> **cariboo907 said:**
> i'm willing to remove posts that don't belong, and even sticky the thread if it isn't busy enough.
                                                                                                                                                                                                                                                          


+1

:)

---

### Post by philinux on 2011-11-27
> **cariboo907 said:**
> I'm willing to remove posts that don't belong, and even sticky the thread if it isn't busy enough.

+1. I'm on it too.

---

### Post by MG&amp;TL on 2011-11-27
Sounds good to me-can we report bugs in L/X/K buntu as well?

Also a link to bug report in launchpad may be idea.
Oh and thanks to ronacc, I have development release installed now. :D

---

### Post by matt_symes on 2011-11-27
I like this suggestion as well.

What about bugs that have raised their head again ? 

I am thinking of the mouse bug i raised that is affecting me (at least).

---

### Post by Elfy on 2011-11-27
> **MG&TL said:**
> Sounds good to me-can we report bugs in L/X/K buntu as well?
Bugs are bugs.

---

### Post by effenberg0x0 on 2011-11-27
> **forestpiskie said:**
> Bugs are bugs.


Exactly. There are people here that use Lubuntu regularly and know a lot about it. Also, The important thing is that hopefully we create something useful/organized for users/helpers/developers in the next months. I'm sure we can make it.

Thank you all for your support on this idea!

---

### Post by effenberg0x0 on 2011-11-27
I'm rewriting / formatting the text for the sticky and testing it with a couple known bugs to make sure the info fields fit / are enough. I'll post it here tomorrow so one of the mods can put it up there.

Then it's up to each of us to dig our own threads and bugs we know and fill in the thread :)

---

### Post by effenberg0x0 on 2011-11-27
> **matt_symes said:**
> I like this suggestion as well.

What about bugs that have raised their head again ? 

I am thinking of the mouse bug i raised that is affecting me (at least).
Yes, every bug we can find that is active. If the bug is fixed closed before PP release, the original bug poster will change it's status to "fixed".
One of the field is a link to existing launchpad bug report. It's important so all of us can keep track of the bugs reported here, "+1" in launchpad reports, hopefully add relevant testing and info there, putting some pressure in it.

---

### Post by ronacc on 2011-11-27
I've been thinking , steps 1>5 + 10& 11 duplicate information that should be in the bug report if one exists , is there any way to get around the duplication of effort and space ? perhaps if there is an existing bug report we would only need to fill in 1+9&6>8 ?

---

### Post by effenberg0x0 on 2011-11-27
Yes, I though of that. I'm rewriting it to simplify as much as possible. But I detected some pitfalls already:

- Some launchpad bug reports are confusing, too long, wrong. One has to read many posts to really be able to summarize it. I want to make it simpler for out target readers (helpers/developers) to read our report than to do what they already try to do (interpret launchpad).

- Sometimes launchpad bug reports were started by an average user and have no usable information in it or it's not properly described. We must be better than that.

- Bug merges are incorrect sometimes. Triagers do what they can but different issues, platforms, etc get put together, unfortunately. And they may also be incorrectly closed too. I trust our testers info more.

- Some bug reports do not have info that relates to PP current status, but to OO and previous versions. We are always more up to date on behaviors and workarounds, as well as affected platforms, software, packages, versions, target Ubuntu flavours, etc.

One thing I'm considering too is that although not all fields are  mandatory in an specific bug report (they sure aren't for all reports),  they _may_ become relevant in some time due to updates or  additional info gathered by us. So fields, even the empty ones, should  probably be kept to  maintain the structure and allow for further additions by the original  poster or other tester.

**My main concern**, which I think it's the most important thing in all of it and should not be compromised in any way, is that the created content shouldn't require a thread viewer to navigate too much out of the thread to fully understand each bug. We are gonna make it as easy as possible for readers (developers, helpers) to get all the critical information about the bug without giving them too much work (read launchpad, etc). We must simplify things for them too.

Also, it should not become a boring job. There's no rush to fill everything in quickly, as we have months ahead  and each one of us can ask for group support into filling the  information (one might now of a better workaround, etc). 

"*Precision*" will be more relevant than volume :) We can all  review the bug thread and contribute to it's completeness. If we, as a group, do one good report a day, that would already be a much valuable contribution until April 26th. 

I'm trying to balance all of it but you can all be sure I'm gonna try me  best to simplify it, as much as possible, into something we can all  participate without putting too much of our time in it. I'm working on  it right now and will send mods a final draft by tomorrow. And if,  during our use of the thread, we feel like we should change it, we can  do it of course.

**EDIT: **Ideally, I would like if we can create such good content that it could also be used to make the life of launchpad **bug triagers** easier. I want to bring some of them to participate in this project. U+1 users that are community official members probably have the resources to put together some sort of announcement / call to the target-audience (helpers, triagers, developers, etc) once we got it running smoothly. But let's cover the first steps and then thinks this things in the future.

---

### Post by ronacc on 2011-11-27
also I think it would be a good Idea to let a bug "cook" for a couple of days before starting a post on it , for instance I was getting repeated crashes of both nautilus and metacity yesterday but none at all today , no use cluttering up the thread (or launchpad ) with things that are transient . It might cause less clutter if we let things develop a bit in the relevant discussion thread before posting to your bug thread .

---

### Post by ventrical on 2011-11-27
@effenberg

 Ok.. I have an example and a question.

 There is this apparent 'bug' that will not allow for smooth scrolling in certain areas of  the Unity Desktop , specifically where  the apps lens is clicked. When I try to used my mouse wheel it is very clunky when it scrolls. I have to go to the side-bar, rightclick my mouse and hold it there while I scroll (move the mouse up and down), yet, when I open a session of GEDIT I can use the unity sidebar tool helper(??)and when I click on that <downpage> the text will smooth scroll. Also when I am in a Unity2D session I am able to smooth scroll with ease using my mouse wheel

 Ok .. so  only **assuming that this is a bug  **how would I make a post  in  this thread? Could you give me an example please.

thanks in advance.

---

### Post by effenberg0x0 on 2011-11-27
> **ventrical said:**
> @effenberg

 Ok.. I have an example and a question.

 There is this apparent 'bug' that will not allow for smooth scrolling in certain areas of  the Unity Desktop , specifically where  the apps lens is clicked. When I try to used my mouse wheel it is very clunky when it scrolls. I have to go to the side-bar, rightclick my mouse and hold it there while I scroll (move the mouse up and down), yet, when I open a session of GEDIT I can use the unity sidebar tool helper(??)and when I click on that <downpage> the text will smooth scroll. Also when I am in a Unity2D session I am able to smooth scroll with ease using my mouse wheel

 Ok .. so  only **assuming that this is a bug  **how would I make a post  in  this thread? Could you give me an example please.

thanks in advance.

Ideally, since this is not a known bug (at least is unknown to me), I would start a normal thread in the U+1 forum, requesting the help of others to confirm this bug. As other test it, confirm it, discuss it, the information needed to fill in in the bug thread will be clearer (affected flavour, possible workaround, etc). The idea is that we should be able to help each other in testing, understanding, studying each bug, as well as finding if it already is posted somewhere in Launchpad, etc. We have to work together to enrich the reports and do something better than the mess at Launchpad.

For example: Running PP on Unity right now, I can't reproduce this bug, so there must be some other condition that triggers it. We must ask the others to try to reproduce this behavior and see how it goes. If it's confirmed, it is a bug (scrolling should not be clumsy in specific portions of the desktop).

---

### Post by effenberg0x0 on 2011-11-27
> **ronacc said:**
> also I think it would be a good Idea to let a bug "cook" for a couple of days before starting a post on it , for instance I was getting repeated crashes of both nautilus and metacity yesterday but none at all today , no use cluttering up the thread (or launchpad ) with things that are transient . It might cause less clutter if we let things develop a bit in the relevant discussion thread before posting to your bug thread .

Agreed. I think there are some bugs we've been dealing since OO and before, and will definitely give some focus to these. We will obviously continue to discuss everything we see, new bugs, etc in the normal threads. But, if a bug persists after many updates, it will get to the bug list. You're totally right on that.

---

### Post by effenberg0x0 on 2011-11-27
Guys, I'm rewriting the text for the sticky, info fields, rules, etc and trying hard to balance keeping it simple for us testers, but still providing valuable info for the information users / target-audience. I told the mod that will post the sticky that I'll send a first draft to him tomorrow morning, so we can all evaluate and discuss specifics over an initial draft of it.

---

### Post by philinux on 2011-11-28
Thread closed new one opened with draft sticky.

---

