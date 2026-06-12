---
title: "Replace my Windows 2003 server with..."
date: 2014-02-25
forum: Server Platforms
---

### Post by Wayneblast on 2014-02-25
I have an HP Proliant Microserver with 2GB RAM (basic spec) with Windows 2003 server with 5 CAL user licenses. The HP server does not support Win 2003 and the upgrade to Win 2012 server poses issues with the HP server specs - so I am stuck between the server spec and the new Windows versions!! 

I want a Linux solution that will allow for a server running email, word processing package, internet access, printer etc with networking (remote access by 5 users from their workstations (could be Windows laptops, tablets and possibly IPhone and Samsung Smart phone). 

I am a complete newbie with regard to Linux and would like suggestions on a list of Ubuntu installs required to cover the above? Thanks!

---

### Post by volkswagner on 2014-02-25
Pleas explain a bit more detail.

You'd like to have a Linux server host word processing software that can be run remotely from Windows pc's and mobile devices?

---

### Post by Wayneblast on 2014-02-25
yes, a Linux server that is accessed remotely (via laptops) for file storage, email and office functions like documents, spreadsheets etc

---

### Post by vcbranco on 2014-02-25
You can try

[http://www.zentyal.org/](http://www.zentyal.org/)

[http://www.clearfoundation.com/Software/overview.html](http://www.clearfoundation.com/Software/overview.html)

---

### Post by Simon_WM on 2014-02-25
> **vcbranco said:**
> You can try

[http://www.zentyal.org/](http://www.zentyal.org/)

[http://www.clearfoundation.com/Software/overview.html](http://www.clearfoundation.com/Software/overview.html)

+1 for Zentyal!!

---

### Post by brokenhachi on 2014-02-25
+2 for zentyal ;)

Word of warning though: OpenOffice/LibreOffice docs sometimes have weird bugs when opening them on Microsoft Office, especially the spreadsheets. If you're just reading the documents there should be no issues but creating/editing them sometimes makes them act extremely weird... super thick cell borders comes to mind [https://bugs.freedesktop.org/show_bug.cgi?id=56960](https://bugs.freedesktop.org/show_bug.cgi?id=56960) (though apparently this is fixed?)

---

