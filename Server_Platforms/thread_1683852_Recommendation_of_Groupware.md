---
title: "Recommendation of Groupware"
date: 2011-02-08
forum: Server Platforms
---

### Post by natomb on 2011-02-08
Hello,

I want to bring my emails and calendar online so that I would have access via a normal web browser. While doing some research for several weeks - and trying numerous products - there was nothing that could really satisfy my needs. Here is what (I think) I need:

- Web-access to my imap-accounts
- Web-access to my LDAP contact list (with edit mode)
- Web-access to my calendar
- Sharing my calendar with my wife (vice versa)
- Authentication against LDAP

Nice would be, but other solutions are in place:

- Notification upon upcoming calendar events via email
- Simple web site management (currently using Joomla to report about the news from my family like pictures of our last holiday)
- Simple file management with file versioning and "download as ZIP" functionality (currently using KnowledgeTree)


My infrastructure is (and must be at least):

- openldap
- apache2
- mysql5
- php5
- postfix / dovecot


I tried the following products but none could really satisfy my needs. Either they were too complex, out of maintenance / buggy (at least what appeared to me) or simply did not fulfil my requirements:

- eGroupware
- SimpleGroupware
- phpGroupware
- PHProjekt
- Kolab
- OpenGroupware
- CIRCABC

The only thread on such topic I could find here is [http://ubuntuforums.org/showthread.php?t=202086&highlight=calendar+ldap+imap](http://ubuntuforums.org/showthread.php?t=202086&highlight=calendar+ldap+imap) . While I have not tried every single product there, I would highly appreciate if anyone could give me proposal for a potential solution.

Thank you very much
  Bjoern

[]("http://www.bit.bund.de/cln_092/nn_1333092/BIT/DE/Meldungen/CIRCA/20081112__CIRCABC__v2__release.html?__nnn=true")

---

### Post by druhboruch on 2011-02-08
It is not on your list but IMHO is the best:
[http://www.sogo.nu/english.html](http://www.sogo.nu/english.html)

---

### Post by keithy on 2011-02-08
also look at group office

[www.group-office.com](www.group-office.com)

has quick easy install for ubuntu

[http://www.group-office.com/wiki/Installation](http://www.group-office.com/wiki/Installation)

---

### Post by natomb on 2011-02-08
Thank you very much for your proposals.

SOGo looks quite interesting, unfortunately it lacks the ability to edit ldap entries for the address book.

Also Group-Office looks interesting but misses the same feature. Nevertheless, I think I will setup a virtual machine and try both of them.

More proposals are welcome.

---

### Post by natomb on 2011-02-09
Hi,

here is my experience:

* Group-Office crashes when I access it using Android. To be more precise, Group-Office crashes my Android.

* SOGo does not work reliably on my virtualized ubuntu box. I could find some hints in Google which suggest that Ubuntu is using the wrong libraries and that I compile the proper libraries. However, I do not want to compile something, particularly not on my web-server.

As a consequence, I keep looking.

---

### Post by keithy on 2011-02-09
Hi again,

thats annoying re android and Group-Office

I'm a big user and about to get a droid :(

the only option would be to use the professional (i.e.paid for) version of Group office which will sync with android

Keep us updated on your quest

Good luck!

---

### Post by natomb on 2011-03-15
Hello together,

just to give a brief update. I think I will give the new version of Horde a try, once it is released in April. Looks promising. Going live of the portal would then be somewhere in June or July then.

---

### Post by Lars Noodén on 2011-03-15
In addition to Kolab, there are also the following. 

Citadel
    Citadel is fully open source with end-to-end GPLv3. It has been production grade for several years.
    [http://www.citadel.org/](http://www.citadel.org/)

Dingo Calendar Server
    CalDAV server using MySQL written in Perl.
    [http://andrew.triumf.ca/dingo/](http://andrew.triumf.ca/dingo/)

Darwin CalendarServer
    A standards-compliant calendar server.
    [http://trac.calendarserver.org/](http://trac.calendarserver.org/)

Bedework
    A standards-compliant enterprise calendar server designed in particular for higher education.
    [http://www.bedework.org/](http://www.bedework.org/)

Zimbra
    Messaging, calendar, collaboration. Owned by Yahoo.
    [http://www.zimbra.com/](http://www.zimbra.com/)

OpenGroupware
    Messaging, calendar, task managing, resource planning, collaboration.
    [http://www.opengroupware.org/](http://www.opengroupware.org/)

---

