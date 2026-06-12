---
title: "Firefox security"
date: 2010-10-27
forum: Security
---

### Post by BobJam on 2010-10-27
Just read an article on a [security blog]("http://krebsonsecurity.com/2010/10/nobel-peace-prize-site-serves-firefox-0day/") about a zero day exploit on Firefox that impacts version 3.6.11.  (Now it does say it's specific to Windows XP, so I'm assuming FF on Ubuntu isn't affected).  The article says that Mozilla came out with a patch for this vulnerability.

But that got me to thinking.  If you have the Canonical version downloaded and installed via the Ubuntu repository, does that get updated with security patches?  Or is it just available if you've downloaded and installed via the Mozilla PPA?

---

### Post by ArgusVision on 2010-10-28
I cannot attest to the exact exploit, but Ubuntu releases regular updates that often include firefox.

---

### Post by uRock on 2010-10-28
Moved to Security Discussions

---

### Post by lovinglinux on 2010-10-28
The [report]("http://www.mozilla.org/security/announce/2010/mfsa2010-73.html") indeed says the exploit is specifically targeting Windows XP and there is no information about Linux. Nevertheless [Mozilla is recommending that ALL Firefox users should update with the patch released yesterday]("https://developer.mozilla.org/devnews/index.php/2010/10/27/firefox-3-6-12-and-3-5-15-security-updates-now-available/").

I'm not a security expert and I don't have any additional information on the subject, but seems to me that, since the exploit is targeting XP among Windows versions, is not a very elaborate exploit. I'm guessing that because Vista and Windows 7 have UAC to prevent unauthorized access to administrative privileges. Additionally, the exploit seems to install malware on the machine, which probably runs on Windows only.

Anyways, the patch [is already available in the repositories]("http://packages.ubuntu.com/maverick/firefox"), although it might take a while before being updated on [all mirrors]("https://launchpad.net/ubuntu/+archivemirrors"). If you are worried, you can install [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/"), which is highly recommended, or change your preferred mirror in the Software Sources, to one that is [up-to-date]("https://launchpad.net/ubuntu/+archivemirrors").

To protect your browser from zero-day exploits, you can use [AppArmor]("http://ubuntuforums.org/showthread.php?t=1008906").

---

### Post by BobJam on 2010-10-28
@ lovinglinux,

Thanks very very much.  I did indeed get the update (3.6.12) and also changed to a mirror that was "up to date".

My concern was prompted by a vague memory that I read somewhere that Canonical DOESN'T release patches to Firefox.  Maybe instead that was just that Canonical doesn't release alpha and beta versions.

I was also concerned that Canonical lagged a release 'till they adjusted it for use with Ubuntu and that this effort sometimes took a while.  I think I've noticed that lag a few times in the past.  (Maybe that was because of the mirror I was using).

I didn't have that much of a concern that this particular exploit was dangerous to Ubuntu users because, as I said in my OP and you reiterated and expanded on, this seemed to be a Windows XP issue.  But it did alert me to the general question, and considering your links to "up to date" mirrors, I'm glad I asked it.

In any case, thanks again,  Very kewl.

On the AppArmor thing, I either installed it one time long ago and forgot about it, or 9.10 includes it by default, because I have it.

I checked the status and saw that all my profiles were set to "enforce".  A little confusing since your link posts explained that the default was set to "complain".  Don't remember going into those profiles (and I'm sure I would remember that kind of manipulation) and changing from "complain" to "enforce".  Any guess why it would be that way?

So is this AA a sort of HIPS program (to use Windows-speak).  Don't really have my arms around it, so will have to reread that tutorial some more.

---

### Post by lovinglinux on 2010-10-28
Canonical (usually) doesn't update Firefox with major releases, that bring new features, for example from 3.5 to 3.6, but it updates with security patches and other minor versions patches, like from 3.6.11 to 3.6.12. However, due to recent changes in Mozilla update policy, Canonical has updated all Firefox 3.0 to 3.6, because 3.0 reached end-of-life and is no longer supported by Mozilla.

---

### Post by cariboo on 2010-10-28
You can always check the [Ubuntu Security Notices]("http://www.ubuntu.com/usn") page to see if an update is available.

---

### Post by d3v1150m471c on 2010-10-28
got a firefox update less than an hour ago.

---

