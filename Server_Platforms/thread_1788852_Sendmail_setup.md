---
title: "Sendmail setup"
date: 2011-06-23
forum: Server Platforms
---

### Post by tsst1 on 2011-06-23
Hello,
I just moved from CentOS to Ubuntu and met the problems with Sendmail configuration (I have several domain on one server):
1. when sending email, it doesn't matter which domain is defined, sendmail always changes it to "name@host.mydomain.com";
2. I defined virtusers to mail outside the server but it does not work.

Please advice me, what to do to fix it.

---

### Post by SeijiSensei on 2011-06-23
> **tsst1 said:**
> Hello,
I just moved from CentOS to Ubuntu and met the problems with Sendmail configuration (I have several domain on one server):
1. when sending email, it doesn't matter which domain is defined, sendmail always changes it to "name@host.mydomain.com";
2. I defined virtusers to mail outside the server but it does not work.

Please advice me, what to do to fix it.

Changing the outbound address requires the use of a "genericstable" in sendmail.  This maps from local user names to the SMTP envelope sender addresses you wish to use.  Something like this:

```
apache             webmaster@example.com
```

Now mail sent by the apache user will be rewritten to use the SMTP envelope sender [email]webmaster@example.com[/email].

You'll need to check whether the genericstable feature is enabled by default in Ubuntu.  (I use CentOS for a mail server, so I can't help you there.) You'll also need a "generics-domains" file that list the domains for which address rewriting is required.  There are lots of documents out there about this; [this one]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch21_:_Configuring_Linux_Mail_Servers#Using_Sendmail_to_Change_the_Sender.27s_Email_Address") seems like a good starting place.

---

### Post by tsst1 on 2011-07-11
well, actually i know that.
But there is different functionality required. i'm logged in with user test and one time i need to show email as [email]info@mydomain.net[/email], [email]webmaster@mydomain.net[/email], another time  [email]info@nextdomain.net[/email], [email]webmaster@nextdomain.net[/email] and so on. I mean i need to use various users, but if i'm sending from localhost, then system should always allow to use that FROM: address.

One more thing. some emails has to be forwarded to external (gmail) email. i added virtusers but they don't work. what can be wrong?

---

### Post by SeijiSensei on 2011-07-11
What do you mean by "sending from localhost?"  Are you using a client or a command-line mail program?

Can you not use sendmail itself using the -f switch?  Certainly root can run:

```
sendmail -f info@somedomain.net someone@example.com < file-with-msg
```

If you're not root, then you must be a "trusted" user.  Is there an "Ft" directive in sendmail.cf?  That file needs to have the user IDs of every user who is permitted to change the envelope From.  (The From: in the message text itself is totally forgeable, but not the envelope From.)  Otherwise you can create your own list with multiple "Tusername" statements.

As for forwarding to GMail, are you talking about forwarding incoming messages?  You can do this with an alias or with procmail.  In /etc/aliases, you can have:

```
joe:     \joe,joe@gmail.com
```

which delivers both to joe's local mailbox and forwards to his GMail account.  Or you can add a "recipe" like this to joe's .procmailrc:

```
:0c
! joe@gmail.com

```

You may need to install procmail separately; I'm not sure it comes standard with Ubuntu Server.

---

### Post by tsst1 on 2011-07-11
I'm using web based e.mail software, so it's localhost.
I have my trusted-users, but when i'm sending with other domain in FROM field, it logs an error:
Authentication-Warning: onedomain.com: myuser set sender to [email]sender@otherdomain.com[/email] using -f[FONT=Arial]
but this myuser is defined in that file and Ft exists in [/FONT]sendmail.cf (does user ID=username?)

as of forwarding, yes i'm talking about incoming messages. and the problem is that i have more domains, some of them are hosted as charity.
so in centos i used virtusers to forward these emails and now it doesn't work.
i need like [email]info@charitydomain.com[/email] forward to gmail, but it is sent to local info emails, set in aliases file.

