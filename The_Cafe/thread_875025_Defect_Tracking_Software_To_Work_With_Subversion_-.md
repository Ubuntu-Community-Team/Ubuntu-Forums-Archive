---
title: "Defect Tracking Software To Work With Subversion - Recommendations"
date: 2008-07-30
forum: The Cafe
---

### Post by therascalking on 2008-07-30
Hello all,

I have been using Ubuntu at home for about 3 weeks now and it is living up to all the hype and seems to handle everything I need to do in daily life.

That being said this thread isn't about Ubuntu but I figured there is a broad range of readers who could possibly help me.

I work an internet marketing/IT shop where my job is the deploying of code to various servers (QA, Staging, Production). We have solid process in place where devs are not granted full access to live. I am like a configuration/deployment manager.

Our basic process is a bug/change/defect is created and assigned to a developer. They do the work, check their files into source control and pin the files to the defect. The workflow status is then changed to reflect where the code must go. ie: "Deploy To QA", "Deploy to Staging", etc. Code is then deployed (by me or someone on my team) to the appropriate environment.

At any given time we can tell EXACTLY where a file (and what version of the file) are in the development process. We do not do "full" builds but rather partial builds. Tip builds are not an option. Some sites we do consist of 50,000+ files and upwards of 20 gigs.

Currently we use StarTeam to manage our source code and defects/bugs. StarTeam does this very well and has a very robust interface.

Our problem is the expense of StarTeam and the learning curve. Many of our developers (both new and old) are quite familiar with Subversion. Having used CVS in the past I am quite comfortable using Subversion.

The issue we are facing is finding a good defect tracking tool that ties in with Subversion.

Requirements:
1. MUST be able to link versions of files directly to an open defect/bug.
2. Deploy/checkout versions of files based on workflow status of a defect/bug.
3. Reporting for Project Managers
4. Robust and supportive of teams of 15+ developers, PMs, DBAs, etc.

I have done some research and haven't found any bug tracking software that meets all these requirements. The big challenge is finding a tool that allows "pinning" of versions of files to a bug.

Trac has been suggested in some meetings we've had but it's lack of ability to pin files to a bug is a problem.

If anyone has any recommendations, questions or needs clarifications on something I said please feel free to ask.

Also, we are not against re-evaluating our process to improve things. This is just the way we have always done things. Haha.

Thanks in advance!

Paul

PS: This post was written while my head is in the fuzz of a bad cold. So if it sounds like incoherent ramblings .. please forgive.

---

