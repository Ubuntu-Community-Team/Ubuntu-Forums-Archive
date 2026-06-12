---
title: "Emails server issues, sending ok, recieving = what email?"
date: 2007-07-21
forum: Server Platforms
---

### Post by henryhynd on 2007-07-21
Ok... so, heres the issue:

I built a pretty basic email server from the following howto:
[https://help.ubuntu.com/community/MailServer]("https://help.ubuntu.com/community/MailServer")

Just used all the basic options for postfix, clamav, spamassassin, courier and squirrel mail.

After some odd issues with apache and php i've got everything working (ie passing the tests in the above howto, mostly telneting the smtp server, courier etc). The problem is the I'm not recieving any emails! it's not that i'm haven't sent myself enough test emails, they just don't show.

I can send emails fine and according to /var/log/mail.info the server is recieving, scanning and passing the emails to my inbox... they just never appear.

below is an extract from mail.info illustrating the above(with server/domain names substituted for generalised names):

> Jul 21 19:04:41 localhost postfix/cleanup[5677]: EFD4020904: message-id=<225E49B5A3A6034BB974354E7D1991DA31CC40@server.externalemailserver.com.au>
Jul 21 19:04:41 localhost postfix/qmgr[4943]: EFD4020904: from=<henry.hynd@externalemailaddress.com.au>, size=4173, nrcpt=1 (queue active)
Jul 21 19:04:41 localhost postfix/smtpd[5682]: disconnect from localhost[127.0.0.1]
Jul 21 19:04:41 localhost amavis[4497]: (04497-01) Passed CLEAN, [150.101.2.67] [150.101.2.67] <henry.hynd@externalemailaddress.com.au> -> <henry@mydomain.com>, Message-ID: <225E49B5A3A6034BB974354E7D1991DA31CC40@server.externalemailserver.com.au>, mail_id: L-ybDKyt0CuZ, Hits: -1.439, 8670 ms
Jul 21 19:04:41 localhost postfix/smtp[5678]: 93AD02080F: to=<henry@mydomain.com>, relay=127.0.0.1[127.0.0.1], delay=9, status=sent (250 2.6.0 Ok, id=04497-01, from MTA([127.0.0.1]:10025): 250 Ok: queued as EFD4020904)
Jul 21 19:04:41 localhost postfix/qmgr[4943]: 93AD02080F: removed
Jul 21 19:04:41 localhost postfix/local[5700]: EFD4020904: to=<henry@mydomain.com>, relay=local, delay=1, status=sent (delivered to command: procmail -a "$EXTENSION")
Jul 21 19:04:41 localhost postfix/qmgr[4943]: EFD4020904: removed



if i've left anything out pls let me know and i'll fill you in, thanks for the help ppl!

Henry

---

### Post by Mr. C. on 2007-07-21
Where do you want your mail to appear ?  How do you want to access it ?

You've followed a guide, but that guide tells you nothing about how to solve these problems.

Your configuration is using procmail to deliver email.  You'll have to look at your procmailrc (both /etc/procmailrc and ~/.procmailrc) to see where procmail is placing the email delivered by postfix.

MrC

---

### Post by henryhynd on 2007-07-22
I would like to access by both pop3 and imap using email clients or the web interface (squirrelmail).

I thought the guide implied that the mail would be delivered to the 
"Maildir" folders set up in each users folder. is this not the case?

I would check out procmailrc but there isn't in /etc/ no mention of a procmail folder either. apt-get thinks it is installed so i don't see why not.


cheers,
henry

---

### Post by kvonb on 2007-07-22
From what I understand pop3 and imap are sort of opposites, you don't need pop3, as most email clients nowadays handle imap.

IMAP is superior if in no other way than it's better if you are going to use a webmail service as it leaves all the emails on the server by default, which means that they are always "syncronised".

I use dovecot instead of courier and also squirrelmail (from the tarball on their site as it has some nicer features), it's very stable.

Don't forget you will have to create all the Maildir folders as well for each account, I simply created the Maildir folder in /etc/skel/ (as root) so it creates it automatically each time I add a new user.

You will also have to add your mail server's address in /etc/hosts (on your DNS server) if your internal clients are trying to access it by name not IP.

Also don't forget to setup your firewall to allow it to fetch mail from the net.  And of course you will need a domain name pointed to your mail server, and your ISP has to allow them through, as some clock mail transport.

> **henryhynd said:**
> I would like to access by both pop3 and imap using email clients or the web interface (squirrelmail).

I thought the guide implied that the mail would be delivered to the 
"Maildir" folders set up in each users folder. is this not the case?

I would check out procmailrc but there isn't in /etc/ no mention of a procmail folder either. apt-get thinks it is installed so i don't see why not.


cheers,
henry

PS.  Here's some more good links on setting up email servers:

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/email-services.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/email-services.html)
[http://ubuntuforums.org/showthread.php?t=185913&highlight=mail+server](http://ubuntuforums.org/showthread.php?t=185913&highlight=mail+server)

Best of luck, Kev :)

