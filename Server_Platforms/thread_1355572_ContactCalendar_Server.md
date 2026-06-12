---
title: "Contact/Calendar Server?"
date: 2009-12-15
forum: Server Platforms
---

### Post by Jekshadow on 2009-12-15
I have been using GMail/Google sync for way too long now, and I don't like the fact that Google has the info of all of my contacts, so I am trying to find a replacement that would run off of my own server at home. It needs to be supported by Evolution, and it would be preferable if it was supported by my iPhone.

Is there any sort of open source exchange server for Linux? Or could I set something else up, possibly LDAP or CardDav + CalDav?

Found "SOGo", I think that might do the trick

---

### Post by HectorG on 2010-09-06
I use calidav it is pretty easy to set up. Haven't figured out what to use for contacts yet though.

---

### Post by drhabber on 2010-12-22
Bump. Any ideas for Google Sync (contacts+calendar) replacement?

---

### Post by hakkie42@gmail.com on 2011-01-25
As the TS indicated, have a look at sogo. It links to a mail server and database and does contacts, mail, calendar. Together with the openchange people they're even working on an Microsoft Exchange replacement that's binary compatible (look for the OpenZEG appliance for a look - note: still in development).
sogo can be used with the built in web frontend (using apache or similar web server), Thunderbird/Lightning, and can synchronize with e.g. mobile phones using Funambol.

---

### Post by drhabber on 2011-01-26
> **hakkie42@gmail.com said:**
> As the TS indicated, have a look at sogo. It links to a mail server and database and does contacts, mail, calendar. Together with the openchange people they're even working on an Microsoft Exchange replacement that's binary compatible (look for the OpenZEG appliance for a look - note: still in development).
sogo can be used with the built in web frontend (using apache or similar web server), Thunderbird/Lightning, and can synchronize with e.g. mobile phones using Funambol.

Thanks!

---

### Post by HectorG on 2011-01-26
I am using webcal for both calendar and contacts and couldn't be happier. Actually I could if it also had a noted server. Anyone know of a standalone notes server?

---

### Post by majedaly on 2011-11-12
For calendar, I use webcal. It is straight forward. I implemented it at work, 20 people are using it, with no problems. it uses a MYSQL as a backend. Hope this helps

---

