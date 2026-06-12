---
title: "Serious Spam Attack"
date: 2008-04-02
forum: Security Discussions
---

### Post by dESAI on 2008-04-02
Hi Good People,

Not sure if this is related to Ubuntu or not. I am sure that the this forum is a good place to get answers to technical problems.

Someone out there has started using my business email address to spam people. This morning at around 6am I started receiving "System Administrator, Undeliverable:" error emails. Since 6am I have received an error email every 4-5 minutes.

It's kind of scary to see this.

What can I do to stop it?
How is this possible it could get so bad so quick?
Can I trace it?
Do you have any suggestions/comments?

It would be a massive inconvenience to have to get a new email address. Hopefully there are other better solutions.


Thanks in advance for any help you can give :-)

---

### Post by brian_p on 2008-04-02
> **dESAI said:**
> Hi Good People,

Not sure if this is related to Ubuntu or not. I am sure that the this forum is a good place to get answers to technical problems.

It's not a security matter but . . . .

> Someone out there has started using my business email address to spam people. This morning at around 6am I started receiving "System Administrator, Undeliverable:" error emails. Since 6am I have received an error email every 4-5 minutes.

Happens all the time. Spam is being sent with your address in the From: field or as the Return-path.

> It's kind of scary to see this.

What can I do to stop it?

You can't

> How is this possible it could get so bad so quick?

Lots of spam with your address in it and addresses at the destinations which are unknown. Therefore - lots of bounces.

> Can I trace it?

The ultimate source of the spam? Maybe. Have you got a month or two to waste?

> Do you have any suggestions/comments?

It would be a massive inconvenience to have to get a new email address. Hopefully there are other better solutions.

Use a mailfiltering program to filter or delete incoming mail with  Return-path: <> for a day or so. It might be back to normal for you by then.

---

### Post by dESAI on 2008-04-02
My office uses a third party to deal with spam. We are already blocking 99% of emails.

I'm not sure if others are having the same problem. I've had this problem before and I know other who have too. 

But it's the scale is what worries me. I'm getting emails every 4-5 minutes!

Thanks for the reply :-)

Have a great day!

---

### Post by brian_p on 2008-04-02
> **dESAI said:**
> My office uses a third party to deal with spam. We are already blocking 99% of emails.

The returned mail notifications are unwanted but are not spam.

> I'm not sure if others are having the same problem. I've had this problem before and I know other who have too. 

But it's the scale is what worries me. I'm getting emails every 4-5 minutes!

Maybe use procmail and/or your MTA to put them in a folder or direct to /dev/null? Not seeing them may reduce the worry factor!

> Thanks for the reply :-)

Have a great day!

You too.

---

### Post by HermanAB on 2008-04-02
Well, one per 5 minutes is only 12 per hour, which is practically zero.  My domain gets about 10,000 spam attempts per hour.  You need to get worried once the spam exceeds several hundred per hour.  What you then need to do then, is run your own mail server with SpamAssassin, ClamAV, Razor, Pyzor, DCC and a handful of RBLs, plus maybe a general purpose connection delay.

Cheers,

Herman

---

### Post by Crafty Kisses on 2008-04-02
> **HermanAB said:**
> Well, one per 5 minutes is only 12 per hour, which is practically zero.  My domain gets about 10,000 spam attempts per hour.  You need to get worried once the spam exceeds several hundred per hour.  What you then need to do then, is run your own mail server with SpamAssassin, ClamAV, Razor, Pyzor, DCC and a handful of RBLs, plus maybe a general purpose connection delay.

Cheers,

Herman

Yeah, that's nothing, one per 5 minutes, don't even worry.

---

### Post by FakeOutdoorsman on 2008-04-02
> **dESAI said:**
> What can I do to stop it?
You can implement Sender Policy Framework (SPF). It will help, but not stop all of the bounces. From Wikipedia:
> The main benefit of SPF is to people whose e-mail addresses are forged in the Return-Paths. They receive a large mass of unsolicited error messages and other auto-replies, making it difficult to use e-mail normally. If such people use SPF to specify their legitimate sending IPs with a FAIL result for all other IPs, then receivers checking SPF can reject forgeries, reducing the amount of back-scatter.

Some SPF creation wizards:
[The SPF Setup Wizard]("http://old.openspf.org/wizard.html")
[easySPF: an Ajax enabled SPF Wizard]("http://wizard.easyspf.com/")

You can also disable any catch-all email accounts.

---

### Post by netlogic on 2008-04-02
> **Codename said:**
> Yeah, that's nothing, one per 5 minutes, don't even worry.

i wish i get that little. the email management can be a pure hell. that is why i let someone else handle it while i do the fun stuff.  Properly configured SpamAssassin does wonders. Also, having a proper guide rules for your MTA can save many headaches. Insecure mail servers will get owned by Windows bot machines. There is a reason kiddie scripters constantly write screwed up warez apps. Not all warez guys hate the big corporations. These days most of them are doing it to own many machines to become bots. That is why if you look at ISPs traffic, it is insane.  Since, it is illegal to monitor people's traffic, you kind of have to let the bots run wild. Only thing you can do is email your users based on their port traffic level not what you have seen. Tell them, their traffic is insane and they need to run a firewall. That is why Verizon and Comcast started to filter certain ports. There is a reason why they let you run ftp, but email and www. 

people love to abuse something free. too bad those cool guys created a virus to combat bots were told to stop what they were doing....

---

### Post by hyper_ch on 2008-04-03
I'd use postfix with according UCE protections and SPF... but SPF will only be of use if the other party also uses it...

But as said, returning email is not spam per se...

what you could do is to create an invididual email address for each contact that you got... I use that when I need to enter my email somehwere... I use  [www.theirdomain.com@mydomain.com](www.theirdomain.com@mydomain.com) as email and once I receive spam to one of them I know where my email was leaked...

---

### Post by dESAI on 2008-04-09
I started doing that, creating email addresses, but only when I register on a new site, like: [email]facebook@mydomain.com[/email]. I did it to see if those companies forwarded my email address to others. In almost 10 years, I don't think I've discovered a company who has sold my email. Anyway thanks for the suggestion. It's a good one.

Thanks and have a great day :popcorn:

---

