---
title: "email problem"
date: 2019-05-23
forum: Server Platforms
---

### Post by tomdf on 2019-05-23
Hi guys,

i use ubuntu 18.04 as webserver with ispconfig.

i have an email [EMAIL="info@artyemotions.com"]info@artyemotions.com[/EMAIL] and changed this domain to a new server. 

when i change my /etc/hosts  and put 

```

173.249.25.125  artyemotions.com

```

then i can receive the emails.
when i dont put the entry in my /etc/hosts/ i can not receive.

the domain is pointed to the new server 173,249,25,125
the domain is with godaddy. 
do i need a mx record as well in the dns zone setting?

how should the mx record be?

type: mx
name: artyemotions.com
mailserver: server1.cl-i.net (which is the email server of my server. 
priority : 1

is this correct?
i just put this mx record to see if it does work.

thanks for your help.

---

### Post by SeijiSensei on 2019-05-23
Well, I don't see an MX record for the domain, so yes, you'll need one to receive external email.  If you want to send mail, you'll need an SPF record and reverse DNS resolution configured for your server.

```

@ IN SOA artyemotions.com ...

    IN MX artyemotions.com.

...

```

You already have an A record for the server.  MX records use hostnames, not addresses.

The bigger question is why doesn't your server know its name?  What nameservers does the local resolver use?  If you type "host artyemotions.com" at the prompt, does it not return your IP address?

A reverse lookup for your IP returns "server1.cl-i.net" not "artyemotions.com".  You'll need to deal with your provider to have that address point to your domain name.

---

### Post by tomdf on 2019-05-23
thanks for your kind answer.


host.artyemotions.com returns:

```

artyemotions.com has address 173.249.25.125



```

the domain use the nameserver of godaddy ns.09 and ns10.domaincontrol.com

I use for all domains nameservers of the domain name providers. 

I have my own VPS with ubuntu 18.04 and ISPconfig and i have postfix running there

how can i make the address point to the domain name and not to the server?

btw: where can i find the emails on the server? normally it should be /var/mail/username ? but i dont find them there..

btw: i use this server installation: [SIZE=1][COLOR=#000000][FONT=&quot]https://www.howtoforge.com/tutorial/ubuntu-ispconfig-automated-install-script/[/FONT][/COLOR][/SIZE]

sorry for the confusion but for me its quite complicated with email. 
however thanks a lot for your help.

---

### Post by SeijiSensei on 2019-05-24
E-mail *is* complicated and not for the faint of heart.

The MX record should point to the public IP address of the server you have running Postfix.

If that's not the same as 173.249.25.125, then you need another A record.  Let's suppose Postfix is running on a machine at 10.10.10.10.  Then you'd have these entries in your DNS:

```

@ IN SOA ....

     IN MX 0 mail.artyemotions.com.

10.10.10.10 IN A mail.artyemotions.com.

```

Are you even sure your server has accepted any mail? What does /var/log/mail.log show when you send a message to the server?  Does the server have
```

mydestination = ... artyemotions.com

```
in /etc/postfix/main.cf?

---

