---
title: "[samba][PDC] 3.4.0-3ubuntu5.5 breaks existing Windows 7 trust accounts"
date: 2010-03-11
forum: Server Platforms
---

### Post by Ovation1357 on 2010-03-11
Hi All,
     I updated to the latest packages and dist-upgrade yesterday, which included an upgrade to Samba "3.4.0-3ubuntu5.4" to Samba "3.4.0-3ubuntu5.5". This morning I received a call from a remote user that her laptop was reporting that it's trust relationship with the sever had failed. 

I see the following messages in the log for her machine:
[2010/03/10 10:50:58,  0] rpc_server/srv_netlog_nt.c:603(_netr_ServerAuthenticate3)
  _netr_ServerAuthenticate3: netlogon_creds_server_check failed. Rejecting auth request from client HELEN-PC machine account HELEN-PC$

We couldn't immediately remember the local user enabled on this host, but fortunately, booting it with the network disconnected, allow us to log in to the offline-cached domain credentials, where I was then able to re-join the domain.

I am left puzzled by this issue. At present, this is the only Windows 7 guest on the network - none of the Vista or XP domain members experienced a problem.

I guess this post is ultimately to record that this happened (significant in my mind as it happened at the first login since the latest update)....

Has anyone else experienced this? 

Is there a cleaner way to rejoin the domain than deleting the machine account with pdbedit and going back through the Network ID Wizard on Windows 7?

Cheers
Jonathan

---

### Post by mitanc on 2012-07-24
I am also having this issue.  I have logged on as local admin to the machine with a problem.  Unjoined and rejoined the domain, but the same issue arrises.  

Any ideas how to fix?

---

