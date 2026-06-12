---
title: "SpamAssassin - Automatically move to Junk?"
date: 2007-02-22
forum: Server Platforms
---

### Post by jmacdonagh on 2007-02-22
I'm in the process of setting up Spamassassin on my mail server. The question is, can I have Spamassassin move suspect spam to a folder in my MailDir? It seems all it can do is add the appropriate header and modify the subject. I'd rather keep the subject untouched and move it to my Junk folder.

I check my e-mail on my computer, webmail, and my phone, so having it filter at my server is much better than adding a client rule.

Thanks.

---

### Post by eric_stewart on 2007-02-25
> **jmacdonagh said:**
> I'm in the process of setting up Spamassassin on my mail server. The question is, can I have Spamassassin move suspect spam to a folder in my MailDir? It seems all it can do is add the appropriate header and modify the subject. I'd rather keep the subject untouched and move it to my Junk folder.

I check my e-mail on my computer, webmail, and my phone, so having it filter at my server is much better than adding a client rule.

Thanks.

The answer depends on your email server software.  I use Maildrop as the intermediary/trash-hauling agent when email arrives on my Courier-MTA server.  I have a blog/forum posting on this subject on my website:  Here's a link to the blog  
[http://www.breezy.ca/?q=node/21](http://www.breezy.ca/?q=node/21)  You can also search "maildrop" in the search engine on the same site.  It will get you started.

I found the process kinda cryptic and I was on a steep learning curve but it seems to work fine, as long as SpamAssassin re-writes the mail headers first, then maildrop simply uses the rewritten email headers as a filter criteria.  The script on my site creates a ".SPAM" directory in Maildir if it doesn't already exist, then dumps the spam there.

/Eric

---

### Post by sorochan on 2008-07-22
How about [http://www.biodef.org/SpamAssassin/Quarantine/](http://www.biodef.org/SpamAssassin/Quarantine/) instead?

---

