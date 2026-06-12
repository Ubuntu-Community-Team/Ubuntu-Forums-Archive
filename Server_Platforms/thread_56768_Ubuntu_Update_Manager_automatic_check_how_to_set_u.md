---
title: "Ubuntu Update Manager automatic check how to set up?"
date: 2005-08-14
forum: Server Platforms
---

### Post by bkasterm on 2005-08-14
I am looking for an option that makes Ubuntu Update Manager (UUM) automatically check for updates, say every day.

Currently UUM displays an information icon which shows the new updates when clicked only after I run Synaptic Package Manager --- which checks if my package listings are up to date, and updates them if not.  So what I am looking for is a setting that automatically checks, and if needed updates, my package listings.

Neither looking through these forums, not using google gave me the answer.  However since all my Linux experience is rather old (this is the first install of Linux I have had in five years) I might not be searching for the right things.

Off course direct answers to my question are very much appreciated, but so are less direct ones that will give me a good method for finding the answer and learning more about the package management at the same time.

Best,
Bart

---

### Post by 23meg on 2005-08-14
this must be it: right click the update manager icon, choose "preferences", then "settings". in the dialog that comes up, check the "automatically check for software updates" checkbox and choose an interval.

---

### Post by bkasterm on 2005-08-15
I have just figured out the problem (but not yet the solution):

See thread at:
[http://ubuntuforums.org/archive/index.php/t-5365.html](http://ubuntuforums.org/archive/index.php/t-5365.html)
If jdong there is right, then with the option from the previous post (which I had set) it all depends on a nightly cron job.  My laptop is not usually on all the time, so this nightly cron job will not run most of the time.

So the problem is now reduced to:
How do I make sure all cron jobs get run regularly without having my laptop on all the time?  I'll do some googling on this, suggestions where to look would be welcome.  (note in the discussion quoted above this is not resolved).

Assumption:
I don't know if this is always the case, but this does depend on update-notifier running.  It did at the time I checked, but as I am not sure how/when it gets started yet, I can't be sure it is always running.

Best,
Bart

---

### Post by steelsnake on 2005-08-30
I just stumbled across your post since I was wondering the same thing :)

Anyway, the way you can get cron to still execute the task once a day is thus (untested version but should work):

#!/bin/bash
if ! test -a /tmp/ubuntu-update-done.`date +"%j"` ; then
  rm /tmp/ubuntu-update-done.*
  <run whatever updates/programs you'd like run once a day>
  touch /root/ubuntu-update-done.`date +"%j"`
fi

If the updater gives you any error codes you can of course make that little script as complicated as you'd like. I'd also like to point out that it's not entirely secure - on a multiuser system it would conceivably possible for any user to overwrite arbitrary files. On a single user system it's not an issue. To make it secure put the ubuntu-update-done file in a root-only directory.

---

