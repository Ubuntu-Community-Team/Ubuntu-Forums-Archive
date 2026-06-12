---
title: "Basic Small Office IT Security?"
date: 2012-05-20
forum: Security
---

### Post by Grandma_DOG on 2012-05-20
Simple Question, what is the basic security measures you'd recommend for a 3 man office?

Security, unfortunately, is always a cost. It never brings in revenue.  There is a trade off of security which prevents downtime vs expense of locking it all down.

I've been an Ubuntu user for years, and have had to step up my knowledge of security when we began getting web hack attacks last year from China.  I had to learn about dd-wrt and install a better firewall, but I know that firewalls are not the biggest hole but one that gets the most attention.

Part of the answer lies in what we do, which is just oil and gas data warehousing.  A breach would steal data which is only valuable to 100 companies on earth. Further the data is perishable, so after a year or two it is worthless.  Thus, we've been more concerned with silo-ing our CRM and our main db.  

But I'd like to hear what else should we do.  Setting up a snort station seems like a bit of a cost and overkill for a 3 man office. App-armor maybe? 

I've read the links on Basic Safety and some of the more advanced by bodhi.zazen Ubuntu Security.

I know I need to meet the basic level, but beyond that I'd like to hear your opinions.

---

### Post by Ms. Daisy on 2012-05-20
Totally depends on what you're running in your office. Do you have a file server? email server? web server? If so, separate machines or all one? What's facing the internet? Will everyone work from home and connect to the office remotely? What protocol? 

What platform is everything running on?

I take it one of the 3 men in the office will deal with IT, but that person has other oil/gas responsibilities? How much time do you have to dedicate to IT services?

---

### Post by SparTacux on 2012-05-20
Well - I very much doubt the pentagon or any other major security establishment have all their PC's exposed to the internet. 

One possible idea is to have  two separate networks. One for internal use and one for internet use. You'd need twice as many computers but it would separate all your sensitive data from the web. 

Just an idea...

---

### Post by Grandma_DOG on 2012-05-20
> **Ms. Daisy said:**
> Totally depends on what you're running in your office. Do you have a file server? email server? web server? If so, separate machines or all one? What's facing the internet? Will everyone work from home and connect to the office remotely? What protocol? 

What platform is everything running on?

I take it one of the 3 men in the office will deal with IT, but that person has other oil/gas responsibilities? How much time do you have to dedicate to IT services?

That is the rub, one of us has to do it. I've got the most experience, so it'll likely be me.  Outsourcing is likely to be too expensive. On the flip side my time is expensive, so I need to balance the time needed to defend 98% as the last 2% costs more to defend than a breach would cost.

Most of our web hosting is external, but we have one webserver in house that also hosts a GIS stack.  ssh, www, and VNC face out. SSH had attacks all the damn time until we shut that down. Apparently the Chinese put petrochemical targets on their priority list last year. We saw the honker nation knocking on our back doors.

I joined OWASP and now know we need to tighten up some php code. So we'll get Top10 compliant later this year.

Then we have two db, a Postgres and mySQL on a single box, dedicated. Only the db ports open to the world. rthunter runs nightly to look for suspicious stuff.

And one accounting machine faces the web, vnc port only.

After we're done some security upgrades recommended here, we'll hire a pen tester to test us and then fix more from that analysis.

---

### Post by Cheesemill on 2012-05-20
> **Grandma_DOG said:**
> And one accounting machine faces the web, vnc port only.

First step is to stop exposing VNC to the internet. VNC is inherently insecure and the password can be cracked in seconds. If you must use VNC for whatever reason then bind it to accept connections from localhost only and use SSH tunnelling to connect.

---

### Post by Ms. Daisy on 2012-05-20
> **Grandma_DOG said:**
> Most of our web hosting is external, but we have one webserver in house that also hosts a GIS stack.  ssh, www, and VNC face out. SSH had attacks all the damn time until we shut that down. Apparently the Chinese put petrochemical targets on their priority list last year. We saw the honker nation knocking on our back doors.
As far as ssh goes, it's normal for bots crawling the web to brute-force your ssh password.  I presume that you have followed the security recommendations (use keys, disable password login) here?

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

