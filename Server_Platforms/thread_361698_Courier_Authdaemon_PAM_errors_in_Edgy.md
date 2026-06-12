---
title: "Courier Authdaemon PAM errors in Edgy"
date: 2007-02-14
forum: Server Platforms
---

### Post by Pollywoggy on 2007-02-14
I am running Courier IMAP on a Ubuntu Edgy system and I am seeing these errors:

authdaemond: PAM unable to dlopen(/lib/security/pam_foreground.so)
authdaemond: PAM [dlerror: /lib/security/pam_foreground.so: undefined symbol: pam_set_data]
authdaemond: PAM adding faulty module: /lib/security/pam_foreground.so
authdaemond: PAM unable to dlopen(/lib/security/pam_foreground.so)
authdaemond: PAM [dlerror: /lib/security/pam_foreground.so: undefined symbol: pam_set_data]
authdaemond: PAM adding faulty module: /lib/security/pam_foreground.so

I also run Courier IMAP on a Debian Sarge system and I was running it on Etch as well, but I only see these errors in Ubuntu.  Any ideas where the problem might be?  I recompiled Courier and the PAM modules but I still see the errors I saw with the stock packages in Ubuntu.

---

