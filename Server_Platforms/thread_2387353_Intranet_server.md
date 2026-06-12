---
title: "Intranet server"
date: 2018-03-18
forum: Server Platforms
---

### Post by carnagelan on 2018-03-18
Hi Guys, 
the company that hosts my clients email server does not want to set it to support imap. They want a shared calendar.

With pop you cannot do that. Is there an app for Linux that can share a calander through to windows clients. I am running ubuntu server 16.4 on there local network. If a stand alone calendar sharing app can't be don't. What local intranet software can I use that suppprts a calendar.

---

### Post by TheFu on 2018-03-18
Nextcloud?  Some of the sentences above don't make sense - like wrong words or missing words are an issue.
I use nextcloud, but don't use the calendar stuff.

---

### Post by carnagelan on 2018-03-19
I do apologies...

My clients email server does not support IMAP.
You can only have a shared outlook calendar if you are using exchange server.

My question is:

Is there an offline calendar app for linux/ubuntu that can be shared across the internal/local network?

---

### Post by TheFu on 2018-03-19
> **carnagelan said:**
> Is there an offline calendar app for linux/ubuntu that can be shared across the internal/local network?

"offline" probably means different things.  To me, it means stand-alone - ZERO networking. Not even a LAN. In a prior job, I had 22K sometimes connected users.  They'd connect only once a week to the company LAN. The rest of the time, they had only specialized networking for 1 program, not any IP networking. Basically, they were disconnected.

Perhaps you mean "offline" as to be on the LAN, but without internet? Please confirm.

Multiple solutions exist. If they are offline, you can use ICS files - just rsync those between the systems before they disconnect.  
Different "flavors" of ubuntu have different built-in calendar applications.  Each of these will support iCal, ICS, CalDAV standards to a different level.

Viewing of public events is possible with most email/contacts/calendar servers.  Nextcloud can connect into those and sync them as needed, when networking is available. 

Thunderbird + lightning has the ability for local (files), LAN (iCAL/CalDAV), and internet (whatever), to be used.  In cache mode, a live LAN/Internet connection isn't needed.   Sharing of the calendar is something the server handles. For that ...

We use Zimbra were I am.  This is an MS-Exchange replacement with enterprise calendaring. To me, Enterprise calendaring means individual, shared, and read-only public calendars.  I keep the Zimbra server off the internet and use a separate, tiny, email gateway system for all inbound/outbound emails.  This gateway can easily be run on a VPS for $5 a month. It doesn't have data, unless our internet is down, then inbound email is held until the Zimbra system becomes available again.  Zimbra is a hog, but extremely capable. It supports almost every email/calendar/address-book protocol that you might want. The Zimbra web interface makes gmail look like a toy.   End users don't have accounts on the email gateway.

I would dump any company who didn't provide IMAPS.

I use Thunderbird + Lightning on my Linux systems.  Others use different email/calendar tools, like Evolution. There are 10+ others.

I'm not exactly sure whether you want a calendar server or some client tool that communicates with a server to allow other local users to share it.  Nextcloud with a calendar addon can do that.

Or am I misunderstanding still?

---

### Post by LHammonds on 2018-03-19
> **carnagelan said:**
> Is there an offline calendar app for linux/ubuntu that can be shared across the internal/local network?
I don't use any of the following for shared calendars but I found them using my Google-Fu

[NextCloud (has Outlook integration)]("https://nextcloud.com/compare/")
[Darwin Calendar Server]("https://www.calendarserver.org/")
[DAViCal]("https://www.davical.org/")
[Badework]("http://www.bedework.org/")
[Radicale]("http://radicale.org/")
[Cosmo]("http://chandlerproject.org/Projects/CosmoHome")
[Zimbra Email Server]("https://www.zimbra.com/downloads/zimbra-collaboration-open-source/")
[Citadel email server]("http://www.citadel.org/doku.php")
[Horde groupware]("https://www.horde.org/")
[OBM groupware]("http://obm.org/")
[Courier PCP extension to Courier mail server]("http://www.courier-mta.org/pcp_README.html")
[Baikal Cal and CardDAV server]("http://sabre.io/baikal/")

---

