---
title: "MTA problems; root gets no mail"
date: 2010-02-10
forum: Server Platforms
---

### Post by narnie on 2010-02-10
Hello,

I am afraid that I goofed up my mailing system.

I have an Ubuntu 9.10 system

```
$ uname -smor
Linux 2.6.31-14-generic x86_64 GNU/Linux

```
I am wanting to receive cron job mails. I noticed that cron jobs were trying to send mail to sendmail. I had installed ssmtp so I could send mail using gmail from the command line which also installed bsd-mailx. OOPS! I think this really messed up configurations. After further research, I purged ssmtp and reinstalled bsd-mailx which has postfix as a dependency.

Now, root doesn't get mail (via mail command), but root can send mail to users ok. Users can send and receive mail from user to user.

I think a side effect of this problem is that it messes up cron, as this is the only significant difference between this and other systems I have and they don't have this problem. Now cron processes hangs (the cron job itself completes) and becomes a zombie. Only restarting the cron service fixes it.

Any ideas how to resolve this short of restalling (which I'd rather not do)?

Thanks,
Narnie

---

### Post by gmargo on 2010-02-10
Do you have an alias for root in **/etc/aliases**?

Try tracking what happens with the -v option on sendmail:

```

echo "Howdy" | sendmail -v root@localhost

```

---

### Post by narnie on 2010-02-10
> **gmargo said:**
> Do you have an alias for root in **/etc/aliases**?

Try tracking what happens with the -v option on sendmail:

```

echo "Howdy" | sendmail -v root@localhost

```

Very interesting things happen.
```

$ cat /etc/aliases
# See man 5 aliases for format
postmaster:    root
```

```
$ echo "Howdy" | sendmail -v root@localhost
Mail Delivery Status Report will be mailed to <woodnt>.
```

I think we are on to something here.

No aliases for root to woodnt, but sendmail is sending to woodnt.

BTW, tried sending mail to root from another user not woodnt and neither woodnt nor root got the mail. See this for the results:

```
woodnt@toshiba-laptop ~/.xchat2/downloads $ su luke
Password: 
luke@toshiba-laptop /home/woodnt/.xchat2/downloads $ mail root
Subject: Hello
root
Cc: 
luke@toshiba-laptop /home/woodnt/.xchat2/downloads $ exit
exit
woodnt@toshiba-laptop ~/.xchat2/downloads $ mail
No mail for woodnt
woodnt@toshiba-laptop ~/.xchat2/downloads $ sudo su
toshiba-laptop downloads # mail
No mail for root
toshiba-laptop downloads # exit
exit
```

---

### Post by gmargo on 2010-02-10
It certainly isn't very friendly of **postfix** to email debugging info when you're trying to debug the email system :confused:.

However, no need to change the MTA yet, try the advice on this page: [SIZE=2][http://www.postfix.org/DEBUG_README.html](http://www.postfix.org/DEBUG_README.html) under "[/SIZE][SIZE=2]Making Postfix daemon programs more verbose" and add "-v" options to the daemons.  Also look in **/var/mail/** to see where that darn mail went.  Also check **/var/log/postfix/*.log** (or **/var/log/postfix.log**?)  Are the permissions on **/var/mail** correct?
[/SIZE]

---

### Post by narnie on 2010-02-10
> **gmargo said:**
> It certainly isn't very friendly of **postfix** to email debugging info when you're trying to debug the email system :confused:.

However, no need to change the MTA yet, try the advice on this page: [SIZE=2][http://www.postfix.org/DEBUG_README.html](http://www.postfix.org/DEBUG_README.html) under "[/SIZE][SIZE=2]Making Postfix daemon programs more verbose" and add "-v" options to the daemons.  Also look in **/var/mail/** to see where that darn mail went.  Also check **/var/log/postfix/*.log** (or **/var/log/postfix.log**?)  Are the permissions on **/var/mail** correct?
[/SIZE]

Oh my goodness! I'd looked in /var/mail all the users there except nobody, because that account meant nothing to me. I checked it, and here is all the mail going to root.

Wow, where do I look to start figuring that one out? I'll research that postfix site asap. 

Thanks,
Narnie!

---

### Post by narnie on 2010-02-10
> **narnie said:**
> Oh my goodness! I'd looked in /var/mail all the users there except nobody, because that account meant nothing to me. I checked it, and here is all the mail going to root.

Wow, where do I look to start figuring that one out? I'll research that postfix site asap. 

Thanks,
Narnie!

OK. Here is the deal. After researching, postfix is built around security. Hence, the author doesn't like the fact one would log in as root to view root mail. Thus, it won't run anything as root and won't send root mail. It seems to default to sending the mail to user "nobody." One must edit /etc/aliases and add a line like this:

```
root:   NON_PRIVALAGED_USER_NAME
```

where NON_PRIVALAGED_USER_NAME is whatever username on the system the admin wants to receive root mail.

the command:

```
newaliases
```

must be run to make these setting take effect.

No "fix" for this. This is the expected behavior.

---

