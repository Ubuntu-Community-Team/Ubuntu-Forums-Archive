---
title: "mdadm and email"
date: 2012-07-29
forum: Server Platforms
---

### Post by davidesweden on 2012-07-29
Hi,

I have a problem with mdadm and email. I would like to receive an email whenever there is a problem with my RAID. The error I get when running the command below to test whether the email is configured correctly is:

mdadm --monitor --scan --test --oneshot
sendmail: 501 Syntax error in arguments

I believe ssmtp is configured correctly as the test email sent using the command below works fine.
echo test|sendmail MYEMAIL

I configured the ssmtp using:
root=MYEMAIL
mailhub=smtp.mail.yahoo.com:465
rewriteDomain=
hostname=MYEMAIL
UseTLS=YES
#UseSTARTTLS=YES
FromLineOverride=YES

mdadm.conf file looks like:
MAILADDR MYEMAIL


Any clue what the problem might be?
Thank you!

---

### Post by rubylaser on 2012-07-30
What if you try to send your test email like this via mdadm?
```
mdadm --monitor -m youruser@yahoo.com /dev/md0 -t
```

---

### Post by davidesweden on 2012-07-31
> **rubylaser said:**
> What if you try to send your test email like this via mdadm?
```
mdadm --monitor -m youruser@yahoo.com /dev/md0 -t
```

Same error:
sendmail: 501 Syntax error in arguments

and the prompt does not come back...

---

### Post by SeijiSensei on 2012-07-31
How about trying this instead?

In /etc/aliases create an alias like this:

```

notify:     root,you@example.com

```

replacing "you@example.com" with the address you wish to receive notices.  Then run the command "sudo newaliases" to rebuild the database.  

If you don't have the command-line **mail** program installed already, use "sudo apt-get install mailutils" to get it.  Then send the notify alias a message:

```
echo 'Hello' | mail -s 'test my connection' notify
```

Does a copy of the message appear in /var/spool/mail/root?  Does one get sent to you at the address you specified in the alias?

If that all works, then try the method rubylaser suggested replacing the email address with "notify".

Are you not able to send mail on port 25?  If you can, try removing the TLS parts of the configuration and use regular ESMTP.

---

### Post by davidesweden on 2012-07-31
> **SeijiSensei said:**
> How about trying this instead?

In /etc/aliases create an alias like this:

```

notify:     root,you@example.com

```

replacing "you@example.com" with the address you wish to receive notices.  Then run the command "sudo newaliases" to rebuild the database.  

If you don't have the command-line **mail** program installed already, use "sudo apt-get install mailutils" to get it.  Then send the notify alias a message:

```
echo 'Hello' | mail -s 'test my connection' notify
```

Does a copy of the message appear in /var/spool/mail/root?  Does one get sent to you at the address you specified in the alias?

If that all works, then try the method rubylaser suggested replacing the email address with "notify".

Are you not able to send mail on port 25?  If you can, try removing the TLS parts of the configuration and use regular ESMTP.

Thank you. I added the entry in /etc/aliases and run newaliases.
This message appears: "newaliases: Aliases are not used in sSMTP"
It seems aliases is not used anymore in sSMTP (I use lubuntu 12.04).

The command "echo 'Hello' | mail -s 'test my connection' notify" does not work. Nothing is in /var/spool/mail/root either.

However, mail is configured correctly: "echo 'Hello' | mail -s 'test my connection' MYEMAIL" works perfectly.

---