basically i understand what should work and how, because i defined in centos these confs, but it seems that new sendmail version is more "secure" and works differently. and i cannot understand where is the bottleneck :(

---

### Post by SeijiSensei on 2011-07-11
> **tsst1 said:**
> I'm using web based e.mail software, so it's localhost.
I have my trusted-users, but when i'm sending with other domain in FROM field, it logs an error:
Authentication-Warning: onedomain.com: myuser set sender to [email]sender@otherdomain.com[/email] using -f[FONT=Arial]
but this myuser is defined in that file and Ft exists in [/FONT]sendmail.cf (does user ID=username?)

I don't know.  As I said, I use CentOS 5.5 for all these tasks.  Is there some significant reason why you had to move to Ubuntu server?  Remember that sendmail isn't the standard MTA in Ubuntu, Postfix is.

> as of forwarding, yes i'm talking about incoming messages. and the problem is that i have more domains, some of them are hosted as charity. so in centos i used virtusers to forward these emails and now it doesn't work. i need like [email]info@charitydomain.com[/email] forward to gmail, but it is sent to local info emails, set in aliases file.

Use procmail.  Create an info user, if one doesn't exist already, and then put this "recipe" into /home/info/.procmailrc:

```

:0
^TO.*charitydomain1.com
! someone@charity1.com

:0
^TO.*charitydomain2.com
! someone@charity2.com

etc.

```

If you'd like to keep an archive of all these messages in user info's inbox, replace :0 with :0c above.  This makes a copy of the message and forwards the copy.

---

### Post by tsst1 on 2011-07-12
Thank's for the answer.
I read a little bit of sendmail docs and it seems You have not the latest version of it.
It looks like Sendmail has been "improved" to be more secure and implemented MSP. Check it out.

I think the code of sendmail is the same in all systems it is always matter of configuration. I tried to configure Postfix before, but it was headache for me.

And i'm using ubuntu because i have it on my pc installed and i am satisfied with it and more or less know it's behaviour and it look for me easier to manage, etc. as of centos, previously i hosted domains on centos4. it had bad support.

---

### Post by tsst1 on 2011-07-14
OK. additionally I added some log excerpts. Maybe it should clarify:
Jul 14 10:59:16 server sendmail[19537]: p6E7xGt3019537: from=user@domain-a.com, size=491, class=0, nrcpts=1, msgid=<1310630356.19535@domain-a.com>, relay=loggedinuser@localhost 
Jul 14 10:59:17 server sendmail[19538]: STARTTLS=server, relay=localhost.localdomain [127.0.0.1], version=TLSv1/SSLv3, verify=NOT, cipher=DHE-RSA-AES256-SHA, bits=256/256 
Jul 14 10:59:17 server sendmail[19537]: STARTTLS=client, relay=[127.0.0.1], version=TLSv1/SSLv3, verify=FAIL, cipher=DHE-RSA-AES256-SHA, bits=256/256 
Jul 14 10:59:17 server sendmail[19538]: p6E7xG06019538: from=<user@domain-b.com>, size=607, class=0, nrcpts=1, msgid=<1310630356.19535@domain-a.com>, proto=ESMTP, daemon=MTA, relay=localhost.localdomain [127.0.0.1] 
Jul 14 10:59:18 server sendmail[19537]: p6E7xGt3019537: to=recepient@domain-c.com, ctladdr=user@domain-a.com (1005/100), delay=00:00:02, xdelay=00:00:02, mailer=relay, pri=30491, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (p6E7xG06019538 Message accepted for delivery) 
Jul 14 10:59:18 server sendmail[19540]: STARTTLS=client, relay=smtp3.domain-c.com., version=TLSv1/SSLv3, verify=FAIL, cipher=DHE-RSA-AES256-SHA, bits=256/256 
Jul 14 10:59:18 server sendmail[19540]: p6E7xG06019538: to=<recepient@domain-c.com>, ctladdr=<user@domain-b.com> (1005/100), delay=00:00:01, xdelay=00:00:00, mailer=esmtp, pri=120607, relay=smtp3.domain-c.com. [93.40.95.67], dsn=2.0.0, stat=Sent (Ok: queued as 2117414003) [FONT=Verdana]
there are too much for one message and i don't understand where is the bottleneck? i understand that it's my knowledge, but anyway i need to find the place to change.
[/FONT]

---

