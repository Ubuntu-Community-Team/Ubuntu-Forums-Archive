---
title: "Multiple Relayhosts in Postfix, choosen by Sender-Mailadress"
date: 2009-12-03
forum: Server Platforms
---

### Post by kleinlohmi on 2009-12-03
Hi guys,

i've set up a postfix/dovecot mail-server at home, that collects the mail from my other web mail accounts via fetchmail.

I would now like to configure multiple relayhosts in postfix, so that i can send mail via my local server. postfix should then automatically choose which relayhost to use, based on the sender-adress in the email.

Is this possible in postfix and could you then provide some instructions?

Best regards,
Enno

---

### Post by kleinlohmi on 2009-12-03
I searched a bit on the web, and found the postfix configuration option sender_dependent_relayhost -- I think that's just what i need!

The problem is, that i can't find some easy documentations for that feature. Could anyone be so kind to explain the setup to me?

---

