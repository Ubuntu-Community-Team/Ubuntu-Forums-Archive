---
title: "Setting up secure email"
date: 2017-08-18
forum: Security
---

### Post by Curlyp on 2017-08-18
Hello Community,

I am not sure if this is the right spot (or even correct forum to post on).  I have received good information for the community in the past so it is worth a try.

I am looking to either create my own email server or purchasing private email hosting that I can use with my own domain.  I have been looking into the laws and it seems Switzerland, Norway, and many EU countries is the best place to have the server located, as they have very strict laws on privacy and data protection.  Currently I use Google/Microsoft for my emails, but they are big into data mining and invading privacy.  I want to move away from it and use my own domain.

What is the best route for me to take and where should I start?

Thanks!

---

### Post by TheFu on 2017-08-18
Email security it hard, because it depends on everyone you email also caring.  Most do not.  I've cut off yahoomail users (even a relative) over their lack of security.  I've considered cutting off gmail and hotmail too.  Those are the 3 largest offenders in my group of contacts/friends.

Sadly, a close relative has turned all his email (including his business) over the google.  He tried running his own email server for decades and found it too hard after multiple hacks and having his subnet black holed.

I've been running a personal email server for decades - since 1995.  I've also run corporate email servers since 1994.  It has gotten harder and harder over the years.  Used to be that SMTP was one of the easiest services to have.  Fighting spam has made it complicated.

Putting data your want to be secure on someone else's computer is never a good idea.  In many locations, your home is the safest place for it, but there are problems doing that without a static IP.  

Are you concerned about govt over-reach or just general security?

Would using GPG be sufficient for your needs, since that will work with any email provider.  I use GPG to exchange super secret recipes within the family.

There are other modes of communications which might fit your needs too - RetroShare.  It is a hassle, since everyone needs to setup the system on their computers and become part of your network.  For laptops, this is non-trivial due to the changing locations and network access.

Start with GPG.  Thunderbird has addons that make it relatively easy in daily use. Setup is a pain, but gpg basically works from thick email client.  People who use webmail don't care about security, so gpg - well, secure gpg - doesn't work with those users.

Have you checked out protonmail?

---

### Post by Curlyp on 2017-08-18
> **TheFu said:**
> Email security it hard, because it depends on everyone you email also caring.  Most do not.  I've cut off yahoomail users (even a relative) over their lack of security.  I've considered cutting off gmail and hotmail too.  Those are the 3 largest offenders in my group of contacts/friends.

Sadly, a close relative has turned all his email (including his business) over the google.  He tried running his own email server for decades and found it too hard after multiple hacks and having his subnet black holed.

I've been running a personal email server for decades - since 1995.  I've also run corporate email servers since 1994.  It has gotten harder and harder over the years.  Used to be that SMTP was one of the easiest services to have.  Fighting spam has made it complicated.

Putting data your want to be secure on someone else's computer is never a good idea.  In many locations, your home is the safest place for it, but there are problems doing that without a static IP.  

Are you concerned about govt over-reach or just general security?

Would using GPG be sufficient for your needs, since that will work with any email provider.  I use GPG to exchange super secret recipes within the family.

There are other modes of communications which might fit your needs too - RetroShare.  It is a hassle, since everyone needs to setup the system on their computers and become part of your network.  For laptops, this is non-trivial due to the changing locations and network access.

Start with GPG.  Thunderbird has addons that make it relatively easy in daily use. Setup is a pain, but gpg basically works from thick email client.  People who use webmail don't care about security, so gpg - well, secure gpg - doesn't work with those users.

Have you checked out protonmail?

TheFu - thanks for your in depth response! You are right, most folks do not care about security or are just oblivious to it in gerneral. I work in Cyber Security field so I am on my wife to make sure she has her things locked down!

I thought about running an email sever out of my house (I would purchase a static IP through my ISP), but I don't know enough about the hardware to keep it fully secure from attacks, etc.  I have never worked for email servers before, so my knowledge really lacks there.

No I am not worried about gov't over-reach (with my job - the gov't knows everything about me already). This is just more for general security.  I am not into doing anything illegal, laundering, selling drugs or whatever it may be; I just don't want Microsoft and Google all in my business data mining the hell out of my emails.  They don't need to know I purchased xyz from amazon, bought a product from xyz store, or received an email from my wife/friend complaining about something.

I have thought about GPG, but I still don't want any to use Google, Yahoo, Microsoft, etc, as the mail server!  I have seriously considered Protonmail; however, for my wife and I to have our own separate email address with username and login, it would cost us $88 a year.  That is not that bad, but I was hopping for something a little cheaper...maybe $4-$5 a month for 10-15gb of email storage on a server over in Switzerland or Norway.  I've even looked at digital ocean for just server space, but I don't know if there servers are located overseas and where to being on setting up my own email server.

