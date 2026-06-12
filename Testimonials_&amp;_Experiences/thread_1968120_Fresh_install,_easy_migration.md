---
title: "Fresh install, easy migration"
date: 2012-04-28
forum: Testimonials &amp; Experiences
---

### Post by ratcheer on 2012-04-28
I tried something a bit different today, and it seems to have worked out wonderfully. I had a 12.04 installation that I had brought along since Beta 1. I had had a bunch of problems here and there and, even though every thing seemed to be working, I just felt like it was basically a mess, internally.

So, I created two new ext4 partitions (for / and /home) and did a fresh install from Thursday's 12.04 release CD. Then I updated and upgraded everything and installed fglrx via Jockey.

My next task was to migrate all my info. I did a backup of /home on my old installation using Deja Dup. When it was backing up, I noticed some very large files (mostly distro iso's) that I do not need on my new installation. So, I deleted those files and ran a Deja Dup incremental backup, wondering if this would avoid copying them to the new system. Then I ran a Deja Dup restore on the new system, checked, and sure enough, it had not migrated them!

But then I got a big surprise. Firefox now had all my extensions installed and configured, and when I log on to websites that require passwords, they recognize me as being already logged in! I am sure things would have come out the same way if I had migrated using tar or some other more common utility, but I am very happy with how Deja Dup handled everything.

On to enjoying my fresh, clean install...

Tim

---

### Post by ratcheer on 2012-04-28
Oh, PS - 

I am planning on doing as much as possible to keep this new installation **free**. I do install fglrx because it makes things so much nicer, and I have heard that other peoples' video cards run cooler when they run it instead of the standard radeon driver that ships with Ubuntu.

However, when the install started, I instructed it not to install 3rd party software. And I have not installed things such as Oracle Java and Adobe Flash. If things do not work, too bad.

Ubuntu is beautiful without a bunch of proprietary license encumbered stuff.

Tim

---

