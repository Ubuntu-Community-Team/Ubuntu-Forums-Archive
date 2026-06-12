---
title: "ssh went down"
date: 2009-01-01
forum: Server Platforms
---

### Post by fizgig on 2009-01-01
I noticed this morning that my xbox couldn't connect to my ubuntu samba server so I tried to ssh in.  Putty told me that the connection was denied which I couldn't understand.

I took my monitor and plugged it into the server and saw the normal login screen so I logged in.  I then restarted the ssh server and was then able to login with putty but putty complained that this was a different certificate than what was given last time.

Does anyone know why the ssh service was denying me and why the certificate might have changed?  I haven't done any apt-get stuff in several months so I don't think I did anything myself.

Very confused.  I have a working system but I don't know if I should be worried.

---

### Post by windependence on 2009-01-01
Apparently, your IP address changed. Look at the message from ssh carefully and it will tell you exactly where to find the key. Just go into the server and delete that key and it will be OK again.

-Tim

---

