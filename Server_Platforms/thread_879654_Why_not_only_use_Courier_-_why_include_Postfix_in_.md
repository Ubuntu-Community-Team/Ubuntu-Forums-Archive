---
title: "Why not only use Courier - why include Postfix in the set-up?"
date: 2008-08-04
forum: Server Platforms
---

### Post by mikl-dk on 2008-08-04
I've installed a couple of mailservers with Postfix, Courier, virtual users etc., but I'm a bit confused of why we don't only Courier (Postfix is not capable of POP3, IMAP etc., so that's why I don't only use that)? Isn't Courier capable of every aspect so why use Postfix together with is? Is it because it's easier to configure SPAM-protection with Postfix or something like that?

---

### Post by hyper_ch on 2008-08-04
Postfix is a MTA - sending and receiving email
Courier is a POP3/IMAP server - giving access to the mailbox / maildir through an email program.

(very simple said)

---

### Post by mikl-dk on 2008-08-04
Yes, that was what I thought, too, but on [http://www.courier-mta.org/](http://www.courier-mta.org/) it says (quoting):
"Courier provides ESMTP, IMAP, POP3, webmail, and mailing list services within a single, consistent, framework."
and
"Courier can function as an intermediate mail relay, relaying mail between an internal LAN and the Internet, or perform final delivery to mailboxes. Courier uses maildirs as its native mail storage format, but it can also deliver mail to legacy mailbox files as well."

As I read that, it's capable of sending and receiving mails, too?

---

### Post by hyper_ch on 2008-08-04
well, never bothered to use courier as mta. Postfix is just so damn powerful yet simple.

---

### Post by mikl-dk on 2008-08-04
> **hyper_ch said:**
> well, never bothered to use courier as mta. Postfix is just so damn powerful yet simple.

In that I agree! And I don't have any plans on letting go of it. I was merely wondering about each component in the set-up (connections to each other, areas of responsibility etc.).

---

### Post by hyper_ch on 2008-08-04
well, by having courier as pop3/imap server and postfix as mta you get the best of both worlds ;)

Actually i have no idea why they set it up like this. I think it's probably the most common combination.

Although I heard some good stuff about dovecot also...

---

### Post by mikl-dk on 2008-08-04
> **hyper_ch said:**
> well, by having courier as pop3/imap server and postfix as mta you get the best of both worlds ;)
That was also my "suspicion". Well, thanks a lot for the quick answer. I'd try to read a bit about dovecot and maybe try it out. Have a nice day :-).

---

