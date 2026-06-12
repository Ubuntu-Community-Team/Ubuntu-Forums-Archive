---
title: "Significant HTTPS Security Issues with Vbulletin Puts UbuntuOne At Risk!"
date: 2020-12-12
forum: Resolution Centre
---

### Post by 64bitguy2 on 2020-12-12
Please take note of my comments at: [https://ubuntuforums.org/showthread.php?t=2449132](https://ubuntuforums.org/showthread.php?t=2449132)

I believe this issue merits immediate attention due to the significant security vulnerabilities that the existence of these holes create for the entire UbuntuOne community.

As a forums administrator since I began writing coding RBBS-PC and with now decades of first hand coding and debugging experience with credits in both phpBB, Vbulletin and every other form of forums software you've ever seen over the past 20+ years as well as 15-years experience coding and administrating SSO, the seriousness of this matter should not be ignored any longer.

Should your Vbulletin administrator wish to see a demonstration of SSO being compromised through a stupid Icon security hole, I can demonstrate exactly how a simple cross script man in the middle attack can lay in wait for the icon to be called, reach into the user session and then capture their SSO data.

Canonical wouldn't be happy.. users sure as hell wouldn't either.

This is easily fixed by looking at all of your Vbulletin templates.  I can tell you right now that "newthread" is fine.

---