For the rest of security, I recommend you do some reading.  
Google for a PDF: NIST SP 800-123, Guide to General Server Security

You may seriously consider hiring a contractor to set up the system and to give you some routine tasks that you'll need to do to maintain the system.  Get some quotes, then compare that to the cost of your time that it will take to get the same thing done.

---

### Post by CharlesA on 2012-05-20
> **Grandma_DOG said:**
> Then we have two db, a Postgres and mySQL on a single box, dedicated. Only the db ports open to the world. rthunter runs nightly to look for suspicious stuff.

Is there a reason your DB servers are exposed to the internet?

> And one accounting machine faces the web, vnc port only.

Is this a Windows box? Why are you running VNC?

> After we're done some security upgrades recommended here, we'll hire a pen tester to test us and then fix more from that analysis.

If you hire a pen tester, they are going to have fun owning your network.

---

### Post by Ms. Daisy on 2012-05-20
> **CharlesA said:**
> If you hire a pen tester, they are going to have fun owning your network.
You will be TOTALLY wasting your money for a pen test if you haven't employed basic security measures first. But that will require research on your part or hiring a pro to do it for you.

---

### Post by CharlesA on 2012-05-20
> **Ms. Daisy said:**
> You will be TOTALLY wasting your money for a pen test if you haven't employed basic security measures first. But that will require research on your part or hiring a pro to do it for you.
Agreed.

---

### Post by Grandma_DOG on 2012-05-21
> **CharlesA said:**
> Agreed.

I agree, too. 

Which is why we need to button up first. The question is how much.

---

### Post by mr-woof on 2012-05-21
Me personally, i'd lock down everything as much as possible, try and perform an audit of your systems.

what ports/services are open to the net? Do we need this to be open etc?

Do you have any sort of hardware firewall?

I'd also consider, depending on your hardware running the webserver in a separate dmz.

---

### Post by Ms. Daisy on 2012-05-21
> **Grandma_DOG said:**
> I agree, too. 

Which is why we need to button up first. The question is how much.
Lots.  I'm a glutton for punishment so I'm going to give you some reading material.  There is absolutely no way that anyone can give you all the security measures needed in a help forum thread.  The best you can hope for is a good reading list.  It sounds like you're totally opposed to hiring a professional to set it up properly, so at least do some SERIOUS reading on the subject.  

At the very least PLEASE read these:

(google for this PDF in the SANS reading room) A Small Business No Budget Implementation of the SANS 20 Security Controls

csrc.nist.gov/publications/nistir/ir7621/nistir-7621.pdf 

