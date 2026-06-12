---
title: "apparmor/selinux and SUID binaries"
date: 2008-03-17
forum: Security Discussions
---

### Post by bluescreen303 on 2008-03-17
Hello,

Today I was looking into apparmor profiles.
I found that the /bin/ping profile does include the net_raw capability.

Why does it still need to be SUID ROOT?

Is apparmor only able to reduce capabilities?
Or will it be able to give MORE capabilities to a certain process as well?

The way it seems to work now is that SUID ROOT gives ping the needed capability(and a lot more), and apparmor locks down everything which isn't needed.

I read that filesystem capabilities will be included in 2.6.24 which is in hardy.
This will allow /bin/ping to be 'normal' (not suid root), since it can allow the net_raw capability on the file itself.

To me it seems that having 2 ways to (dis)allow certain capabilities is kind of strange. Of course choice is good, but having to use 2 systems that partially complement/overlap each other feels not good.

Is this the way it's supposed to work?
Using the filesystem to allow extra capabilities, and then use apparmor to lock it down again?

To take it to extremes, all binaries can be installed SUID ROOT, so apparmor can be used to set ALL permissions. This way there is one central place to manage everything.
Of course I feel this is a bad idea and I'm not proposing it in any way, but this would at least centralize all capability-management for now.

Of course I know apparmor is far more fine-grained with respect to what it can (dis)allow compared to fs-perms, so I would definitely want to use that.

Any chance apparmor can ADD capabilities to processes started without special permissions(suid root, or fs-perms)?

How about SELinux? I believe SELinux can both ADD and REMOVE capabilities.

Thanks for any information,
Mathijs

---

