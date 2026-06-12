---
title: "Bind Question"
date: 2010-08-19
forum: Server Platforms
---

### Post by terazen on 2010-08-19
This is more of an information question than a problem.  I updated bind yesterday through apt-get upgrade and when I made a change to a record today it started giving me this error:
bad owner name (check-names)

The fix was to change a "#" to ";" on a commented line.
From: #@ .... MX ....
To:   ;@ .... MX ....

When I check the man page for named.conf it says # is supported.  Is there any logic behind this?

---

