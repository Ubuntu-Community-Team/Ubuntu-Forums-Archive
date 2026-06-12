---
title: "opening external access to internal server"
date: 2009-09-09
forum: Security
---

### Post by equick on 2009-09-09
I know this is not specifically a ubuntu question but thought it worth trying as this forum usually has quite a lot of expertise ;-)

I'm running a cluster of tomcat servers on my internal network, and was thinking of setting up a reverse proxy in the dmz to open up external access to them over https. However my colleague advised me this would be insecure, and that I need to move my tomcat cluster into the DMZ before I open up access. Is that true?

Thanks,
Ed.

---

### Post by phillw on 2009-09-09
Yes.

Put them into a DMZ. Your HHTPS server then becomes the guardian between them and the BIG BAD WWWorld.

Read the stuff on securing servers VERY carefully - If you mess it up, they get compromised.

Phill.

---

### Post by equick on 2009-09-09
Yes but the reverse proxy could be your guardian and you could run mod_security on it to filter requests. But I suppose if you've got a badly developed application running on the tomcats, they could be compromised and run commands on your internal network....

---

