---
title: "ThreatFire Free: A Good Antivirus?"
date: 2009-01-06
forum: Windows
---

### Post by cardinals_fan on 2009-01-06
I have a long and sordid history with so-called antivirus* applications.  In general, I've been irritated, disturbed, and outraged.  Almost all of the major AV players rely on definitions-based scanning (aka signature-based) to detect and remove intruders.  This is all fine and good **after** your system is infected, but it's useless when it comes to prevention.  And I think the goal should be to prevent the nasties from running, not ceding the system to them without a fight and resigning oneself to removing them.  Basically, these apps download lists of known intruders from their manufacturers and commence a mind-numbing scan of every file on the computer.  Many claim "real-time" protection, but that just means that they scan files as they are created.  There are a few problems with this:
[LIST=1]
[*]Definitions are out of date the moment they are published.  Zero-day assaults have become quite common, and AV makers simply can't keep their software up-to-date against the endless waves of new attackers.

[*]Almost all definitions-based antivirus apps have abysmal performance.  For one thing, they depend on file-by-file scanning to detect threats.  Scanning every file on a modern computer (or even just the new files) takes some serious time and resources.  In addition, those definitions demand constant updating, wasting bandwidth and resources.
[/LIST]

This leads us, at last, to ThreatFire.  Unlike most of its definitions-based cohorts, ThreatFire scans for intruders based on behavioral analysis.  No, it won't replace your psychiatrist, but it will block malware based on known malicious characteristics.  Here are some advantages to this method:

[LIST=1]
[*]ThreatFire stops malware as it attempts to execute.  This is still no replacement for safe browsing (which stops malware before it's downloaded :P), but it sure beats waiting for it to take control.

[*]Behavior-based scanning is inherently real-time.  Only new malware that actually works in completely new ways can slip by - no worries about updated definitions.

[*]ThreatFire is quite light on resources.  This doesn't make it right for truly ancient machines, but it is far lighter than any signature-based AV I've seen.

[*]ThreatFire has sane defaults that seem to work quite well without going overboard.
[/LIST]

To be fair, here are some caveats:

[LIST=1]
[*]ThreatFire can have conflicts with other software.  Some popular registry optimizers, for example, set off some of ThreatFire's behavioral tripwires.

[*]ThreatFire is closed source.  No, I'm not going all Richard Stallman on you, but you're granting control of your system to something you can't audit.  Then again, the same is true for any other AV besides Clam, and is even true of Windows itself.

[*]ThreatFire is designed to work on a clean system.  If you are already contaminated, it won't help you out.

[*]As is true of any AV, ThreatFire can provide a false sense of security.  99% of security lies with you, the user.  More on this below.
[/LIST]
Does it work?  I can't give a definitive answer.  I've never let anything through in six years on XP, and I doubt if I will soon, so ThreatFire is sitting there twiddling its proverbial thumbs.  However, [this reviewer]("http://www.pcmag.com/article2/0,2817,2191336,00.asp") had good luck with it in his tests.

Safe computer use is still the most important method for preventing infection.  Sensible browsing with something other than IE, NoScript or an equivalent, and maybe SiteAdvisor are key to keeping safe.  A firewall helps prevent any real viruses* that slip through one's ISP.  Finally, a limited user account is the cornerstone in any secure system.  However, ThreatFire is a worthy component in any setup.

Interested?  Check out [the site]("http://www.threatfire.com/").  Be sure to grab the free version; the Pro version only adds limited scanning capabilities.

* Technically, most malicious software stopped by these apps are not viruses.  True viruses install without any user knowledge through unpatched security holes.

---

