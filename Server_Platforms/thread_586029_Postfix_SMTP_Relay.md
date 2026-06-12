---
title: "Postfix SMTP Relay"
date: 2007-10-21
forum: Server Platforms
---

### Post by notaloafer on 2007-10-21
Hey I need help! :P

As a final thing to get rid of my Windows server entirely (yes I am proud) I am now moving all my mailboxes to linux.

Right now everyone can do a POP login and get their mail just fine. However the problem lies within the Postfix SMTP server.

Here is the error message everyone is getting:
"The mail server responded 5.7.1 Relay access denied"

1) The way I want my SMTP outbound to be setup is to relay all outbound emails sent to mail.notaloafer.com to smtp.comcast.net
2) Instead of only allowing relaying for specific domains, I'd rather have it so you have to authenticate with a SMTP login username/password (the same for POP3). Once you authenticate you can send all the mail you want to mail.notaloafer.com and it will relay through smtp.comcast.net . The main thing I am trying to prevent is having a open relay!

Below is my current Postfix main.cf file (The relevant information. If you need additional info please let me know):

```

home_mailbox = Maildir/
mailbox_command = 
mydestination = mail.notaloafer.com, localhost.localdomain, localhost, notaloafer.com
inet_interfaces = all
inet_protocols = all
mynetworks = 127.0.0.0/8, 192.168.1.0/24
unknown_local_recipient_reject_code = 550
relay_domains = $mydestination
relayhost = smtp.comcast.net
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)

```

As you can see my relay_domains is only allowing relaying to the domains in notaloafer.com. I can send mail to [email]anything@notaloafer.com[/email] just fine, but when I attempt to send to anything (such as @hotmail addresses) I get the error message (for obvious reasons).

Thank you guys so much! I love Ubuntu!!!!!
-Eric

---

### Post by robert_pectol on 2007-10-22
Add the following:
```

smtpd_recipient_restrictions = permit_mynetworks, reject_unauth_destination

```

---

### Post by notaloafer on 2007-10-22
> **robert_pectol said:**
> Add the following:
```

smtpd_recipient_restrictions = permit_mynetworks, reject_unauth_destination

```

I added it and restarted postfix but I'm still getting the same relay denied error...

-Eric

---

### Post by robert_pectol on 2007-10-22
> 1) The way I want my SMTP outbound to be setup is to relay all outbound emails sent to mail.notaloafer.com to smtp.comcast.net

If that's the case, then why do you have notaloafer.com listed in your mydestination directive?  You should only list domains for which your server is the ultimate destination.  Domains listed in the mydestination will be delivered locally using the $local_transport mail delivery transport.

> 2) Instead of only allowing relaying for specific domains, I'd rather have it so you have to authenticate with a SMTP login username/password (the same for POP3). Once you authenticate you can send all the mail you want to mail.notaloafer.com and it will relay through smtp.comcast.net . The main thing I am trying to prevent is having a open relay!

When setup properly, Postfix should relay for clients that are local to the, "trusted" network as specified by the mynetworks directive, as well as accepting all mail for which it itself is the ultimate destination, regardless of what client sent it.  So first, I'd fix your mynetworks and then I'd reload postfix (sudo /etc/init.d/postfix reload) and then try again making sure you are sending mail from a local host in the, 192.168.1.0/24 network range. Otherwise you'll get the relay access denied message.

---

### Post by notaloafer on 2007-10-22
I'm really getting confused now =P. I guess what I'm asking is how to setup my configuration file to fit what I described I need to be able to do... I'm very "green" to Ubuntu mailing and postfix and I don't really understand what I need to do...

By the way with the SMTP I need to be able to send mail to mail.anydomainihost.com even if I am not in the 192.168.0.1/24 address space...

Thanks
-Eric

---

### Post by robert_pectol on 2007-10-23
> **notaloafer said:**
> By the way with the SMTP I need to be able to send mail to mail.anydomainihost.com even if I am not in the 192.168.0.1/24 address space...

Then you want to look into something like SMTP-AUTH.  Just Google it.

---

### Post by notaloafer on 2007-10-23
So I take it this means Postfix does not support SMTP Authenication?

-Eric

---

### Post by notaloafer on 2007-10-24
I'm really having trouble here guys. I really am completely lost in what direction I want to go with my mail server... there are just way too many options to consider!!! If anyone can give me 1-on-1 help with it let me know or PM me or something because I'm frankly loosing it. I went through 3 tutorials today and every single one of them (I'm trying to control my rage) CUT OFF (as in they never finished) at the SMTP part. These tutorials do me NO GOOD AT ALL! I wasted a good 7 hours to accomplishing nothing at all.

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) (Does not contain information about setting up SMTP-Auth)


I need to be able to SMTP-Auth with Ubuntu. All the guides out there are like 1000x more complicated than what I want. 

Yes I can receive mail
**No I cannot** send mail out. Every time I either get a relay error or something related.

**Here is what I want to accomplish (re-evaluated):**

1) Have virtual mail users / domains in MySQL instead of setting up a user account for Linux for every one of them (very inconvenient).
2) Be able to send mail to mail.notaloafer.com (using SMTP TLS user/password authentication) and have mail.notaloafer.com relay the email to smtp.comcast.net . I have to be able to send mail to mail.notaloafer.com off any IP address without safelisting IP's (I find it really surprising that these apps like postfix come with safelisting IP's as default and not SMTP auth).
3) Be able to retrieve mail from mail.notaloafer.com through SquirrelMail OR clients such as Thunderbird
3) Be able to control postfix through postfix mysql admin utility (so designated admins can control their own domain mailboxes).

So far switching my windows server to Linux has be a awesome pleasant experience. Everything seemed way easier to setup on Linux. However so far this mail thing has been a nightmare on Linux!

If someone could at least tell me the packages I'm going to need that'd be a huge help. Right now I need to get off this computer before I unleash my anger on the physical being of my server.

-Eric

---

### Post by notaloafer on 2007-10-24
okay I found another tutorial that was much simpler and decided to give it a go....

[https://help.ubuntu.com/community/Postfix?highlight=%28postfix%29](https://help.ubuntu.com/community/Postfix?highlight=%28postfix%29)

I am having the following issues:
1) When I try to send a email I "Use TLS if available" and I get a password box prompt, however I fail to authenticate for any Linux user that I created.
2) I cannot download my messages... connection refused. Any ideas? surely not my firewall.

-Eric

---

