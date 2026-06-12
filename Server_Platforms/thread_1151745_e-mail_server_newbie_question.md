---
title: "e-mail server newbie question"
date: 2009-05-07
forum: Server Platforms
---

### Post by _sluimers_ on 2009-05-07
Okay, I have installed postfix, courier & sendmail 
and I'm able to use mutt to send and recieve mails.

Now I have the following questions

a) How do I set up my thunderbird mail program to receive these mails? 
b) I have installed squirrelmail as well, what is my username/password?
c) How do I add/edit and remove users/passwords, so far I can only send from [email]*myLinuxUserAccount@mydomainname*.com[/email]

---

### Post by _sluimers_ on 2009-05-16
Anyone?

I'm able to recieve mail in ~/Maildir


So I tried setting up an e-mail account in thunderbird like this:


Account name: [email]*myLinuxUserAccount@mydomainname.com[/email]*
Email address [email]*myLinuxUserAccount@mydomainname.com[/email]*

Server type:   IMAP mail server
Server name:   *mydomainname.com*
Email address: *myLinuxUserAccount*

It then asks for a password and I fill in my myLinuxUserAccount password.
That fails.

these are my settings:

/etc/mailname

```
*mydomainname.com*
```

I don't what else is important to know. :(

---

### Post by sahabcse on 2009-05-16
pls follow below url this may help

[http://sahabm.blogspot.com/2008/08/blog-post.html](http://sahabm.blogspot.com/2008/08/blog-post.html)

---

### Post by _sluimers_ on 2009-05-16
[EDIT]bad statement[/EDIT]

I can't reach *www . mydomainname . com/webmail*
because I put tomcat in front of apache.
And I don't know how to put tomcat in front of apache in root in such a way
that it only uses *.jsp and servlets.

---

### Post by windependence on 2009-05-16
If I had any idea what you are doing I may be able to help. What would you need Apache or Tomcat for e-mail?

Do you have your MX and A records set up with your domain registrar?

There are easier ways to do mail BTW.

-Tim

---

### Post by _sluimers_ on 2009-05-16
I have a home server running a website.
I have a contact form on that website.
I can send an e-mail to Maildir using that contact form.
Tomcat is running the website.
I have setup MX and A records with my domain registrar.

I thought it'd be nice to have both apache and tomcat running in case I want to use php files and I heard apache is faster with that, so I tried putting tomcat in front of apache and half-succeeded (php's are read by tomcat). [But that's another problem. ]("http://ubuntuforums.org/showthread.php?t=1149507")

I just want to read the e-mails any other way than using ssh to login to my server computer and vimming the Maildir.
That's my main problem. Creating a user database of mail accounts is one step ahead, unless it's required.

---

### Post by dwouters on 2009-05-16
> **_sluimers_ said:**
> I followed it... so? 

You know, it's a statement like this that may be the reason for the lack of responses. It gives off an air of "I asked a question, you gave a link, now give me the answer. Before you post a line of text like that, you may want to think before hitting the submit button. If I was sahabcse, I would ignore the rest of this thread and tell you to figure it out yourself. Good day!

---

### Post by _sluimers_ on 2009-05-16
> You know, it's a statement like this that may be the reason for the lack of responses. It gives off an air of "I asked a question, you gave a link, now give me the answer. Before you post a line of text like that, you may want to think before hitting the submit button. If I was sahabcse, I would ignore the rest of this thread and tell you to figure it out yourself. Good day!

Okay, you have a point there. Sorry. My apologies. I got a little peeved that I was given a link about how to set up a mail server, when my main question is how to reach it through thunderbird. And if those settings are correct?

Thank you for the link sahabcse. It is very helpful. 
By the way, is there some bug on your blog?
For some reason half the letters on your blog vanish on my browser on the right. 
It'd be also great to explain what the person is doing step by step.

---

### Post by llamaX on 2009-05-16
> **_sluimers_ said:**
>  a) How do I set up my thunderbird mail program to receive these mails?
 b) I have installed squirrelmail as well, what is my username/password?
 c) How do I add/edit and remove users/passwords, so far I can only send from *myLinuxUserAccount@mydomainname*.com

Depends!  I assume that you have Courier setup for IMAP already since you've mentioned trying to use it.  If not, you'll have to configure that first.

