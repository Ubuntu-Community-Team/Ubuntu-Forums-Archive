---
title: "What happened to arm64 daily builds of Lunar?"
date: 2023-01-23
forum: Ubuntu Development Version
---

### Post by perockwell on 2023-01-23
I've been testing out prior Lunar arm64 daily builds on VMware Fusion 13 on Apple Silicon. I'm finding that arm64 daily builds have disappeared - they are no longer available, although the landing page for cdimage.ubuntu.com/daily-live/current has a dead link for the arm64 ISO.

Is there some issue why arm64 dailies are no longer available?

---

### Post by astermask on 2023-01-24
I join the request too! What happened to the file: lunar-desktop-arm64.iso ?

---

### Post by guiverc on 2023-01-24
A +1 Maintenance report on 23-Jan-2023 mentioned only
> 
[COLOR=#000000][FONT=arial]r-cran-rpact[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]============[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]While looking at r-cran-* packages, I found r-cran-rpact's[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]autopkgtests were being Killed on arm64 and ppc64el.  I triggered the[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]tests again on amd64 and s390x and found whatever had pushed arm64 and[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]ppc64el over the edge was now affecting them too.  I added[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]r-cran-rpact to 'big_packages', triggered the tests again, and they[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]passed.[/FONT][/COLOR]

but I don't support/use ARM64 so take little notice sorry.   (*that was the last ARM64 reference in my inbox*)

---

### Post by corradoventu on 2023-01-26
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/2003967](https://bugs.launchpad.net/ubuntu-cdimage/+bug/2003967)

---

### Post by perockwell on 2023-01-30
I'm a little concerned after reading the launchpad discussion that someone thinks that 'arm64'/ARM v8 architectures are a "legacy" platform....

---

### Post by astermask on 2023-01-30
> **perockwell said:**
> I'm a little concerned after reading the launchpad discussion that someone thinks that 'arm64'/ARM v8 architectures are a "legacy" platform....
Absurd! Where is this "discussion"?

---

### Post by deadflowr on 2023-01-31
Not sure discussion is the right word, it's comment in the bug report that explains it well enough; even I understand it.

Basically, there was a commit that changed the builds for the new desktop installer images to only build amd64.
arm64 was suppose to be added to the legacy desktop installer image builds.

Somehow they dropped the ball and it was never added to the legacy installer builds. (For whatever reason.)
Which is why the bug has been assigned to the person who made the commit, so they can fix it and hopefully add arm64 to the proper builds.

Has nothing to do with arm64 being considered a legacy platform.

---

### Post by perockwell on 2023-01-31
Apologies. "discussion" was indeed the wrong word that I used. I'm fairly new here, so again I apologize for not fully understanding the terminology used by Ubuntu.
My experiences in the industry have influenced my understanding of the term "legacy", which may be different from the meaning here.

---

### Post by perockwell on 2023-02-01
The latest comments in the bug report in launchpad are explaining the situation. 
From what I'm reading there is work that the Desktop Team has completed for the new flutter installer for x86_64, but has not been done yet for arm64. "Legacy" in this case refers to the legacy installer. 

My interpretation is that the flutter installer work not being completed for arm64 is holding up the creation of new dailies for the platform. Is my understanding correct?

---

### Post by deadflowr on 2023-02-01
> My interpretation is that the flutter installer work not being completed for arm64 is holding up the creation of new dailies for the platform. Is my understanding correct?

I think it's part that and part they were suppose to add arm64 to the legacy builds but didn't.
So if they can add those to legacy, which I assume will be quicker than porting the new installer, 
then I think they should get some dailies for legacy at least.

But that's just guessing, who knows what they'll do.

---

