---
title: "[Postfix] Foreign Bounce"
date: 2006-08-27
forum: Server Platforms
---

### Post by Kurdt on 2006-08-27
I had setup a mail server using flurdy's guide [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) It's working really fine but i have one thing that i want to clear up so i don't have problems in the future.
I am using logwatch to send me day emails about what happened, and i have a section called **foreign bounce**

Postfix website says:
>  bounce
    Send postmaster copies of undeliverable mail. If mail is undeliverable, a so-called single bounce message is sent, with a copy of the message that was not delivered. 

Well, my mail server received SPAM, that was identified by amavis with BAD-HEADERS, the email was **BOUNCED** and my mail server tried to send a "postmaster copy of undeliverable mail" to the spam sender address, (this is what i thought) and i got this log:

>   To [email]aemasfahGq@mail.ru[/email] Msg="host mxs.mail.ru[194.67.23.xx] said: 550 Access from ip address 200.xx.xx.xx blocked. 

200.xx.xx.xx is my ip address. Why i am being blocked? (i checked and i am not an open relay) maybe this other log in the same section says something:

>  To [email]rkdtyt@comcast.net[/email] Msg="host gateway-r.comcast.net[204.127.198.26] said: 521-EHLO/HELO from sender 200.xx.xx.xx does not map to pc009 in DNS 521-sending machine name must be provided as a fully 521-qualified domain via EHLO/HELO command. 521-see section 4.1.1.1 and 4.1.4 of RFC 2821 521 521: Comcast requires that all mail servers must have a PTR record with a valid Reverse DNS entry. Currently your mailserver does not fill that requirement. For more information, refer to: [http://www.comcast.net/help/faq/index.jsp?faq=Email118405](http://www.comcast.net/help/faq/index.jsp?faq=Email118405) (in reply to MAIL FROM command" : 1 Time(s)

Ok, so i have to provide a fqdn with command ehlo, **Can i resolve this simply adding to hosts file my fqdn ? or i need something more?**

I think that this 2 log lines are related with the fqdn thing... I know that is email trying to be sent to an spammer (bounce mail) but **i cannot send mailto hotmail.com addresses (i can receive) so i think is happening the same** (i just noticed this and i cannot confirm is a fqdn problem because i am not at the site of the server)

Well, thanks for your help, i really need you guys

---

### Post by chrisfay on 2006-08-27
Two things I would check:

1. Make sure that your mail servers has a reverse DNS entry. Some servers will reject mail without a valid reverse entry specified.

2. Check what "origin" address was used in the email that your machine generated. Make sure it has your email address instead of something like foo@localhost. I was having a problem where bounced mail notifications to users where not going out becuase my server was using foo@localhost as the "origin" address for automated responses. Mail servers won't allow mail from addressess like that and will reject it.  

just a thought....

---

### Post by Kurdt on 2006-08-28
1. how do i do that? the story is: we had a Exchange Server and was replaced with this setup,  nothing changed, only the computer, maybe i had to setup something in it?

2. Look this two messages sources:

Before Postfix (exchange):
> Received: by exserver.domain.com.ar 
	id <01C6BD6A.60B908C0@exserver.domain.com.ar>; Fri, 11 Aug 2006 14:20:01 -0300

After Postfix

> Received: from localhost (localhost [127.0.0.1])
	by pc009 (Postfix) with ESMTP id 360C332388B;

See the difference ? but my hosts file always looked like this:

```
===============================================================================
127.0.0.1 localhost pc009.domain.com.ar
192.168.1.51 pc009 pc009.domain.com.ar

```

Why is postfix taking localhost [127.0.0.1] and pc009 (not fqdn) to identify itself??

Please help me :(

---

### Post by Kurdt on 2006-08-31
Well, i forgot to add the fqdn to myhostname line in postfix :-$ :-& 

but still,** i am not being able to send to hotmail.com domain**, :( Maybe someone that's running a mail server too can tell me if anything in special has to be enabled.

Even i fixed this in message source: 

> Received: from pc009.domain.com.ar ([200.x.x.x])

I thought that hotmail required fqdn helo and i think that is what i am providing...

Help please

---

### Post by jimm on 2006-08-31
Hi,

Are you by any chance sitting behind an IP address that is in an ISP pool of addresses?

Even if you have a static IP address from your ISP some of the ranges are still blocked out in the anti-spam databases as possible spammer addresses. i.e. the spam db operators find out what blocks are assigned to ISP's and blacklist them by default.

If the destination MTA is doing a blacklist lookup and finding your IP address in there they will reject it. This is what happened to me... I dont think hot mail bothers to do this lookup that's why it will be working for them.

You can get round this by using a smarthost (just a mail server that will relay from ISP members machines) at the ISP (or another commercial smarthost) to relay your mail. I dont know how you set that up in postfix (havent got round to learning that one yet!), but you will be able to do it.

Thanks,
James

---

### Post by Kurdt on 2006-08-31
Hi, i think i found the problem, i got this in my message sources

> Received-SPF: neutral (gmail.com: 200.x.x.x is neither permitted nor denied by best guess record for domain of [email]user@domain.com.ar[/email])

Well, as you see, gmail accepts neutral spf but hotmail won't, as i read here

[http://www.howtoforge.com/forums/showthread.php?p=38165](http://www.howtoforge.com/forums/showthread.php?p=38165)

What can i do to receive a SPF pass ?

---

### Post by Kurdt on 2006-08-31
Look this too:

> 550-Bad HELO: pc009.domain.com.ar does not resolve 550-Additionally, 200.x.x.x has no rDNS 550-Please see RFC 2821 section 4.1.1.1, 550 RFC 1123 section 6.1.1 and RFC 1912 section 2.1 (in reply to RCPT TO command" : 1 Time(s)

This is from log files, my mx point to mail.domain.com.ar and the computer name is pc009.domain.com.ar also myhostname line.

Do i have to changed it to mail.domain.com.ar ? why is that? the old server was server.domain.com.ar and i had no problems...

Thanks

---

### Post by chrisfay on 2006-08-31
Read this:
[http://www.ubuntuforums.org/showthread.php?t=240470&highlight=rbl+hotmail](http://www.ubuntuforums.org/showthread.php?t=240470&highlight=rbl+hotmail)

You are probably listed in the RBL and will not be able to send mail to hotmail without relaying through your ISP for outbound mail. I was having the same problem until I setup a relayhost.

---

