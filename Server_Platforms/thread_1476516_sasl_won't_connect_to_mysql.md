---
title: "sasl won't connect to mysql"
date: 2010-05-07
forum: Server Platforms
---

### Post by blake82 on 2010-05-07
I've been having a problem getting sasl working with a remote email client

I've set up the email system on my server using this guide:
[https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)

I can send and receive emails fine through squirrelmail, and I can receive emails in kmail, but I can't send them.

When sending through kmail, mail.log says:
May  7 19:14:59 ip-173-201-36-53 postfix/smtpd[5032]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: Bad file descriptor

which is strange because sasl is setup to connect to mysql, and all of the config files are telling it to do that.

Any idea why it refuses to connect to mysql? Is it because it's chrooted?

I've been trying to figure this out forever (though this is my first email server), and have had no luck.

Any suggestions are appreciated

Thanks,

Blake

---

### Post by blake82 on 2010-05-10
[bump] any ideas?

---

