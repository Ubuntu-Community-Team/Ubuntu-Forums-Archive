---
title: "Is safe surfing possible?"
date: 2011-08-30
forum: Security
---

### Post by steve11911 on 2011-08-30
[Firefox has been my browser of choice for security reasons until this recent Slashdot post has forced me to reconsider:]("http://news.slashdot.org/story/11/08/29/1454224/Updated-Mozilla-Community-Contributor-Departs-Over-Bug-Handling")

[http://news.slashdot.org/story/11/08/29/1454224/Updated-Mozilla-Community-Contributor-Departs-Over-Bug-Handling](http://news.slashdot.org/story/11/08/29/1454224/Updated-Mozilla-Community-Contributor-Departs-Over-Bug-Handling)

What is the safest way to access Internet content?

---

### Post by Thewhistlingwind on 2011-08-30
Noscript

Add some more similar add-ons and you should be good.

If your still feeling paranoid, learn to write apparmor rules and write a firefox profile.

Or just install the pre-made one from repos.

---

### Post by Dragonbite on 2011-08-30
The truly paranoid, doesn't use the Internet.

also known as there is no such thing as safe surfing.

---

### Post by bodhi.zazen on 2011-08-30
Firefox is know to have tons of vulnerabilities.

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

I suggest either apparmor or a selinux sandbox.

---

### Post by tubezninja on 2011-08-31
The way to be safe: don't rely solely on your web browser to catch vulnerabilities.

Be vigilant.  Be wary of visiting unfamiliar sites and downloading unknown software.

There are free virus scanners such as ClamAV.  Use them.

And regardless of how you feel about security through obscurity, using Linux DOES help.  The fact remains that the biggest fish in desktop mindshare remains windows, and that is where the most numerous threats are.


One thing to note: the article doesn't make clear what percentage of Firefox's current bug backlog are security issues, as opposed to minor glitches and usability problems.

---

### Post by Rob_H on 2011-09-03
You can boot from a live CD to do your "high-risk" browsing or a virtual machine (e.g. under VirtualBox) that you revert back to a known-good snapshot at the end of each session.

But as others have said, browsing from Linux is inherently safer, mainly because it is rarely targeted by malware authors.

---

### Post by 2F4U on 2011-09-03
A friend of mine uses a Knoppix liveCD to do his homebanking stuff. This way, nothing gets stored on the machine and every potential changes in the live environment disappear after booting.

---

### Post by tubbygweilo on 2011-09-03
Browsing via a guest session may be safe enough for safe browsing as it uses the latest Ubuntu code and is flushed away when the session ends.

---