If it's a local user account, it will be the same way you log into the system.  No domain name appended after the username.  Changing passwords is easy as running passwd from that user's account.

If it's a virtual user account, it will depend upon how you have those setup.  You generally do append the domain name for these.

If you have not done so already, take a look at some of the [Postfix documentation]("http://www.postfix.org/docs.html") for some pointers.  The [Virtual Domain]("http://www.postfix.org/VIRTUAL_README.html") documentation is specially useful if you're trying to go that route.

---

### Post by _sluimers_ on 2009-05-16
Thanks guys, I finally figured out how to front tomcat to apache somewhat properly, so now I can reach the postfix admin. Everything is much clearer now.

---

### Post by _sluimers_ on 2009-05-18
Hmmm... I have installed ispconfig now and am able to add and delete users.
But when I try to login into one of them in squirrelmail I see this:

ERROR:
ERROR: Could not complete request.
Query: SELECT "INBOX"
Reason Given: Unable to open this mailbox.

and

ERROR: Connection dropped by IMAP server.
Query: SUBSCRIBE "INBOX.Sent"

telnet gives me this:

```

*me@mydomainname*:/usr/lib/sasl2$ telnet localhost 143
Trying ::1...
Connected to localhost.localdomain.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2008 Double Precision, Inc.  See COPYING for distribution information.
A01 LOGIN "*test@mydomainname.com*" "*password*"
A01 OK LOGIN Ok.
A02 SELECT INBOX
A02 NO Unable to open this mailbox.
A03 LOGOUT
* BYE Courier-IMAP server shutting down
A03 OK LOGOUT completed
Connection closed by foreign host.

```

Squirrelmail configtest gives me this:

```


SquirrelMail configtest

This script will try to check some aspects of your SquirrelMail configuration and point you to errors whereever it can find them. You need to go run conf.pl in the config/ directory first before you run this script.

SquirrelMail version:	1.4.15
Config file version:	1.4.0
Config file last modified:	17 May 2009 22:30:29
Checking PHP configuration...
    PHP version 5.2.6-3ubuntu4.1 OK.
    display_errors: 1
    error_reporting: 6135
    variables_order OK: EGPCS.
    PHP extensions OK. Dynamic loading is disabled.
Checking paths...
    Data dir OK.
    Attachment dir OK.
    Plugins OK.
    Themes OK.
    Default language OK.
    Base URL detected as: http://192.168.1.38/webmail/src (location base autodetected)
Checking outgoing mail service....
    SMTP server OK (220 mydomanname.com ESMTP Postfix (Ubuntu))
Checking IMAP service....
    IMAP server ready (* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2008 Double Precision, Inc. See COPYING for distribution information.)
    Capabilities: * CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS
Checking internationalization (i18n) settings...
     gettext - Gettext functions are available. On some systems you must have appropriate system locales compiled.
     mbstring - Mbstring functions are available.
     recode - Recode functions are unavailable.
     iconv - Iconv functions are available.
     timezone - Webmail users can change their time zone settings.
Checking database functions...
    not using database functionality.

Congratulations, your SquirrelMail setup looks fine to me!


```

Hmmm.... my mail.warn gives me this:

```

May 18 11:13:38 *mydomainname* postfix/trivial-rewrite[23538]: warning: do not list domain *mydomainname.com* in BOTH mydestination and virtual_mailbox_domains

```

---

### Post by _sluimers_ on 2009-05-18
I solved the squirrelmail problem with creating directories like this:

maildirmake /var/vmail/*mydomainname.com/user1*

I can finally see the inbox in squirrelmail and send messages from there.
I managed to log in with thunderbird with thunderbird as well with a virtual user.
I'm still clueless as why I'm not allowed to log in with my linux account name.

Just in case other clueless newbies might lurk in here and wonder:

```

Account name: user1@mydomainname.com
Email address user1@mydomainname.com

Server type: IMAP mail server
Server name: mydomainname.com
Email address: user1@mydomainname.com

```

Now my only problem remains that all my receiving e-mails seem to end up in /var/mail/vmail and not in /var/vmail/user or better yet /home/vmail/user.

---

### Post by _sluimers_ on 2009-06-03
Solved it. Redid the whole tutorial.  I should never have made the vmail user manually.

---

