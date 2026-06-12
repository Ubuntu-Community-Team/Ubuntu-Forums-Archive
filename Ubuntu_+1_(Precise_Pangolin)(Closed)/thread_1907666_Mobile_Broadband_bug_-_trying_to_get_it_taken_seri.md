---
title: "Mobile Broadband bug - trying to get it taken seriously"
date: 2012-01-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by fabricator4 on 2012-01-11
If anyone is using Mobile (3G) Broadband on their netbooks etc, There's what I consider to be a serious bug in that everytime you boot or resume the Mobile Broadband has to be re-enabled.  This is made worse with a related bug that cases Mobile Broadband to become disabled if you lose signal for any reason.

Details of my orginal Launchpad bug report are here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/880084](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/880084)

Initially it seemed to be taken seriously but then got marked as "incomplete" which means the bug will expire if it doesn't get any further input.  I don't know why it would be considered "incomplete" but I decided to go upstream and report it on Gnome Bugzilla:
[https://bugzilla.gnome.org/show_bug.cgi?id=667488](https://bugzilla.gnome.org/show_bug.cgi?id=667488)

My understanding is that if it can be confirmed in the bugzilla report then the Launchpad report will also progress in classificaton and priority.

If you are suffering from this bug please consider adding a confirmation to the bugzilla report, and any other comments you would care to make.

I note that this has only been a problen since 11.04.  10.04 and 10.10 worked perfectly in that once you enable Mobile Broadband then it stays enabled until you choose to change it.  This problem is a deal breaker for my netbook on 11.04 and 11.10 since it seriously impacts the usability of the machine when actively mobile.

Thoughts and comments appreciated.

Chris

---

### Post by TDK800 on 2012-01-12
Is it Gnome only or Unity also?

---

### Post by fabricator4 on 2012-01-13
> **TDK800 said:**
> Is it Gnome only or Unity also?

It's anything using Netork Manager.  Primarily I've been using 11.10 and 12.04 (both Unity) for testing, but I've also tried Lubuntu 11.10 with the same results.  The problem first showed up in 11.04 as far as I know, and I had been hoping that it was just a temporary problem that would be fixed.

I never put 10.10 on the netbook (EeePC 900SD) so I don't know if the problem was in that release: it would depend on when the change from NetworkManager 0.8.x to 0.9.x was actually made.
(Edit)  Actually I do remember trying 10.10 on the Netbook, but this bug was not a problem.

I think there's very few people using netbooks with built-in 3G otherwise there'd be more people trying to get this fixed.

Chris

---

