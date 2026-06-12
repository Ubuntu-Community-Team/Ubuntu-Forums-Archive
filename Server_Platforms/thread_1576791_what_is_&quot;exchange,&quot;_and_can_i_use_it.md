---
title: "what is &quot;exchange,&quot; and can i use it?"
date: 2010-09-17
forum: Server Platforms
---

### Post by skullmunky on 2010-09-17
People at work are encouraging me to "get on exchange."  I don't know what that means exactly, but it's because they want to schedule meetings with me.  Is that something I can do from Linux?  I'm using Kubuntu Lucid.

If the answer is "no", or "yes, but the calendar sync won't work," I won't be too sad.  It'll mean I won't have to go to as many meetings.

---

### Post by VastOne on 2010-09-17
> **skullmunky said:**
> People at work are encouraging me to "get on exchange."  I don't know what that means exactly, but it's because they want to schedule meetings with me.  Is that something I can do from Linux?  I'm using Kubuntu Lucid.

If the answer is "no", or "yes, but the calendar sync won't work," I won't be too sad.  It'll mean I won't have to go to as many meetings.

Exchange is Microsoft's email platform and yes it you can connect to it from Linux and using something like davmail, which includes calender use.  See [_[COLOR="SeaGreen"]here[/COLOR]_]("http://davmail.sourceforge.net/")

Even easier is evolution-mapi. Go to Synaptic package manager and find the package evolution-mapi

Then, go into Evolution and choose server type: Exchange MAPI. Then, its a lot more straightforward and all you have to enter is the Server Username & Domain.

And by the way&#8230;.EVERYTHING WORKS. Mail, Contacts, Calendar&#8230;got it all.

---

### Post by HermanAB on 2010-09-18
Get them to install OWA on Exchange - they probably already have it - and access it via a web browser.

Evolution may also work - it uses the same OWA interface though, so the first step is to get them to install OWA and use it via a web browser.

---

### Post by arrrghhh on 2010-09-18
This is the server section, but you're running Kubuntu... So I'm guessing you're not talking about running an Exchange server, you just want to connect to an Exchange server as a client.

Evolution does a pretty good job of being an Exchange client, but I think the different versions of Exchange react differently with Evolution.  I'm not sure, but I don't think Exchange 2010 works with it, and 2003 is probably the best supported version.

I could be off-base on that tho, it's been a while since I've played with Exchange and Linux...

---

### Post by skullmunky on 2010-09-23
That's right, I don't need to run an exchange server, just (maybe) connect to one.  I posted here only because there doesn't seem to be a specific forum for business productivity, and I figured here is where folks will have the knowledge.  Thanks! 

My other colleagues have recommended I avoid "getting on the exchange server" because it'll allow everyone with higher clearance to arbitrarily schedule me into meetings whenever they want.  So I'm torn - I could claim I can't do it and use Linux as the excuse and keep control over my schedule, but I feel bad deliberately claiming that Linux can't do something important when it actually can! :)  Oh, ethical dilemmas ...

---

### Post by scrooge_74 on 2010-09-23
Hook to the exchange server (so people cant say Linux cant), then do as Alice (Pointy Hair boss secretary in Dilbert) and fulll your schedule with things so no one can put you in meetings ;)

---

