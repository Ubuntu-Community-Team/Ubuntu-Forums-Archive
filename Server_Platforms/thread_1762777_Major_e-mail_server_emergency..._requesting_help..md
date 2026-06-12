---
title: "Major e-mail server emergency... requesting help."
date: 2011-05-19
forum: Server Platforms
---

### Post by jeff[0] on 2011-05-19
Hey all. In a lot of trouble here and I've done my best but I cannot solve this.

Just for reference, I've followed flurdy's e-mail server guide down to the letter (aside from correcting some typos he made, etc).

Everything has been going great for awhile, until about 4 days ago. We started to get listed on blacklists as sources of spam.

I can confirm that there are no other machines on the network that the e-mail server is on, aside from the router of course.

I am going through the logs as best I can, but I am only seeing information like this:

> May 19 15:21:20 mail postfix/error[12498]: 8C37F607B22: to=<FBI@office.org>, relay=none, delay=11739, delays=11739/0.06/0/0.09, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to office.org[69.64.147.249]:25: Connection timed out)


Ok, this tells me I have some ridiculous bogus connection going on, but I don't see what I can do about it? I have a million lines going on about bogus "FBI" addresses.

I've used every tool I can find to confirm that I am not an open relay or an open proxy (every test confirms that I am not).

I really am at a loss at what to do here.. I see all this bad traffic coming in and I don't know how it's doing it, or how to stop it anymore.

And again, just for reference, I've setup all the security, sender restrictions, etc, using the flurdy e-mail guide for 10.04 ([http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/))

:confused:

---

### Post by jeff[0] on 2011-05-19
Even have some amavis scans going on which is picking up on this traffic, but I still have no idea how to stop it.

> May 19 12:04:47 mail amavis[22558]: (22558-11) Checking: e7K+FlO7cuIr [82.200.11.166] <FBI@office.org> -> <gers@adelphia.net>,<gert.hartwig.lescow@alum.mit.edu>,<gerryw@austarmetro.com.au>,<gershopoin@bigpond.com>,<gers73@chariot.net.au>,<archiver@defender.mohawkschools.org>,<gervin@hughessupply.com>,<ges@medegal.com.au>,<gersh2@n2basketball.com>,<gertib@nielsen.mail.dk>,<gersdahl@optusnet.com.au>,<gershy@optusnet.com.au>,<gersal62@wmconnect.com>,<gertrude.thompson@worldnet.att.net>,<gervaise_minne@yahoo.com.au>,<geschaf2@yahoo.com.au>,<gesermartinez@yahoo.com.au>


---

### Post by nsnidanko on 2011-05-20
Hi Jeff,
 
Do you have any hosts relaying email via your smtp? I had that, where infected host (from the trusted network in postfix) was pumping spam via our email gateway. Cleaning it resolved the problem. Try to play with mynetworks in postfix's main.cf file to make it tight as possible. Also you can try investigating using netstat -a but it is hard on busy mail server. 
 
Let me know,
Naz

---

