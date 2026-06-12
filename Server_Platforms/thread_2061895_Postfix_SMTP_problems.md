---
title: "Postfix SMTP problems"
date: 2012-09-23
forum: Server Platforms
---

### Post by the1joker on 2012-09-23
Okay, i've been trying this for days now. Googled hundreds of forums and all come with about the same solution, but none seem to really work for me.
 
Here's what i got:
 
Ubuntu Server 12.04
Postfix (duuh)
ISPConfig 3.0.4.5
 
Everything, like web, DNS,e-mail in, and all other services work fine.
 
Can send my e-mails fine through webmail (roundcube)....
 
Just not when using an E-mail Client (like Outlook)
 
When i send an email i get it returned right away with the message:

[FONT=Consolas]Server error: '554 5.7.1 <[EMAIL="tobiashagenbeek@gmail.com"][COLOR=#0000ff]tobiashagenbeek@gmail.com[/COLOR][/EMAIL]>: Relay access denied'[/FONT]

[FONT=Consolas][FONT=Arial][SIZE=2]Now these are the (what i recon after all forum searches) important lines in main.cf of postfix:[/SIZE][/FONT][/FONT]

[FONT=Consolas]myhostname = server1.hunique.nl[/FONT]
[FONT=Consolas]mydestination = localhost, localhost.localdomain[/FONT]
[FONT=Consolas]relayhost =[/FONT]
[FONT=Consolas]mynetworks = 127.0.0.0/8 [::1]/128[/FONT]
[FONT=Consolas]smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination[/FONT]
 

[FONT=Consolas][FONT=Arial][SIZE=2]I've tried the following:[/SIZE][/FONT][/FONT]

[FONT=Consolas]- [/FONT][FONT=Consolas]smtpd_recipient_restrictions = permit_sasl_authenticated, check_recipient_access, hash:/etc/postfix/filtered_domains , permit_mynetworks , reject_unauth_destination[/FONT]


[FONT=Consolas][FONT=Arial][SIZE=2]But then i get the error in my mail log that the file doesn't excists, okay so i tried:[/SIZE][/FONT][/FONT]

[FONT=Consolas]mydestinations = $mydomain, $myhostname, localhost, localhost.localdomain[/FONT]

[FONT=Consolas][FONT=Arial][SIZE=2]Then i still get relay access denied with the following mail log error:[/SIZE][/FONT][/FONT]

[FONT=Consolas]postfix/smtpd[8342]: NOQUEUE: reject: RCPT from unknown[10.1.10.3]: 554 5.7.1 <[EMAIL="tobiashagenbeek@gmail.com"]tobiashagenbeek@gmail.com[/EMAIL]>: Relay access denied; from=<[EMAIL="sure@hunique.nl"]sure@hunique.nl[/EMAIL]> to=<[EMAIL="tobiashagenbeek@gmail.com"]tobiashagenbeek@gmail.com[/EMAIL]> proto=ESMTP helo=<HunqiueWork1>[/FONT]
 
[FONT=Consolas][FONT=Arial][SIZE=2]and i've tried variations on these, since most sites proclaim that that's the solution, but i can't really get further with this. [/SIZE][/FONT]

[FONT=Arial][SIZE=2]Anyone any bright ideas??[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Thanks in advance.[/SIZE][/FONT][/FONT]

---

### Post by kennethconn on 2012-09-23
I'm guilty of not thoroughly reading posts like this, but gut reaction is that the problem lies with your Outlook configuration.

---

### Post by the1joker on 2012-09-23
Well as i said there is a problem in any email client, and if that was the case, my mail.log wouldn't have an error...

---

### Post by volkswagner on 2012-09-23
I believe web mail works because it is on the same machine as Postfix.

```
mynetworks = 127.0.0.0/8 [::1]/128
```

So if you are connecting from a remote machine and trying to send mail you will get denied.

You will want to check out "Getting selective with SMTP access restriction lists" using the following link.
[http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html)

Do you have the following directive in main.cf?
```
smtpd_client_restrictions
```

If you don't want to add a list of approved networks, or if it's not practical you may try something like:

```
smtpd_client_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_rbl_client zen.spamhaus.org, reject
```

This should work if you have sasl working.

---

### Post by the1joker on 2012-09-27
Thanks i will give this a shot asap and let you know. sorry for the late response, i just got married :)

---

### Post by lisati on 2012-09-29
> **the1joker said:**
>  i just got married :)
Congratulations, enjoy the journey, and good luck! (Coming up 20 years for Mrs Lisati & myself in about 7 weeks)

---

### Post by newhambo on 2012-11-03
Hi there,

I have the same problem, did you find any solution?

---

