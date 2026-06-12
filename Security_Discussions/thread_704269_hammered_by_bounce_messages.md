---
title: "hammered by bounce messages"
date: 2008-02-22
forum: Security Discussions
---

### Post by posterboy on 2008-02-22
Help me think this out, please. I am running postfix, and it has been running great for years. I have a domain, (blah.com), For outgoing mail, I use my ISP. Last couple days, I am getting bounce messages by the hundreds, from all over the world. All are addressed to a fictitious, randomized user in my domain. I am set up to DISCARD these, not bounce them. I don't want to contribute to the "backscatter" problem. 
First thought, I have been hacked and am sending spam out. I have another hard drive in a desk drawer, couldn't have been hacked, it's not plugged in, so I pull that one out and put it in, and this continues. Most of these show <> as the from address. A few show barracuda, a few postmaster, etc. 

What is this, what's happening?

Thanks

---

### Post by rickyjones on 2008-02-22
> **posterboy said:**
> Help me think this out, please. I am running postfix, and it has been running great for years. I have a domain, (blah.com), For outgoing mail, I use my ISP. Last couple days, I am getting bounce messages by the hundreds, from all over the world. All are addressed to a fictitious, randomized user in my domain. I am set up to DISCARD these, not bounce them. I don't want to contribute to the "backscatter" problem. 
First thought, I have been hacked and am sending spam out. I have another hard drive in a desk drawer, couldn't have been hacked, it's not plugged in, so I pull that one out and put it in, and this continues. Most of these show <> as the from address. A few show barracuda, a few postmaster, etc. 

What is this, what's happening?

Thanks

Just the normal SPAM that Spoofs the "from" domain. Some spammer is sending out messages with your domain attached. All the bounce messages go to you after the fact.

It has increased immensely since yesterday. My gmail spam folder has grown from 1 or 2 messages a day to over 500 in the last day. I own multiple domains and they all forward (email wise) to my gmail account.

Something you just have to live with.

I hope it helps!

-Richard

---

### Post by astrotech226 on 2008-02-22
I don't know what your particular setup is, but this is something that MIMEDefang and SpamAssassin are really good at.  SpamAssassin will grade the messages and give them a score, MIMEDefang can do whatever you want based on that score.  Silently discard the message, quarantine, etc...

---

### Post by posterboy on 2008-02-22
OK, I feel better. BTW, I do run spamassassin, and have postfix set up to discard any email for any user that doesn't actually exist in this domain. 

Thanks, folks!!!!!!!!

---

### Post by aysiu on 2008-02-22
If you have a catch-all email account, disable it. That may help.

---

### Post by rickyjones on 2008-02-22
> **aysiu said:**
> If you have a catch-all email account, disable it. That may help.

Yes, that will definitely help for people that own their own domains. Problem for me is that sometimes people will send me email to addresses that don't exist, but it is still legitimate, so I try to make sure I can view it all. And that is why I use gmail to filter out the spam :)

-Richard

---

### Post by FakeOutdoorsman on 2008-02-23
How annoying.  If more servers were setup to discard messages at the SMTP level instead of bouncing we would see less of this.  Setting up SPF records for each of your domains might help.  From Wikipedia:
> The main benefit of SPF is to people whose e-mail addresses are forged in the Return-Paths. They receive a large mass of unsolicited error messages and other auto-replies, making it difficult to use e-mail normally. If such people use SPF to specify their legitimate sending IPs with a FAIL result for all other IPs, then receivers checking SPF can reject forgeries, reducing the amount of back-scatter.

---

### Post by rickyjones on 2008-02-24
> **FakeOutdoorsman said:**
> How annoying.  If more servers were setup to discard messages at the SMTP level instead of bouncing we would see less of this.  Setting up SPF records for each of your domains might help.  From Wikipedia:

I've considered creating those SPF records but whenever I look at the official SPF website it appears as though I have to pay to create the records.

Does anyone know if this is true? I'd love to implement them but I'm not sure of the costs involved. If it helps, I do all my domain hosting through Godaddy so I have manual control of my DNS records.

Thanks,

-Richard

---

### Post by FakeOutdoorsman on 2008-02-24
> **rickyjones said:**
> I've considered creating those SPF records but whenever I look at the official SPF website it appears as though I have to pay to create the records.

Does anyone know if this is true? I'd love to implement them but I'm not sure of the costs involved. If it helps, I do all my domain hosting through Godaddy so I have manual control of my DNS records.

A fee?  Blasphemy!  Dump that fee site and try these:
[Creating SPF Records - GoDaddy Help Center]("http://help.godaddy.com/article.php?article_id=3047&topic_id=165")
[The SPF Setup Wizard]("http://old.openspf.org/wizard.html")
[easySPF: an Ajax enabled SPF Wizard]("http://wizard.easyspf.com/")

---

### Post by astrotech226 on 2008-02-24
I don't know how Godaddy's dns administration works, but all you need is the ability to add TXT records.  An SPF record is simply a TXT record with particular information in it.  An example might look like:

```
mx1.yourdomain.com. IN TXT "v=spf1 a -all"
```

There are a few other places you need to do this as well and there are different ways to set it up, but this should give you an idea how the dns part works.

---

### Post by Mr. C. on 2008-02-25
> **rickyjones said:**
> Yes, that will definitely help for people that own their own domains. Problem for me is that sometimes people will send me email to addresses that don't exist, but it is still legitimate, so I try to make sure I can view it all. And that is why I use gmail to filter out the spam :)

This argument doesn't make sense - people sending email to your domain with typos will *never* know that you received the email, or whether it went into a black hole.  However, a bounced message due to a typo in the recipient address WILL tell them they have a typo!

You can't have your cake and eat it too.  Perform proper recipient validation or accept the consequence of bounce messages.  And never bounce back bounce messages or you will become blacklisted as a backscatter source.

Catch all addresses today are foolhardy.  Use address extensions if you want.

MrC

---

