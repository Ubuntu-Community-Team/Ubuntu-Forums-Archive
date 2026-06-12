---
title: "Send system logs to another user"
date: 2010-12-03
forum: Server Platforms
---

### Post by latebeat on 2010-12-03
Hello all,

I have a question regarding an issue and I don't know where to start so any direction would be greatly appreciated. 

We have a backup program that works with HP's ultrium tapes that whenever it's failing it's sending an error to the root's system logs. Now if I run mutt as root I can see the system logs and it's very easy to pinpoint any backup error messages. 
Is there any way to copy all these system messages to another user as well so that someone with no root access could run mutt as well and check for these logs daily?

any help is greatly appreciated...


anestis

---

### Post by arrrghhh on 2010-12-03
Just setup a cron job that copies the log & chmod's it to something that can be read by a normal user.

I say cp it because you don't want to change permissions on the logfile directly.

---

### Post by latebeat on 2010-12-03
> **arrrghhh said:**
> Just setup a cron job that copies the log & chmod's it to something that can be read by a normal user.

I say cp it because you don't want to change permissions on the logfile directly.



i was thinking maybe there was a way to be able to setup the system to send these system logs to both root and another account as well. 
But I guess that's the simplest and easiest way..

thanks a lot!

---

### Post by arrrghhh on 2010-12-03
> **latebeat said:**
> i was thinking maybe there was a way to be able to setup the system to send these system logs to both root and another account as well. 
But I guess that's the simplest and easiest way..

thanks a lot!

Ha, sorry I'm not aware of one.  That's what cron jobs are for IMHO, those pesky weird issues that you feel there should be a feature for... but there isn't ;)

If you feel this thread has been solved, please use the "Thread Tools" drop down menu to mark it [SOLVED]!

---

### Post by SeijiSensei on 2010-12-04
It sounds like all you want to do is send a second copy of the messages sent to root to another mailbox.

If so, you can try one of two approaches.  One is to set up an email alias for root that includes both the root account and the other address.  On systems that use /etc/aliases, that would mean adding:

```
root:     \root,someone@example.com
```

The "\root" entry tells the mailer to deliver the message to root's mailbox as well as sending another copy to [email]someone@example.com[/email].  On sendmail-based systems, you'd then run (as root) the command "newaliases" to update the alias database.

Another approach creates the copy at delivery.  As long as the mail system uses procmail as its "delivery agent," this method will work as well.  (I'm pretty sure Ubuntu uses procmail.)

Create the file /root/.procmailrc and enter the following:

```

:0c
! someone@example.com

```

This makes a copy of the message and sends it to the specified address.  The original copy is delivered to root's mailbox.

---

