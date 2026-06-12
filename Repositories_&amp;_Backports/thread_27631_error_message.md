---
title: "error message??"
date: 2005-04-17
forum: Repositories &amp; Backports
---

### Post by lmellen on 2005-04-17
Is this anything to worry about:

root@ubuntu:~ # aptitude update
Reading package lists... Done
Building dependency tree... Error!
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?
root@ubuntu:~ #

                            Thank you -- Larry :)

---

### Post by nautilus on 2005-04-17
Hmm, looks like another program is using the Apt resources at the same time.

Check if apt-get or aptitude or aptigator or aptipotimus are running elsewhere, and finish those off.  Or kill them.

---

### Post by lmellen on 2005-04-17
Curious, i tried apt-get in the morning and it was gone?????

---

