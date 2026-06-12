---
title: "Lucid open for development"
date: 2009-11-03
forum: The Fridge Discussions
---

### Post by TheFridge on 2009-11-03
I&#8217;m happy to report that the Lucid Lynx is now open for uploads.

We do not recommend that users upgrade to Lucid at this time; it is likely to be in very considerable flux until the initial round of merges is complete. As ever, any developers wishing to take the plunge at this early stage should ensure that they are comfortable with recovering from anything up to complete system failure.

Automatic syncs from Debian will begin shortly.  Because Lucid is an LTS, autosyncing will track the Debian testing series for this cycle, rather than Debian unstable as we normally do.

  [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

We expect this more conservative policy for package syncing will enable us to prepare a more stable long-term support release.  The cost of this approach is that not only regressions will be delayed from reaching Lucid - bugfixes uploaded to Debian unstable will be delayed too (packages uploaded to Debian unstable normally don&#8217;t reach Debian testing for at least 10 days).  If you believe a newer package version from unstable is needed for any reason, please don&#8217;t hesitate to request a sync using the normal process:

  [https://wiki.ubuntu.com/SyncRequestProcess](https://wiki.ubuntu.com/SyncRequestProcess)

Likewise, package merges from either testing or unstable are perfectly ok, as needed.  Merge-o-Matic ([https://merges.ubuntu.com/](https://merges.ubuntu.com/)) currently points at Debian unstable; we hope to be able to provide merge data for Debian testing in a week or so, in the meantime please be aware of this fact when preparing any merges.

As usual, the release schedule for Lucid is available at <a href="https://wiki.ubuntu.com/LucidReleaseSchedule"https://wiki.ubuntu.com/LucidReleaseSchedule/a>.  This year, the first milestone will come in mid-December, well after UDS, and the end of automatic Debian package syncs is not planned until February - shortly before feature freeze itself.  Since this cycle&#8217;s schedule includes a significant number of changes compared with respect to past releases, there&#8217;s been a lot of feedback, some of which is still being incorporated.
This may still result in some fine-tuning of the more specific freezes on the timeline; you can expect this to all be finalized by the end of this week.

Originally sent to the [ubuntu-devel-announce mailing list]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-November/000636.html") by Steve Langasek on Tue Nov 3 11:40:22 GMT 2009



[More...](http://fridge.ubuntu.com/node/1934)

---

