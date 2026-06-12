---
title: "Email Server Recommendation"
date: 2008-01-12
forum: Server Platforms
---

### Post by tbrothers on 2008-01-12
I'm looking for a mail server recommendation.

I have 2 domains with approximately 10 mailboxes each and will use Fetchmail to pull down from POP accounts.

It is not a show stopper but it would be nice to have webmail access.

I'm looking for something Reliable.
I'd like something that will not take 3 days and a fried brain to setup and configure (I know - that's asking a lot)

---

### Post by chris.zeman on 2008-01-12
The way I understand it, you have your server already setup to retrieve messages from an external mail server. Please correct me if I'm wrong, because the following information is useless otherwise.

Provided your server already has an HTTP server (such as Apache) installed, along with PHP, there are plenty of webmail clients available that are easy to setup. 

My personal favorite is DWMail. It's not free, but it's reasonably priced and nice. You wouldn't need to use Fetchmail to pull messages from an external server, either. DWMail can log you into any POP3 or IMAP server. It's easy to setup (in my opinion), and should take you no more than half an hour to get going if all software pre-requisites are met. 

Squirrelmail is a free client you could use. I personally don't like Squirrelmail, but it seems to be pretty popular.

Good luck!
Chris

---

### Post by tbrothers on 2008-01-12
My email is currently hosted at my ISP.  I want a mail server in my house that will fetch from the ISP.

---

### Post by HermanAB on 2008-01-12
Well, if you want it working yesterday, then there is only one answer: 
[http://www.citadel.org/doku.php/installation:easyinstall:easyinstall](http://www.citadel.org/doku.php/installation:easyinstall:easyinstall)

That will take about 20 minutes.  

Any other mail system with webmail etc will take you at least 2 weeks to get to work.

Cheers,

Herman

---

### Post by tbrothers on 2008-01-12
CITADEL looks like a great product.  I think I will install it tonight.

---

### Post by HermanAB on 2008-01-12
Ensure that your machine has a proper, fully qualified hostname before you install.  Even if it is a home server and you don't really have a domain name, use your ISP domain name to give it something of the form: citadel.telus.net

Otherwise, Citadel will refuse to send mail, which can be rather perplexing.

You'll have to figure out how to hook fetchmail to it (it is in the documentation somewhere) and you have to set it to relay outgoing mail via your ISP mail server, eg. mail.telus.net.

Anyhoo, subscribe to the Uncensored forum and ask questions there.  You may even be honoured with an answer from the venerable Ignatius T. Foobar himself.

I suspect that about 2 weeks after setting it up, you'll wish to have your own domain and make your forums, chat and instant messaging public to all your relatives and friends.  In that case, buy a domain name at Godaddy and upgrade your ISP account to a 'Server' account.  That will cost about $10 more per month.  They will then remove all the blocked ports, give you at least two IP addresses and likely a lot more bandwidth too.

Cheers,

Herman

---

### Post by chris.zeman on 2008-01-12
That does look good! I'll have to check it out!!! :)

---

### Post by tbrothers on 2008-01-12
I already have around 20 domains  :)

Yep - I will probably make one available to family and friends.

Thanks again!

---

### Post by tbrothers on 2008-01-14
CITADEL - What a GREAT product!!

Thank you Herman for the recommendation.

1. Fresh install of CentOS 5.1,
2. Installed and configured DNS.
3. Installed one library.
4. Did the Easy Install from CITADEL.

60 seconds after the installation was complete I sent my first message.  I spent the next 30 minutes getting familiar with it and finalized the configuration.

Really - That's It.

CITADEL is a Very Nice product as well.  The webmail is Fast, looks nice, intuitive, etc. CITADEL has a Full set of Groupware features.

I'm in the process right now of setting up another freshly installed server to use as a hot stand-by.

---

### Post by HermanAB on 2008-01-14
My standby server is a Virtual Machine which I can activate on another server using VMware.  It will be slow, but it will work OK till I can get the primary back online.

---

### Post by artcancro on 2008-01-15
> **HermanAB said:**
> You'll have to figure out how to hook fetchmail to it (it is in the documentation somewhere)

Actually, you don't even have to hook up fetchmail to it anymore.  The most recent version of the Citadel system has built-in POP3 aggregation.  You simply configure the remote account from the web interface and Citadel will periodically retrieve mail from that account (or accounts) and place it in your mailbox.  No fetchmail needed.

---

### Post by salaberrios on 2008-01-17
How do you set up mail boxes? what if yo are hosting multiple sites? It conflicts with Apache. How does it compare with ZImbra? Citadel is cool but you have tp shut off a lot of processes so it will run correctly. I still haven't got it to send an email yet...LOL!

---

