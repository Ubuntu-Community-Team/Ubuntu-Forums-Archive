---
title: "Apache2 and SSL, apache fails on server restart"
date: 2009-11-23
forum: Server Platforms
---

### Post by martink87 on 2009-11-23
Hello!
I'm having a rather annoying issue in Ubuntu server. I'm new to SSL, I installed a self generated certificate just to encrypt the files being sent via the http server.

Ok everything works great, except when the system is restarted apache doesn't work straight away. I need to "killall apache" and then start it with "apache2 start" to enter the passphrase. How can this be done automatically, because it's really annoying to do this every time the server restarts.

Hopefully I was clear enough

Regards

Martin

---

### Post by martink87 on 2009-11-30
bump, anyone?

---

### Post by martink87 on 2010-01-14
bump for a solution :(

---

### Post by noway2 on 2010-01-14
It might be easier for you to recreate your certificate and specify the -nodes option.  This will eliminate the password.  My reading on the subject leads me to believe that the password was meant to protect against someone with physical access starting the Apache server and or getting the key file(s).  If this is not a concern for you, then eliminate the password requirement.

---

