---
title: "Security Advisory for Adobe Flash Player, Adobe Reader and Acrobat"
date: 2010-10-29
forum: The Cafe
---

### Post by dinamic1 on 2010-10-29
[http://www.adobe.com/support/security/advisories/apsa10-05.html](http://www.adobe.com/support/security/advisories/apsa10-05.html)

A [critical]("http://www.adobe.com/support/security/severity_ratings.html")  vulnerability exists in Adobe Flash Player 10.1.85.3 and earlier  versions for Windows, Macintosh, Linux and Solaris operating systems;  Adobe Flash Player 10.1.95.2 and earlier versions for Android; and the  authplay.dll component that ships with Adobe Reader 9.4 and earlier 9.x  versions for Windows, Macintosh and UNIX operating systems, and Adobe  Acrobat 9.4 and earlier 9.x versions for Windows and Macintosh operating  systems.

This vulnerability (CVE-2010-3654) could cause a crash and potentially  allow an attacker to take control of the affected system. There are  reports that this vulnerability is being actively exploited in the wild  against Adobe Reader and Acrobat 9.x. Adobe is not currently aware of  attacks targeting Adobe Flash Player.

 **[COLOR=Red]work around[/COLOR]**, Adobe currently recommends that users delete or rename the vulnerable file, which is authplay.dll in Windows, AuthPlayLib.bundle on Macs and libauthplay.so.0.0.0  on Unix-based systems. The workaround will cause Reader to crash when a  PDF file attempts to render Flash content, but it will also prevent  arbitrary code from being injected.

---

### Post by ubunterooster on 2010-10-29
On a friend's PC, Adobe Reader keeps freezing the PC. A cold shutdown is required. I wonder if this is related...

---

