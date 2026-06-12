---
title: "HUD Issue (Can't Navigate Menu)"
date: 2012-03-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jasonsmith01 on 2012-03-29
Anyone else experiencing an issue with HUD. I can't seem to navigate down through the menu suggestions, it just bounces me back to the beginning. 

[https://bugs.launchpad.net/unity/+bug/962984](https://bugs.launchpad.net/unity/+bug/962984)

[https://www.youtube.com/watch?v=SgqEONmygsQ&feature=youtube_gdata_player](https://www.youtube.com/watch?v=SgqEONmygsQ&feature=youtube_gdata_player)

---

### Post by jasonsmith01 on 2012-03-29
A good amount of views so far, if no one else is suffering from this can anyone suggest what I may try to fix it? Was hoping all the Beta2 updates today would have fixed it but sadly no.

---

### Post by jasonsmith01 on 2012-03-30
A bit of troubleshooting and have noticed that this bug does NOT happen in my Guest Account which is untouched.

:KS

I had Indicator-Multiload running in my Indicator bar. I noticed when I hit the ALT key the colors that I had chosen for the graphs were all turned white.

[Lightbulb Moment]

I thought to my self... Self, what if the indicators are effecting the HUD menu?

I noticed that the HUD navigation response is directly correlated to what is running in the indicator bar.

I had the following running:

Indicator-Mutliload
Psensor
PS3 Media Server
Indicator Weather

I quit Indicator Multiload and when I arrowed down in the menu the selection remained for a few seconds before moving back up. That is a few seconds longer than it ever did so was a good thing. It appears that when the added indicators refresh, the refresh also forces the HUD to refresh back the top position.

I deleted the rest and it fixed itself. I can now move through the menu bar without an issue.

I will re-apply the indicators one by one and see what I can use and what I can't. Google-Music-Manager so far is running and is not causing a issue.

All is good, how do I mark this thread as solved? EDIT: Marked as Solved.

---

### Post by santosh83 on 2012-03-30
> **jasonsmith01 said:**
> A bit of troubleshooting and have noticed that this bug does NOT happen in my Guest Account which is untouched.

:KS

I had Indicator-Multiload running in my Indicator bar. I noticed when I hit the ALT key the colors that I had chosen for the graphs were all turned white.

[Lightbulb Moment]

I thought to my self... Self, what if the indicators are effecting the HUD menu?

I noticed that the HUD navigation response is directly correlated to what is running in the indicator bar.

I had the following running:

Indicator-Mutliload
Psensor
PS3 Media Server
Indicator Weather

I quit Indicator Multiload and when I arrowed down in the menu the selection remained for a few seconds before moving back up. That is a few seconds longer than it ever did so was a good thing. It appears that when the added indicators refresh, the refresh also forces the HUD to refresh back the top position.

I deleted the rest and it fixed itself. I can now move through the menu bar without an issue.

I will re-apply the indicators one by one and see what I can use and what I can't. Google-Music-Manager so far is running and is not causing a issue.

All is good, how do I mark this thread as solved? EDIT: Marked as Solved.

The "thread tools" menu at the top has the option to mark it solved.

---

### Post by palimmo on 2012-04-07
Same problem.
Should I give up using Indicator Multiload and weather indicator?

---

### Post by jasonsmith01 on 2012-04-07
> **palimmo said:**
> Same problem.
Should I give up using Indicator Multiload and weather indicator?

I did. Kinda wanted the HUD to be usable. 

There's a bug report here:

[https://bugs.launchpad.net/unity/+bug/962984](https://bugs.launchpad.net/unity/+bug/962984)

---

### Post by palimmo on 2012-04-07
> **jasonsmith01 said:**
> I did. Kinda wanted the HUD to be usable. 

There's a bug report here:

[https://bugs.launchpad.net/unity/+bug/962984](https://bugs.launchpad.net/unity/+bug/962984)


Subscribed.
But I need Indicator multiload. I'll wait until they fix it.

---

### Post by palimmo on 2012-04-13
> **jasonsmith01 said:**
> I did. Kinda wanted the HUD to be usable. 

There's a bug report here:

[https://bugs.launchpad.net/unity/+bug/962984](https://bugs.launchpad.net/unity/+bug/962984)

Solved! Now you can use HUD and system monitor ;):guitar:

---

