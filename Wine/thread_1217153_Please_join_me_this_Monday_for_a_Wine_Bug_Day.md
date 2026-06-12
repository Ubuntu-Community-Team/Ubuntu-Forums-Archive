---
title: "Please join me this Monday for a Wine Bug Day"
date: 2009-07-19
forum: Wine
---

### Post by YokoZar on 2009-07-19
The Wine project needs some serious help cleaning up its bug tracker.  There are a *lot* of bugs that are over 6 months old but no one's really sure if they're still live or not.

Many of these bugs have a link to a free download, and all that's needed is for someone to just download and test them.


I'm organizing a Bug Day this Monday (July 20).  It's much easier if we're all doing this together, as if you're unsure about what to do you can easily ask and I (or someone else) will be there to answer for you. I've set up a wiki page for Bug Day here: [http://wiki.winehq.org/BugDay](http://wiki.winehq.org/BugDay)

Bug triage like this isn't always glamorous, but it's really important - by taking care of the bug triage for them the other Wine developers can spend a *lot* more time doing actual development.


So, please help me by joining #winehackers on freenode this Monday, and I'll thank you personally.  My name is YokoZar, and I'll try to be logged in all day.


Feel free to post questions or suggestions in this thread or at the wiki.  Again, thank you.

---

### Post by NightMKoder on 2009-07-19
> **hiramiXD said:**
> Will we need to have a similar hardware setup to those who originally reported the bug?

For D3D/opengl bugs, probably, but only if the bug mentions a specific video card. If it doesn't mention anything and it is D3D/opengl, then you should probably ask the reporter.

---

### Post by YokoZar on 2009-07-19
> **hiramiXD said:**
> Will we need to have a similar hardware setup to those who originally reported the bug?
Most Wine bugs are not hardware dependent at all - and for those few that are (direct 3d), it's still useful to know if it *doesn't* occur on your particular setup.  When it works for you, the bug is in their drivers.

---

### Post by YokoZar on 2009-07-20
Our target for bug day will be [This search](http://bugs.winehq.org/buglist.cgi?query_format=advanced&short_desc_type=allwordssubstr&short_desc=&product=Wine&long_desc_type=substring&long_desc=&bug_file_loc_type=allwordssubstr&bug_file_loc=&status_whiteboard_type=allwordssubstr&status_whiteboard=&keywords_type=allwords&keywords=download&bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=RESOLVED&emailassigned_to1=1&emailtype1=substring&email1=&emailassigned_to2=1&emailreporter2=1&emailcc2=1&emailtype2=substring&email2=&bugidtype=include&bug_id=&votes=&chfieldfrom=&chfieldto=2009-01-01&chfieldvalue=&cmdtype=doit&order=Reuse+same+sort+as+last+time&field0-0-0=noop&type0-0-0=noop&value0-0-0=).  These are all the bugs that haven't been touched since 2008 and are tagged "Download", meaning the bug can be verified by testing against a freely downloadable app.  At the start of Bug Day, there are 574 of them.

Let's get digging!

---

### Post by YokoZar on 2009-07-21
I'd like to thank everyone that participated in our first Bug Day.  I'm
definitely going to repeat it again next release, although I may move it
back a few days.

Some statistics:

Our bug target search (bugs unchanged since January 1st with the
download tag) started at 574 bugs.  Now it's down to 508.  That's 66
bugs that were either resolved, confirmed, or at least checked in on.

In the past two days there have been 30 bugs newly resolved.  By
comparison, over the previous 2 weeks before then there were only 16
bugs resolved.


So, we're definitely making progress.  Quite a few of us had some fun,
and I personally get a real satisfaction out of transforming our bug
database from a scary mess to a place we actually look forward to visiting.

Again, thanks!

---

