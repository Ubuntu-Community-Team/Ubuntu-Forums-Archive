---
title: "Thunderbird 11b2 freezes up"
date: 2012-02-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by prana on 2012-02-22
This is on Xubuntu 12.04 i386.

I can't reproduce this consistently with the latest version of Thunderbird in Precise (11b2) so I am looking for some guidance on how to debug this.

I am using Thunderbird to log into my corporate Exchange server. I use IMAP for emails and the lightning extension and Davmail (davmail.sourceforge.net) to get calendar functionality.

Everything works quite well but occasionally, when switching from one IMAP folder to another, Thunderbird just freeezes up and the arrow pointer changes to an arrow with a spinning circle. I can't interact with Thunderbird after that. My Inbox has about 11000 messages in it if that makes a difference.

I don't remember this happening with Thunderbird 10 so this may be a recent issue.

Thanks.

---

### Post by Harry33 on 2012-02-23
> **prana said:**
> This is on Xubuntu 12.04 i386.

I can't reproduce this consistently with the latest version of Thunderbird in Precise (11b2) so I am looking for some guidance on how to debug this.

I am using Thunderbird to log into my corporate Exchange server. I use IMAP for emails and the lightning extension and Davmail (davmail.sourceforge.net) to get calendar functionality.

Everything works quite well but occasionally, when switching from one IMAP folder to another, Thunderbird just freeezes up and the arrow pointer changes to an arrow with a spinning circle. I can't interact with Thunderbird after that. My Inbox has about 11000 messages in it if that makes a difference.

I don't remember this happening with Thunderbird 10 so this may be a recent issue.

Thanks.

Well you should be aware that something like this may happen, when using a dev version.
They are not meant to be used in your main pc.
Anyway, first try downgrading your Thunderbird 11b2 to the stable released 10.0.2 version.
You can get it either from Mozilla Security Team PPA (Oneiric branch) or from Oneiric official repo.
These work fine in Precise too.
Download them manually (all relevant packages) and install with dpkg.

---

### Post by prana on 2012-02-23
> **Harry33 said:**
> Well you should be aware that something like this may happen, when using a dev version.
They are not meant to be used in your main pc.
Anyway, first try downgrading your Thunderbird 11b2 to the stable released 10.0.2 version.
You can get it either from Mozilla Security Team PPA (Oneiric branch) or from Oneiric official repo.
These work fine in Precise too.
Download them manually (all relevant packages) and install with dpkg.

Oh, I am fully aware of the risks of using a dev version. I just wanted to know if anyone had any pointers on how to debug the issue.

I can live with this issue by just killing TB and restarting it but I wanted to find a more permanent solution.

Thanks.

---

### Post by scottku on 2012-03-19
prana-  Did you find a solution to this problem?  I'm experiencing a similar issue.  It started happening immediately after I upgraded to Thunderbird 11.

---

### Post by Gregory Lee on 2012-03-19
I did have a freeze up of Thunderbird a few weeks ago, just after I first pointed it to my email server.  I'm guessing, but I thought it might have been caused by trying to move a message into an imap folder before Thunderbird had had a chance to figure out which messages went in which folders.  After I rebooted and tried again, this time not being so impatient, the problem never recurred.  With so many messages involved, maybe it takes Thunderbird an especially long time to do whatever initialization it has to do for imap folder organization.

---

### Post by prana on 2012-03-20
> **scottku said:**
> prana-  Did you find a solution to this problem?  I'm experiencing a similar issue.  It started happening immediately after I upgraded to Thunderbird 11.

I tried it once after TB 11 (release) was updated in the repo and there were no symptoms. I haven't tested it thoroughly though. I will do that some more tomorrow.

---

### Post by prana on 2012-03-21
Unfortunately, I was able to reproduce it again this morning.:(

Luckily, TB can be killed and restarted easily but the workaround is not optimal.

---

### Post by scottku on 2012-03-22
I was able to capture a stack trace from the problem and reported it on an existing bug report on the Mozilla bug tracker:
[https://bugzilla.mozilla.org/show_bug.cgi?id=713624](https://bugzilla.mozilla.org/show_bug.cgi?id=713624)

---

### Post by rhaces on 2012-03-30
Ohh Man, this sucks, and now that 11 is Stable I can't go back to 10 (with apt) since it's not in the repos, it goes down to 7 and now my plugins (Lightning) doesn't work.. and I hate having to compile or use an app that is not in the repo...

---

### Post by amd-64 on 2012-03-31
The number of freezes reduced significantly when I disabled play a sound when mail arrives in TB and event alerts in lightning. They were both pointing to some non-existing files.

---

