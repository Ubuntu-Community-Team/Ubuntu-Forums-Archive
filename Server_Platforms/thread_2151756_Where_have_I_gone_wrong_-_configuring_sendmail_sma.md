---
title: "Where have I gone wrong - configuring sendmail smarthost on port 465/587"
date: 2013-06-05
forum: Server Platforms
---

### Post by PM47 on 2013-06-05
I've not set up a linux mail server before so apologies if this has been asked (many) times already. I have Fetchmail, Sendmail and Procmail set up as a SOHO mail server. It works great for fetching external emails and distributing local email but despite trawling the web for info I can't persuade Sendmail to send mail to the outside world. I have to use Fastmail ([www.fastmail.fm]("http://www.fastmail.fm")) as a smarthost as my ISP blocks port 25 and their mail relay is unreliable (loses mail). Fastmail can accept smtp mail on ports 465 or 587, not sure what the difference is ??

As instructed in many places on the web I've done the following :

Added /etc/mail/auth/client-info containing...

    AuthInfo:my.isp.net "U:root" "I:user" "P:password"
    AuthInfo: "U:root" "I:user" "P:password"

Run...

   # makemap hash client-info < client-info
   # chmod 600 client-info*

...and client-info.db has been created

Added the following to the M4 configuration file...

    dnl # Send outgoing mail to Fastmail relay
    define(`SMART_HOST',`mail.messagingengine.com')dnl
    define(`RELAY_MAILER_ARGS', `TCP $h 587')dnl
    define(`ESMTP_MAILER_ARGS', `TCP $h 587')dnl
    define(`confAUTH_OPTIONS', `A p')dnl
    TRUST_AUTH_MECH(`EXTERNAL DIGEST-MD5 CRAM-MD5 LOGIN PLAIN')dnl
    define(`confAUTH_MECHANISMS', `EXTERNAL GSSAPI DIGEST-MD5 CRAM-MD5 LOGIN PLAIN')dnl  
    FEATURE(`authinfo',`hash -o /etc/mail/auth/client-info.db')dnl

...and re-compiled sendmail.cf and re-started sendmail.

I've tried variations on this, from all over the web, but cannot get sendmail to connect to Fastmail's smtp server. At present this gives...

** error occurred on SMTP session
*** Error occurred while sending the message:
550 5.7.1 <recipient@mail.com>... Relaying denied. Proper authentication required.

...but in the past I've had time-outs and various other errors which all appear to be related to the authentication.

Can some kind soul please talk me through how to get sendmail to talk to Fastmail please ??

---

