---
title: "Hotspot Shield like software for Ubuntu?"
date: 2009-03-30
forum: Security
---

### Post by casbahdk on 2009-03-30
Has anyone come a cross a piece of software for Ubuntu laptops like Hotspot Shield?

[http://www.hotspotshield.com/]("http://www.hotspotshield.com/")

Cheers

---

### Post by cdenley on 2009-03-30
Ubuntu allows you to connect to VPN's, but a SSH server would probably be easier. The hard part is you need a server to connect to. You could run your own on your home computer. You could also use a free encrypted proxy service like tor, but this will give you really slow speeds and make you an easy target for a malicious person running their own server.

I feel solutions such as these give you a false sense of security. It is really easy for people to capture your traffic at hotspots, but you should always assume somebody is reading your traffic whenever you send anything over the internet. You don't know what path your traffic takes through the cloud, and who may manage to intercept your data. The best solution, in my opinion, is don't send any sensitive data through a website unless it is SSL encrypted (verified by a CA), and you trust the server you are sending it to. This goes for web surfing from any location.

---

### Post by casbahdk on 2009-03-30
I would also prefer not running a server on my laptop as I am trying to keep the system as low-resource-demanding as possible. I am getting interested in the subject mainly because of services like Last.fm, Spotify and Hulu that require IP addresses originating from specific geographical locations.

That does not mean that I take Internet security lightly. I appreciate your comments and will try to improve my skills in dealing with Internet security threats.

Cheers

---

### Post by cdenley on 2009-03-30
> **casbahdk said:**
> I would also prefer not running a server on my laptop as I am trying to keep the system as low-resource-demanding as possible.
The client would run on the laptop, not the server. There would have to be a server for your laptop to connect to, though, to create an encrypted tunnel. The server would have to be somewhere on another network. That is the type of service you referred to.

---

### Post by casbahdk on 2009-03-30
> **cdenley said:**
> The client would run on the laptop, not the server. There would have to be a server for your laptop to connect to, though, to create an encrypted tunnel. The server would have to be somewhere on another network. That is the type of service you referred to.

Ok, I see.

---

