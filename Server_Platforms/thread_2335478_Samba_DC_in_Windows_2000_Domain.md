---
title: "Samba DC in Windows 2000 Domain"
date: 2016-08-29
forum: Server Platforms
---

### Post by lonpm2 on 2016-08-29
Hi

have an old Windows 2000 domain, server has been reliable but I realise long out of support now.

So I thought that I would set up a Samba Domain controller, allow it to sync and then get rid of the 2000 DC

No experience of Linux

downloaded the server version of UBUNTU 16.04.1 burned the iso and ran through the install which seemed straightforward

Following various Internet posts over the last few days have managed to give it a static name, static IP, configured it to provide DHCP and DNS and tested these fine.

Samba I installed using the samba Wiki, it appeared to install all the packages ok.

however using the samba-tool gives me the following error:

ERROR(runtime): uncaught exception - Connection to SAMR pipe of PDC of domain 'MYDOMAIN' failed: NT_STATUS_OBJECT_NAME_NOT_FOUND
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/__init__.py", line 175, in _run
    return self.run(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/domain.py", line 621, in run
    machinepass=machinepass, use_ntvfs=use_ntvfs, dns_backend=dns_backend)
  File "/usr/lib/python2.7/dist-packages/samba/join.py", line 1170, in join_DC
    ctx.do_join()
  File "/usr/lib/python2.7/dist-packages/samba/join.py", line 1073, in do_join
    ctx.join_add_objects()
  File "/usr/lib/python2.7/dist-packages/samba/join.py", line 602, in join_add_objects
    newpassword=ctx.acct_pass)

sadly so new to this I do not understand how to begin troubleshooting it.

Would welcome help on this, particularly if it is at the level of absolute newbie

if I have to undo what I have done would welcome guidance on how!

thanks

---

### Post by howefield on 2016-08-29
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

