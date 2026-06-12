---
title: "Ejabber doesn't work"
date: 2015-05-27
forum: Server Platforms
---

### Post by Hector_Daniel_Prad on 2015-05-27
ejabberd.service - LSB: Starts ejabberd jabber server
   Loaded: loaded (/etc/init.d/ejabberd)
   Active: failed (Result: exit-code) since Thu 2015-05-28 01:25:26 UTC; 23s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 4264 ExecStart=/etc/init.d/ejabberd start (code=exited, status=4)

May 28 01:25:26 alternate.gq su[4268]: + ??? root:ejabberd
May 28 01:25:26 alternate.gq su[4268]: pam_unix(su:session): session opened for user ejabberd by (uid=0)
May 28 01:25:26 alternate.gq su[4312]: Successful su for ejabberd by root
May 28 01:25:26 alternate.gq su[4312]: + ??? root:ejabberd
May 28 01:25:26 alternate.gq su[4312]: pam_unix(su:session): session opened for user ejabberd by (uid=0)
May 28 01:25:26 alternate.gq ejabberd[4264]: ERROR: The ejabberd node 'ejabberd' is already running.
May 28 01:25:26 alternate.gq systemd[1]: ejabberd.service: control process exited, code=exited status=4
May 28 01:25:26 alternate.gq systemd[1]: Failed to start LSB: Starts ejabberd jabber server.
May 28 01:25:26 alternate.gq systemd[1]: Unit ejabberd.service entered failed state.
May 28 01:25:26 alternate.gq systemd[1]: ejabberd.service failed.

That is the error please tell me what went wrong.

---