Thanks!

---

### Post by SeijiSensei on 2017-08-18
[Linode]("https://www.linode.com") maintains a server farm in Frankfurt, Germany.  (They also have one in London, but given Brexit, I'd probably choose Frankfurt.)  You can spin up pretty much any mainstream Linux distribution on a virtual server there, including Ubuntu. You can rent a server with 1 GB of memory and 20 GB of storage for $5/month.  That's plenty of capacity for an email server.

Beyond that you'll need to read some online guides.

---

### Post by TheFu on 2017-08-18
You can run an email gateway on the lowest end machine from a provider and have it sent to your home system. If your home system (a raspberry pi would be sufficient) isn't available, then any inbound emails would sit on the gateway.  When your home server is  finally available, it would flush all email to it.  That would get the emails into your house which has special greater protections in the USA.  Amazon has a free tier which would be more than enough for an email gateway to a house. Plus you wouldn't need a static IP for the house.  I'm not suggesting that Amazon be used, just that a very low end system with good connectivity is more important than Ghz or RAM.

All your concerns about amazon, microsoft, google, apple, oracle, your ISP and whatever your wife is complaining about are already known to everyone. If your wife sends email outside your server, it is safer to assume it is known than to have any false sense of security.  SMTP is a postcard, after all.  Enough servers don't do SMTPS to make that assumption false.

Protonmail is free - at least my accounts there are.  I use it about 10 times a year and only through a VPN.

There is a reason that google assumes their network, including internal network, is non-secure.  They have their network architecture and security information online - mainly they use service-to-service certificates. Everything on storage and network is encrypted.

Email is never going to be secure.  Even when using gpg, there is leakage due to the headers. Those headers are shared all over the world with LE everywhere.  For years, there have been laws that mandated it.  The EU repealed those laws after 5+ yrs of mandating the data.  It was sent to a data center in France, BTW.

The US and Chinese govts know all about me too - China thanks to the USGovt leaking my data.  Data wants to be free. Seems the best idea is not to have the data if you want it to be secure and never use a computer or network to share anything you don't want known.  If you work and follow data security, you know this already. And clearly, never use or carry a cell phone. If you have one or 5, keep them in faraday bags and never let them be enabled in the same location at the same time. For the non-personal devices, never use them near your neighborhood or work.  OpSec is hard - even for the CIA. They were caught by Italians kidnapping someone due to poor opsec.

Absolute security is impossible in the modern world. 

What is good enough is hard to determine since we all have different acceptable risk and inconvenience levels.

Do you really want to use email? ;)

---

### Post by Curlyp on 2017-08-18
> **TheFu said:**
> You can run an email gateway on the lowest end machine from a provider and have it sent to your home system. If your home system (a raspberry pi would be sufficient) isn't available, then any inbound emails would sit on the gateway.  When your home server is  finally available, it would flush all email to it.  That would get the emails into your house which has special greater protections in the USA.  Amazon has a free tier which would be more than enough for an email gateway to a house. Plus you wouldn't need a static IP for the house.  I'm not suggesting that Amazon be used, just that a very low end system with good connectivity is more important than Ghz or RAM.

All your concerns about amazon, microsoft, google, apple, oracle, your ISP and whatever your wife is complaining about are already known to everyone. If your wife sends email outside your server, it is safer to assume it is known than to have any false sense of security.  SMTP is a postcard, after all.  Enough servers don't do SMTPS to make that assumption false.

Protonmail is free - at least my accounts there are.  I use it about 10 times a year and only through a VPN.

There is a reason that google assumes their network, including internal network, is non-secure.  They have their network architecture and security information online - mainly they use service-to-service certificates. Everything on storage and network is encrypted.

Email is never going to be secure.  Even when using gpg, there is leakage due to the headers. Those headers are shared all over the world with LE everywhere.  For years, there have been laws that mandated it.  The EU repealed those laws after 5+ yrs of mandating the data.  It was sent to a data center in France, BTW.

The US and Chinese govts know all about me too - China thanks to the USGovt leaking my data.  Data wants to be free. Seems the best idea is not to have the data if you want it to be secure and never use a computer or network to share anything you don't want known.  If you work and follow data security, you know this already. And clearly, never use or carry a cell phone. If you have one or 5, keep them in faraday bags and never let them be enabled in the same location at the same time. For the non-personal devices, never use them near your neighborhood or work.  OpSec is hard - even for the CIA. They were caught by Italians kidnapping someone due to poor opsec.

