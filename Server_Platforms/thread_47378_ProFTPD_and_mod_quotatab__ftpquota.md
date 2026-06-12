---
title: "ProFTPD and mod_quotatab / ftpquota"
date: 2005-07-08
forum: Server Platforms
---

### Post by epohs on 2005-07-08
I recently installed ProFTPD, and have set up a functioning anonymous FTP directory.  I would like to limit the maximum filesize on an upload directory.  I gather I can do this with mod_quotatab (which appears to be compiled with ProFTPD).  However, I am not seeing either the QuotaLimitTable or the QuotaTallyTable.

From what I see in the [documentation](http://www.castaglia.org/proftpd/modules/mod_quotatab.html), these can be created using the [ftpquota](http://www.castaglia.org/proftpd/modules/ftpquota.html) script, however I don't believe it is a part of the default ProFTPD package that is installed by Synaptic.

My question would be, how should I go about limiting the maximum filesize on an upload directory using ProFTPD?

Here is the results of [COLOR=Green]proftpd -l[/COLOR] on my machine: ```
Compiled-in modules:
  mod_core.c
  mod_xfer.c
  mod_auth_unix.c
  mod_auth_file.c
  mod_auth.c
  mod_ls.c
  mod_log.c
  mod_site.c
  mod_auth_pam.c
  mod_quotatab.c
  mod_ratio.c
  mod_tls.c
  mod_rewrite.c
  mod_radius.c
  mod_wrap.c
  mod_quotatab_file.c
  mod_delay.c
  mod_readme.c
  mod_ifsession.c
  mod_cap.c
```


Thank you for any help or advice you can offer.  :)

---

### Post by epohs on 2005-07-11
Does anyone have any additional info on mod_quotatab, or the ftpquota script?  It seems like the documentation on castaglia.org is quite sparse, and I'm having a hard time finding much elsewhere.

I'm open to alternative ways of doing this, but I'm very much new to the anonymous FTP scene.

Any advice at all, even if it's just to say that this is a bad way of handling it would be appreciated.

---

