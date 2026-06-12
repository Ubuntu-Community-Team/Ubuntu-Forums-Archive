---
title: "Several problems on a Notebook install, how do I go about reporting them?"
date: 2012-03-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Kakitus on 2012-03-10
Using the live CD I encountered the following problems:

**Hardware**

[LIST]
[*]**horizontal desktop shift in multi-display mode**: When using 12.04 on a multi monitor setup (Notebook panel at 1366x768, external display at 1920x1080) the desktop is shifted to the right side. As a result there's a small but visible black border on the left side of the first panel while pixels are cut off on the right side of the external display
[*]**WLAN hotkey** (Fn + F3 on Acer TimelineX series) **controls both bluetooth and WLAN**: Tapping the key combination once switches both WLAN and bluetooth off. Tapping it again only activates WLAN. On previous installations (10.10 and 11.04) WLAN and bluetooth control was distinct. Double taps controlled WLAN, single taps bluetooth. Seems like the preferable option to me.* Any way to change the Fn hotkey config?*
[*]**jockey-gtk doesn't recognize dedicated GPU**: Previous installations such as 11.04 automatically recognized my graphics card and provided optional proprietary drivers. At the moment, that doesn't seem to be the case with 12.04.
[/LIST]
**GUI**

[LIST]
[*]**Unity launcher reveal on second screen buggy when in auto-hide mode**: Revealing the launcher took considerably longer on the second screen
[*]**Unity HUD functionality doesn't work with Firefox or Libreoffice**: Can't execute the displayed commands in FF. The HUD doesn't seem to offer any LO commands in the first place.
[*]**Can't access Login screen**: At least in live mode logging off lead to a continuous loop between terminals and an empty GUI
[/LIST]
System setup: Acer TimelineX 3820TG Notebook; CPU: Core i5-450M; GPU: Ati Mobility Radeon HD5650 and integrated Intel unit




I am no expert in reporting bugs or tracing them down to the packages involved. So what's the best way of going about this? What's the right platform for me to post these bugs/problems so that they reach the developers?


Thanks,
Kakitus

---

### Post by manzdagratiano on 2012-03-10
Take a look at:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

This shows you all the ways of reporting bugs... The last resort is to directly report the bug on Launchpad (described on that page).

---

