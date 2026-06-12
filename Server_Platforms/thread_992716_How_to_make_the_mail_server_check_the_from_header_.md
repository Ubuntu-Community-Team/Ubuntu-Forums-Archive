---
title: "How to make the mail server check the from header before sending?"
date: 2008-11-25
forum: Server Platforms
---

### Post by DjDarkman on 2008-11-25
The problem is that I want the mail server not send emails that contain invalid from headers mostly by via php mail(), I would like to provide a list of allowed from-addresses like: foo.com,bar.com,foobar.com and the mail server would only send mails from these addreses, this would prevent someone from sending a mail with a From: Fake Header <foo@invalid.com>.

So basicly I would want to filter out emails which contain invalid from headers, I would provide a list of valid addreses. Is this possible? and if yes, can you point me to the best solutionm for this? I don't want an overkill, just a simple solution to this and only this problem.

---

### Post by MJN on 2008-11-25
You can use the smtpd_sender_restrictions directive to check sender addresses (as specified with the MAIL FROM: command) against a whitelist of allowed senders).
 
Firstly, create a file (e.g. /etc/postfix/permitted_senders) with your allowed addresses@
 
```
# Permitted senders list
 
[EMAIL="fred@domain.com"]fred@domain.com[/EMAIL] PERMIT
@example.com PERMIT
```
 
Then convert the text file into a Postfix-readable binary format:
 
```
postmap /etc/postfix/permitted_senders
```
 
Finally, reference the file in Postfix:
 
```
smptd_sender_restrictions = check_sender_access hash:/etc/postfix/permitted_senders, reject
```
 
Note the default 'reject' at the end of the line - this will mean that unless a sender address matches the permitted list (and thus gets PERMITed) then it will be rejected.
 
Note also that this rule will apply to all connecting clients, so if this server accepts incoming mail then it will restrict those senders too. If this is not acceptable we will have to get a bit more creative with implementing the solution (most likely creating another instance of Postfix listening on a different port and getting your clients to only connect to this one).
 
Mathew

---

