---
title: "Small Business Communications (Exchange Alternative)"
date: 2008-08-29
forum: The Cafe
---

### Post by lazerradial2003 on 2008-08-29
I'm trying to set up basic IT systems for a client who's starting a small business. Both are used to the standard MS Exchange environment for Calender, Email and Contacts. 

They are each working from home and so need a central address book, access to each others calenders and access to their email via BlackBerry. Also ideally a way of sharing a few files but that's not essential and public folders would probably do fine.

Personally I use Google Apps for most of this but they are keen to stick with Outlook because that's what they're used to. Initially I just figured buy a hosted exchange package for them and it would do it all but having looked around I'm not convinced it's the best way.

Just wondering if anyone had any recommendations either for alternative packages for these services on such a small scale or for a hosted exchange provider who would be able to provide these services competitively.

---

### Post by freebeer on 2008-08-29
I've been tinkering with Zimbra.  So far it looks like a decent replacement on the back-end.  There are service providers that you can check out.  And they do offer an Outlook connector (if your customers insist on using Outlook).  I haven't tried it, though.

---

### Post by lazerradial2003 on 2008-08-30
Thanks, Zimbra looks very promising, think I'll put a copy of that up on my development server and have a play. Has anyone come across [www.simplymailsolutions.com](www.simplymailsolutions.com) as an exchange or zimbra provider?

---

### Post by thisllub on 2008-08-30
I have set up 2 ZImbra servers and it is a simple and good mail server solution.

However exchange has a few features mostly to do with calendars that Zimbra doesn't support.

OpenXchange looks like it should be the best of these but a year ago when I looked at it it was a beast to set up.

Zimbra is a real problem to back up though as it can't be backed up live
I get around this by installing it on a virtual machine and backing up LVM snapshots.

---

### Post by lazerradial2003 on 2008-08-30
Do you know offhand what the unsupported calender features are?

---

### Post by freebeer on 2008-08-30
> **lazerradial2003 said:**
> Do you know offhand what the unsupported calender features are?

I'm not sure (primarily because I'm trying to move away from Outlook) but I think it has to do with adding invitees to calendar events.  I think there's a work-around whereby Zimbra emails the invite, as opposed to handling it directly, but I can't be sure.  (It was just something I caught when reading through docs and forums.)  Hopefully thisllub will post up his experience.

---

### Post by artcancro on 2008-08-30
> **lazerradial2003 said:**
> Just wondering if anyone had any recommendations either for alternative packages for these services on such a small scale or for a hosted exchange provider who would be able to provide these services competitively.

During your research you'll also definitely want to check out Citadel -- [http://www.citadel.org](http://www.citadel.org) 

Citadel integrates not only email and calendars but also other features such as RSS aggregation, instant messaging, message boards, and sticky notes.  It can be accessed via a nice web interface or with any standard client.  Best of all it is 100% Free Software (some products in this category have certain features removed from their open source versions).

And if you want to use it with Outlook, there's a version of the Bynari Connector you can obtain to integrate it with Citadel.

Do check it out -- it's a bit unusual at first but millions of happy users and thousands of delighted system administrators are already addicted to it  :)

---

