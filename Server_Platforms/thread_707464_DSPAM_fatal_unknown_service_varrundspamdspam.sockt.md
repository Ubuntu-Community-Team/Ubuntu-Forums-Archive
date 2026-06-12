---
title: "DSPAM: fatal: unknown service: /var/run/dspam/dspam.sock/tcp"
date: 2008-02-25
forum: Server Platforms
---

### Post by jelle-e on 2008-02-25
I've searched in a lot of places but can't seem to find what the following error in '/var/log/mail.log' relates to:
"fatal: unknown service: /var/run/dspam/dspam.sock/tcp"

In dspam.conf I use:
DeliveryHost        127.0.0.1
DeliveryPort        10026
DeliveryIdent      localhost
DeliveryProto      SMTP

In postfix master.cf:
smtp       inet  n       -       n       -       -       smtpd -o content_filter=lmtp:unix:/var/run/dspam/dspam.sock

dspam      unix  -       n       n       -       10      pipe
  flags=Ru user=dspam argv=/usr/local/bin/dspam --deliver=innocent --user ${recipient} -i -f $sender -- $recipient

Any ideas on what this error is and how to solve it?

Thanks!

---

