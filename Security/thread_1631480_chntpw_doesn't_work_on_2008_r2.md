---
title: "chntpw doesn't work on 2008 r2"
date: 2010-11-26
forum: Security
---

### Post by wetlivers on 2010-11-26
I found several instructions on how to use a live CD to reset the local admin password to blank.
 
I download 10.10, installed chntpw, mounted the drive, and used the utility on the SAM dbase.
 
Seems to work everytime and I write the changes and get a return code of 0.
 
Then I reboot and the blank password doesn't work. Tried 3 times.
 
So I noticed that there was an "x" in the box that showed a policy that says you can't have a blank password when you 1st run chntpw. So I tried changing it to something else instead of blank.
 
Still no go.
 
Anyone have any ideas or seen something similar?
 
thanks

---

### Post by wetlivers on 2010-12-02
In addition, I tried the "change password" and then we were unable to log into the system at all, I believe the utility "broke" the SAM dbase.

---

### Post by elsalsa on 2010-12-31
I had the same problem with chntpw on a 10.10 live usb. Everything seemed to work properly, but it didn't actually do anything. I only tried blanking the password; I was hesitant to change it to something else.

I finally got it working by installing an older version of chntpw. Ubuntu Software Center automatically installs 0.99.6-2 (I'm using i386, not AMD) which is listed as unstable by Debian ([http://packages.debian.org/sid/chntpw](http://packages.debian.org/sid/chntpw)). So I uninstalled that version, and downloaded and installed version 0.99.5-0+nmu1 which is listed as Stable:

[http://packages.debian.org/stable/chntpw](http://packages.debian.org/stable/chntpw)

Finally I was able to reset a Windows password to blank. Next I needed to figure out why elevating my test user to Administrator didn't work.

---

### Post by uRock on 2010-12-31
Closed for review.

---

### Post by Elfy on 2010-12-31
Re-opened.

---

