---
title: "Permissions of /dev/null changed?"
date: 2009-06-21
forum: Server Platforms
---

### Post by Kareeser on 2009-06-21
Just a quick question.

I noticed today that for some reason, I couldn't scp any files to my server. I logged in and was instantly inundated with about a hundred "-bash: /dev/null: Permission denied" spamming the screen. Weird.

Googling for awhile brought up the fact that my /dev/null permissions may have gone awry, and lo and behold, when checked, the permissions were c---------, when they should be crw-rw-rw-.

Weird! Can anyone explain what happened here, and why?

What's even weirder is that my server has also been queuing up mail to be delivered, and dropping them after 5 days (as instructed), because it times out for some reason. Resetting the /dev/null permissions and restarting the sendmail process worked fine, and the mail went through, and analysing the logs, this has been going on longer than the logs run! (Jeez... I should be more observant).

I didn't notice it before because I was still getting mail in my local mailbox, so it seems as though it was dropping mail selectively, delivering some, but not others. Ergh!...

---

### Post by cariboo on 2009-06-22
I use logwatch, which sends me a digest of log changes daily. Logwatch is in the repositories.

---

