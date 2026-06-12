---
title: "Stop Postfix from rewriting senders address"
date: 2013-06-24
forum: Server Platforms
---

### Post by CaptainSlowSA on 2013-06-24
Good day,

I am new to this forum. I have searched for this problem outside of this forum as well and am not able to find the solution.

I have a Postifx box, downloading mail from my ISP using fetchmail, and forwarding the mail to my exchange box. Everything works 100%, except when we get email from an company that uses non standard characters or non standard english in their addresses, postfix then rewrites the address to [email]client@myservername.domain.co.za[/email] - where 'client' would have a '?' in place of the special character - when it should in fact be [email]client@clientdomain.com[/email] - with no '?'.

This mainly happens when we get mails from clients/users in Europe or Russia and espicially when they have non-standard english in the address.

I would like to try stop postfix from rewriting these addresses and to keep them in the form sent to us? Is this possible? I would appreciate any help going forward.

Thanks in advance!

---

