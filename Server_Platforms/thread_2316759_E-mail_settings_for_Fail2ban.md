---
title: "E-mail settings for Fail2ban"
date: 2016-03-10
forum: Server Platforms
---

### Post by Grigoriy on 2016-03-10
Hello!
 I've just installed Fail2ban on Ubuntu 14.04. I don't need fail2ban  to send me e-mail alerts, but I did notice in jail.local file (which in  my case is a copy of jail.conf file) certain parameters that I don't  really understand. In ACTION ==> email action section there's:

```
mta = sendmail
```

I don't even have Sendmail SMTP server, I've got Postfix, actually.  Should I do anything with that setting, leave it alone (it's the  default) or even delete it?
On the same note, there's also another setting, concerning e-mail, which is:

```

destemail = root@localhost
```

I understand that I can change it to my real e-mail address, so fail2ban  would e-mail me. Though I don't really need it. What would be the best  thing to do in regard to this whole fail2ban e-mail policies?

P.S. Is the default for fail2ban NOT to send e-mail alerts? If so, maybe I should just stick to defaults?

Another thing is... I've read somewhere that if I use Postfix, then I should use this:

```
mta = mail
```

---

### Post by Seb_Boffen on 2016-03-10
Set to:
destemail =

---

### Post by TheFu on 2016-03-10
postfix is 100% sendmail compatible from the interface level. While I think you are crazy NOT to get fail2ban emails, that is your choice. OTOH, I suppose after getting 200 of those a day (like I did when ssh was running on port 22), it would get boring.

I'd leave it set to root@localhost and have an aliases setting that forwards that for all root emails to some other account that gets reviewed daily.

Don't forget that logwatch needs to send email too ... so if you are using that to watch all the logs, having it forward root emails somewhere else is smart.

---

### Post by Grigoriy on 2016-03-11
> **Seb_Boffen said:**
> Set to:
destemail =

That is IF I wish the mail not be send?

---

### Post by Grigoriy on 2016-03-11
> **TheFu said:**
> postfix is 100% sendmail compatible from the interface level.

Do you personally (or the case you know of) have Postfix running and you  still use the setting above and fail2ban successfully sends e-mail  alerts?

---

### Post by Seb_Boffen on 2016-03-11
Yes then there is no address for the email to be sent to.
If you have postfix configured to sent and receive emails and you fill an valid email address in at destemail = you will receive emails from fail2ban.

---

### Post by Grigoriy on 2016-03-12
> **Seb_Boffen said:**
> Yes then there is no address for the email to be sent to.
If you have postfix configured to sent and receive emails and you fill an valid email address in at destemail = you will receive emails from fail2ban.

That makes sense, but on the other hand, it might result in an error, saying that the e-mail address isn't a valid one. 
Regardless, by default fail2ban doesn't send out anything, so it's best to leave it at its default settings.
But thanks for your input anyway!

---

### Post by mastablasta on 2016-03-14
I get about 2-5 emails from fail2ban a day. during Chinese new year this usually increases to slightly over 10. still relatively low. it would be good if fail2ban would add all reports into one file to be sent per day. then again the idea is to immediately notify the admin.

I always go through the emails at least glance through them to see the method of attack. mostly they are scripted (admin user, then they try password). and I am not particularly worried about those (unless there would be a larger volume). but targeted attack would get me worried and I would likely take server offline before i figure out what to do. I set it to max 3 attempts then IP get's locked for a long time. something even have 1 attempt set. so you can get it wrong only one time. 

so far I has been mostly scripted attacks (trying to guess username and password) and I hope it stays that way. I would get a bit more alert if they figured out the user name. I use keys + password to access the server.

---

### Post by TheFu on 2016-03-14
I was seeing over 1,000 a day on one of my systems.  Server-side email filters rule!  I still wanted the individual emails, but don't look at them except about once a week, if there are other issues.  Wrote a tiny script to look through the refused connections many years ago - run that daily at 11:59pm which emails a summary.  Having a daily summary is nice.

Then installed **logwatch** and it does this AND more for me.  ssh-server, fail2ban, postfix in satellite config and logwatch are all installed and configured in my [1st 5 minutes on a server.]("http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server") Not that anyone cares.

I don't allow passwords for any remote connections, only on the console, which I can get to from a remote connection via ssh-keys through other systems.

---

