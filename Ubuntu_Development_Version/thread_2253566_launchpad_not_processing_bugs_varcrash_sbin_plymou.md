---
title: "launchpad not processing bugs: /var/crash/_sbin_plymouthd.0.crash"
date: 2014-11-20
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2014-11-20
Internal error reported, I select report problem, then launchpad never opens nor registers a bug

ls -l /var/crash
-rw-r----- 1 root     whoopsie   920414 Nov 20 16:31 _sbin_plymouthd.0.crash
-rw-r--r-- 1 root     whoopsie        0 Nov 20 16:31 _sbin_plymouthd.0.upload
-rw------- 1 whoopsie whoopsie        0 Nov 20 16:31 _sbin_plymouthd.0.uploaded

I search on launchpad bugs for
 _sbin_plymouthd.0.crash
and there's nothing there listed recently.

Next I do
sudo ubuntu-bug _sbin_plymouthd.0.crash
Drop down window, I select to report the error, nothing happens.

I do a search in launchpad bugs, nothing there.

Now from the above, something gets uploaded - where? 

Yesterday I got
_usr_lib_chromium-browser_chromium-browser.1000.crash
no bug is ever recorded as far as I can tell.

?

Am I doing something wrong or has launchpad figured out a way to reduce bugs reported, at least from me?

Thanks for any ideas.

DISTRIB_DESCRIPTION="Ubuntu Vivid Vervet (development branch)"
Linux Lenovo2 3.16.0-24-generic #32-Ubuntu SMP Tue Oct 28 13:07:32 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by mc4man on 2014-11-20
Crashers to launchpad reports is probably still disabled in apport. It is disabled prior to release and not reenabled for some period of time during the next dev cycle.
So right now apport crashers are likely still being uploaded to a db.
As far as that crash, probably the same one that has been happening for quite some time, hasn't been fixed, most likely will never  be fixed. 
(- may go away down the road but not because it was 'fixed' - 
likely to be this one
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/927636](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/927636)

---

