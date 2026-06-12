---
title: "Crashplan on a headless server"
date: 2018-03-09
forum: Server Platforms
---

### Post by fredfillis on 2018-03-09
[COLOR=#000000]Managed to post this in the wrong place originally (general help), apologies.

Still very much a noob, been running ubuntu server 14.04.5 for a few years on a basic headless box as a media server. I was running Crashplan (Home account) on that box to back up about 50,000 digital images. Successfully survive the transition to a Small Business account. I recently lost my boot disk. I've been progressively reinstalling the apps I need but have run into issues with Crashplan. Does not seem to matter how I try, I just cannot get an installation to "work". Everything installs without error but, with reference to the procedure [/COLOR][here]("https://support.code42.com/CrashPlan/4/Configuring/Use_CrashPlan_on_a_headless_computer")[COLOR=#000000], there is never a [/COLOR][COLOR=#434951].ui_info file created and there is no [/COLOR][COLOR=#434951]/var/lib/crashplan folder.

The last working version on my old machine was 6.6.0 ([/COLOR][COLOR=#000000]Build: 4347). I have tried to install CrashPlanSmb_6.7.0_1512021600670_4503_Linux.tgz and also tried CrashPlanPRO_4.9.0_1436674888490_33_Linux.tgz but result is the same for both. [/COLOR]

[COLOR=#000000]In looking around for a solution, I found this [/COLOR][here]("https://support.code42.com/Release_Notes/CrashPlan_for_Small_Business_version_6.6")[COLOR=#000000]:[/COLOR]

[HTML]Using CrashPlan for Small Business on a headless computer and installing CrashPlan for Small Business on a NAS device remain unsupported. 
Beginning with version 6.6.0, the CrashPlan for Small Business app does not function in either of these configurations. 
See Back up networked storage or NAS devices for additional options.
Makes me wonder if I'm wasting my time.[/HTML]

[COLOR=#000000]Anyone got this to work recently? I have tried the method described by Crashplan and also this one: [/COLOR][http://www.benwagner.net/computing/i...11-forwarding/]("http://www.benwagner.net/computing/installing-crashplan-on-headless-server-x11-forwarding/")

[COLOR=#000000]Any help gratefully accepted, must have spent 8 hours bashing my head against the wall on this so far [/COLOR]:smile:

---

