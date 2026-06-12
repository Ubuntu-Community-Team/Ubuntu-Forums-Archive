---
title: "Mail Server use via Mobile Phone"
date: 2008-08-03
forum: Server Platforms
---

### Post by kvn290 on 2008-08-03
I have set up a mail server thanks to Flurdy's advice.  THANKS!!!

Now I'd like to get even more advanced with the setup, but I'm not sure where to start.  I have a dynamic IP, so I'm forced to use a relay service.  (My emails were getting kicked back by Yahoo, MSN, etc....nothing i could do.  My ISP's fault!)

Anyways, I have a fancy cellphone, and I can connect to my server just fine.  The problem comes when sending.  Because I use a relay service, the username/password for SMTP is for the relay, not for the email account.  The phone doesn't allow for a seperate password for SMTP.

The question....is there a way that I can connect to MY server via SMTP, which would then send out the email i created from my mobile phone via the relay service SMTP?

I'm setup per Flurdy's instructions, so that should help you understand my basic setup.  It's gotta be possible!!!  I'm just lost as to howto...

Maybe I could set up a second "virtual" email server that is for mobile, only?  Seems overkill, but just an idea.

I'm a newb, so semi-detailed instructions will be needed.

Thanks!!!

---

### Post by StickyStyle on 2008-08-03
Take a look at the SMTP authentication section of the server guide, [http://doc.ubuntu.com/ubuntu/serverguide/C/postfix.html](http://doc.ubuntu.com/ubuntu/serverguide/C/postfix.html) that way you auth against your server then your server sends the mail through the relay.

---

### Post by AdamWood on 2008-08-04
> It's gotta be possible!!! I'm just lost as to howto...

Yes it is possible, I use a setup just like this.

The basic principle of what you want to do is configure your phone to send an e-mail to your personal server (on the dynamic IP) and have that server act as a relay.

Since you mention you're already sending e-mails out via another relay you should have most of the configuration done. I'm not familiar with Flurdy's guide but I'll assume it's secure, which probably means it's only accepting e-mails from outside your private network with a "TO" address that it is supposed to be handling. Otherwise you're risking running an open relay and that's bad in many ways.

You're probably also restricting the forwarding of outgoing e-mails (via the ISP relay) to those originating from within your private network. If you're using Postfix you'll have a line like **mynetworks=192.168.0.0/24** and **permit_mynetworks** in a **smtpd_recipient_restrictions** line. StickyStyle already pointed you to a good resource but the part your interested in is **permit_sasl_authenticated**. There's a bit of other configuration needed to get sasl working for password authentication but that's where you want to start.

---

