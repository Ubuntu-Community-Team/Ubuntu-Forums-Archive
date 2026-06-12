---
title: "Postfix relay/mailbox unknown  problems"
date: 2007-05-23
forum: Server Platforms
---

### Post by williamtaft on 2007-05-23
Alright, I apologize if this is bit long.

postfix config file: [http://www.nightbakery.net/main.cf](http://www.nightbakery.net/main.cf)
dovecot config file: [http://www.nightbakery.net/dovecot.conf](http://www.nightbakery.net/dovecot.conf)

I'm trying to set up a mail server with postfix/dovecot/squirrelmail on Fiesty Fawn through a router.
Everything is set up okay through webmin, I have the router and firewall ports open for 25 and 143.
At first, after configuring postfix and dovecot, I couldn't send or receive mail to anything but my local address.
I've pretty much scoured the internet to troubleshoot my configurations, changing things as I went along.  
     For a period of time, I was able to send mail remotely to a gmail account, although it went into spam. 
When I tried to send mail from gmail, I kept getting relay access denied errors.  Somewhere along the way I screwed everything up (because I am an idiot), and now I cant even send mail from postfix, getting the error: 
[I] [CENTER]  host gmail-smtp-in.l.google.com[64.233.167.27] said:
    550-5.7.1 [74.139.211.88] The IP you're using to send email is not
    authorized  550-5.7.1 to send email directly to our servers. Please use
    550 5.7.1 the SMTP relay at your service provider instead.
[/CENTER][/I]
 and when I try to send mail from gmail, I get a 
*[CENTER]PERM_FAILURE: SMTP Error (state 13): 550 sorry, no mailbox here by that name (#5.1.1 - chkusr)[/CENTER]*

So I'm trying to find problems.
When I looked at the logs, postfix starts with warning: "*/var/spool/postfix/etc/resolv.conf and /etc/resolv.conf differ*" although i have made them the same (i dont even know whats supposed to go in them).

I'm starting to get beyond confused about everything, and trying to comprehend the idea of nameservers, and why my dns provider will only forward my domain to my ip, instead of maintaining a persistent domain.
I want to transfer my domain to a different host but I don't know where i should go if its even possible to not deal with setting nameservers and what not. 

Id appreciate if you guys could help me get through this; I wasn't aware setting up a mail server could be this complicated.

---

### Post by crmanski on 2007-05-24
I'm wondering if your IP(74.139.211.88) is from a cable or DSL modem? Many mail services (such as gmail) will block email coming from a residential IP netblock since then send so much spam.

---

### Post by brigux on 2007-05-24
I believe you need to Masquerade your IP... Looks like Google doesnt like your private IP (just a thought)

---

### Post by ruy_lopez on 2007-05-24
In "/etc/postfix/main.cf" add the line:

```
smtp_generic_maps = hash:/etc/postfix/generic
```

And in /etc/postfix/generic
```

username@hostname     username@gmail.com
```

where the lvalue is your local username and hostname, and 
the rvalue is the ISP account you want to masquerade as.

Then:

```
sudo postmap /etc/postfix/generic
sudo postfix reload
```

This will send outgoing mail as though it was from your gmail account.

As for the warning about /var/spool/blah/blah, that directory is used for chrooting the server, and if files don't agree with their non-chroot counterparts, then you get a warning. Unless you are running chroot, you don't need to worry about it.

You should concentrate on trying to receive mail first, making sure you have valid MX entries somewhere (like a dynamic dns service), checking your ```
mydestination
```: parameter in /etc/main.cf.

Sending mail is a whole other mess. Some mailservers won't accept your mail unless you have a valid PTR record. Others just bounce your mail because they feel like it.

---

