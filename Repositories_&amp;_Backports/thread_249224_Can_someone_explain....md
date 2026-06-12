---
title: "Can someone explain..."
date: 2006-09-02
forum: Repositories &amp; Backports
---

### Post by The Keeper on 2006-09-02
Why there is no symlink or hardlink called "stable", "current-stable" or something along these lines in [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/) pointing to the latest stable release? The link could be updated a week or two after release of a stable version to give time to fix possible upgrade bugs that had slipped in.

Then instead of "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted" you could use "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) current-stable main restricted" and have it always point to the latest stable release.

This would be pure gold for those who want to set up an ubuntu box for non-sudo users, set up aptitude cron job to keep the system up-to-date and then just forget it.

---