Absolute security is impossible in the modern world. 

What is good enough is hard to determine since we all have different acceptable risk and inconvenience levels.

Do you really want to use email? ;)

Thanks again for the great information. 

I have never setup an email gateway before, so I will need to look into it.  Do you have any pointers of some good sites/software I could read up on?

You are absolutely correct; "amazon, microsoft, google, apple, oracle, your ISP and whatever your wife is complaining about are already known to everyone"!  Which is why I want to get away from the Microsoft, google, etc. lol.  The one thing with Proton mail versus lets say, google, or outlook, is "All emails are secured automatically with end-to-end encryption. This  means even we cannot decrypt and read your emails. As a result, your  encrypted emails cannot be shared with third parties."  In addition, since their servers are located in Switzerland, all user data is protected by strict Swiss privacy laws.  Here is America, there is no such thing as privacy!

You mentioned that you use ProtonMail.  How come you only use it through VPN?  Is there an issue with connecting to the site directly without masking our IP through VPN?  I think I may just end up spend the $88 a year for the privacy and encryption.  They seem to have the best package and allow folks to use their own domain for email addresses.

You are correct again, email will never be 100% secure nor is there such a thing as absolute security!  However, there are some services/encryptions that are better than none!

---

### Post by kevdog on 2017-08-28
Unless you're an expert -- don't run your own email server.  Yea I know a statement like this just probably makes you want to do it more, but take time and read the forums and internet about the hundreds of people that have done this and just later came to the conclusion it just wasted and exceedingly large portion of their time.  You can go proton mail, or gpg, or s/mime or just use Signal if texting is what you want.  Just save yourself the headache.  In a nutshell I think this is what the other contributors to this thread are saying, just not in a so blunt way

---

### Post by HermanAB on 2017-08-29
Hmm, first you need to decide who exactly you want to communicate with.

If it is public email, then just use Google or something as you are doing now.  Since nobody else cares about security, secure email won't work when you are the only one that does...

If it is a select group of people - consider setting up something like Retroshare.

---

### Post by gordintoronto on 2017-08-29
I'm with kevdog. If your ISP provides an email address (eg. [email]gordc@myisp.ca[/email]) then you can use GPG with it.

The vast majority of people are too boring to be worth intercepting their email. Google and Microsoft might mine your email (but mostly your browsing) to send you "relevant" ads, but they don't care about you as an individual.

---

### Post by HermanAB on 2017-08-30
The main problem with running your own mail server (I have actually done it for about a decade out of sheer bloody mindedness), is spam.  

The faster your computer system, the more spam you get.  The more filters you throw at it, the bigger the head-ache becomes to keep false positives down.  In the end, the only solution is to pass the buck to a place with a small army of computer scientists and aircraft hangar size warehouses full of computers - i.e. Google or Microsoft.

---

### Post by TheFu on 2017-08-30
I use a tiny VM that is an email gateway (scrollout) to handle 99% of the spam.  The main email server barely sees any spam.  Not hard at all.  Can't remember the last time I did any filter tuning ... perhaps a year ago.

Slowing down email delivery on the gateway is possible.  I don't remember the name of the tool. It is built into the gateway that I use.  Some people automatically reject email whenever a new, never-seen-before server makes a connection.  Then on the 2nd attempt, it is allowed in for more checks.  Most spammers never come back.

---

### Post by SeijiSensei on 2017-08-30
> **HermanAB said:**
> The main problem with running your own mail server (I have actually done it for about a decade out of sheer bloody mindedness), is spam.
I've used [MailScanner](http://mailscanner.info) in conjucntion with SpamAssassin and ClamAV for at least a decade now.  That combination has proven very effective at reducing spam and eliminating viruses.  You do have to do some tweaking of the SA rulesets and MS configuration at the outset.

---

### Post by HermanAB on 2017-08-30
Ayup - Spamassassin, Clamav, Spamhaus block lists, Greylisting, time delays... all a total waste of time and resources, since for every good message your server has to process about 100,000 junk messages.

---

### Post by SeijiSensei on 2017-08-30
I stop a bunch of crap at the doorstep with sendmail's access database.  Just blocking mail from servers that don't have reverse DNS resolution enabled, and using delays like "[greetpause]("http://www.deer-run.com/~hal/sysadmin/greet_pause.html")" can help a lot.  (Postfix has the "sleep" and "reject_unauth_pipelining" options to accomplish the same task.)

I have 917 nonspams and 3160 spams so far this week.  Looking back a few weeks that's a pretty typical ratio for me.

