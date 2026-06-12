---
title: "Email System with Web Frontend"
date: 2008-08-01
forum: Server Platforms
---

### Post by smccarthy945 on 2008-08-01
I would like some suggestions on what type of email server I can run on Ubuntu with a good web interface. Is there anything that is decent out there or do I need to go to a commercial package? 

I want to setup a free email system like gmail as project and need a solid email server and web interface. 

Thanks in advance.

---

### Post by windependence on 2008-08-01
[http://www.zimbra.com/](http://www.zimbra.com/)

It's great. Try it.

-Tim

---

### Post by skyfolly on 2008-08-02
roundcube or squirrelmail

---

### Post by artcancro on 2008-08-05
> **smccarthy945 said:**
> I would like some suggestions on what type of email server I can run on Ubuntu with a good web interface. Is there anything that is decent out there or do I need to go to a commercial package?

Steer clear of Zimbra, it's completely useless unless you buy the expensive proprietary version.  That's their dirty little secret.

You definitely want to try Citadel.  End-to-end GPL code, compact footprint, feature rich, nice web interface, completely self contained, easy to install.

[http://www.citadel.org](http://www.citadel.org)

---

### Post by smccarthy945 on 2008-08-05
Thanks. I looked at the Zimbra page and pretty much you can't do anything with the open source version. I will check out Citadel. I just don't see anything out there that is free and worth anything.

[www.icewarp.com](www.icewarp.com) has a linux version that looks good but costs $.

---

### Post by windependence on 2008-08-06
> **artcancro said:**
> Steer clear of Zimbra, it's completely useless unless you buy the expensive proprietary version.  That's their dirty little secret.

You definitely want to try Citadel.  End-to-end GPL code, compact footprint, feature rich, nice web interface, completely self contained, easy to install.

[http://www.citadel.org](http://www.citadel.org)

Just because you don't know how to operate a package or you are not familiar with it doesn't mean you should trash it. Plenty of folks here including myself have had very good results with Zimbra. It uses a REAL database for the backend as opposed to Citadel's flat file model, and the interface is , well, normal.

What exactly is it that you think Zimbra doesn't do that Citadel does? Also, they are different products. The OP asked about a mail server with a GUI interface. That's exactly what Zimbra is. Let him evaluate both and make his own decision.

-Tim

---

### Post by gtdaqua on 2008-08-06
Adding to what windipendence says, Zimbra is fantastic and the performance outblows Exchange. We are using it on a production environment and has been rock-solid since then. Its been more than 180 days without service disruption! The server never required a restart.

I dont think Citadel is Enterprise-grade. Zimbra is. It uses various opensource elements and the Anti-spam/AV is simply superb. With a little bit of tweak, you can almost completely block ALL spam.

Give Zimbra a try - you wont regret.

---

### Post by hyper_ch on 2008-08-06
postfix with squirrelmail or horde

---

### Post by MJN on 2008-08-06
I'd second the Postfix/Squirrelmail combination - unsurpassed in terms of meeting your stated requirements of 'free' and 'solid'.
 
A common criticism of Squirrelmail is its aesthetics however it is skinnable should appearance be high up your list of priorities. I like its native simple look - if I was into eye-candy I'd be using Vista.
 
Mathew

---

### Post by windependence on 2008-08-06
While I agree with you and hyper_ch that is is "free" and "solid", it certainly isn't easy to set up. Even myself, I cringe when I have to do one of these, and I consider myself pretty proficient. Zimbra actually uses postfix, MySQL, ldap, Tomcat, and few other things all packaged with an install script that makes it rather easy to set up. Like gtdaqua said, it's also been extremely stable for all the deployments I have done, and when there are any problems, I can admin it via ssh, OR the secretaries can add e-mail accounts through the web interface. It's just much less hassle in a production situation where you don't have time to mess around.

-Tim

---

### Post by artcancro on 2008-08-06
> **windependence said:**
> Just because you don't know how to operate a package or you are not familiar with it doesn't mean you should trash it.  It uses a REAL database for the backend as opposed to Citadel's flat file model, and the interface is , well, normal.You might consider taking your own advice, then, and making note of the fact that Citadel uses a database as well -- in fact, it even uses a database for the mail store (Z simply bolts on a copy of Cyrus, which has some metadata in db but stores the mail itself in flat files).

I also take exception to your assertion that there is any such thing as a "normal" user interface.  If by "normal" you mean "clone of Exchange" then ... well, if you want the user interface of Exchange then you should probably be running Exchange.

---

### Post by windependence on 2008-08-07
> **artcancro said:**
> I also take exception to your assertion that there is any such thing as a "normal" user interface.  If by "normal" you mean "clone of Exchange" then ... well, if you want the user interface of Exchange then you should probably be running Exchange.

Well some people claim the UI in Citadel is "different". I don't consider that a bad thing myself and I don't see anything wrong with Citadel's interface, but apparently some people do. 

The fact is if you are replacing Exchange in a small business as I often do, management usually wants something fairly familiar for the users. Whether I like it or not, it's not usually productive to argue with them. I'm just glad they're not using Micro$haft.

Why all the hostility? Can't you at least try to be objective? OSS is about choice. Personally, I don't care which one they use as long as they are using something other than M$. It's all about choice.

-Tim

---

### Post by MJN on 2008-08-07
> **windependence said:**
> Personally, I don't care which one they use as long as they are using something other than M$. It's all about choice.

You must have a different definition of choice than me! ;)

---

### Post by windependence on 2008-08-07
Well I know what you are saying, that M$ is a choice, of course, but IMHO only on the desktop. It has no business in MY server room. ;)

-Tim

---

### Post by gtdaqua on 2008-08-07
I tried Citadel. Its quite complex considering what Zimbra offers on its free edition (i cant call it open-source).

I really wanted to use Citadel as a secondary mail server, but its not quite as flexible as Zimbra. Obviously, Citadel on secondary would only be receiving and relaying emails but still not impressed. 

With each release, Zimbra is getting better although its next release 5.5 is getting super-delayed as there is not even a road map yet! 

Also know that Zimbra was purchased by Yahoo! just after 2 years in the market. The takeoever has not stopped Zimbra from releasing new versions, but definitely seems to have slowed down. Zimbra's free version is licensed under Yahoo Public License.

---

### Post by c2olen on 2008-08-07
Since it's all about choice, why not take a look at Kerio Mail Server.
It is feature rich too, support an exellent Ajax enabled web interface, supports multiple domains, spam scanning, email scanning, push mail and many other features. It is rocksolid. 
It does not run on Ubuntu by default, but is easily installed using alien.

The downside is that it is not open-sources and commercial and therefore does not meet one of your requirements. But I am extremely happy with it and I think it is worth its $$.

---

### Post by Friday on 2008-08-07
I've played around with three so far. 

[Citadel]("http://citadel.org")
I'm about to deploy a citadel server this week, only for the fact that no one will use the webmail, and it runs very lean. Backing up looks to be an easy process too. 

[Zimra]("http://www.zimbra.com")
Zimbra's client is much easier to use than the "rooms" of citadel. The management console isn't. I find citadel's to be easier. Then again, deploying an email server isn't always about the person administrating it. Zimbra also takes more system resources to run comparedt to citadel. 

[ISPConfig]("http://www.ispconfig.com")
This is way to much overkill to run just an email server. ISPConfig needs as much resources to run as Zimbra, if not just a little more. But, if you also need a web and ftp services on the same box, you can't wrong with this. ISPConfig really should not be compared to zimbra or citadel, and comparing it to C-Panel is a better comparison.

---

### Post by OhioLen on 2008-08-07
Just to toss some news items into the mix, first from Ubuntu.com:

> Sunnyvale, Calif., August 7, 2008 – Zimbra has announced that Canonical, sponsors of Ubuntu, the fastest growing Linux distribution, will give users direct access to Yahoo! Zimbra Desktop, which provides a centralized hub to manage multiple e-mail accounts and calendars online and offline, through the Ubuntu Partner Repository. Zimbra, a Yahoo! (Nasdaq:YHOO) company, is a leader in open source, next-generation messaging and collaboration software.

Sounds nice, until you read [this]("http://www.managementconsultancy.co.uk/computing/news/2222179/icahn-gets-seat-yahoo-board"):

> Yahoo has agreed to give activist investor Carl Icahn a seat on its board of directors and the power to nominate two further directors.

The move comes after Icahn and Microsoft discussed a fresh bid for the company last weekend, and seems to be designed to prevent a hostile takeover.

Icahn has nominated Jonathan Miller, former chief executive of AOL, as one of the chosen directors.

The deal means that Icahn and his two nominated directors will have to work closely with the six remaining board members, including chief executive Jerry Yang, whose resignation Icahn has repeatedly called for.

Icahn has been critical of the Yahoo board over its refusal to accept Microsoft's hostile takeover bid and had planned to oust the entire board at the search firm's annual general meeting in an attempt to force further discussions with Redmond.

If Microsoft eats Yahoo, I'd say that the competing Yahoo product will be cannibalized for any useful code and that will be the end of it. Hasn't that been their business model from the beginning?

FWIW.

---

### Post by HermanAB on 2008-08-07
BTW, Citadel uses Oracle BerkeleyDB as its back-end.  It can handle 256 Terabytes of mail and tens of thousands of users.  I have been running it for more than a year with no issues.

---

