---
title: "TN Team VPS"
date: 2009-09-16
forum: Tennessee Team - US
---

### Post by netritious on 2009-09-16
Some if not all of you are aware of the VPS that I am contributing to the team for the ubuntu-us-tn.info web site. ([contrib link]("http://ubuntuforums.org/showpost.php?p=7906989&postcount=6"))

I am currently at a crossroads with the VPS and need some team input.

The server is almost ready using Ubuntu jeOS (minimized Hardy x86). Using a minimal installation of an LTS version appealed to the administrator in me, that is until I got my hands dirty and realized some of the security implications of using an older version of Ubuntu.

Specifically I have concerns about the age of the packages used for hosting a web site. For instance in Hardy repos PHP is at version 5.2.4 (5.2.10 and 5.3 are out) and openssh-server used for shell access and sftp is at 4.7 (5.1 is out and supports chroot'ed sftp logins). Even with hardy-backports enabled the versions thus far have not changed.

So it leaves us with basically three choices using Ubuntu as a web server platform:

1. Stick with jeOS regardless of these issues.
2. Install the latest stable non-LTS version (Jaunty) which in the next month or so would be upgraded to Karmic. (Or not...we don't /have/ to dist-upgrade if we don't want.)
3. Be crazy and install Karmic Alpha. (If the team as a whole thinks it might be worth doing, Karmic /is/ practically out the door.)

Two other facets of deployment that I am uncertain of is the provision of DNS and a complete mail solution (POP/IMAP/SMTP) on the VPS.

Since I can not provide geographically redundant DNS service at this time, and seeing that DNS will indeed consume some of the meager resources available, I recommend using one of the many free DNS hosting services. It really doesn't matter what provider we go with if the majority has a preference, but if not I recommend Sitelutions for free DNS hosting. Another option is to install BIND and be done with it.

Where mail is concerned my instinct is not to bother with it. All of us have our own email addresses already, and a full mail stack is not required to send emails from the server via web applications. Besides it will just consume more precious resources. Again, this is really up to you guys/gals...if the majority is for a full mail stack on the web server then I'm for it to.

So this is where I'm at -- my gut instinct is to start from scratch with Jaunty server (supports minimal install mode which replaces 'jeOS') so that we have the latest enhancements, security patches, etc for our working environment, and to ditch DNS and mail services to make the most of meager resources.

It may be my host servers, but this is the Team's VPS, and as such you have a say. Any suggestions and feedback are welcome.

Thanks, Rich

---

