---
title: "Email server recommendation..."
date: 2007-06-18
forum: Server Platforms
---

### Post by matt_b on 2007-06-18
Hi all,

I need a mailserver app installed on my 6.06 server. Fundamentally I need it to have a webmail interface, POP3 & IMAP support, and be able to support multiple domain aliases. The domains issue is the biggest - I want users to have one mailbox (joe@domain1.com) that can send and receive mail for [email]joe@domain2.com[/email] and [email]joe@domain3.com[/email] as well, all from the same mailbox.

Can anyone suggest a solution? I've looked at Zimbra and OpenXchange so far but can't seem to identify whether my "multiple domains one mailbox" requirement is catered for in either.

Thanks
matt_b

---

### Post by MJN on 2007-06-18
You'll be relieved to hear that's quite a common configuration for many people.
 
For mine, I use Postfix for the MTA and Dovecot for the IMAP server (also supports POP but I don't recommend this given you'll want webmail and hence multi-point access with presumably the same 'view' regardless of access method/point (e.g webmail, standard e-mail client etc)) and Squirrelmail for the webmail. Multiple domains running, multiple identities, and all wrapped into the same mailboxes if required.
 
My biggest tip would be to take on step at a time - however tempting it may be do not give in to impatience and try and build the whole lot in one go. Start with the mail server (receiving, then sending) and then progress onto accessing the mailbox via a 'standard' (i.e. known working) e-mail client. Then move on to the webmail. The trickiest (yet entirely doable) part to get exactly right will be the MTA - the IMAP server and webmail are relatively straight forward and don't require much configuration out of the box.
 
Mathew

---

