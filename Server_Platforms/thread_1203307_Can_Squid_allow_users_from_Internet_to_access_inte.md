---
title: "Can Squid allow users from Internet to access internal network through password?"
date: 2009-07-03
forum: Server Platforms
---

### Post by koukos on 2009-07-03
Can Squid allow users from Internet to access internal network through password? And if yes, how?

---

### Post by Boondoklife on 2009-07-03
It sounds like what you want is a VPN so people can connect to your network from the internet.

---

### Post by koukos on 2009-07-05
No. I have setup an [anonet.org]("http://www.anonet.org") vpn in my server, and i want to access the anonet cyberspace with squid from any computer with a web browser.

---

### Post by Boondoklife on 2009-07-05
> **koukos said:**
> No. I have setup an [anonet.org]("http://www.anonet.org") vpn in my server, and i want to access the anonet cyberspace with squid from any computer with a web browser.

Ok so let me see if I have this right.

Internet -> Your network -> anoNET

This what you are trying to do correct?

---

### Post by koukos on 2009-07-05
Yes. Is it possible?

---

### Post by Boondoklife on 2009-07-05
I dont think there is a way to do this with out a vpn setup, squid if i am correct is just a http proxy so it may be able to redriect to a webserver but as far as access to the entire network as if you were on it, I dont think so.

---

