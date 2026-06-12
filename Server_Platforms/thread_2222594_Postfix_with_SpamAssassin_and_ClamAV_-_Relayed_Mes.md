---
title: "Postfix with SpamAssassin and ClamAV - Relayed Messages Missing Content Filtering"
date: 2014-05-07
forum: Server Platforms
---

### Post by Robin_Wilson on 2014-05-07
Hello

I have set up a new Ubuntu Server running 14.04 and managed to get SpamAssassin and ClamAV both working and scanning the messages which I have checked by looking at the headers in the email.
However whilst I do plan to deliver some email to local mailboxes I was hoping to be able to use the server to relay the messages to an Exchange server to filter the incoming messages.

I used the transport_maps setting to specify the domains that need to be forwarded to Exchange. This works however this causes the spam and virus filtering to be skipped and the messages are forwarded on unfiltered.

In /etc/postfix/master.cf I have this setting which forwards to ClamAV:

```

smtp      inet  n       -       -       -       -       smtpd
  -o content_filter=scan:127.0.0.1:10025

```

I then have this lower down to receive the mail back from ClamAV and forward it to SpamAssassin:
```

# AV scan filter (used by content_filter)
scan unix - - n - 16 smtp
  -o smtp_send_xforward_command=yes
# For injecting mail back into postfix from the filter
127.0.0.1:10026 inet n - n - 16 smtpd
  -o content_filter=spamassassin
  -o receive_override_options=no_unknown_recipient_checks,no_header_body_checks
  -o smtpd_helo_restrictions=
  -o smtpd_client_restrictions=
  -o smtpd_sender_restrictions=
  -o smtpd_recipient_restrictions=permit_mynetworks,reject
  -o mynetworks_style=host
  -o smtpd_authorized_xforward_hosts=127.0.0.0/8

```

Lastly the code for SpamAssassin is this:
```

spamassassin unix -     n       n       -       -       pipe
  user=spamd argv=/usr/bin/spamc -f -e
  /usr/sbin/sendmail -oi -f ${sender} ${recipient}

```

From what I read I think the solution might be to specify the first content filter in main.cf instead but if I put it there instead then mail transfer all fails with an error of too many hops so I think it is getting stuck in a loop and maybe bouncing backwards and forwards between SpamAssassin and ClamAV.

I have spent hours on this now and don't seem to be getting anywhere so am hoping someone can help.

Thanks
Robin

---

### Post by Robin_Wilson on 2014-05-09
Or is there a specialised Postfix forum where it would be better to post this issue to as I suppose it is probably not specific to Ubuntu and would be the same with other non-rpm distributions of Linux although I am running it on Ubuntu 14.04?

Thanks
Robin

---

### Post by Robin_Wilson on 2014-05-11
I have now resolved my problem.

After spending a while trying a combination of different settings I have now managed to get this working.

I needed to specify a content filter in main.cf which redirects all mail through the filter (in this case it is ClamAV) and then on the listener which injects the mail back into Postfix I put the SpamAssasin filter on there and this seems to force all mail through both of the content filters which is working well.

I did find that I also had to add the domains and users into the virtual_users and virtual_domains tables in the database otherwise it rejects the domain as relay access denied and rejects the users saying the user was not found. I suppose this is required as I wouldn't want to allow the server to relay for anything.

So I think everything is sorted now.
Not sure if this is the best way but at least it seems to work.

Robin

---

