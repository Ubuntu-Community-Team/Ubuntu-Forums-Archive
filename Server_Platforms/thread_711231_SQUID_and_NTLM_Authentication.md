---
title: "SQUID and NTLM Authentication"
date: 2008-02-29
forum: Server Platforms
---

### Post by b0red on 2008-02-29
I'm trying to get NTLM auth working with Squid and it's not going so well.

Seems to be similar to the issue [http://ubuntuforums.org/showthread.php?t=127603](http://ubuntuforums.org/showthread.php?t=127603)

The link  by Ariek to siriusit no longer works, or at least I'm getting a 404 now.

I get the following error in cache.log

ogin for user [DOMAIN]\[GOODUSER]@[WIN_2K_TEST] failed due to [winbind
client not authorized to use winbindd_pam_auth_crap. Ensure permissions on
/var/run/samba/winbindd_privileged are set correctly.] 

I have chgrp'd the pipe file to the proxy group and even chmod 777 and it made no difference.

tried this and it's not helping [http://wiki.squid-cache.org/ConfigExamples/WindowsAuthenticationNTLM](http://wiki.squid-cache.org/ConfigExamples/WindowsAuthenticationNTLM)

---