[http://www.applicure.com/blog/database-security-best-practice](http://www.applicure.com/blog/database-security-best-practice)

And then if you're still interested, read these too:

[http://internalaudit.wayne.edu/security-practices.php](http://internalaudit.wayne.edu/security-practices.php)

[http://www.belltcg.com/index.php/best-practices-for-network-security-in-small-and-medium-size-businesses.html](http://www.belltcg.com/index.php/best-practices-for-network-security-in-small-and-medium-size-businesses.html) (written for windows but the basic concepts are the same across platforms)

[http://www.metroinfo.com/keeping-the-office-running-it-best-practices-for-small-businesses.php](http://www.metroinfo.com/keeping-the-office-running-it-best-practices-for-small-businesses.php)

[http://operationstech.about.com/od/informationtechnology/a/Information-Security-Best-Practices.htm](http://operationstech.about.com/od/informationtechnology/a/Information-Security-Best-Practices.htm)

[http://www.corporatecomplianceinsights.com/information-security-best-practices/](http://www.corporatecomplianceinsights.com/information-security-best-practices/)

---

### Post by CharlesA on 2012-05-21
> **mr-woof said:**
> Me personally, i'd lock down everything as much as possible, try and perform an audit of your systems.

what ports/services are open to the net? Do we need this to be open etc?

Do you have any sort of hardware firewall?

I'd also consider, depending on your hardware running the webserver in a separate dmz.

This pretty much sums it up. I'm still kinda curious why VNC would be exposed to the internet on an accounting box. That seems like all sorts of bad as VNC is not encrypted and easily cracked if a strong password is not in use.

TBH, it is better *not* to use VNC unless it is being used over SSH or a VPN.

If remote access is really needed, I would set up a VPN and only have that exposed to the internet. Connect to the VPN and you have access to everything on the internal network.

> **Ms. Daisy said:**
> Lots.  I'm a glutton for punishment so I'm going to give you some reading material.  There is absolutely no way that anyone can give you all the security measures needed in a help forum thread.  The best you can hope for is a good reading list.  It sounds like you're totally opposed to hiring a professional to set it up properly, so at least do some SERIOUS reading on the subject.

+1. It takes a while to get good at security and it involves a ton of reading. :)

---

### Post by mr-woof on 2012-05-21
Like Charles, I'm also very curious why you have vnc open to the internet and totally agree on the VPN point. Get yourself a hardware firewall and setup a vpn :)

---

### Post by computeratin on 2012-05-21
There's no quick, cheap, easy fix to this. It will take time, knowledge and money; especially if the Chinese have painted a target on you.
 
I've been a desk jockey at several DoD facilities over the years and was good friends with a lot of the IT guys. I can't get in to specifics, but I will say they employed everything that everyone here is telling you and more.
 
If you really need to keep the Chineese out of your data then you need to hire a pro with a mil-spec background in state level IT espionage.
 
I'd recommend that you start reaching out to folks you know for somebody with a good rep and the right background; preferably someone with Cyber Command experience. Or at the very least CEH and CISSP.
 
And then be prepared to keep them on retainer. This is not going to be a "set it and forget" solution.
 
How important is your data to you? Because now that the Chinese after it you're in an arms race. Every new trick under the sun will be tried on you as soon as it comes out until they either own you and your data or own you and determine that you have nothing of value.

---

### Post by Ms. Daisy on 2012-05-21
If you're legitimately being targeted then I would agree.  However, based on the information given by the OP, this company's services are low-hanging fruit. The attacks the OP experienced are likely just automated ones scanning for poorly configured internet-facing apps.

Honestly, in order to configure security you need to understand your risks.  Again a **professional** can tell you whether you're actually being targeted by the Chinese or if it's just a basic bot attack.  It's important to answer that and defend appropriately.  You'll be totally wasting resources if you defend against targeted attacks if there are no chances of any happening.  Vice versa if you only defend against basic bots then you'll get owned quickly by a targeted attack.

---

### Post by computeratin on 2012-05-21
I agree 100% on the pro.
 
But, I'll have to disagree on the low hanging fruit; even if it is just auto scanners at the moment. Especially since the Chinese are very fond of both "thin edge of the wedge" and "boot strapping" tactics.
 
If your data is only of use to 100 computers in the world then I'll *assume *(with all of the inherient associated risks) that the data you're warehousing will, at some point, play in to projections of national reserves. Which is data the Chinese (and a lot of others) would absolutely kill for (literally); espeically with all of the wild variations coming out of the projections for the Williston and Marcellus basins.
 
Which is why you need a ****_pro*_*** with the right background. Not just one with a handle on the IT aspec, but who will also understand the market and strategic value of your data so that they can design an appropriate solution for you.

---

### Post by OpSecShellshock on 2012-05-21
It wouldn't do to just safeguard the production data against the risks of industrial espionage if you aren't also protecting your financial and payroll transactions from regular financially motivated thieves, who prefer to hit small businesses (assuming your shop's in the US, basically individual bank account holders are not liable for fraudulent charges/transfers, but business account holders are, so if you get hit you're pretty much on your own).

Luckily that part's easy and pretty cheap. All you need to do is have a computer that is dedicated to only doing the financial transactions and that is never under any circumstances used for web browsing or email. It should be shut off whenever it isn't being used to perform a transaction. I say it's cheap because the cost of acquiring a separate computer for this is way lower than the cost of implementing monitoring systems/software and then actually spending the time to constantly watch them, and it's also less than the labor cost of repairing a computer that is used for financial transactions and browsing/email if it gets malware on it.

As to the production systems and data, well that is quite a big topic. The above advice about key-based remote authentication over SSH and not using VNC is the most important. Have a look at the links provided in previous posts. A good place to start might be making a list of things that absolutely have to happen in order for you to meet your business requirements, and go from there. A well configured system should do everything you need and only what you need.

---

