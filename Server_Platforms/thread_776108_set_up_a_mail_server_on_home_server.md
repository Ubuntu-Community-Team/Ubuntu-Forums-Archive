---
title: "set up a mail server on home server?"
date: 2008-04-30
forum: Server Platforms
---

### Post by lefnire on 2008-04-30
Got hardy server, and tasksel installed the mail server only to find that my ISP blocks port 25 & won't unblock on request.  Is there any hope left in installing a mail server?  I notice ubuntu asked for a proxy URL and something about a smarthost during installation, could either of these be helpful in doing mail?  I remember hearing some mumbo jumbo about tunneling through ssh to a proxy, or something like that, to bypass the need for ports when ISP's block them...

---

### Post by exaviorn on 2008-04-30
If you want to open the port on your router go to [portfoward.com]("http://portforward.com/")and select your router and select imap (something like that :lolflag:)after that select stuff like pop3.

---

### Post by lefnire on 2008-04-30
well, i can open ports on my router, but then when the data gets to the ISP [it's blocked there]("http://www.postcastserver.com/help/Port_25_Blocking.aspx").

---

### Post by SpaceTeddy on 2008-04-30
[OFFTOPIC]
sorry to talk off topic, but blocking INCOMING port 25 has nothing to do with spam sending - that is OUTGOING port 25 (correct me if i am wrong).
does that mean you cannot send any mail anywhere via any smtp - or do just the mail servers from your ISP work and no other ?

the only way i can think of going around this is by tunneling your mailserver to the outside world through a third party or use a smarthost (since then your email server would act as an email client).

a full blown MX-server is not possible with port 25 blocked... 

Just read the full article... this is crazy. I've never known this was happening, but this is just... i can't find any words for it. I'd be a reason for me to change providers... 
[/OFFTOPIC]

---

### Post by jbaileypro on 2008-05-06
Hey your ISP will block it but they will provide you with their e-mail server. Talk Talk used to block mine but they told me to use their servers, they had no restrictions ever, so i was ok with that!

Hope that helps, JJ

---

### Post by lsutiger on 2008-06-08
You could use a 3rd party in order to redirect your mail to a different port. Dyndns has a mail-hop service, but I wouldn't recommend their spam scanning and virus scanning associated with that service. We were using it at my company and we were loosing a hell of a lot of legit emails.

---

### Post by windependence on 2008-06-09
> **jbaileypro said:**
> Hey your ISP will block it but they will provide you with their e-mail server. Talk Talk used to block mine but they told me to use their servers, they had no restrictions ever, so i was ok with that!

Hope that helps, JJ

Kinda defeats the purpose of having your own mail server doesn't it?

-Tim

---

### Post by windependence on 2008-06-09
> **lsutiger said:**
> You could use a 3rd party in order to redirect your mail to a different port. Dyndns has a mail-hop service, but I wouldn't recommend their spam scanning and virus scanning associated with that service. We were using it at my company and we were loosing a hell of a lot of legit emails.

no-ip has a service for this. I like them beter than dyndns anyway.

-Tim

---

### Post by hyper_ch on 2008-06-09
you can relay your outgoing mail through your ISPs server... that should be possible.

---

