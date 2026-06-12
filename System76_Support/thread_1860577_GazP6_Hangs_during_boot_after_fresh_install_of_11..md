---
title: "GazP6 Hangs during boot after fresh install of 11.10"
date: 2011-10-14
forum: System76 Support
---

### Post by chriscross93 on 2011-10-14
Hello,

After performing a fresh install of 11.10, my GazP6 fails to boot up.  The only workaround I have found is booting into recovery mode and then selecting resume normal boot, which seems counter-intuitive - but works like a charm.

Any ideas are appreciated.

---

### Post by senortroll on 2011-10-15
When it hangs are you able to switch to a new virtual console?  I think I'm seeing the same behavior on my gazp6.  I can log in on a vc, then run 'sudo /etc/init.d/lightdm restart', and then I get the login screen.

---

### Post by chriscross93 on 2011-10-15
Yes I can.

What is really strange is that now it boots just fine.  I left it to work on something else for an hour, and now it boots fine.  I just restarted successfully three times to help confirm.

Strange...

Still having issues with twinview, but at least now I have a working computer.

EDIT: Spoke too soon - same issue, same workaround.

---

