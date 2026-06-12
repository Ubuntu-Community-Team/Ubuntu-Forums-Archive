---
title: "Fail2ban 2000 bans a day."
date: 2015-12-04
forum: Security
---

### Post by christopher41 on 2015-12-04
Hi guys, 

At our company we have a postfix server since two years back or so, it works really good. I am not a sysadmin but i have some linux knowledge to do easier tasks.
We are running postfix version 2.9.6 @ Ubuntu 12.04.5 LTS.

Recently the amount of fail2ban bans changed from 100 to 1500-2000 bans a day. 
Is there something more we could do to tweek our fail2ban config? Or somthing else that we could to to not make us a target?

EDIT: Most attacks are agains postfix-jail

[DEFAULT]
bantime  = 3600
maxretry = 3

[postfix]
enabled  = true
port     = smtp,ssmtp,submission
filter   = postfix
logpath  = /var/log/mail.log


[sasl]
enabled  = true
port     = smtp,ssmtp,imap2,imap3,imaps,pop3,pop3s
filter   = sasl
logpath  = /var/log/mail.log
maxretry = 3

[couriersmtp]
[courierauth]
Active = false

---

### Post by coldraven on 2015-12-04
Although it's a bit ( read: a lot!) over my head I was reading this thread a few days ago. Maybe you can glean some info from it.I gather that the intention is to create a bad guy list that is permanent.
[http://ubuntuforums.org/showthread.php?t=2304442&highlight=fail2ban](http://ubuntuforums.org/showthread.php?t=2304442&highlight=fail2ban)

---

### Post by Habitual on 2015-12-04
coldraven: My ears 'itched' :)

IMO, the bantime is too low
What is "findtime" set to?
I set my bantime to 1 year using
```
bantime  = 31556926 ; 1 year in seconds
```
Scan /var/log/fail2ban.log for "INFO [<jail>] Ban <ip>" messages.
as you may need to "tune" another jail.
perhaps it is unbanning too rapidly... Could be a couple of things.

Subscribed with interest...

---

### Post by christopher41 on 2015-12-07
> **coldraven said:**
> Although it's a bit ( read: a lot!) over my head I was reading this thread a few days ago. Maybe you can glean some info from it.I gather that the intention is to create a bad guy list that is permanent.
[http://ubuntuforums.org/showthread.php?t=2304442&highlight=fail2ban](http://ubuntuforums.org/showthread.php?t=2304442&highlight=fail2ban)

I dont know if it is necessary to create a permanent blocklist if we almost never reboot the server? 

> **Habitual said:**
> coldraven: My ears 'itched' :)

IMO, the bantime is too low
What is "findtime" set to?
I set my bantime to 1 year using
```
bantime  = 31556926 ; 1 year in seconds
```
Scan /var/log/fail2ban.log for "INFO [<jail>] Ban <ip>" messages.
as you may need to "tune" another jail.
perhaps it is unbanning too rapidly... Could be a couple of things.

Subscribed with interest...

I changed **bantime** to 1 year. Maybe creates more work if real customers IP get banned.
**findtime** - I could not find this in my configuration... I added this with default value 600, is that ok?

I dont really know what I should look for in the fail2ban.log, it looks like the banned IPs are not used for attacks more than 1-2 times in the latest logfile.

---

### Post by Habitual on 2015-12-07
> **christopher41 said:**
> I dont know if it is necessary to create a permanent blocklist if we almost never reboot the server? 

I changed **bantime** to 1 year. Maybe creates more work if real customers IP get banned.
**findtime** - I could not find this in my configuration... I added this with default value 600, is that ok?

I dont really know what I should look for in the fail2ban.log, it looks like the banned IPs are not used for attacks more than 1-2 times in the latest logfile.

findtime = 600 is good/default
Permanent block is additional and not necessary at all.
[recidive] jail is pretty close to the same thing.

Here's a real example of what to look for in /var/log/fail2ban.log
```
fail2ban.actions: WARNING [c9badbots] Ban 193.189.143.159
...
fail2ban.actions: WARNING [c9badbots] Unban 193.189.143.159
```
c9badbots is my custom [jail], or one of them.
excessive banning and unbanning.

---

