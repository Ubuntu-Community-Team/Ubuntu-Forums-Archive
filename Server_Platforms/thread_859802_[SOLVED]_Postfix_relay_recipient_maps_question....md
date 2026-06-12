---
title: "[SOLVED] Postfix relay_recipient_maps question..."
date: 2008-07-14
forum: Server Platforms
---

### Post by SJI on 2008-07-14
Hello everyone,

I'm in the process of creating an email server running hardy/postfix with a view to replacing an old redhat/sendmail system with it if all goes well.

I've got most of what I need working so far but have a question regarding entries in the relay_recipient_maps file.

Everything is set up for domains mydomain1.com and mydomain2.com.

In the sendmail configuration I can define wildcard entries such as user1@ which would accept mail for [email]user1@mydomain1.com[/email] or [email]user1@mydomain2.com[/email].

From what i've gathered I must now explicitly make the two entries in the relay_recipient_maps file in order to accept mail in the same manner under postfix. Is this correct or have i missed something in the config files?

Many thanks,

Stephen

---

### Post by skunkbad on 2008-07-15
I had followed a couple tutorials trying to get Postfix set up, and it wasn't until I followed this one:
[B][COLOR="Blue"][URL="https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto"]
https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto[/URL][/COLOR][/B]

that I got it working. This tutorial covers sending emails to different domains/recipients, and could easy be modified to map to the same email box within /etc/postfix/vmaps (which is set up during the tutorial).

I just ordered a Postfix book from Amazon tonight, so hopefully after reading it I will be a Postfix guru.

---

### Post by SJI on 2008-07-18
Thanks for the link.

I solved my particular issue with regexp.
I have domain1, domain2, domain3 etc...
With user1@domain1, user1@domain2 etc...

By having an entry in the recipient relay map of /^user1@/ it performs the match nicely and forwards the mail onto my exchange server.

Stephen

---

