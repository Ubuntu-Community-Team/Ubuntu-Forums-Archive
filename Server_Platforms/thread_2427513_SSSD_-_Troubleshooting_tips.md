---
title: "SSSD - Troubleshooting tips"
date: 2019-09-23
forum: Server Platforms
---

### Post by steviehyperb on 2019-09-23
Hi everybody,

Anyone got any advice on troubleshooting SSSD?

I have an active directory environment and want to use SSSD as the primary means for Ubuntu to authenticate users against it. Everything seems to be going well apart from an annoying issues. So if I SSH onto the machine 99% of the time the first login will fail (I spent a few days thinking it was my typing) - then the next login will work and subsequent ones after - till the machine is restarted. Then the process starts again. Or sometimes it takes a few goes to get in.

From experience what are the most sensible places to start looking? Not sure if I have been looking at the right logs but they are not telling me much, perhaps there is a de-bugging level I need to enable?

I have been using WinBind without an issues and just though I would have a look at moving to SSSD, as it seems to be less config hungry.

Any tips on how to troubleshoot this would be great, just want to know where to look and if anyone has found any gotach's?

Many Thanks
Stephen

---

### Post by TheFu on 2019-09-23
I don't know anything about sssd (no AD here), but I have seem similar with LDAP configured in PAM.  I never saw it with ssh, but we don't use password for ssh access. Passwords aren't allowed. Users must use ssh-keys.

If you use ssh-keys, this specific issue won't happen.  It is possible to place keys into LDAP, but I've not do it myself.

I don't know why it happened, but I always *assumed* that the first request for credentials from LDAP is what did the query and cached those credentials, until either the timeout or a mismatched forces a refresh.  [https://docs.pagure.org/SSSD.sssd/design_pages/cached_authentication.html](https://docs.pagure.org/SSSD.sssd/design_pages/cached_authentication.html) is the request with a link to the tracking as it was added to sssd code.

As for troubleshooting, there are logs on the Linux-side, definitely.  Most Linux processes have a debug option or a way to increase logging levels.  For ssh clients, there's a -v option.  ssh -vvvv will be VERY verbose for the connection steps.

---

### Post by steviehyperb on 2019-09-23
Thanks TheFu,

I done some work and its a bit better, that was changing a few settings in nsswitch.config but still not great. 

ssh-keys are an option, but the environment is mixed between Windows and Linux, so just trying to keep access uniform between the two. But that is an interesting point though, I may give this a try with an AD account and keys and see what happens. 

The initial failure happens so quickly it is like SSSD is ready to respond to requests even though it is running. 

Thanks for the pointers, I'll do some more digging and see what I can find

---

