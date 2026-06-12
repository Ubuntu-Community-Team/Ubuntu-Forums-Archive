---
title: "Trying to setup postfix/dovecot, cant send/receive mails"
date: 2014-04-05
forum: Server Platforms
---

### Post by Thee on 2014-04-05
Hi, I'm trying to setup a mail server on my Raspberry Pi for the first time and I'm having some problems. Namely, I can't send or receive any mails at all (nothing arrives).
I must have missed something but I don't know what...

For a test, when I do:

```
telnet localhost imap
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE AUTH=PLAIN] Dovecot ready.
a login "thee" "pass"
a OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE SORT SORT=DISPLAY THREAD=REFERENCES THREAD=REFS MULTIAPPEND UNSELECT CHILDREN NAMESPACE UIDPLUS LIST-EXTENDED I18NLEVEL=1 CONDSTORE QRESYNC ESEARCH ESORT SEARCHRES WITHIN CONTEXT=SEARCH LIST-STATUS SPECIAL-USE] Logged in
b select inbox
b NO [SERVERBUG] Internal error occurred. Refer to server log for more information. [2014-04-05 13:04:51]
```

in the dovecot log it says:

```

Apr  5 13:04:31 gameflask dovecot: imap-login: Login: user=<thee>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=3232, secured, session=<JKhImUn2nAB/AAAB>
Apr  5 13:04:51 gameflask dovecot: imap(thee): Error: open(/var/mail/thee) failed: Permission denied (euid=1001(thee) egid=1004(thee) missing +w perm: /var/mail, we're not in group 33(www-data), dir owned by 33:33 mode=0775)
Apr  5 13:04:51 gameflask dovecot: imap(thee): Error: Opening INBOX failed: Mailbox doesn't exist: INBOX


```


Now, I guess that error is related to my problem, but I'm not quite sure how to fix it.

Any help would be appreciated.
Thanks.

---

### Post by Catalys on 2014-04-05
Try:

```
chmod 777 /var/mail
```

It seems like a permission issue.

---

### Post by SeijiSensei on 2014-04-05
No, you definitely do not want to make /var/mail 777.  Then all users on the system can read everyone else's mail.

By default on Ubuntu with Postfix /var/mail is owned by root with group mail.  That group has write privileges, and the "sgid" bit is set as well.  A "ls -l /var" should show the mail directory like this:
```
drwxrwsr-x  2 root mail     4096 Jan 21 10:54 mail
```

To set the permissions correctly use:
```

cd /var
sudo chown root:mail mail
sudo chmod 2775 mail

```
The "2" sets the sgid bit.  That makes the group owner of all files in /var/mail the same as the group owner of /var/mail itself, in this case group "mail."

Granting world read/write permissions to a directory should absolutely be your last resort, and even then it shouldn't be needed.

---

### Post by Thee on 2014-04-05
Thank you SeijiSensei, that solved the error messages, but I still can't send or receive any mails even tho everything seems to work. Any suggestions on that?
Also I installed AfterLogic WebMail Lite as a webmail and with it I'm not able to login to my mail account. It just says "Error while connecting to mail server".

---

### Post by SeijiSensei on 2014-04-05
Are you sure your ISP allows mail servers? If you are on a residential service, the ISP may simply have blocked inbound and outbound traffic on port 25.  The Terms of Service for most residential Internet accounts prohibits the use of servers, and your ISP may enforce that prohibition by blocking ports.  I suggest reading your ToS on the ISPs website as a first step.

---

### Post by Thee on 2014-04-05
I don't think my ISP is blocking port 25 because I can connect to my server using:

```

telnet gameflask.com 25

```

Try it yourself.

---

### Post by Thee on 2014-04-05
OK i changed some things in my /etc/hosts file and I made some changes to my MX records (not sure which one did the trick), now I see that I managed to receive a mail, but the mails that I send still aren't arriving...

---

### Post by thnewguy on 2014-04-05
By default Postfix will not allow you to send e-mails to other domains. You need to enable this in the main.cf file. Toward the bottom of the file there should be two options in /etc/postfix/main.cf which read

smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sender_restrictions = reject_unknown_sender_domain

Typically one of these options has too many restrictions and blocks outgoing e-mail.

---

### Post by Thee on 2014-04-05
I added those lines to the main.cf and restarted postfix but the problem persists.
I also noticed that I'm having problem authenticating user when I do:

```

$ telnet gameflask.com 143
Trying 109.90.3.188...
Connected to gameflask.com.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE AUTH=PLAIN] Dovecot ready.
a login thee@gameflask.com pass
a NO [AUTHENTICATIONFAILED] Authentication failed.

```

I don't know why is that...

---

### Post by Catalys on 2014-04-05
> **SeijiSensei said:**
> No, you definitely do not want to make /var/mail 777.  Then all users on the system can read everyone else's mail.


I forgot about that *rubs the back of his head* :oops:.

---

### Post by SeijiSensei on 2014-04-06
How about outbound blocking, a common ISP policy to prevent spambots?  Can you connect with this?
```
telnet gmail-smtp-in.l.google.com 25
```

---

### Post by Catalys on 2014-04-06
Perhaps you can set the relayhost to the SMTP server of your ISP.

---

### Post by Thee on 2014-04-06
@SeijiSensei
Yes I can.

```

$ telnet gmail-smtp-in.l.google.com 25
Trying 173.194.65.26...
Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP b48si20324551eew.37 - gsmtp

```

@Catalys
What would that do?

---

