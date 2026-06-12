---
title: "postfix root email forward"
date: 2012-03-20
forum: Server Platforms
---

### Post by DanHorniblow on 2012-03-20
Hi, I would like to forward all mail that goes to postfix's root email account to a different account on the same server.

Any ideas?

I am a little new to postfix.

Thanks Dan

---

### Post by SeijiSensei on 2012-03-20
Postfix uses the same /etc/aliases file as sendmail does.  Edit, as root with sudo, the file /etc/aliases and add this line to the top:

```
root:     yourusername
```

replacing "yourusername" with the name of the account to which you'd like root's mail delivered.  Then run the command "sudo newaliases" to update the alias database.  That's it!

---

### Post by DanHorniblow on 2012-03-20
Hi thanks for the reply, I am not working now so I will try this tomorrow.

Would it make any difference that the email account I want to forward all emails to is in courier and not postfix?

---

### Post by SeijiSensei on 2012-03-20
> **DanHorniblow said:**
> Hi thanks for the reply, I am not working now so I will try this tomorrow.

Would it make any difference that the email account I want to forward all emails to is in courier and not postfix?

???

You said the account is on the same server as Postfix.  Are you running two MTAs on the same server listening on different ports?  Or by "in courier" do you mean the mailboxes are in the Maildir format (one message per file) rather than mbox (one file per folder)?

I suspect the answer is it doesn't make any difference since Postfix uses the aliases file simply to rewrite the destination address.  If mail to user "joey" gets delivered correctly now, then having an alias that points "root" to "joey" should work fine.

---

### Post by DanHorniblow on 2012-03-20
I did not create the server myself, so I don't know a massive amount about it.

I think that postfix handles all of the SMTP traffic and Courier is used for all of the IMAP. We don't use POP3.

However for example I know that all the emails for the email account "name@domain.com" would be stored as seperate files in "/var/vmail/domain.com/name/" and all of the users mail folders would be in their aswell.

---

### Post by DanHorniblow on 2012-03-22
In the end I just created a file in "/root/" called ".forward" and on the first line of that file I just wrote my email address.

I didn't expect it to work but it did! Now any mail that goes to the root account is forwarded to my email address.

---

### Post by SeijiSensei on 2012-03-22
Yep, the old tried-and-true Unix method.  Since only root can edit /etc/aliases there needed to be a way for unprivileged users to forward mail.  The .forward file is that method.

You can add additional addresses separated by commas, and you can even have the mail delivered to both root and yourself like this:

```
\root,dan,fred@example.com
```

That puts a copy of each message in /var/spool/mail/root and sends another copy to the local account dan and a third to [email]fred@example.com[/email].  See "man aliases" for details on other options like piping messages to a program.  (The hoary Unix [vacation]("http://www.computerhope.com/unix/uvacatio.htm") program uses this method.)

---

