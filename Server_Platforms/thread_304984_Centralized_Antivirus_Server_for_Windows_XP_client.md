---
title: "Centralized Antivirus Server for Windows XP clients"
date: 2006-11-22
forum: Server Platforms
---

### Post by cyris| on 2006-11-22
Hey everyone.

I'm interested in setting up a centralized antivirus server for my windows xp clients and I was wondering if anyone got this done with ubuntu?

---

### Post by wasert on 2008-04-03
I have the same question.

---

### Post by cferthorney on 2008-04-03
> **cyris| said:**
> Hey everyone.

I'm interested in setting up a centralized antivirus server for my windows xp clients and I was wondering if anyone got this done with ubuntu?
This should be possible with ClamAV - as this works on Windows, and Linux.  You will need to specify your Ubuntu box as your DB mirror.  In your freshclam file you should see something along the lines of 
```

DatabaseMirror db.us.clamav.net

```

change this to 
```

DatabaseMirror your.clamserver.ip.address

```
where your.clamserver.ip.address is your IP address.

Please remember Clam on Windows uses cygwin to get all its information, and I can not remember (Nor find with a quick google) the exact location of the freshclam.conf file under your /cygdrive .

For any other AV service - most have an AV mirror server and remote admin console available and these are often simple to set up - Nod32's is excellent in past experience and Sophos' is pretty good as well.  I have no experience of Norton's or AVG's.

Hope this helps.

---

