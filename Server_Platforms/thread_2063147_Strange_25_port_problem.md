---
title: "Strange 25 port problem"
date: 2012-09-26
forum: Server Platforms
---

### Post by heretic381 on 2012-09-26
Hi,

Let me introduce my case quickly. 
I have a vps hosting plan with Ubuntu 11.04 installation 32bit.
Lamp, Webmin, Usermin, Virtualmin.

I've had one first success in setting dns, bind with domain name with a registrar. So that's ok.

I've also set a mail server, first with sendmail, and then with postfix.

The problem is that the port 25 does not work any more. I've activated the alternate submission 587, and it's working. Well, almost.

Accordingly to the face that root can't receive an email directly, an alias like postmaster is used. But the problem is that the alias expansion is giving some strange result with the user address like this:

[EMAIL="root@domain.domain.com"]root@domain.domain.com[/EMAIL]     where it should be: [EMAIL="root@domain.com"]root@domain.com[/EMAIL]

I found it in mail log.

Trying to find out what's the problem with port 25 is driving me crazy, and time consuming.



More infos:

1)My ISP is not blocking port 25. I've already checked it with other smpt servers.

2)Nmon says:  tcp/25 filtered


Thanks in advance, all suggestions and ideas are welcome.


):P

---

### Post by smtp on 2012-09-28
So what you are using now Postfix or Sendmail?

---

### Post by d4m1r on 2012-09-28
Any error messages? Is your VPS host blocking port 25?

I'd create a support ticket with them if you are paying for hosting...

---

### Post by heretic381 on 2012-09-29
Hi guys,
thanks for reply.

Well I was wrong. The problem was my ISP. When I checked it with telnet, I did it with their own smtp server, so of course it worked.  Outgoing smtp was however filtered for the rest od the internet, so it was for my vps hosting or anything else. The good thing is that I could easily open the smtp port and I then successfully telnet my domain. Phew!!

Finally I'm using sendmail again and get things to work. The last encountered problem is that gmail is filtering my mail as spam. So I must look back precisely my dns config.

So before this thread goes to trush or is closed, I'm willing to ask few more questions, about dns. But maybe I should open a new post???

When I set my own private name servers at my registrar, I'm not quite sure if Internet completely ignores registrar dns zone settings???

It seems to me that both records from registrar and vps BIND zone are used for some quests. But it's not clear to me how it's merged.

Thanks again for reply.
Cheers.

---

### Post by lisati on 2012-09-30
Each email provider is different in how they classify incoming mail and whether to shove it in the spam folder. Things they sometimes look at are Reverse DNS and if you have set up things like SPF, DKIM or DMARC.

---

### Post by SeijiSensei on 2012-10-01
See if you can tell the VPS provider what hostname to reply with in response to reverse DNS queries against your IP address.  [Linode]("http://www.linode.com/"), for instance, makes this very easy.  You just go to a page in the server management application and enter the hostname you want assigned to your IP address.  If your provider was blocking port 25, then I suspect they may make you jump through some additional hoops to get reverse DNS set up correctly.

---

