---
title: "Email server question"
date: 2007-11-02
forum: Server Platforms
---

### Post by notaloafer on 2007-11-02
Right now I have setup a MySQL + Dovecot + Postfix and they're all communicating somewhat well.

Here is my problem: My virtual users are working fine, I can create virtual email users in postfix admin and I can login to them using Thunderbird. For a few test emails I tried sending email from [email]eric@anotherdomain.com[/email] to [email]eric@notaloafer.com[/email] . I get no failure errors sent back to [email]eric@anotherdomain.com[/email] but I also do not get the email message in [email]eric@notaloafer.com[/email]'s mailbox (however I can POP3 login to the mailbox, there's just no message in it).

I don't know what I need to post in order to get support so your guess is as good as mine =P

Here is the awesome guide I followed to get this far:
[http://johnny.chadda.se/2007/04/15/mail-server-howto-postfix-and-dovecot-with-mysql-and-tlsssl-postgrey-and-dspam/](http://johnny.chadda.se/2007/04/15/mail-server-howto-postfix-and-dovecot-with-mysql-and-tlsssl-postgrey-and-dspam/)

Thank you
-Eric

---

### Post by PaulFr on 2007-11-02
Well, first you can check whether the mail is reaching your machine - please check in the various mail.* (starting with **/var/log/mail.log**) files in **/var/log** directory for any sign of your email from anotherdomain.com:

1. If there is no sign of the email in the log files, I would suspect that anotherdomain.com does not know where to send the email (in DNS terms, there is no MX record for the notaloafter.com domain).

2. OTOH, if there is an entry in the /var/log/mail.* files, then reading the entries should give you an idea of what happened to the email.

---

### Post by notaloafer on 2007-11-02
Can you make any sense from this stuff?
It's from mail.log:

---

### Post by MJN on 2007-11-02
Is mail.notaloafer.com under your control?
 
For some reason your machine (mail.d2tbpk.com) attempted to authenticate with mail.notaloafer.com but this is unnecessary given mail.notaloafer.com is undoubtedly the final desination for notaloafer.com's mail. Anyway, it tried to authenticate and failed hence disconnected (without getting as far as sending the mail).
 
It may be useful if you expand on which machines you control as this could be a source or destination issue at the moment and we need some means to narrow down the cause. Can you send mail to other domains okay? Can you receive mail to notaloafer.com addresses from other domains?
 
Oh, and keep the logging verbosity down low to start with - only when you have an idea where the problem is is it worth increasing verbosity - as you can see even one -v flag dumps out a whole load of stuff which can make spotting problems tricky.
 
Mathew

---

### Post by tkharris on 2007-11-02
Can you post your /etc/postfix/main.cf file?

---

### Post by notaloafer on 2007-11-02
I wish I could post it but I am not home at the moment (I'll post it at the end of the day)

However, I noticed in a few other error logs more related to the "transport to dovecot" error. There is one line in my master.cf file for postfix that I had to add:

dovecot unix - n n - - pipe flags=DRhu user= vmail:mail argv=/usr/lib/dovecot/deliver -d $(recipient)

Could there be a problem with this line? It would make sense because this is the point where it takes my inbound mail and drops it in the correct virtual mailbox. (It would explain why I can login just fine, but cannot receive mail because it's not making it to the virtual mailbox).

Also the reason I turned verbose on was because I was getting no errors with that option set off (I was told by someone else to add verbose on).

Thanks guys!
-Eric

---

### Post by notaloafer on 2007-11-02
Also to address the issue of whether or not the mail is getting to the boxes, in mail.log there is no sign that the email is being received (the only things that are in the log are POP3 connection logs, nothing related to mail delivery).

-Eric

---

### Post by tkharris on 2007-11-02
Is DNS set up correctly?

I usually do:

domain.com -> ( type-> MX, data -> mailserver.domain.com }
mailserver.domain.com -> { type -> A, data -> ip.address.of.mail.server }

If there are no signs that the server is accepting connections, you likely have an issue with DNS.  I had thought you had a failure with the server not being able to authenticate when recieving email.  Since the server sending email shouldn't be authenticating to the mail end-point I assumed a messed up smtpd_receptient_restrictions in main.cf.

---

### Post by notaloafer on 2007-11-02
My DNS is perfectly setup... I haven't changed it for years. I had a working system-based mail system up and working just yesterday before I started all of this.

-Eric

---

### Post by notaloafer on 2007-11-02
Okay something new! I can now get messages, but when I tried sending a email from [email]eric@howitworks.com[/email] to [email]eric@notaloafer.com[/email] I got this error addressed to [email]postmaster@notaloafer.com[/email] (which was re-directed to [email]eric@notaloafer.com[/email] 's mailbox).

::

Transcript of session follows.

 Out: 220 mail.notaloafer.com ESMTP Postfix (Debian/GNU)
 In:  EHLO moab.howitworks.com
 Out: 250-mail.notaloafer.com
 Out: 250-PIPELINING
 Out: 250-SIZE 10240000
 Out: 250-VRFY
 Out: 250-ETRN
 Out: 250-STARTTLS
 Out: 250-AUTH PLAIN
 Out: 250-AUTH=PLAIN
 Out: 250-ENHANCEDSTATUSCODES
 Out: 250-8BITMIME
 Out: 250 DSN
 In:  STARTTLS
 Out: 220 2.0.0 Ready to start TLS
 In:  EHLO moab.howitworks.com
 Out: 250-mail.notaloafer.com
 Out: 250-PIPELINING
 Out: 250-SIZE 10240000
 Out: 250-VRFY
 Out: 250-ETRN
 Out: 250-AUTH PLAIN
 Out: 250-AUTH=PLAIN
 Out: 250-ENHANCEDSTATUSCODES
 Out: 250-8BITMIME
 Out: 250 DSN
 In:  MAIL From:<eric@howitworks.com> SIZE=1117
 Out: 250 2.1.0 Ok
 In:  RCPT To:<eric@notaloafer.com>
 Out: 451 4.3.5 Server configuration error
 In:  DATA
 Out: 554 5.5.1 Error: no valid recipients
 In:  RSET
 Out: 250 2.0.0 Ok
 In:  QUIT
 Out: 221 2.0.0 Bye

---

### Post by PaulFr on 2007-11-03
As far as your authentication error goes,

1. The link you mentioned states that in the /etc/dovecot/dovecot-sql.conf file > # The new name for MD5 is MD5-CRYPT so you might need to change this depending on version
default_pass_scheme = MD5So maybe you can try both MD5 and MD5-CRYPT to see if that is the problem. See **[http://wiki.dovecot.org/Authentication/PasswordSchemes](http://wiki.dovecot.org/Authentication/PasswordSchemes)** for explanation of password schemes in Dovecot.

2. If you can try this out without connecting to the Internet, I would suggest you first store the password in the SQL table in plain text, i.e. with no encryption, then set the default_pass_scheme in the /etc/dovecot/dovecot-sql.conf file to PLAIN, test out everything, and then if that succeeds, try out the various encryption schemes. I used this to debug my mail connection issues using the **[http://www.howtoforge.com/virtual_users_and_domains_with_postfix_debian_etch](http://www.howtoforge.com/virtual_users_and_domains_with_postfix_debian_etch)** guide.

---

### Post by notaloafer on 2007-11-03
After spending 12 hours on it, I realized the whole entire problem was I spelled "authenication" wrong in the main.cf file =P. Thanks for all of your support on it! As soon as I fixed the spelling error, all was good.

-Eric

---

