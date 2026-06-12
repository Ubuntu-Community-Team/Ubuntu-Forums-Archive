---
title: "Migrate services from Google"
date: 2015-12-31
forum: Server Platforms
---

### Post by dkerlee on 2015-12-31
Morning folks. Just looking for some input and suggestions on how I could start replicating Google's services on my own ubuntu server. I'm mostly concerned with privacy, and my lengthy digital paper trail over the years. The three big services are: email, calendar, and contacts.

Email. A regular postfix email server with IMAP enabled. Then I could connect the Gmail app via IMAP to the home server. I think this would take advantage of the Gmail app features without sharing personal email with Google.? 

Calendar. Looks like caldav is the way to go here. Then I'd need a calendar app (been using Digical) that will connect to the iCal server for sync and sharing with the wife. 

Contacts. LDAP server? 

Wouldn't it be interesting to make a Google Bug Out package that bundled up all these services and played nicely with iPhone and android?

---

### Post by slickymaster on 2015-12-31
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by nerdtron on 2015-12-31
> **dkerlee said:**
> 

Email. A regular postfix email server with IMAP enabled. Then I could connect the Gmail app via IMAP to the home server. I think this would take advantage of the Gmail app features without sharing personal email with Google.? 



Building you own email server is easier said than done. There would be a lot of choices and tons of configuration options you'll need do. Are you sure you want to ditch gmail?.
Anyway, for starters, you can install this email suite from iredmail. [http://iredmail.org/](http://iredmail.org/) It has an email server with a web email interface, also comes bundled with spam assassin and antivirus scanning. You can try to install it your own server and see how it goes. [http://iredmail.org/docs/install.iredmail.on.debian.ubuntu.html](http://iredmail.org/docs/install.iredmail.on.debian.ubuntu.html)
Yes, you can use the android gmail app to connect to your IMAP server.

---

### Post by houstonbofh on 2015-12-31
> **dkerlee said:**
> Morning folks. Just looking for some input and suggestions on how I could start replicating Google's services on my own ubuntu server. I'm mostly concerned with privacy, and my lengthy digital paper trail over the years. The three big services are: email, calendar, and contacts.

Email. A regular postfix email server with IMAP enabled. Then I could connect the Gmail app via IMAP to the home server. I think this would take advantage of the Gmail app features without sharing personal email with Google.? 

iredmail was already mentioned, and there are some other "easy suites" for mail that can work...  And while the Android gmail app will work, I do not think using it addresses your privacy concerns.  Pick another imap client or use a web client and firefox.  sqmail and roundcube are good ones.

> **dkerlee said:**
> Calendar. Looks like caldav is the way to go here. Then I'd need a calendar app (been using Digical) that will connect to the iCal server for sync and sharing with the wife. 

Yep.  And caldav can go on any webdav server.

> **dkerlee said:**
> Contacts. LDAP server? 

Why not just load the contacts in webdav?  (for a thick client?)  Or, if you use the web client, you can keep them there.

> **dkerlee said:**
> Wouldn't it be interesting to make a Google Bug Out package that bundled up all these services and played nicely with iPhone and android?

Another option is to use a different service.  At least you are spreading your data around.  I have used zoho for mail, and find them quite nice.  PM me if you want an invite that will give us both 5 extra free addresses.

---

### Post by dkerlee on 2015-12-31
Excellent ideas. Thank you very much. I was also looking at fastmail.com, they also have an android app that has a calendar, email, notes, and contacts in it.

---

