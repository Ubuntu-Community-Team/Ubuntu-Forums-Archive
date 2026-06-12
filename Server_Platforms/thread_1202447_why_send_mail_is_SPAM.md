---
title: "why send mail is SPAM"
date: 2009-07-02
forum: Server Platforms
---

### Post by boyguapo on 2009-07-02
im using this howto [http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04)

why send mail is to spam, im using no-ip free services to redirect my mail server.

how to fix this?

thanks to all...

---

### Post by randyks on 2009-07-02
If your outgoing mail is getting marked as spam by other machines, it is because you are sending email out from a dynamic ip address. Your isp will probably let you forward outgoing email through their email server, which will allow you to send out email without issue (getting marked as spam). The how2forge howto doesn't really cover that very well, if at all. I had the same issue and the folks in #postfix on irc helped me out.

This link may give you a little background.

[http://www.nber.org/REASON-FOR-REJECTION/smarthost.html](http://www.nber.org/REASON-FOR-REJECTION/smarthost.html)

Randy

---

### Post by slickflick on 2009-07-02
if the email is important you should probably get a hosted SMTP server to send them.

---

### Post by boyguapo on 2009-07-03
ok thanks.. to all replays, i have an idea.

---

### Post by boyguapo on 2009-07-04
any idea pls... i like to read more idea.

---

### Post by black_shadow on 2009-07-05
Hi

If you sendmail is behind a router and your IP gives you a dynamic IP then it will be marked spam as you IP will never be registered as a mail server.

Email server have to have a registered IP address for them not to be marked as spam.

Mike

---

### Post by windependence on 2009-07-05
> **randyks said:**
> If your outgoing mail is getting marked as spam by other machines, it is because you are sending email out from a dynamic ip address. Your isp will probably let you forward outgoing email through their email server, which will allow you to send out email without issue (getting marked as spam). The how2forge howto doesn't really cover that very well, if at all. I had the same issue and the folks in #postfix on irc helped me out.

This link may give you a little background.

[http://www.nber.org/REASON-FOR-REJECTION/smarthost.html](http://www.nber.org/REASON-FOR-REJECTION/smarthost.html)

Randy
This I never understand. If the OP has an ISP that provides him with an SMTP server, WHY run a mail server? I can't get this relaying thing. If you are going to run a real e-mail server, you really really need a static IP with a registered domain and  valid DNS. You will also need rverse DNS if you want to be able to send to everyone. Mail servers have become a lot more picky these days and most of them won't even talk to you if you don't have a static IP and reverse DNS.

-Tim

---

### Post by randyks on 2009-07-07
> **windependence said:**
> This I never understand. If the OP has an ISP that provides him with an SMTP server, WHY run a mail server? I can't get this relaying thing. If you are going to run a real e-mail server, you really really need a static IP with a registered domain and  valid DNS. You will also need rverse DNS if you want to be able to send to everyone. Mail servers have become a lot more picky these days and most of them won't even talk to you if you don't have a static IP and reverse DNS.

-Tim

Tim,

All of your assumptions are wrong. **Every email I send from my Linux box with Dyndns is received by the intended party.**With your ISP email you have one email address, sometimes a few more with some ISPs. If you set up your own email server and use your ISP as a smarthost you can then have pretty much unlimited email address. I have 5 dyndns domains registered and I can receive emails on all of them. Since my outgoing email bounces through the ISP I can send out all I want with out it getting marked as spam. The email appears on the receiving machine with my server email addy and not the ISP addy. ie: [email]xxxxxxx@patterson.webhop.net[/email]. This set up allows me to control my email a little closer. I can set up emails for certain jobs, or even one time use email addresses. Do I have to do this? No. But you do have to admit, it is pretty neat. 

So no, you do not have to have a static ip to run am email server or reverse dns or anything else besides a service such as dyndns. I have been running one (5 actually) for over a year without issue. All of this on a 6 meg dsl account.

Nothing is impossible with Linux and the ability to Google.

Randy

---

### Post by netztier on 2009-07-07
> **randyks said:**
> and use your ISP as a smarthost 

That actually IS the point!

If you were sending directly from your dynamic IP, all your connections would be denied, for exactly the reason that they come from a dynamic IP address.

I used to be co-responsible for a the mail gateway for a 3000 employee company, that had a very restrictive configuration. No less than 98% of all incoming connection attempts (~1 million per 24h) were denied because of a blacklisted (dyn. IP ranges of the well-known ISPs) or source IP address or domains with "bad reputation".

Every two weeks, an IT admin from a small company needed to be explained that it was not too clever to send e-mail directly from their M$ Exchange server connected through their SOHO broadband router, but that they should use their ISP's SMTP server as smarthost.

> 
The email appears on the receiving machine with my server email addy and not the ISP addy.

Are you sure you understood SMTP correctly? I very much doubt that the receiving mail server will see your (dynamic) IP address as the source IP of the incoming connection. It will see the IP address of your ISP's smarthost, which is why it will accept the SMTP connection from it.


regards

Marc

---

### Post by randyks on 2009-07-07
I think you are missing the point. I will try to address it slowly since there may be a translation problem.

1. The OP said his outgoing mail was getting flagged as spam by other servers.

I explained that that could be avoided by using a smarthost, and provided a link that explains a smarthost. The OP asked how to fix his issue and this is a solution. 

2. Tim asked shared that he didn't understand this whole process and implied that it wouldn't work.

I gave him examples of how it does work, and reasons for hosting your own email server and using a smarthost. 

3. You (netztier) shared that you formerly ran a large mail server. I can only assume that you are no longer employed due to your interpersonal skills. When I stated that my return address was used, I did not mean in the headers, I just meant in the from: bar in outlook/eudora/whatever email client and the email could be responded to at that address. Dyndns (or user preference) route the domain name to the dynamic address.

I hope a clarified this. To recap.

*[SIZE="3"]You can use a server with a dynamic ip to send and receive email if you use the combination of a dynamic dns solution and a smarthost. There may be other ways to accomplish this, I am just unaware of them. The only way your email would be marked as spam is if your smarthost is marked as a spammer. Gmail can be used as a smarthost, btw.[/SIZE]*

Again this is a solution to the OP's issue. If you cannot see why, or how this works, or understand the usefulness of this solution is irrelevant, as it was not addressed to you.

---

### Post by Andre_luis_bsrsoft on 2009-07-07
You can send/receive email through a dynamic ip, but this emails can be spam markeds.

A email provider can deny this emails. Is a internal politics of each company.

---

### Post by windependence on 2009-07-08
> **netztier said:**
> That actually IS the point!

If you were sending directly from your dynamic IP, all your connections would be denied, for exactly the reason that they come from a dynamic IP address.

I used to be co-responsible for a the mail gateway for a 3000 employee company, that had a very restrictive configuration. No less than 98% of all incoming connection attempts (~1 million per 24h) were denied because of a blacklisted (dyn. IP ranges of the well-known ISPs) or source IP address or domains with "bad reputation".

Every two weeks, an IT admin from a small company needed to be explained that it was not too clever to send e-mail directly from their M$ Exchange server connected through their SOHO broadband router, but that they should use their ISP's SMTP server as smarthost.



Are you sure you understood SMTP correctly? I very much doubt that the receiving mail server will see your (dynamic) IP address as the source IP of the incoming connection. It will see the IP address of your ISP's smarthost, which is why it will accept the SMTP connection from it.


regards

Marc

Exactly. If I can't send the mail directly from the mailserver, there is no point since I can buy 100 e-mails from GoDaddy for $9.99 a year.  Also I realize this may not be possible in Europe but I have 5 IPs which I pay $14.95 a month for from my ISP. There are ISPs all over the USA that do this very cheaply. I just could never see the point.

-Tim

---

### Post by netztier on 2009-07-08
> **randyks said:**
> as it was not addressed to you.

I was addressing my reply to *you*, because you boldly (in literally bold letters) stated that you were successfully sending email from your dynamic address, which is not quite what you are actually doing. 

Had you emphasised the same way that what you do only works because you are using your ISP's smarthost as relay, I'd stayed put. 


regards

Marc

---

### Post by jasonsjunk on 2009-07-08
Hmmmm simple solution use google apps.  I run the email's for three different domains that are hosted from my house through google apps.  I get 50 e-maill accounts per domain for FREE and I don't even have to bother running a mail server I just route everything through google and all my server at home has to do is server web pages and record TV shows.  All of my emails come from [email]xxx@mydomainname.com[/email]  and are not @gmail.com emails.  


Running a mail server is a headache and I fail to see the point of running one unless there is a specific need.  

I use the spare CPU cycles that would have been wasted on Postfix for something important like Folding@Home.

---

### Post by randyks on 2009-07-08
How does this help with the original posters question of how to send email from his server without marking it as spam? If he wanted to use google apps/isp/Santa Claus/ he would use them.

---

### Post by jasonsjunk on 2009-07-24
It helps the original poster because his emails won't be marked as spam and it is easy to setup without having to deal with running a mail server and relaying through his ISP.  All of the mail is controlled elsewhere and the original poster can focus his efforts on other things while Google deals with the spam filtering and mail server security issues.

---

