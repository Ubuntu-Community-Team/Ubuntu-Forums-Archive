---
title: "exchange replacement"
date: 2004-12-16
forum: Server Platforms
---

### Post by jdodson on 2004-12-16
does anyone know of anything they have personally setup as an exchange replacement that is both free as in freedom and beer?  this is one area that i have done research in and have not had much luck in finding solutions.  exchange supporting email(sendmail, qmail, etc), calendaring, webmail(squirrelmail, openmail, etc), etc.  i am mostly looking for a calendaring server, but if there is some project that harmonizes them all that is cool too.

---

### Post by water on 2004-12-16
i haven't installed any of them my self, but i'm looking into :
 
 
[list]
[*][http://www.opengroupware.org/en/index.html](http://www.opengroupware.org/en/index.html)   
[*][http://mirror.open-xchange.org/ox/EN/community/](http://mirror.open-xchange.org/ox/EN/community/) 
[/list] :water

---

### Post by calvinpriest on 2004-12-20
Another option is EGroupWare/PHPGroupware (forked from same base):
[http://www.egroupware.org/](http://www.egroupware.org/)
[http://www.phpgroupware.org/](http://www.phpgroupware.org/)

They're web based, but my understanding is that you can access the email with any IMAP-supporting client (Outlook, Evolution, etc.) and the contacts with an LDAP-supporting client (Outlook, Evolution, etc.).  The most important part, unfortunately is the calendar and for that you're stuck with a web interface.

PHPGroupware has been around a long time and is considered solid and stable.

---

### Post by cpinto on 2004-12-20
[QUOTE=calvinpriest]
The most important part, unfortunately is the calendar and for that you're stuck with a web interface.
[/QUOTE]

I can't agree with that. If you install Kontact (or at least KOrganizer) and it's wizards, you'll be able to use php/eGroupware's calendar in it's calendar part, because both groupware suites provide an XML-RPC interface that is used for Kontact.

I can't confirm this, but someone told me that Evolution also supports this but I haven't checked.

You can go with installing eGroupware on a server and deploying Kontact on the workstations, if you're really looking to migrate a MS Exchange/Outlook shop.

---

### Post by jdodson on 2004-12-21
this is helpful, thank you.

---

