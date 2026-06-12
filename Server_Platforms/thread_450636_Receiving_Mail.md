---
title: "Receiving Mail?"
date: 2007-05-21
forum: Server Platforms
---

### Post by blmartin777 on 2007-05-21
I set up a mail server. It seems to be working fine I am using roundcube right now for webmail because I like the look of it but would prefer squirrelmail for the plugins. I just think squirrelmail is ugly and I don't want to pay for a theme.

Anyways now that I have the mail server up and running, Can I set it up so if I set up a email for a friend that instead of using the webmail they have it downloaded to a client like thunderbird or something?

---

### Post by Brazen on 2007-05-21
You bet, any number of protocols can access the email store at the same time - webmail, pop3, imap, etc.  Look here for more info on setting up pop3 and/or imap on your server: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html#dovecot-server](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html#dovecot-server)

---

### Post by blmartin777 on 2007-05-21
Is dovecot different then sendmail and postfix? Then how do you set up the email client. for say my service provider, charter, I enter pop.charter.net and smtp.charter.net. Do I use pop.myhostname.com and smtp.myhostname.com. Is this right?

---

### Post by blmartin777 on 2007-05-21
Ok I can receive email in thunderbird but I can't send? Any ideas

---

### Post by Brazen on 2007-05-21
> **blmartin777 said:**
> Is dovecot different then sendmail and postfix? Then how do you set up the email client. for say my service provider, charter, I enter pop.charter.net and smtp.charter.net. Do I use pop.myhostname.com and smtp.myhostname.com. Is this right?

pop.charter.net and smtp.charter.net just means that the smtp server and pop server are on two different machines (or they use 2 different dns names that point to the same ip).  If your email server is called 'frank' and the dns entry for frank is 'frank.mydomain.com' then you would put 'frank.mydomain.com' into both the smtp server and pop server fields since you are installing your pop3 and smtp server on the same machine.

---

### Post by Brazen on 2007-05-21
And yes, dovecot is different then sendmail or postfix.  To simplify it, smtp is used for sending off an email to another server and pop3 is used for pulling down an email from a server.  Sendmail and postfix implement smtp, dovecot implements pop3 (and imap).

---

