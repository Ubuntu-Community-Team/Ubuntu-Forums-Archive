---
title: "Mail accounts for several domains"
date: 2010-02-28
forum: Server Platforms
---

### Post by 4747 on 2010-02-28
Hi everyone!

I'm using Debian 5 with Exim 4 on my VPS. My purpose is to make mailboxes for each virtual host on my server. What do I have:

1. Exim is set correctly - receiving mail from gmail.com is successfull.

2. Mail for [email]root@main.com[/email] is delivered, and the mail for [email]root@site1.com[/email] too. But main.com is the site written to /etc/hosts (it's localhost), and site1.com is virtual host. But mail from both boxes writes to /var/mail/mail.

Now what do I need:

1. Make mail for [email]root@site1.com[/email] store in www/site1.com.
2. Make mailboxes like [email]user@site1.com[/email] to receive mail by Thunderbird.
3. Set passwords for [email]root@main.com[/email] and [email]root@site1.com[/email] (I don't want to enter my system user/root passwords).
4. It's not a big deal, but I'd like to store [email]root@main.com[/email] mail into /root/Maildir, as it's done for my system user: /home/4747/Maildir

Will be grateful for any help!

---

