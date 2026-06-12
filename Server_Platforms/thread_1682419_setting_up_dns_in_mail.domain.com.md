---
title: "setting up dns in mail.domain.com"
date: 2011-02-05
forum: Server Platforms
---

### Post by jrtboht on 2011-02-05
I have created a mail server using citadel that seems to be working nicely.  My only problem is the only way to access the server is to go to 71.114.220.3:2000  (it's running on port 2000).  I would like to be able to access the server by going to mail.annarrankings.com

I'm using godaddy for my dns and set an A record as host=mail, points to =@
Then set the mx server to priority=10, host=mail.annarrankings.com, points to = @

When I did this I got "permission denied"

How would I set this up?

---

### Post by sandyd on 2011-02-05
> **jrtboht said:**
> I have created a mail server using citadel that seems to be working nicely.  My only problem is the only way to access the server is to go to 71.114.220.3:2000  (it's running on port 2000).  I would like to be able to access the server by going to mail.annarrankings.com

I'm using godaddy for my dns and set an A record as host=mail, points to =@
 
When I did this I got "permission denied"

How would I set this up?
you can't map ports in DNS.
mail.annarrankings.com:2000 will likely work

---

