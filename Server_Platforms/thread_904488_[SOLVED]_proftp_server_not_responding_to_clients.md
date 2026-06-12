---
title: "[SOLVED] proftp server not responding to clients"
date: 2008-08-29
forum: Server Platforms
---

### Post by freebeer on 2008-08-29
Hi guys!

I just discovered this morning that my proftp server isn't responding to clients.  I haven't changed the configuration at all, and it was working fine for months.

According to the processes, it's running.  According to gproftp gui, it's running.  According to WebAdmin, it's running.  (I even issued a stop and start from WebAdmin, still no joy.)

I can't get a response from it either on the LAN, or from the internet.  I've a dynamic IP addy, but that check out ok.  (I can access my web server just fine.)

If I try to telnet to it, I get a "connection closed by foreign host".  If I use the command line ftp, I get "421 Service not available remote server has closed connection".

If the latter error is accurate, I'm reading that the service is responding, but isn't accepting connections.

Anything else I should be checking?

Thanks!

---

### Post by cdenley on 2008-08-29
Have you by any chance configured a password-protected SSL certificate?

---

### Post by freebeer on 2008-08-29
Hi!  Thanks for your reply.

Not for the ftp server, I haven't.  (I played around with a certificate for a mail server, but that shouldn't affect the ftp server, should it?)

Dummy me... I forgot to mention that the only thing that changed on the machine was the recent kernel update (plus ancillary stuff that came with it).

---

### Post by cdenley on 2008-08-29
I suspected it may have been a problem I experienced. If you use a password-protected SSL certificate, when the log is rotated at the same time every month, it stops responding presumably because it is waiting for the certificate's password.

Apparently, you are not experiencing the same problem, and I can't think of any suggestions except typical troubleshooting (boot into an older kernel, change options in the configuration, etc).

---

### Post by freebeer on 2008-08-29
Yeah.  I'll be playing around once I get back home and have access to the machine again.  Thanks for your ideas!

---

### Post by freebeer on 2008-08-30
Ok... I found the problem (once I had some time at the machine).  For some reason, I lost my config file and it reverted to a default config.  *shrug*  I don't know how that came to be, but at least I've got it working again.

---