### Post by christopher41 on 2015-12-07
[recidive] seems interesting, found one blogpost about it here: [http://www.dghost.com/techno/internet/the-power-of-fail2ban](http://www.dghost.com/techno/internet/the-power-of-fail2ban) 

postfix is the most used jail, probable 99% get caught there.
Sometimes I see "**already banned**" but most of the lines is just the usual Ban <IP> and Unban <IP>

> 07:10 ... fail2ban.actions: WARNING [postfix] Ban 113.190.149.4
07:10 ... fail2ban.actions: WARNING [postfix] 113.190.149.4 **already banned**
08:10 ... fail2ban.actions: WARNING [postfix] Unban 113.190.149.4


---

### Post by Habitual on 2015-12-07
Unbanning in 600 seconds...

With such I high bantime, I don't think recidive is a worthwhile feature to enable.
With defaults, maybe, quite possibly a worthy feature.
I utilize over-the-top values for what I consider high-value targets and I monitor
my logs.
My hosts have iptables-persistent installed, so my action.d and filter.d custom scripts
have code to iptable-save and iptables-restore in them.

edit your postfix jail and add
```
bantime  = 31556926
```
or
change "[DEFAULT]" in jail.conf to something other than
```
bantime = 600
``` whatever is appropriate to your environment, or requirements.
[COLOR=#ff0000]^^[/COLOR]This[COLOR=#ff0000]^^[/COLOR] DEFAULT directive may or may not exist.

```
[postfix]
...
bantime  = 31556926
...
``` is read second,  after "[DEFAULT]"...

Save your current rules:
```
iptables-save > /root/saved.rules
service fail2ban restart
iptables-restore < /root/saved.rules
```

Monitor the /var/log/fail2ban.log file for "Unban" keyword.

Subscribed with interest...

---

### Post by christopher41 on 2015-12-08
Sorry I cut to much from that datestring... 7 and 8 is hours, so my earlier bantime was 3600 seconds.

---

### Post by Habitual on 2015-12-08
ack. Even simple math eludes me sometimes.
1 hour it does seem to be. I blame lack of caffeine.

---

### Post by christopher41 on 2015-12-10
The 1 year change did not work that good.. Some customers called due to this permanent block. :| So i reverted the change to 1 Hour.
I guess that some of the customers have badly configured email clients, example: Not using authentication with SMTP. 

Here is one example from the mail.log, where the customer-IP (12.345.678.910) was blocked around 11:14.
I know that fail2ban searches for this lines "reject: RCPT from" , could someone explain why they are generated?

I think that the user "sofia@customerdomain.se" is not authenticated, but I am not sure...

```
Dec  9 11:07:23  ourserver postfix/submission/smtpd[28699]: connect from c12-345-678-910.bredband.comhem.se[12.345.678.910]
Dec  9 11:07:24  ourserver postfix/submission/smtpd[28699]: disconnect from c12-345-678-910.bredband.comhem.se[12.345.678.910]
Dec  9 11:11:47  ourserver amavis[20830]: (20830-03) Passed CLEAN, [164.40.177.69] [12.345.678.910] <order@customerdomain.se> -> <store1@customerdomain.se>, Message-ID: <3D0B6568-9817-4987-A829-14E7923F2292@customerdomain.se>, mail_id: yipkjp4recHf, Hits: -1.234, size: 136880, queued_as: 165571BC005D, 1295 ms
Dec  9 11:13:33  ourserver postfix/submission/smtpd[28665]: connect from c12-345-678-910.bredband.comhem.se[12.345.678.910]
Dec  9 11:13:33  ourserver postfix/submission/smtpd[28665]: NOQUEUE: reject: RCPT from c12-345-678-910.bredband.comhem.se[12.345.678.910]: 554 5.7.1 <c12-345-678-910.bredband.comhem.se[12.345.678.910]>: Client host rejected: Access denied; from=<sofia@customerdomain.se> to=<filip@buddomain.se> proto=ESMTP helo=<[192.168.0.41]>
Dec  9 11:13:33  ourserver postfix/submission/smtpd[28665]: disconnect from c12-345-678-910.bredband.comhem.se[12.345.678.910]
Dec  9 11:14:47  ourserver postfix/submission/smtpd[28665]: connect from c12-345-678-910.bredband.comhem.se[12.345.678.910]
Dec  9 11:14:47  ourserver postfix/submission/smtpd[28665]: NOQUEUE: reject: RCPT from c12-345-678-910.bredband.comhem.se[12.345.678.910]: 554 5.7.1 <c12-345-678-910.bredband.comhem.se[12.345.678.910]>: Client host rejected: Access denied; from=<sofia@customerdomain.se> to=<firstname.lastname@customerdomain.se> proto=ESMTP helo=<[192.168.0.41]>
Dec  9 11:14:47  ourserver postfix/submission/smtpd[28665]: NOQUEUE: reject: RCPT from c12-345-678-910.bredband.comhem.se[12.345.678.910]: 554 5.7.1 <c12-345-678-910.bredband.comhem.se[12.345.678.910]>: Client host rejected: Access denied; from=<sofia@customerdomain.se> to=<asa@customerdomain.se> proto=ESMTP helo=<[192.168.0.41]>

```

---

