---
title: "Courier authdaemon errors in Feisty"
date: 2007-05-31
forum: Server Platforms
---

### Post by Pollywoggy on 2007-05-31
I run Courier IMAP on Debian and I also installed it on a new Feisty system but I get the errors shown below although I can receive and access mail:

May 31 08:03:54 slider authdaemond: PAM unable to dlopen(/lib/security/pam_foreground.so)
May 31 08:03:54 slider authdaemond: PAM [dlerror: /lib/security/pam_foreground.so: undefined symbol: pam_set_data]
May 31 08:03:54 slider authdaemond: PAM adding faulty module: /lib/security/pam_foreground.so
May 31 08:04:01 slider authdaemond: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=pollywog
May 31 08:04:01 slider authdaemond: PAM unable to dlopen(/lib/security/pam_foreground.so)
May 31 08:04:01 slider authdaemond: PAM [dlerror: /lib/security/pam_foreground.so: undefined symbol: pam_set_data]
May 31 08:04:01 slider authdaemond: PAM adding faulty module: /lib/security/pam_foreground.so

I do not run Courier SMTP, I use Postfix for that.
These are the Courier packages that are installed:

ii  courier-authdaemon                         0.58-5ubuntu1                              Courier authentication daemon
ii  courier-authlib                            0.58-5ubuntu1                              Courier authentication library
ii  courier-authlib-mysql                      0.58-5ubuntu1                              MySQL support for the Courier authentication
ii  courier-authlib-userdb                     0.58-5ubuntu1                              userdb support for the Courier authenticatio
ii  courier-base                               0.53.3-5ubuntu1                            Courier Mail Server - Base system
ii  courier-imap                               4.1.1.20060828-5ubuntu1                    Courier Mail Server - IMAP server
ii  courier-imap-ssl                           4.1.1.20060828-5ubuntu1                    Courier Mail Server - IMAP over SSL
ii  courier-ssl                                0.53.3-5ubuntu1                            Courier Mail Server - SSL/TLS Support

The question is:  Are these errors coming from PAM or Courier and can it be fixed?
What about installing Courier from Debian Etch, since I don't have these problems in Etch?

---

