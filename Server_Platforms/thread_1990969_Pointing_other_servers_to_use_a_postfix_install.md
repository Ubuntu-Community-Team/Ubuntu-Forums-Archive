---
title: "Pointing other servers to use a postfix install"
date: 2012-05-30
forum: Server Platforms
---

### Post by moorsey on 2012-05-30
All,

This may be obvious, or something I have overlooked, but can't find the info anywhere.

I setup a postfix install on one of my machines at the weekend, quite impressed that I managed it OK.  That night, I started getting emails from cron etc, so all good.

My question is, how do I get my other home servers to use that postfix install?  There must be somewhere where I can enter smtp address, username, password and port, but where is this set?

Also, can I change the email address cron sends FROM, I have read that the email address it sends to it the owner of the cron job unless otherwise specified on the cron job.

Thanks

Martin

---

### Post by SeijiSensei on 2012-05-30
> **moorsey said:**
> My question is, how do I get my other home servers to use that postfix install?  There must be somewhere where I can enter smtp address, username, password and port, but where is this set?

What kind of software is running on these servers?  Usually you'd just set a "relay" or "smart" host entry in the server software configuration that points to the Postfix box.  In Postfix, it's the "relayhost" directive; for sendmail, it's the value of the "DS" variable in sendmail.cf.

> Also, can I change the email address cron sends FROM, I have read that the email address it sends to it the owner of the cron job unless otherwise specified on the cron job.

I can't tell from reading this if you really want to change the FROM or the TO.  To have a cron script mail results to a different address than its owner, set the environment variable "MAILTO" at the top of the crontab:
```

MAILTO=me@example.com
0 0 * * * root /path/to/my/midnight_script >> /var/log/midnight

```
Remember that cron only mails output without a pre-defined designation like a log.  You're much better off piping the output to log files like this:
```

0 0 * * * root /path/to/my/midnight_script >> /var/log/midnight

```

I don't know of any way to change the FROM cron uses.  It's probably not too malleable for security reasons.

---

### Post by moorsey on 2012-05-30
Hi, thanks for the reply.

It would mainly be for cron emails, I run Zoneminder and Mythtv on their own boxes, so have various backups etc running.  One server runs Webmin and Mysql however, in Webmin, I have daily backups of the databases set (which I guess might just be cron anyway) and it has failed on occasion in the past.  Would be great to know when this happens!

The Webmin/Mysql server is on another network, so I would have to give it the hopto address I use on my network for the Postfix access.

I found something about "/etc/mailname", which holds the address to be used for mail, but the server would still have to authenticate with Postfix on the server, where does this info go?

On one of my local machines, I edited /etc/mailname and entered the name of the server running Postfix, setup a simple cron job with "MAILTO" set at the top as you describe, but nothing happens, I don't even get a failed message in the postfix logs.

So "relayhost" is a list of allowed computer names that can send mail through the Postfix server?  I guess adding in the name of the external machine should do the trick then..

Thanks for the help

---

### Post by SeijiSensei on 2012-05-30
> **moorsey said:**
> So "relayhost" is a list of allowed computer names that can send mail through the Postfix server?  I guess adding in the name of the external machine should do the trick then.

No, the relay host is a server upstream to which all mail is sent for further processing.  You'd need to configure the mail software *on the other servers* to use the server you just built as their common relay host.  If there isn't any "mail transfer agent" like Postfix or sendmail on the other servers, they can't send mail to you.  Each server that needs to send mail needs a copy of Postfix with the relayhost parameter pointing to your new server.

There's a different parameter in Postfix called "mynetworks" that controls which networks and hosts can relay mail through a machine.  On your central server, you'll need to set this to your local subnet address (e.g., 192.168.1.0/24); on the other machines you should leave it alone.

---

### Post by moorsey on 2012-06-01
ahhh, I think I now understand.

I (stupidly) thought that only one postfix install was required.

I will give this a try when I am back home next week, thanks for your help

---

### Post by LHammonds on 2012-06-01
I have a Zimbra mail server.  On all of my other servers, I install "sendemail" and whenever I need a script to send an email, I use the sendemail program.

Example:
```

MYDOMAIN="[COLOR="red"]mydomain.com[/COLOR]"
ADMINEMAIL="admin@${MYDOMAIN}"
REPORTEMAIL="[COLOR="red"]lhammonds[/COLOR]@${MYDOMAIN}"
SUBJECT="Howdy"
BODY="Hello world"
srv-mail="192.168.107.25"

sendemail -f "${ADMINEMAIL}" -t "${REPORTEMAIL}" -u "${SUBJECT}" -m "${BODY}" -s srv-mail:25 1>/dev/null 2>&1

```

---

