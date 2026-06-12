---
title: "Why can't we have the manual we need?"
date: 2013-09-28
forum: Ubuntu, Linux and OS Chat
---

### Post by JP_Rockagetty_III on 2013-09-28
Forgive the following rant.

I've been running Linux since July 1998.  At that time, I thought "half the stuff you need to know was never written down".  And I was right.  The problem is I am STILL right.  If anything, the problem has gotten worse in recent years.

I condensed this down from an old repair manual for a car:

"These models feature four coil suspension (McPherson Strut design) and front wheel drive.  They feature transversely-mounted 4 cylinder or V6 engines, with carburetors or fuel injection, depending on model.  The engine drives the front wheels through a choice of either a 4-speed manual or a 3 or 4-speed automatic transaxle by way of unequal length driveaxles.  The brakes are disc brakes at all four wheels."

Can anybody produce a wiki like that for ubuntu?  It might read like this:

Ubuntu provides an initialization routine at /etc/rc/*, which loads daemons, initializes hardware, sets certain system parameters, loads password databases, and finally the GUI, discussed in the "general" section of this manual.  There is a choice of either KDE 4.x or Gnome X.Y, which is set in the file /etc/x86/foorc.  KDE and Gnome are covered in separate chapters.  Separate root and user logins are not used as they are in other distros -- see the "users and permissions" chapter for information on "sudo".  And finally the "apt-get" chapter will describe the mechanism for receiving patches and updates.  Log files are kept in /var/log/* and can be viewed with any text editor or viewer.

Perhaps server stuff like apache, or MySQL, or languages like python or ruby would be too advanced for these guides.  And you wouldn't need a chapter on Office programs either.  But a good primer on how the basic stuff ties together (kernel, init, users and permissions, mounting, log files) would help us learn why things don't work.

Can anybody write such a guide?

(Typing rpm -qpi (or is it -qpl?) doesn't help you understand the way the basic bootup, kernel and init processes work [for RPM-based distros]. It shows a few rc files though.  I assume apt-get, dpkg or other installer has the ability to list files in packages the same way rpm does, and thus give limited help.)

Seriously, can anybody write such a manual?  It would help immensely !

---

### Post by Gyokuro on 2013-09-28
[http://ubuntu-manual.org/](http://ubuntu-manual.org/) could be a  start but kernel, init system are only interesting for advanced users, developers and administrators - average users do not care about this topic as long everything works. Every distribution is different and you have only to compare rpm based distributions and you will find a lot of different tools which get used - users should learn basic commands of Linux/Unix systems and they can work with most systems and not to be shy/lazy to use "your favorite search engine" can be helpful too.

---

### Post by oldos2er on 2013-09-28
There's already a help page on sudo [here]("https://help.ubuntu.com/community/RootSudo"). For APT I'd start with the [Debian wiki]("https://wiki.debian.org/Apt").

If I'm not mistaken (and I could be) Ubuntu still uses a mix of [Upstart]("http://upstart.ubuntu.com/") and SystemV init stuff.

In short the information you want exists, but it's spread all over the 'net. Collating it all would not be a small task.

---

### Post by buzzingrobot on 2013-09-29
Writing good documentation, including manuals, is not a widely distributed talent.  The author needs to combine superior technical knowledge and skills with superior writing skills, and wrap both of those in superior teaching skills.  

The state of Linux documentation reflects the scarcity of such people.  Windows and OS X are no different.

Publishers have released, and still release, books on Ubuntu and other distributions. The pace of development and change in Linux quickly rather quickly renders them obsolete.

Finally, the Linux approach to building an OS platform -- many individuals working more or less autonomously on some small bit -- does not transfer to the world of authorship. If you want something more than a spotty hodge-podge collection of howto's written mostly by people who do not know how to write, explain, or teach (e.g., man pages) you need a single author and a good editor willing to devote month's of fulltime effort to the task, and then find a way to stay on top of all the revisions that Linux churn will generate.

---

### Post by 1clue on 2013-09-29
Gyokuro and buzzingrobot are right.  There is a combination of lack of interest by the average user and the lack of truly gifted documenters.  To that I would add that by the time somebody documents it in that sort of detail, something will surely have changed.

The best documenters need to focus on where the need is greatest.  As the user gets more skilled they can find out more by looking at the system itself and asking questions from there.

When I got curious about the boot process (right about 1998 or 1999) I typed **man boot** and then started from there.  IMO that's just about the perfect man page for the boot process.  It tells you where to look, but since each distro is a bit different it can't be too detailed or it will be inaccurate.  Fortunately on most distros all the files are text files and you can use your favorite editor to go spelunking through your boot process.

---

### Post by 1clue on 2013-09-29
As far as that goes, maybe if you feel there's a lack of good documentation you might consider writing man pages.  Man pages are better IMO because they help all with online (as in on-the-computer online) documentation, distributions, and they're available online too.

---

### Post by Buntu Bunny on 2013-09-29
> **buzzingrobot said:**
> Writing good documentation, including manuals, is not a widely distributed talent.  The author needs to combine superior technical knowledge and skills with superior writing skills, and wrap both of those in superior teaching skills.  

Exactly! And since most of those needing the documentation are at some beginner level, the author has to be able to put the cookies on the bottom shelf, so to speak, and write in terms and illustrations a beginner can understand. Not so easy for a technical subject. 

I keep a my own list of links, picking up a bit here and a bit there, all to help me find answers when I have questions.

---

### Post by deadflowr on 2013-09-29
> **JP_Rockagetty_III said:**
> 
Seriously, can anybody write such a manual?  It would help immensely !

You can.

Get involved if something bothers you.

---

### Post by philinux on 2013-09-30
One of our ex admins has written one.

[http://www.amazon.co.uk/Ubuntu-Unleashed-2013-Covering-12-10/dp/0672336243/ref=la_B003W60CN4_1_1?s=books&ie=UTF8&qid=1380556407&sr=1-1](http://www.amazon.co.uk/Ubuntu-Unleashed-2013-Covering-12-10/dp/0672336243/ref=la_B003W60CN4_1_1?s=books&ie=UTF8&qid=1380556407&sr=1-1)

---

### Post by BluegrassHero on 2013-09-30
Along those lines, it would be nice if each man page would include a few legitimate examples of the command.  Many list the flags but never show how to compose the entire command sensibly.

---

