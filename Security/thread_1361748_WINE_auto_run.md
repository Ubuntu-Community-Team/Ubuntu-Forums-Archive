---
title: "WINE auto run"
date: 2009-12-22
forum: Security
---

### Post by Bill-Gates on 2009-12-22
I have been reading about wine being vulnerable to malware and since I am so new to Ubuntu I thought I should tell you what I have done so far.

Last week I reformatted someone's XP Home OS for them but didn't have time to tweak a few things while I was there.

I installed WINE on my Main user account and immediately downloaded team-speak. 

Then I connected to there computer from my main account and began tweaking there OS to make it safer.
 Everything went fine.

I just started using another application on my limited user account that uses WINE. 

What I noticed is that when I use this other app is that it starts right up up without asking me if I want it (WINE or the app) to run.

This seems like it could be a security issue. 

I was wondering if there is a setting that would force wine, or the apps, to ask me if I want them to run before they actually start up?

---

### Post by bodhi.zazen on 2009-12-22
You can try to confine wine with apparmor =)

for the most part, so long as you do not run wine as root any damage would be contained to your wine directory.

---

