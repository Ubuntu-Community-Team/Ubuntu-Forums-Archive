---
title: "linux apache server in a windows environment"
date: 2009-02-09
forum: Server Platforms
---

### Post by csergec on 2009-02-09
hi


I have an apache server for intranet.
Users will get email through this site.
We use MS Exchange for the emails inside and outside our LAN.
How can I be able to use the php mail function to send mail? How to configure postfix [i suppose i need it for sending mail] to send the mails to MS Exchange?

Thank you for help

Serge

---

### Post by rickyjones on 2009-02-09
> **csergec said:**
> hi


I have an apache server for intranet.
Users will get email through this site.
We use MS Exchange for the emails inside and outside our LAN.
How can I be able to use the php mail function to send mail? How to configure postfix [i suppose i need it for sending mail] to send the mails to MS Exchange?

Thank you for help

Serge

I can't give you specific step by steps but here is what needs to be  done:

1. Configure postfix as an internet smarthost and the mail relay is your Exchange server.

2. Configure the Exchange server policies so that it will accept relayed mail from your local postfix server. You can add IPs to a whitelist for this.

That should be it - I did the same thing for a server at a client.

Thanks,
Richard

---

### Post by csergec on 2009-02-10
Hi Richard

Thank you for your quick answer.
It helped me a lot.

As the visitors  only send a feedback email though my linux apache webserver , I just enter the id of the MS exchange server as the relayhost.

Thank you again for your help.

Serge

---

### Post by rickyjones on 2009-02-10
> **csergec said:**
> Hi Richard

Thank you for your quick answer.
It helped me a lot.

As the visitors  only send a feedback email though my linux apache webserver , I just enter the id of the MS exchange server as the relayhost.

Thank you again for your help.

Serge

You're very welcome - good luck!

Thanks,
Richard

---

### Post by csergec on 2009-02-10
Hi 
Now that it works for me I have to figure out how to solve another problem...
The problem of encodings.

With php, I use utf-8. When I export to excel I can make the conversion to be able to see the characters.
But with MS Echange/Outlook I just get kinds of x and points.
I think I tried everything ( iconv(), mb_convert_encoding() ).

Is there anybody who faced this situation and was able to resolve it?


Thanks in advance!

EDIT:
After having googled a very long time I found the solution:
[http://bitprison.net/php_mail_utf-8_subject_and_message]("http://bitprison.net/php_mail_utf-8_subject_and_message")

Serge

---

