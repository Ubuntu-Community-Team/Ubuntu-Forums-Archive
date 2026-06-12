---
title: "Frustrating Launchpad Experience"
date: 2020-06-09
forum: The Cafe
---

### Post by JSeymour on 2020-06-09
Don't know where else to post this, so I hope this is the appropriate sub-forum.

Attempted to install an app from a launchpad ppa.  The install errored-out.  Ok: Off to file a bug report.

First surprise: One files bug reports via... **email**?!?!  Ok.  Read up on the formatting requirements, etc., composed the email and off it went.

Not so fast.  Got back an error: "No PGP signature."  What?  Oh, it turns out I have to digitally sign such things.  Ok, install *seahorse*, create a PGP key, get it sent up to Ubuntu's PGP key server. (That, in itself, was an annoying exercise.  Ubuntu's keyserver appears to be a mite... erratic.)  Try again.

Rejected again.  Same deal.  Say what?  Oh, it turns out _Ubuntu's_ launchpad doesn't directly shake hands with _Ubuntu's_ keyserver, so you have to **manually** tell launchpad to import (?) your public key.  Ok, did that, too.

The bug-reporting system **still** wasn't happy.  I surmised that was because I was using the tagged email address in my Ubuntu One credentials but I put my untagged email address in my PGP key.

Ok, fine.  That's all clearly end-user headspace.  Failure to Read The Fine Manual.  That's on me. But send the bug report off for a **another** time, and...

<crickets>

No reject and no email confirming receipt of the bug report. Nothing is showing up under open bugs on the package page.

So, several hours later I send a message off to the packaging team's lead, summarizing what I'd gone through to try to bug-report this problem, asking for guidance/suggestions.

<crickets>

Is this utter lack of response normal, or is something still possibly awry?  And, if something's still awry, how am I to figure it out, getting no feedback whatsoever?

Anybody have any suggestions on how I might proceed, or should I just give up on the package?

---

### Post by wildmanne39 on 2020-06-09
*Thread moved to **The Cafe.**.*

There is not really a good sub-forum for this topic, filing bugs on launchpad is for bugs with ubuntu, ppa's are 3rd party applications and you have to contact the developer of the app, this is information on how to report bugs for ubuntu on launchpad.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by guiverc on 2020-06-10
The most common issue I see with PPAs, is people trying to get software for a release that the PPA (3rd party resource) doesn't support.

Was the PPA you were trying to use still maintained? supported the release you are using?  Did you verify it was from a trusted source (being third party, the security checks are all your responsibility, which includes these tests and more).  Is your release supported, as I'm aware some projects empty PPAs on unsupported (ie. after the release has gone EOL/end-of-life) releases too.  You provided no details, so we cannot look for you.

---

### Post by JSeymour on 2020-06-10
Thanks for the follow-ups, guys!  Sorry about getting it in the wrong place, wildmanne39.

guiverc: Yes to all questions.  The PPA is still maintained, the package I downloaded is for the release I'm using and was updated less than a month ago, it would **appear** the source is trustworthy, and, yes: The OS release I'm using, while EOL'd, is supported.

I didn't mention the package in question because I'm trying to avoid throwing shade on the maintainers of that PPA.  I'll try one more time, this time messaging the dev that uploaded the package, rather than the PPA team lead, then I'll call it quits.  It's a package I'm just playing with.  I don't really **need** it, per se, and I've more than enough other projects with which to keep myself amused :)

---

### Post by CelticWarrior on 2020-06-10
> The OS release I'm using, while EOL'd, is supported.


So this is the problem.
The PPA may still provided content for an old EoL release but all it takes to fail is one single package there that has dependencies in the official repositories. It'll fail because those repositories have been moved to archive. Not the developers' and PPA maintainers' fault, this is entirelly the user's fault for running a release past its expiration date.

Please upgrade to a supported release and be happy.

---

### Post by JSeymour on 2020-06-10
> **CelticWarrior said:**
> So this is the problem.
... this is entirelly the user's fault for running a release past its expiration date.
Is it also the user's fault that the launchpad bug-reporting system isn't providing any feedback at all?  The user's fault that the PPA Team leader does not respond to inquiries?

I understand your point.  I've made the exact same point, myself, on occasion.  But you're nicking me for a point I'm not making and questions I'm not asking.  Fine: If the EOL'd OS release is no longer supported, it's no longer supported.  I can live with that.  I **expect** that.  But when the PPA provides a package for an OS release, I don't think it unreasonable to expect the package to actually install and work.  If it's **not** reasonable to expect it to install and work, then should that package not be withdrawn for that OS release?  That would seem to me the reasonable thing to do.

This ain't my first rodeo, CelticWarrior.  That would be why I'm not **complaining**, but asking questions.

---

### Post by CelticWarrior on 2020-06-10
> (...) when the PPA provides a package for an OS release, I don't think it  unreasonable to expect the package to actually install and work.

Again, if at least one the software's packages has dependencies on other packages from the official repositories, not the PPA itself, but the EoL user has payed support ([ESM - Extended Security Maintenance]("https://ubuntu.com/esm")) and/or manually edited the software sources to point to the now archived versions of the repositories then it's reasonable to expect the PPA package to install and work just like it did during the normal release life cycle. It is unreasonable in any other cases.

> If it's **not** reasonable to expect it to install and work, then should that package not be withdrawn for that OS release?

No, because ESM.
And it's always the maintainers' prerogative to add and remove support for a specific release.

---

### Post by JSeymour on 2020-06-10
Fair enough, CelticWarrior, but my question isn't so much about whether I should have expected it to work.  In fact it wasn't about that at all.  It was about interaction with launchpad's bug-reporting system and package maintainers.

Thanks for your follow-ups.

---

### Post by QIII on 2020-06-10
Please, let's stop the bickering.

> **JSeymour said:**
> But when the PPA provides a package for an OS release, I don't think it unreasonable to expect the package to actually install and work.  If it's **not** reasonable to expect it to install and work, then should that package not be withdrawn for that OS release?  That would seem to me the reasonable thing to do.

None of those expectations are out of line.  However, neither we nor anyone at Canonical can dictate to the maintainer of a PPA or predict what the maintainer will do.  It is, after all, a *Personal* Package Archive.  That places the onus on the *Person* maintaining the archive.

It being a PPA, it is not a reasonable expectation that Canonical should be able to respond to a bug report about the application.  

There is no "fault" here on anyone's part.

And now, since this thread seems to have gotten a bit testy, I'm closing it.  JSeymour, if you take issue with this closure, you are welcome to start a thread in the Resolution Centre.

---

