---
title: "Linux based alternative to MS Exchange?"
date: 2008-01-21
forum: The Cafe
---

### Post by UrbanSage on 2008-01-21
Hey,

Aside from personal preference. Take a step back and look at mail servers for linux.

Is there a good alternative to Microsoft Exchange? I'm sure there is but I don't have any experience with managing anything else.

This will be for home use and a very limited amount of users.

Is there a good alternative that provides a client web interface?

Thanks
Nick

---

### Post by compiledkernel on 2008-01-21
Postfix, with Imap and SquirrellMail.

Howtoforge has a pretty nice build for that -- 

[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

---

### Post by DigitalDuality on 2008-01-21
d

---

### Post by FFighter on 2008-01-21
Chandler together with the Chandler Hub might be a viable alternative. However, Chandler has a historic of being pretty unstable, but it is an amazing idea and I hope the project succeeds.

Search google for Chandler Project.

HTH.

---

### Post by UrbanSage on 2008-01-21
Thank you for the suggestions.

I have been through some older posts here and other places and what scares me the most is finding a great number of "Best option anno 2005" and seeing the news have not been updated in two years.

The Postfix, with Imap and SquirrellMail setup looks like a good robust tried and true setup, but the Zimbra solution looks fairly interesting in spite of the (like mentioned) steep hardware requirements and I think I will give it a swing.

:guitar:

---

### Post by spidermonkey on 2008-01-21
zimbra

---

### Post by hkgonra on 2008-01-21
If I was going to do my own I would use zimbra. 
Have you looked at google apps for your domain ? 
I use it for my business and several others that I do work for and it works great.

---

### Post by FFighter on 2008-01-22
Well, I just checked the last release of Chandler (0.7.3) client and it is pretty stable comparing to previous ones (it has been some time since I had played with it).

There's also the server which you can install on your server or use it as part of the Chandler hub (free online hosting of the server OSAF provides).

Chandler is an amazing project, guided by great ideas and great programmers and designers. Take a look, it certainly could be a good alternative to Exchange.

[http://www.osafoundation.org/](http://www.osafoundation.org/)

If you would like to know more about the project's history you could take a look and read the "Dreaming in Code" book - a great read! :)

HTH.

Marcelo.

---

### Post by macogw on 2008-01-22
> **FFighter said:**
> Chandler together with the Chandler Hub might be a viable alternative. However, Chandler has a historic of being pretty unstable, but it is an amazing idea and I hope the project succeeds.

Search google for Chandler Project.

HTH.

Chandler is dying.  The guy in charge just quit.

---

### Post by FFighter on 2008-02-20
> **macogw said:**
> Chandler is dying.  The guy in charge just quit.

Not it is not.

[http://dirtsimple.org/programming/](http://dirtsimple.org/programming/)

Take a look at the post "Rumors of Chandler's Death Are Greatly Exaggerated".

I use it everyday. The 0.7.4 version (released last week) is amazingly stable (comparing to old releases).

Also, I think that the main issue with Chandler is that few of its users become active developers, helping the project. Remember, Chandler is an Open Source effort, the core developers are calling for help from the community! 

Chandler's wiki has plenty of info regarding Chandler's architecture and its various packages and APIs. It's a valuable learning experience.

Remember, our life is a constant paradigm shift. Don't let old paradigms rule your life :) (aka, Chandler is a useful piece of software and can be successful).

---

### Post by timcredible on 2008-02-20
google apps.

---

### Post by wthanna on 2008-02-20
Citadel.  It can be found at [www.citadel.org](www.citadel.org) and you can literally be up and running your full featured mail server in MINUTES.. not hours or days.  I've been using it for months and have no regrets.

---

### Post by phrostbyte on 2008-02-20
We use Zimbra were I work. Highly recommended.

---

### Post by fatality_uk on 2008-02-20
Zimbra looks excelent. Could be just what I am looking for :)

---

### Post by KCPokes on 2008-02-20
I recommend Zimbra as well.  Been running it for two years without an issue.  It just keeps getting better and better.  

But always fun to mess with a few of the others.  I've heard Citadel mentioned quite often, thus worth a look.

---

### Post by SlayerMan on 2008-02-20
Take a look at Scalix. It is said to be an Exchange killer. It can be used with Evolution, Outlook, Kontact and with a web based interface.

[http://www.scalix.com](http://www.scalix.com)

---

### Post by KCPokes on 2008-02-20
> **SlayerMan said:**
> Take a look at Scalix. It is said to be an Exchange killer. It can be used with Evolution, Outlook, Kontact and with a web based interface.

[http://www.scalix.com](http://www.scalix.com)

Good call.  After all, he didn't specify free.  If, by linux, though you do mean free, then you should specify because not all of these are available at no cost.  Otherwise, from what I understand, Scalix is very capable.

---

### Post by hkgonra on 2008-02-20
> **timcredible said:**
> google apps.

+1 

Google apps FTW !!!


But if you want to host your own scalix and zimbra are free.

---

### Post by Mateo on 2008-02-20
I don't see a web interface based system working.  Who wants to check their mail on the web?  If you are traveling and didn't bring your own computer, that's fine.  But when I'm using my home computer I want to know instantly when I have new mail, I don't want to have to periodically load up a web browser and manually check.  I just don't see a way around this problem without a mail client.  And as far as I know these projects don't integrate with any mail clients.

---

### Post by hkgonra on 2008-02-20
Google Apps , Zimbra and Scalix all offer pop , imap and web interface. 
Just like any oher e-mail service.

---

### Post by macogw on 2008-02-20
> **Mateo said:**
> I don't see a web interface based system working.  Who wants to check their mail on the web?  If you are traveling and didn't bring your own computer, that's fine.  But when I'm using my home computer I want to know instantly when I have new mail, I don't want to have to periodically load up a web browser and manually check.  I just don't see a way around this problem without a mail client.  And as far as I know these projects don't integrate with any mail clients.

I only use webmail.  I think it's a pain in the butt that if I have my mail setup on one computer, I can't get it from another without hunting down server names and port numbers, and then if it's POP they'll be all messed up on the read status.  Plus, you have to have yet another app running (the mail client).  Using webmail doesn't involve opening up yet another app since Firefox is only closed if it just crashed a moment ago or if it's restarting because an extension was updated.

---

### Post by Mateo on 2008-02-20
> **hkgonra said:**
> Google Apps , Zimbra and Scalix all offer pop , imap and web interface. 
Just like any oher e-mail service.

Right, but that only applies to mail.  An exchange alternative would encompass the complete package, including Calendar, Contacts and Tasks (and preferrable notes as well).  To my knowledge, Zimbra and Scalix don't do this, and I know for a fact that Google doesn't.

---

### Post by Mateo on 2008-02-20
> **macogw said:**
> I only use webmail.  I think it's a pain in the butt that if I have my mail setup on one computer, I can't get it from another without hunting down server names and port numbers, and then if it's POP they'll be all messed up on the read status.  Plus, you have to have yet another app running (the mail client).  Using webmail doesn't involve opening up yet another app since Firefox is only closed if it just crashed a moment ago or if it's restarting because an extension was updated.

You have to go with IMAP.  POP is an outdated technology, from the days when people only used 1 computer.  With IMAP you don't have to worry about keeping computers in sync.

I see your point about keeping a browser window open, but to me this isn't a good alternative.  For one, it's easier to accidentally close a browser window than an entire application.  And secondly, I don't always use the internet, so if I keep a browser window open just for mail, that's a lot of memory waste taking place, as lightweight web applications like Evolution only take about ~10mb of memory whereas Firefox or Epiphany are going to be in the mid 30s, at least.

---

### Post by macogw on 2008-02-20
> **Mateo said:**
> Right, but that only applies to mail.  An exchange alternative would encompass the complete package, including Calendar, Contacts and Tasks (and preferrable notes as well).  To my knowledge, Zimbra and Scalix don't do this, and I know for a fact that Google doesn't.

Er...have you used Google Apps?  If you have a date & time listed in an email, on the side it asks if you want to add it to your Google Calendar.  If you get an attachment, it asks if you want to open it in Google Docs.  There's nothing stopping you from using Google Docs as a place to type your Notes to Self.  It of course has a contact list as well.

---

### Post by igknighted on 2008-02-20
> **hkgonra said:**
> Google Apps , Zimbra and Scalix all offer pop , imap and web interface. 
Just like any oher e-mail service.

Zimbra also has it's own desktop client that is very nice.  It's still a beta, but is in a very usable state (technically, even gmail is in beta).

IMO, each has it's own strength.  Right now I am working for a small business (~100 employees, 60 email addresses) and am looking at this from a point of view where we would be buying a license and getting a supported version, so consider that.  We currently have only simple email, but would like a true collaboration suite.  We are a mixed netware (soon to be replaced, either linux or windows, unsure at the moment) and windows environment, but no loyalty to exchange or outlook (outlook express and thunderbird are the clients of choice currently).  This is how I see them all stack up:

* Zimbra is the most innovative solution out there.  They look at how things have been done and try to improve, not imitate other solutions (eg, exchange).  They are pricey, as it's $33/yr/user for the small business version.  There is an open source version for home users, but you are limited to 10 premium accounts so from a business needing at least 50 it is worthless.  Also, if Yahoo! is purchased by Microsoft, the future of Zimbra would be in doubt.  The desktop client is also another huge plus.

* Scalix is simple to manage, runs fairly quickly, and best of all comes with a perpetual license for 50 users for $995.  No yearly fees or anything like that (aside from support tickets, of course).  They are not as innovative as Zimbra, but the product certainly seems to be sufficient.  There is an community version for those who want to try it out at home.  It can connect to Outlook and Evolution (unsure about Kontact), and has a nice web client (slower than Zimbra's in my experiences).  The only real concern I have is that it was recently purchased by Xandros, who seem to ruin everything they touch.

* PostPath is Microsoft Exchange, Linux Edition (essentially... i don't think there is any actual relationship).  Administration is done through active directory, and you can bring up a PostPath server in an exchange environment and the system really doesn't know the difference.  It's pricey (4,000 one-time fee, includes 60 users), but if you are currently using exchange it's a seamless alternative.

* OpenXchange seems to be behind the others, but they do sell a pre-set-up server (running on Ubuntu) that looks pretty nice.  I haven't demo's this so I can't comment fully.  It was too pricey for us so we eliminated it quickly.

* Google Apps is a tough decision.  It can be done for free, or for a rather steep $50/user/yr.  You get text ads on the free version, no migration support and no 99.9% uptime guarantee.  It's tough to decide if this is business ready or not.  I love google apps... I use gmail, igoogle is my homepage, my life is on google calendar, etc.  But is it good enough for business yet?  I can't decide, after all even google still claims all that stuff is beta.

Keep in mind when I talk of price, I am at an organization looking at purchasing between 35 and 50 premium account licenses, while having a total of 60-80 email accounts total.  Assuming 40 premium accounts, the $33/user/yr Zimbra is $1320/yr and Google's premium service would be at least $2000/yr (assuming only 40 premium accounts get charged the fee... we would need a simple mailserver in-house for the others with this plan).  Scalix, on the other hand, is a simple one time fee of $995.  Even the "pricey" PostPath would pay for itself in 3 years, well within the life of the system.

What's the best?  I have no idea.  I have demo'd a lot, but not administered any regularly.  For home use, I strongly recommend Zimbra.  But for a business setting, Scalix and PostPath need to get some press, and Google Apps is something to watch closely.

EDIT:  I didn't even mention Novell Goupwise, IBM Domino or other services...

---

### Post by igknighted on 2008-02-20
> **Mateo said:**
> Right, but that only applies to mail.  An exchange alternative would encompass the complete package, including Calendar, Contacts and Tasks (and preferrable notes as well).  To my knowledge, Zimbra and Scalix don't do this, and I know for a fact that Google doesn't.

Zimbra and Scalix both include connectors to Outlook and Evolution, and Zimbra has it's own desktop client that is brilliant.  Google only has a web interface... for now.  But you could use Google Gears to run many google apps offline.  Soon this will be much easier, so it may be a bit early to assume this as a usable function... but it's coming.

FWIW... the Gmail interface (IMO) is more functional than any desktop client I have used (save Zimbra's, but that's running through Prism so it is drawn the same way).  I haven't used an email client since switching and I don't miss it.

---

### Post by phrostbyte on 2008-02-20
> **Mateo said:**
> Right, but that only applies to mail.  An exchange alternative would encompass the complete package, including Calendar, Contacts and Tasks (and preferrable notes as well).  To my knowledge, Zimbra and Scalix don't do this, and I know for a fact that Google doesn't.

Zimbra has a MAPI connector for MS Outlook. The MAPI connector supports all of the above. It is not in the open source version however.

However it does support CalDav, which is supported by Evolution and Sunbird for calender sync. So between CalDav and IMAPv4 you have most of the functionality anyways, and this is in the open source version.

---

### Post by hkgonra on 2008-02-21
> **igknighted said:**
> Zimbra also has it's own desktop client that is very nice.  It's still a beta, but is in a very usable state (technically, even gmail is in beta).

IMO, each has it's own strength.  Right now I am working for a small business (~100 employees, 60 email addresses) and am looking at this from a point of view where we would be buying a license and getting a supported version, so consider that.  We currently have only simple email, but would like a true collaboration suite.  We are a mixed netware (soon to be replaced, either linux or windows, unsure at the moment) and windows environment, but no loyalty to exchange or outlook (outlook express and thunderbird are the clients of choice currently).  This is how I see them all stack up:




Same size business as yours and I handle all the IT. ( ok we only have 56 e-mail addresses. :wink: )
We have been using google apps (free versions) for our mail since Jan. 1st 07 and LOVE it. 
I have set it up for 6 diiferent smaller companies since then and have had nothing but  a good experience with it.

---

### Post by igknighted on 2008-02-21
> **hkgonra said:**
> Same size business as yours and I handle all the IT. ( ok we only have 56 e-mail addresses. :wink: )
We have been using google apps (free versions) for our mail since Jan. 1st 07 and LOVE it. 
I have set it up for 6 diiferent smaller companies since then and have had nothing but  a good experience with it.

Thanks!  Does it ever go down?  Do people mind using the online interface?

---

### Post by hkgonra on 2008-02-21
> **igknighted said:**
> Thanks!  Does it ever go down?  Do people mind using the online interface?

It has gone down but not near as many times or for as long as our internet or phones go down. 

Most people don't use the web interface , we use Outlook ( mostly 2003 with a few xp's or 2007's mixed in) with POP access. A few users use the web interface when they are away from the office and love it. It is SO much better than the isp based e-mail we switched from. A few users are using the imap and have no problems with it. 
Overall it has been a very positive experience.

To be fair we used our isp ( Time Warner at the time ) based e-mail for 5-6 years and it went down WAY more then google apps does. 

You will always have downtime in one way or another there is no getting around that unless you are willing to have multiple types of  internet connections into the office as well as mutliple mail serves in several locations. Even then I imagine it still happens from time to time.

---

### Post by HermanAB on 2008-02-21
Citadel is by far the easiest to set up and configure and it is zero maintenance.  Feature wise, it simply does everything and every mail protocol ever invented.

MS Outlook works pretty good with it using IMAP and for calendar support, an Outlook Connector is available.

Citadel is also very efficient, since it has an Oracle BerkeleyDB backend and saves only one copy of a message, so it is good for organizations large and small and scales way better than MS Exchange (which frankly doesn't scale at all, with its 75 user and 100GB limits).

---

### Post by dca on 2008-02-21
It's kinda' pricey but IBM's Lotus Domino is a better end to end solution to MS Exchange IMHO...

---

### Post by igknighted on 2008-02-21
> **dca said:**
> It's kinda' pricey but IBM's Lotus Domino is a better end to end solution to MS Exchange IMHO...

Feaure-wise, I agree.  Lotus is great.  But Notes is so slow, and the web-based client is even slower.  My school uses it and I really cannot stand it... so it gets forwarded to gmail haha.

---

### Post by dca on 2008-02-21
> **igknighted said:**
> Feaure-wise, I agree.  Lotus is great.  But Notes is so slow, and the web-based client is even slower.  My school uses it and I really cannot stand it... so it gets forwarded to gmail haha.

Couldn't agree more on the web-based side, the only thing that helps is eliminating the need to update individual clients on each workstations in the future, other than that...  However, you could use Outlook as the email handler which most enterprises still unfortunately are vendor-locked into the Windows/Office combo on their desktops...

---

### Post by dca on 2008-02-21
I'm too tired to look back, did anyone mention OpenExchange, the one from Novell/SuSE???

---

### Post by Mateo on 2008-02-21
> **igknighted said:**
> Zimbra and Scalix both include connectors to Outlook and Evolution, and Zimbra has it's own desktop client that is brilliant.  Google only has a web interface... for now.  But you could use Google Gears to run many google apps offline.  Soon this will be much easier, so it may be a bit early to assume this as a usable function... but it's coming.

Right, but an open-source alternative to Exchange needs to be the the complete package.  It needs to do all of the things that Exchange can do, but it also needs to be extendable to any client that wants to use it.   So when I say Zimbra's not ready now, that's not necessarily saying it's Zimbra's fault.  There needs to be easy ways to connect the server to the client.  So far there is not.  Otherwise all of the clients would have this capability.  They do not.

---

### Post by KCPokes on 2008-02-21
> **Mateo said:**
> Right, but an open-source alternative to Exchange needs to be the the complete package.  It needs to do all of the things that Exchange can do, but it also needs to be extendable to any client that wants to use it.   So when I say Zimbra's not ready now, that's not necessarily saying it's Zimbra's fault.  There needs to be easy ways to connect the server to the client.  So far there is not.  Otherwise all of the clients would have this capability.  They do not.

Zimbra does have it, but you have to pay for it.  Open Source does not necessarily mean FREE, especially when it requires the MAPI plugin.  Going to be hard to replace Exchange and all its functionality with something else without expecting to pay for it, to some degree.

---

### Post by igknighted on 2008-02-21
> **dca said:**
> I'm too tired to look back, did anyone mention OpenExchange, the one from Novell/SuSE???

I mentioned it briefly.  Novell's offering is actual Novell Groupwise.  OpenXchange is something different [http://en.wikipedia.org/wiki/Open-Xchange](http://en.wikipedia.org/wiki/Open-Xchange)

---

### Post by igknighted on 2008-02-21
> **Mateo said:**
> Right, but an open-source alternative to Exchange needs to be the the complete package.  It needs to do all of the things that Exchange can do, but it also needs to be extendable to any client that wants to use it.   So when I say Zimbra's not ready now, that's not necessarily saying it's Zimbra's fault.  There needs to be easy ways to connect the server to the client.  So far there is not.  Otherwise all of the clients would have this capability.  They do not.

What other clients are out there aside from Evolution, Kontact and Outlook?  If I knew of another, I would look up if it would connect.  As mentioned, Zimbra has their own now, and kicks kicks the crap out of the 3 I mentioned already.

---