That's just my server.  I have a similar setup at a client with 200 employees.  I get similar or better ratios there.  Last week saw an even split between spam and non-spam.  There we block more things at the doorstep, particularly mail from senders and servers in country-code domains other than .us and .ca.  (The client is a domestic health-care agency that doesn't communicate overseas.)

---

### Post by Curlyp on 2017-09-03
> **kevdog said:**
> Unless you're an expert -- don't run your own email server.  Yea I know a statement like this just probably makes you want to do it more, but take time and read the forums and internet about the hundreds of people that have done this and just later came to the conclusion it just wasted and exceedingly large portion of their time.  You can go proton mail, or gpg, or s/mime or just use Signal if texting is what you want.  Just save yourself the headache.  In a nutshell I think this is what the other contributors to this thread are saying, just not in a so blunt way''

In general, what email hosting company would you recommend so I can use my own domain and get away from the data mining from Microsoft, Google, Yahoo, etc?

> **HermanAB said:**
> Hmm, first you need to decide who exactly you want to communicate with.

If it is public email, then just use Google or something as you are doing now.  Since nobody else cares about security, secure email won't work when you are the only one that does...

If it is a select group of people - consider setting up something like Retroshare.

Basically anyone I communicate with via email.  If I send my buddy an email, wife, a random person at a company inquiring about something, etc.  I want to keep my communications secure and in the European laws, which are much better than U.S.

> **gordintoronto said:**
> I'm with kevdog. If your ISP provides an email address (eg. [EMAIL="gordc@myisp.ca"]gordc@myisp.ca[/EMAIL]) then you can use GPG with it.

The vast majority of people are too boring to be worth intercepting their email. Google and Microsoft might mine your email (but mostly your browsing) to send you "relevant" ads, but they don't care about you as an individual.

True, but I don't want to given in to Google and Microsoft. They don't need to make anymore money off data mining my emails!  I would use my ISP, but I change ISPs to keep really good deals and low prices.  I would rather use my own domain (which I have purchased).

---

### Post by SeijiSensei on 2017-09-03
> **Curlyp said:**
> Basically anyone I communicate with via email.  If I send my buddy an email, wife, a random person at a company inquiring about something, etc.  I want to keep my communications secure and in the European laws, which are much better than U.S.
Unless you and every one of your correspondents set up GPG- or PGP-encrypted messaging, this is an impossible goal.  Ordinary e-mail has the security of a postcard.  

What do you mean by "secure?"  Transport security?  Encryption of your account on the server?  Again anything other than end-to-end encryption with public/private keys should not be considered "secure."

---

### Post by Curlyp on 2017-09-03
> **SeijiSensei said:**
> Unless you and every one of your correspondents set up GPG- or PGP-encrypted messaging, this is an impossible goal.  Ordinary e-mail has the security of a postcard.  

What do you mean by "secure?"  Transport security?  Encryption of your account on the server?  Again anything other than end-to-end encryption with public/private keys should not be considered "secure."

Gotcha, that I had a misunderstanding of private secure emails.  What I mean by "Secure", is that the data is not stored, IP's are not logged, privacy, etc.  ProntonMail and Posteo have their severs in Europe and they have strict privacy laws.  I guess what I am really looking for is an email hosting company that keeps their servers overseas which are governed by laws that embrace privacy.

---

### Post by SeijiSensei on 2017-09-04
Well, of course the mail is going to be stored unless you set something up to suck the mail down to a server in your home or office.  If you use IMAP, all mail sits on the server until deleted.  With POP3 your server can retrieve the traffic and delete it from the server as it does so.  You can use the **fetchmail** program for this task.

---

### Post by Curlyp on 2017-09-04
> **SeijiSensei said:**
> Well, of course the mail is going to be stored unless you set something up to suck the mail down to a server in your home or office.  If you use IMAP, all mail sits on the server until deleted.  With POP3 your server can retrieve the traffic and delete it from the server as it does so.  You can use the **fetchmail** program for this task.

Thank you very much.  Is there an email hosting company your recommend I use that allows me to use my own domain?

---

### Post by SeijiSensei on 2017-09-05
I can't help with that, I'm afraid.  I've hosted my own mail for a couple of decades now.

---

### Post by HermanAB on 2017-09-07
BTW, just like Spam, about 99% of spam originates from the USA.  This is clear because the spam quantities go up and down according to the USA holidays.  However, the actual spam servers can be all over the world.

Anyhoo, I had enough of spam.  It was a nice mental exercise to stick it to the spammers, but eventually I got fed-up with it and went over to the dark side - gmail.

---

### Post by Curlyp on 2017-09-07
> **SeijiSensei said:**
> I can't help with that, I'm afraid.  I've hosted my own mail for a couple of decades now.

No problem.  Thank you for trying though!

---