---

### Post by henryhynd on 2007-07-22
yeh i creeated the maildir folders in skel also.. 

I have the domain and firewall settings all working fine as you can see in the mail.info extract in my first post my server is actually recieving the mail, it just gets lost once it gets sent to my maildir

> You will also have to add your mail server's address in /etc/hosts (on your DNS server) if your internal clients are trying to access it by name not IP.
 and i';ve sorted this on my windows server's dns server setup. all computers on internal network look at windows server for dns, so when i connect to my external domain, it just goes straight to my linux box... took me like 1yr to figure out how to do that, all of 30 secs to do!


cheers for your input
henry

---

### Post by henryhynd on 2007-07-26
No one has responded for a while. I've been looking into it for that time.

I think its to do with procmail.

could anyone shed some light on setting up procmail?

cheers,
Henry

---

### Post by Mr. C. on 2007-07-26
henryhynd,

The "guide" you refer to is really many guides; you've given no indication which one you followed, or why you made the choices you did.  Therefore, we can't know what you've done, or why you've done it.

Search for Procmail at this link:

[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

If you don't know why you configured procmail, and don't know how its used, you probably don't need it.

MrC

---

### Post by HermanAB on 2007-07-26
Hmm, I suggest that you deliver directly to /var/spool/mail without using procmail.  

Edit /etc/postfix/main.cf like this:
mail_spool_directory = /var/spool/mail

and comment out this:
# mailbox_command = /usr/bin/procmail -Y -a $DOMAIN -d $USER

Then reload postfix with:
postfix reload

Now send yourself a message:
mail -s test username@localhost
.

Look for the message in /var/spool/mail:
ls -al /var/spool/mail
mutt -f /var/spool/mail/username

If you really want to use procmail, then you have to go to the procmail web site and start reading.  Procmail is tricky to set up.  If and only if you got the above going without procmail and you still want to use procmail, then I can make you an example configuration file.

Cheers,

Herman

---

### Post by henryhynd on 2007-07-26
cheers for the quick reply Mr C, 

Once you get started on that HOWTO, it pretty much walks you through a single track with few options, I setup the following as per the guides in the howto:

MTA = postfix,
Mail filtering by the 'PostfixAmivisNew' link,
MDA = Courier (just all the bog standard settings as per the courier page
and Webmail = Squirrelmail

All is working, except that email isn't being delivered to inboxes. if you read the mail.info in my first post, email comes in and (being a noob) from what i can figure is that is being scanned for viruses and spam then is transfered to what it thinks is my mail box.

> Jul 21 19:04:41 localhost postfix/local[5700]: EFD4020904: to=<henry@mydomain.com>, relay=local, delay=1, status=sent (delivered to command: procmail -a "$EXTENSION")

All the configuration was exactly as the guide described for all the basic options., obviously with the correct server settings etc.

let me know if you need anymore additional info and i'll try to get it to you asap

thanks for the help

---

### Post by Mr. C. on 2007-07-26
We're covering old ground that's already in the post; diagnosis requires information, not stories.

I'm really not interested in trying to debug someone else's instructions, or missteps in following them.  Consider that either of the following *must* be true: a) the instructions are wrong, or b) they are correct, and you did not follow the directions.   So saying you followed the instructions as per guide when your setup does not work doesn't help us.

You have to locate your procmail recipe file.  What do you find with? :

```
locate procmail
```

Do any of those look like procmail rc file I asked about a while back?

Herman - the OP is using courier, therefore Maildir, not mbox.  There is no reason to have mail in the spool directory.

MrC

---

### Post by henryhynd on 2007-07-26
Herman,

Cheers for the input, it helped me find where my mail is currently going!

so yeh, the email server actually works, which is great. 

but now to fix procmail to deliver to my maildir.

thanks again,


Mr C,

```
locate procmail
```

turned up some example procmailrc files and a quickstart guide (among other things).

I'll do some reading and try a few things and let you know how I get on. 

cheers for your help,

Henry

---

### Post by henryhynd on 2007-07-26
problem solved.

Thanks to kvonb!

I hadn't seen the second half of you post with the links to other setups in it, followed one, searched for procmail and it was saying not to use it. So following this instructions as follows:

Instruct Postfix to use Maildirs instead of Mboxes: 

```

 sudo postconf -e "home_mailbox = Maildir/"

```

Ensure Procmail isn't used: (if the step was taken during dpkg-reconfigure, by mistake) 

```

sudo postconf -e "mailbox_command = "

```

Restart Postfix to make changes effect. 

```

sudo  /etc/init.d/postfix restart

```

Test your setup again

I managed to recieve for the first time. Thanks to Mr C (who actually told me not use procmail at one point too) for all your help and anyone else who gave some input.

cheers,
Henry

---

