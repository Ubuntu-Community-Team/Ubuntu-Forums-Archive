---
title: "Firefox cannot start due to AppArmor profile"
date: 2008-10-17
forum: Security
---

### Post by kindloaf on 2008-10-17
I wanted to use AppArmor profile to confine firefox.  But the
firefox failed to start.

I did the following

sudo cp /usr/share/doc/apparmor-profiles/extras/usr.lib.firefox.firefox-bin /etc/apparmor.d/
sudo aa-enforce /usr/bin/firefox
sudo /etc/init.d/apparmor reload

Now firefox cannot be started.  The messages in /var/log/messages
are as follows:

Oct 17 13:51:41 xxxxxx kernel: [13592.992000] audit(1224265901.573:4):  type=1503 operation="file_lock" requested_mask="wk" denied_mask="k" name="/home/xxxx/.mozilla/firefox/pja6n7se.default/.parentlock" pid=7936 profile="/usr/lib/firefox/firefox-bin"
...

From the profile of usr.lib.firefox.firefox-bin, it should have
the following right:
  @{HOME}/.mozilla/firefox/** lrw,

Can anyone explain what's happening?

---

### Post by cariboo on 2008-10-17
I would check the permission on:

> /home/xxxx/.mozilla/firefox/pja6n7se.default/.parentlock

It should be 644

Jim

---

### Post by kindloaf on 2008-10-18
Thanks for the reply.

Yes it's 644:

ls -l /home/xxxx/.mozilla/firefox/pja6n7se.default/.parentlock 
-rw-r--r-- 1 xxxx xxxx 0 2008-10-18 10:58 /home/xxxx/.mozilla/firefox/pja6n7se.default/.parentlock

And there are totally four messages:

Oct 17 13:51:41 Apollo kernel: [13592.992000] audit(1224265901.573:4):  type=1503
operation="file_lock" requested_mask="wk" denied_mask="k" name="/home/hong/.mozilla/firefox/        pja6n7se.default/.parentlock" pid=7936 profile="/usr/lib/firefox/firefox-bin"

Oct 17 13:51:41 Apollo kernel: [13593.004000] audit(1224265901.573:5):  type=1503                   operation="inode_permission" requested_mask="r" denied_mask="r" name="/usr/share/firefox/greprefs/" pid=7936 profile="/usr/lib/firefox/firefox-bin"

Oct 17 13:51:41 Apollo kernel: [13593.004000] audit(1224265901.573:6):  type=1503                   operation="inode_permission" requested_mask="r" denied_mask="r" name="/usr/share/firefox/defaults/  pref/" pid=7936 profile="/usr/lib/firefox/firefox-bin"

Oct 17 13:51:41 Apollo kernel: [13593.008000] audit(1224265901.573:7):  type=1503                   operation="inode_permission" requested_mask="r" denied_mask="r" name="/etc/firefox/pref/" pid=7936  profile="/usr/lib/firefox/firefox-bin"

Oct 17 13:51:41 Apollo kernel: [13593.008000] audit(1224265901.573:8):  type=1503                   operation="inode_permission" requested_mask="r" denied_mask="r" name="/usr/share/firefox/chrome/"   pid=7936 profile="/usr/lib/firefox/firefox-bin"

---

### Post by cariboo on 2008-10-18
I don't suppose you can undo the changes to apparmor, to see if Firefox still works? What are you trying to accomplish? 

Jim

---

### Post by kindloaf on 2008-10-19
I disabled that profile and firefox worked.  I just saw the profile there and wanted to try it.  It's quite weird that firefox can't event start.

---

### Post by phorgan1 on 2009-12-31
> **kindloaf said:**
> 
And there are totally four messages:

Oct 17 13:51:41 Apollo kernel: [13592.992000] audit(1224265901.573:4):  type=1503
operation="file_lock" requested_mask="wk" denied_mask="k" name="/home/hong/.mozilla/firefox/        pja6n7se.default/.parentlock" pid=7936 profile="/usr/lib/firefox/firefox-bin"

You need to give it k permission like this:
  @{HOME}/.mozilla/**/*.sqlite* k,
  @{HOME}/.mozilla/**/.parentlock k,
(N.B. assumes that the HOME variable is already set.  If it doesn't work then you can just give the explicit path to your home directory.)
> 

Oct 17 13:51:41 Apollo kernel: [13593.004000] audit(1224265901.573:5):  type=1503                   operation="inode_permission" requested_mask="r" denied_mask="r" name="/usr/share/firefox/greprefs/" pid=7936 profile="/usr/lib/firefox/firefox-bin"
You need to give it read permission like this:
/usr/share/firefox/greprefs/** r,
> 
Oct 17 13:51:41 Apollo kernel: [13593.004000] audit(1224265901.573:6):  type=1503                   operation="inode_permission" requested_mask="r" denied_mask="r" name="/usr/share/firefox/defaults/  pref/" pid=7936 profile="/usr/lib/firefox/firefox-bin"

add:
/usr/share/firefox/defaults/pref/** r,
> 
Oct 17 13:51:41 Apollo kernel: [13593.008000] audit(1224265901.573:7):  type=1503                   operation="inode_permission" requested_mask="r" denied_mask="r" name="/etc/firefox/pref/" pid=7936  profile="/usr/lib/firefox/firefox-bin"

add:
/etc/firefox/pref/** r,
> 
Oct 17 13:51:41 Apollo kernel: [13593.008000] audit(1224265901.573:8):  type=1503                   operation="inode_permission" requested_mask="r" denied_mask="r" name="/usr/share/firefox/chrome/"   pid=7936 profile="/usr/lib/firefox/firefox-bin"
add:
/usr/share/firefox/chrome/** r,
of course you can get by with less rules, for example:
/usr/share/firefox/** r,
works for anything under /usr/share/firefox
after the changes you need to restart apparmor with for example /etc/init.d/apparmor restart.

---

### Post by bodhi.zazen on 2009-12-31
Starting with Ubuntu 9.10 there is a profile available for firefox.

That alone is enough for me to advise upgrading to Ubuntu 9.10  =)

---

