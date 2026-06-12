---
title: "How to get a patch accepted when there's no maintainer?"
date: 2020-08-27
forum: Ubuntu, Linux and OS Chat
---

### Post by marginallosses on 2020-08-27
Hello, my apologies if this is considered off-topic. Please feel free to move this thread to a more appropriate forum.

There is a package which Ubuntu includes from Debian. There is no Ubuntu-specific maintainer. In Launchpad, the maintainer listed is just the Debian maintainer, and it's clear that this person does not have or use a Launchpad account.

In this package there is a program which behaves in a way that is not helpful to users. When I searched the Debian bug tracker I found a report, which included a patch to improve the behavior, but the patch was rejected and the bug closed with WONTFIX because the maintainer does not want the program to handle documents which do not perfectly comply with the relevant standards. I understand their reasoning, but imagine trying to build a web browser that people would want to use, but refusing to handle malformed HTML in a sensible way. Nearly every page on the web would be broken and no one would want to use your browser. I believe this is a similar situation with this package.

I am hoping that the people maintaining Ubuntu are more interested in usability than ideological purity and would consider applying the patch in question if it can be demonstrated that a substantial number of vendors are producing non-compliant documents.

Since the package has no Ubuntu maintainer, where should I look for people who might have the knowledge and interest in getting this patch included in future releases of Ubuntu? (It's related to graphics files.)

Thanks

---

### Post by QIII on 2020-08-27
Moved to **Ubuntu, Linux and OS Chat** as it is not a request for Ubuntu-specific technical help.

---

### Post by TheFu on 2020-08-27
Contact the debian maintainer directly. Offer him/her a "pull request" URL, probably from gitlab would be preferred.

Since the maintainer isn't likely to accept that "pull request", the other option is for you to fork the code, patch it, rename the resulting binary - perhaps a _program-xyz_ name which denotes the file type it claims to fix.

The fix for malformed HTML is to spew errors and refuse to load it until the team/person who created that HTML fixes it. Anything else is "enabling" their bad form, fractures the web, and counter productive. For a long time, I.E. did this. Shame on Microsoft.  Google has been doing something similar with Chrome. [https://www.theregister.com/2020/08/27/brave_webbundles_google/](https://www.theregister.com/2020/08/27/brave_webbundles_google/) for example.

I feel the same way about anything that isn't working through a standards committee, and really don't care if MSFT, Apple, or Google are pushing it.  I want standards-based solutions. If the file format produces doesn't meet standards, those companies need to fix it, not any tools that follow the standards.

We've seen this extend, embrace, then kill technique deployed. We need to specifically NEVER support bad behavior.

---

### Post by grahammechanical on 2020-08-29
If this Debian package should trigger some kind of a crash then Ubuntu will usually offer to send a bug report. I am sure that the Ubuntu developers will pass the bug report upstream to the Debian maintainer to fix. That is the first reason why this package does not need a Ubuntu maintainer.

A second reason would be the refusal of the Debian maintainer to accept any patches (improvements) to his code. If the developer of a program or application is happy with the results of his/her work and does not want suggestions on how to improve the program, then there is not much a Ubuntu developer can do about it.

Forking the code would just be the beginning. The new and improved program would need to be maintained and updated to co-exist with the upgraded code on every new version of Ubuntu. May be the Debian maintainer of this program is happy to do this for new versions of Debian but not happy to do much more than that.

Perfectly good programs often get left behind because of the habit of Life and Death interfering with human activities.

Regards

---

### Post by TheFu on 2020-08-29
At DebConf this week, saw a presentation about package maintenance and other topics for Debian packages.  The title was Virtualizing the Whole Internet (or something close), if you'd like to seek it out.  The presentation jumped topics, but they were all related in the end.

---

