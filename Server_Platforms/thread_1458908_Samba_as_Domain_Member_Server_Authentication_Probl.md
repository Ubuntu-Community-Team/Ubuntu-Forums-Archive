---
title: "Samba as Domain Member Server Authentication Problem"
date: 2010-04-20
forum: Server Platforms
---

### Post by tgice on 2010-04-20
I've been working for hours with Samba on Ubuntu Server 9.10 (Samba version 3.4.0), trying to get it setup simply as a fileserver that performs authentication to an NT 4 server (yes, I know, old and out of date).

After much struggling, I finally realized that my configuration *was* working when the clients connecting (from XP, and Win2k clients, mostly) were actually joined to the domain (where the PDC is the NT 4 Server) and logged into the domain.

For various reasons, many of the Windows clients at this location don't actually log into the domain, even though they have login/passwords that are valid users on the domain and they'll typically have some drives mapped to the PDC.

By the way, I have this working on another Linux box running Samba 3.0.28, so I'm sure it's possible, I'm just lost as to how to do it.

When I try to connect to a share on my new Samba box, I see entries like these in the logs:

> [2010/04/20 15:24:29,  3] auth/auth.c:222(check_ntlm_password)
  check_ntlm_password:  Checking password for unmapped user []\[]@[client1] with
the new password interface
[2010/04/20 15:24:29,  3] auth/auth.c:225(check_ntlm_password)
  check_ntlm_password:  mapped user is: [FILESRV]\[]@[client1]
[2010/04/20 15:24:29,  3] auth/auth.c:271(check_ntlm_password)
  check_ntlm_password: guest authentication for user [] succeeded
[2010/04/20 15:24:29,  0] param/loadparm.c:9783(widelinks_warning)
  Share 'IPC$' has wide links and unix extensions enabled. These parameters are
incompatible. Wide links will be disabled for this share.
[2010/04/20 15:24:29,  3] auth/auth.c:222(check_ntlm_password)
  check_ntlm_password:  Checking password for unmapped user [client1]\[user1]@[ILLI
NI] with the new password interface
[2010/04/20 15:24:29,  3] auth/auth.c:225(check_ntlm_password)
  check_ntlm_password:  mapped user is: [FILESRV]\[user1]@[client1]
[2010/04/20 15:24:29,  3] auth/auth_sam.c:282(check_sam_security)
  check_sam_security: Couldn't find user 'user1' in passdb.
[2010/04/20 15:24:29,  3] auth/auth_winbind.c:54(check_winbind_security)
  check_winbind_security: Not using winbind, requested domain [FILESRV] was for this SAM.
[2010/04/20 15:24:29,  2] auth/auth.c:320(check_ntlm_password)
  check_ntlm_password:  Authentication for user [user1] -> [user1] FAILED with error
 NT_STATUS_NO_SUCH_USER
[2010/04/20 15:24:29,  1] smbd/service.c:676(make_connection_snum)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED

I think the critical part is where it says "Not using winbind, requested domain [FILESRV] was for this SAM" I *do* want it to use winbind and authenticate via the remote NT 4 Server, not locally only.

This is an example on the Samba 3.4.0 box where the login *works*, but I think only because the user is actually logged into the domain:

> [2010/04/20 15:23:20,  3] auth/auth.c:222(check_ntlm_password)
  check_ntlm_password:  Checking password for unmapped user [DOMNAME]\[client2]@[M
AILMAN2] with the new password interface
[2010/04/20 15:23:20,  3] auth/auth.c:225(check_ntlm_password)
  check_ntlm_password:  mapped user is: [DOMNAME]\[client2]@[client2]
[2010/04/20 15:23:20,  3] auth/auth.c:271(check_ntlm_password)
  check_ntlm_password: winbind authentication for user [client2] succeeded
[2010/04/20 15:23:20,  2] auth/auth.c:310(check_ntlm_password)
  check_ntlm_password:  authentication for user [client2] -> [client2] -> [MAI
N+user2] succeeded
[2010/04/20 15:23:20,  0] param/loadparm.c:9783(widelinks_warning)
  Share 'Admin' has wide links and unix extensions enabled. These parameters are
 incompatible. Wide links will be disabled for this share.
[2010/04/20 15:23:20,  1] smbd/service.c:1062(make_connection_snum)
  user2 (::ffff:192.168.1.5) connect to service Admin initially as user DOMNAME+
user2 (uid=70030, gid=70005) (pid 4821)
[2010/04/20 15:23:20,  0] param/loadparm.c:9783(widelinks_warning)
  Share 'Admin' has wide links and unix extensions enabled. These parameters are
 incompatible. Wide links will be disabled for this share.
[2010/04/20 15:23:20,  1] smbd/service.c:1062(make_connection_snum)
  user2 (::ffff:192.168.1.5) connect to service Admin initially as user DOMNAME+
user2 (uid=70030, gid=70005) (pid 4821)
[2010/04/20 15:23:39,  1] smbd/service.c:1241(close_cnum)
  user2 (::ffff:192.168.1.5) closed connection to service Admin

This is an example of the same authentication (from user1, *not* logged into the domain) succeeding on Samba 3.0.x:

> [2010/04/20 16:09:21, 2] smbd/sesssetup.c:setup_new_vc_session(1200)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all ol
resources.
[2010/04/20 16:09:21, 2] smbd/sesssetup.c:setup_new_vc_session(1200)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all ol
resources.
[2010/04/20 16:09:21, 3] auth/auth.c:check_ntlm_password(221)
  check_ntlm_password:  Checking password for unmapped user []\[]@[client1] wit
the new password interface
[2010/04/20 16:09:21, 3] auth/auth.c:check_ntlm_password(224)
  check_ntlm_password:  mapped user is: [DOMNAME]\[]@[client1]
[2010/04/20 16:09:21, 3] auth/auth.c:check_ntlm_password(270)
  check_ntlm_password: guest authentication for user [] succeeded
[2010/04/20 16:09:21, 2] lib/access.c:check_access(323)
  Allowed connection from  (10.9.0.62)
[2010/04/20 16:09:21, 3] auth/auth.c:check_ntlm_password(221)
  check_ntlm_password:  Checking password for unmapped user [client1]\[user1]@[IL
NI] with the new password interface
[2010/04/20 16:09:21, 3] auth/auth.c:check_ntlm_password(224)
  check_ntlm_password:  mapped user is: [DOMNAME]\[user1]@[client1]
[2010/04/20 16:09:21, 3] auth/auth.c:check_ntlm_password(270)
  check_ntlm_password: winbind authentication for user [user1] succeeded
[2010/04/20 16:09:21, 2] auth/auth.c:check_ntlm_password(309)
  check_ntlm_password:  authentication for user [user1] -> [user1] -> [DOMNAME\user1] suceeded
[2010/04/20 16:09:21, 2] lib/access.c:check_access(323)
  Allowed connection from  (10.9.0.62)
[2010/04/20 16:09:21, 1] smbd/service.c:make_connection_snum(1033)
  client1 (10.9.0.62) connect to service DatabaseBackup initially as user backu
(uid=10049, gid=10049) (pid 21909)

I can provide plenty more information if it would help diagnose the situation.  Does anyone have an idea of how I can get this to work?  I'm sure it's possible, since the exact scenario worked in a recent version of Samba.

Thanks.

---

### Post by tgice on 2010-04-22
I cross posted this problem to the Samba list and got a quick reply.  Here's the solution for me:

Adding:

   map untrusted to domain = Yes

to my smb.conf solved the problem and reverted to the behavior I'm used 
to (and currently relying on).

---

