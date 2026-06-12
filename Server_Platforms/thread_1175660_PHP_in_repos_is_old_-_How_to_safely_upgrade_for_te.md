---
title: "PHP in repos is old - How to safely upgrade for testing?"
date: 2009-06-01
forum: Server Platforms
---

### Post by Jesdisciple on 2009-06-01
I need to submit a PHP bug, but they don't accept reports from v<5.2.9; the repos give 5.2.6.  So I guess I have to install it from source, but first I should remove the old one.  Should I just remove the php5 package and then install the source?

Alternatively, would I be wiser to install a new server just for reporting bugs, and leave my development server updated by repo?

Thanks.

---

### Post by cariboo on 2009-06-01
You could create a bug report on [Launchpad]("http://bugs.launchpad.net"). 

The way Ubuntu works, is the version that is in the debian repos at the time of the package freeze is the only package available for that particular version. If you are using an LTS version, it is supported for 5 years. Even a regular versions is supported for 18 months, so reporting bugs in Launchpad is the proper way to do things.

---

### Post by Jesdisciple on 2009-06-02
Alright, thanks.

---

