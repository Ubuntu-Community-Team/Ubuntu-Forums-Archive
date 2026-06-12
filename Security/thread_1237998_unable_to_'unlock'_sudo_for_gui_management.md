---
title: "unable to 'unlock' sudo for gui management"
date: 2009-08-12
forum: Security
---

### Post by grayhatter on 2009-08-12
Tasks requiring 'root' access such as manual network configuration have an 'unlock' button, however when I click on unlock the window that comes up has the options grayed out such as 'select user'. It prompts for a password but the field is grayed out and i can't type anything in or hit submit.

I tried searching but frankly wasn't sure what to search for.  I read the sticky and didn't see anything.

trying to export display:0.0 as root and running the command fails (i guess ubuntu doesn't like taking this approach to sudo?).

I'm basically trying to configure the network and setup WLAN and it's not going very well.

I also get the same grayed out options if I try to grant specific users escalated rights.  (not sure what that application is called).  I think system-backend-tools?

This worked previously, but i think it stopped working after running the automatic system updates (or i screwed something up unknowingly)

---

### Post by cariboo on 2009-08-12
Does sudo work for you? If not, make sure you are in the admin group. Open a terminal and type:

```
groups
```

If somehow you removed yourself from the admin group, restart in recovery mode and at the menu select drop to root prompt, once at the prompt type:

```
gpasswd -a <user> admin
```

once you have added yourself to the admin group, type exit at the prompt, then select resume from the menu.

---

### Post by grayhatter on 2009-08-12
sudo works just fine.

I can also login as root from CMD.

I'll try and get a screen shot tonight...

---

### Post by kerry_s on 2009-08-12
welcome to the wonderful world of policykit. :lolflag:

those programs can not be accessed with root, it's all done through policykit now, so you have to use the normal admin user.
are you running as your normal user?

---

