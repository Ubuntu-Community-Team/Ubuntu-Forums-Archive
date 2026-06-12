---
title: "Samba as a front-end for WebDAV"
date: 2010-03-16
forum: Server Platforms
---

### Post by Patrick Hayes on 2010-03-16
I have a webdav system working great with users, passwords, groups etc. However, much to my annoyance, Windows is basically unusable when it comes to accessing webDAV resources. I was wondering if anyone can think of a method of using Samba as a 'front-end' for webDAV. Basically using it like a protocol translation service - users would connect to samba, give samba their username / password (which samba would pass on to the webDAV server for authentication), and then users could access their webdav resources via a samba link. Basically I'm looking for the opposite of Davenport (which provides webdav access to samba, but not vice-versa as far as I can see). Any suggestions?

---

