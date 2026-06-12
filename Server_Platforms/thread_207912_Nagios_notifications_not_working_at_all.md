---
title: "Nagios notifications not working at all"
date: 2006-07-02
forum: Server Platforms
---

### Post by djcronos on 2006-07-02
Hey all,

I know this isn't on the Nagios forum, but I've already asked there and no one has answered back.  I figured people who have set up Nagios properly could help shed some light on this problem I am having.

I have compiled Nagios from source and set everything up as described in the Nagios documentation, but for some reason Nagios will not send out any type of mail notification.

I went to the Nagios forum and people who have had similar problems were told to issue the following command:

```
/usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\n\nService: $SERVICEDESC$\nHost: $HOSTALIAS$\nAddress: $HOSTADDRESS$\nState: $SERVICESTATE$\n\nDate/Time: $LONGDATETIME$\n\nAdditional Info:\n\n$SERVICEOUTPUT$" | /bin/mail -s "** $NOTIFICATIONTYPE$ alert - $HOSTALIAS$/$SERVICEDESC$ is $SERVICESTATE$ **" blah@email.com 
```

And it says:
```

bash: /bin/mail: No such file or directory 

```

One thing to note is that I installed ISPConfig via HowToForge's Perfect Setup instructions.

What am I missing?  Thanks in advance!

---

### Post by faultyCPU on 2006-07-03
change to /usr/bin/mail or what o/p you get from `which mail`

mail is in /usr/bin and nagios looking at /bin

---

### Post by djcronos on 2006-07-06
Okay there's my problem.  I thought by installing ISPConfig that Postfix would take care of that - guess I was wrong.

What should I install then to get mail to work?  And will that interfere with Postfix?

Thanks again.

---

### Post by Randomskk on 2006-07-06
If it's failing because of the /bin.mail thing, try this:
sudo ln /usr/bin/mail /bin/mail

---

### Post by djcronos on 2006-07-06
Actually, I don't even have mail in /usr/bin - what package should I install to get the mail command?

Keep in mind I have Postfix installed...kinda odd that doesn't create a /usr/bin/mail command...

---

### Post by djcronos on 2006-07-07
Okay I did an install of mailx and created a symlink from /usr/bin/mailx to /bin/mail - I can now issue mail commands, but something still isn't working.  I'll update this tomorrow when I have more time.

Thanks for the help everyone.

---

### Post by djcronos on 2006-07-07
Okay I just ran that command again, and it emails me, and I get the following email:

```

***** Nagios *****

Notification Type: $

Service: $
Host: $
Address: $
State: $

Date/Time: $

Additional Info:

$

```

Is that correct?  If so, then why am I not getting any emails?  What should I look at?

---

### Post by geep on 2007-01-24
can you show use your services.cfg / contact.cfg

---

### Post by djcronos on 2007-01-24
Hello,

This post is rather old.  Since then I've followed this tutorial and was able to get everything working:

[http://ubuntuforums.org/showthread.php?t=223498](http://ubuntuforums.org/showthread.php?t=223498)

Hope this helps others who are in search.

---

### Post by joeyoung25 on 2007-06-15
I see that no one has posted to this forum for a while but i am having some troubles getting nagios to send mail out. In the web UI if i click on notifications there are notifications in there the only problem is that im not receiving the email that it says its sending. I have postfix installed and sendmail also because ive been looking for the problem and each forum tells me i should do something different. Someone please help me. all i want is for nagios to email me when a host is down

---

