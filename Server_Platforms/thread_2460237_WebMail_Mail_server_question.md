---
title: "WebMail Mail server question"
date: 2021-04-05
forum: Server Platforms
---

### Post by agent-ibo on 2021-04-05
I want to install an email server with ubuntu server or desktop doesn't really matter. 

I've search a lot but also interested in a nice webmail interface that looks more like yahoo or proton mail or something. 

Many of the webmail UI that have seen look sort of primative IMO. Although their functionality is very good. 

Please advise, thanks

---

### Post by slickymaster on 2021-04-05
*Thread moved to **Server Platforms**.*

---

### Post by LHammonds on 2021-04-05
I use NethServer which comes with [RoundCube]("https://roundcube.net/") for its default webmail interface.

Other front-end clients I found with a quick search (there are a LOT):

[Rainloop]("https://www.rainloop.net/")
[ProtonMail]("https://github.com/ProtonMail/WebClient")
[Cypht]("https://cypht.org/index.html")
[Afterlogic Webmail Lite]("https://afterlogic.org/webmail-lite")
[Isotope Mail Client]("http://blog.marcnuri.com/isotope-mail-client-introduction/")
[SOGo]("https://www.sogo.nu/")
[Atmail]("https://www.atmail.com/")
[NextCloud]("https://nextcloud.com/") (has chat and webmail add-ons)
[Horde]("https://www.horde.org/")
[Mailr]("http://mailr.org/")
[Postaci]("http://postaci-webmail.github.io/Postaci/")
[MailSping]("https://www.getmailspring.com/")
[Mailpile]("https://www.mailpile.is/")
[Squirrelmail]("http://squirrelmail.org/index.php")
[yawebmail]("http://yawebmail.sourceforge.net/")
[Mu4e]("https://www.djcbsoftware.nl/code/mu/mu4e.html") ;)

LHammonds

---

### Post by agent-ibo on 2021-04-05
thanks, I saw roundcube before and mailcow has a similar look. 

I'm having trouble atm with outgoing port 25 and postfix. Not sure what to do about that atm. 
thanks

---

### Post by rsteinmetz70112 on 2021-04-05
What kind of connection/ISP do you have? Some ISPs block port 25.

---

### Post by TheFu on 2021-04-05
I've been running Zimbra communications server [https://www.zimbra.com/](https://www.zimbra.com/) for about 14 yrs now.  The 100% F/LOSS version.  It is extremely full featured, but has system requirements to match. Also, because it is huge, I don't allow it directly on the internet.  Email gateways are used for all SMTP in and out.  For web or imap access, I enforce users to connect through our VPN. They didn't like it, but it has become second nature.

Zimbra is freakin' awesome with an ajax web GUI. Basically, it is like MS-Exchange, but with great searching because Yahoo owned it previously. It is the best webmail interface I've ever seen.  Great for automatic filtering, tagging, and moving messages to different folders.  It supports LDAP address books, LDAP centralized logins, Calendaring, shared email folders, distribution lists, and delegation for all of those things - if you like.

2 core + 3GB of RAM is the minimal system requirements and it REALLY, REALLY, wants you to run a DNS server on the LAN.  Run Zimbra on a dedicated VM. Upgrades can be highly manual, especially if you customize stuff.

It is possible to have a minimal email gateway at a VPS and Zimbra running in your house on a VM you control.  The email gateway would be setup as store and forward to Zimbra and zimbra shouldn't accept any SMTP except from your LAN or the remote gateway(s) under your control.

I didn't like the Nextcloud email interface, nor the SquirrelMail one.  I've looked at a few others over the decades, but Zimbra has me completely addicted for the integrated calendaring (thunderbird connects), and server-side filters, organization.  All my email clients have the exact same view of all messages. That is mandatory for me.

---

