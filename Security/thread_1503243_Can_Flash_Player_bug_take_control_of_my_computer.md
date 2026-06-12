---
title: "Can Flash Player bug take control of my computer?"
date: 2010-06-06
forum: Security
---

### Post by UranUtan on 2010-06-06
Hi,

Reading from this article [New Flash Bug Exploited By Hackers : How to avoid it?]("http://www.hungry-hackers.com/2010/06/new-flash-bug-exploited-by-hackers-how-to-avoid-it.html")

In particular the article said
> A new attack on a Flash bug has surfaced that would give attackers control of a victim’s computer after crashing it, reports PC World. Adobe put out a Security Advisory about this on June 4. It is categorized as a critical issue and all operating systems with Flash are vulnerable including Windows, Linux, and Apple and it is also found in the recent versions of Reader and Acrobat.

Could the attacker really gain control to my machine (Ubuntu 10.04 x64) without me confirming the password?

---

### Post by Rubi1200 on 2010-06-06
I don't have a specific answer for your question, but this sticky is well worth reading:

[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

For more general as well as in-depth security information:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by OpSecShellshock on 2010-06-06
In this case I don't believe the linked article has interpreted Adobe's announcement correctly. It crashes the flash application and the browser that's running it, not the whole computer itself. After the crash it may then run arbitrary code which on some setups could, if it were coded to do so, install a backdoor of some kind. If the session of the browser and Flash content were being run by an administrator, then it could install further malicious software. If it were being run with regular user permissions then there's a slight chance that a follow-up exploit could be run that would elevate the privilege of the payload. Also, this would really only affect people who allow Flash content to load automatically when browsing to a page that contains it. Otherwise you'd have to go out of your way to get exploited.

---

### Post by rookcifer on 2010-06-06
Most browsers and plugins behave exactly the same on all platforms, thus when exploited the exploits will typically effect all OS's.  The question then becomes how well is the OS fortified against remote code execution.  I would definitely feel more secure under a default Ubuntu install compared to a default Windows install, even though both can be locked down pretty well.

---

### Post by BoneKracker on 2010-06-07
Here is the original bulletin from Adobe:

[http://www.adobe.com/support/security/advisories/apsa10-01.html](http://www.adobe.com/support/security/advisories/apsa10-01.html)


Excerpt:

> _Summary_
A critical vulnerability exists in Adobe Flash Player 10.0.45.2 and earlier versions for Windows, Macintosh, Linux and Solaris operating systems, and the authplay.dll component that ships with Adobe Reader and Acrobat 9.x for Windows, Macintosh and UNIX operating systems. This vulnerability (CVE-2010-1297) could cause a crash and potentially allow an attacker to take control of the affected system. There are reports that this vulnerability is being actively exploited in the wild against both Adobe Flash Player, and Adobe Reader and Acrobat. This advisory will be updated once a schedule has been determined for releasing a fix.

_Affected software versions_
Adobe Flash Player 10.0.45.2, 9.0.262, and earlier 10.0.x and 9.0.x versions for Windows, Macintosh, Linux and Solaris
Adobe Reader and Acrobat 9.3.2 and earlier 9.x versions for Windows, Macintosh and UNIX 

Flash has a long history of security vulnerabilities.

---

