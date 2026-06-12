---
title: "Can I run webmin through Apache2?"
date: 2005-05-29
forum: Server Platforms
---

### Post by BKonkle on 2005-05-29
I have apache2 installed, and I also have webmin installed listening on port 10000. . . I want to know if there is any way I can run webmin through apache, instead of using its own server?  I want to be able to administrate my server through my work computer, but they block all ports except for 80 for web access.

If I do that, am I opening myself up to a myriad of security problems as well, though?  I don't have any kind of sensitive information on my server at all, and I make frequent backups - but I don't want a random hacker destroying everything either. . .

Thanks!

---

### Post by DJ_Max on 2005-05-29
To run Webmin under apache,  look here. [http://webmin.com/apache.html](http://webmin.com/apache.html)
The only problem I see if you're not connecting via a SSL cert.

---

### Post by BKonkle on 2005-05-30
Thanks!  I appreciate the help!

---

### Post by Spudgun on 2005-05-31
It is possible to change the port Webmin listens on.

---

### Post by BKonkle on 2005-05-31
If I change the Webmin port to 80 though, won't that conflict with the Apache2 server I have running on 80?  I think I'm going to go ahead and run Webmin through Apache2 anyways, though - from what I can see it will actually run a bit smoother with a more developed server such as apache at the helm.

---

