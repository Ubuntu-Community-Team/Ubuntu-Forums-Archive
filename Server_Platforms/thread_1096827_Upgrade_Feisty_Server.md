---
title: "Upgrade Feisty Server"
date: 2009-03-15
forum: Server Platforms
---

### Post by zhenya on 2009-03-15
I have a file server that is still running Feisty that I'd like to upgrade to a LTS release.  As the Feisty package archives are down, what would be the best way for me to go about doing this without having to do a clean install?

Thanks.

---

### Post by ugm6hr on 2009-03-16
Edit sources.list to reflect changes:
[https://answers.launchpad.net/ubuntu/+question/54520](https://answers.launchpad.net/ubuntu/+question/54520)

Full details / links on Server upgrades Feisty to Gutsy, the Gutsy to Hardy: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by zhenya on 2009-03-16
Hmm.  Thanks for the suggestions.  This looks like a fairly involved process that may or may not work.  That's really a bummer given that the benefit of having my fileserver running Ubuntu is that it stays up forever without me doing anything.  By the time I remembered to get around to updating it, the distribution is EOL and there is no decent mechanism in place to upgrade...

Not sure how I'm going to proceed from here.  It may be that I just leave it alone as it is still functioning fine, and I don't really feel like investing the time to update it right now.

Thanks for the suggestions.

---

### Post by ugm6hr on 2009-03-16
Did you read the link I gave?

All that is required to update to Gutsy is to edit 1 file (sources.list), install update manager (single command), then update (single command).  

To then update to Hardy, just install update manager (single command), then update (single command) again.

If you wait until after EOL for Gutsy, it will genuinely be impossible.  Editing sources.list is only necessary, since you failed to upgrade within the well-documented 18 month support window.

---

### Post by zhenya on 2009-03-16
Ok - thank you.  I had gotten bogged down in a couple of other links within those links that you gave me where people were going to extreme lengths to upgrade and gotten discouraged.  I edited my sources.list, ran the update manager, when it asked me if it could over-write sources.list, I opened a second session and restored my original feisty sources.list, and then the upgrade started.  It looks to have gone ok to Gutsy so far.  I'll move on to Hardy from here.

Thanks for the assistance.  :D

---

### Post by ugm6hr on 2009-03-16
Remember Hardy needs to be upgraded before its EOL in April 2013 too.

---

