---
title: "no-ip and ubuntu server"
date: 2012-03-18
forum: Server Platforms
---

### Post by augustkk on 2012-03-18
New to this...

I've installed ubuntu server 10.04 and an app called subsonic.  I'd like to access this remotely.  I've created a donaim name with no-ip, but I'm unsure how to associate this to the app on my server.

can anyone help?

---

### Post by kevdog on 2012-03-18
I have no idea about subsonic, however I'm going to assume its like most processess where its listening on a specific port.  With noip and other dynamic dns providers you either need to install their update service or manually type in your WAN address via the web interface to ensure your dynamic IP address is associated with your WAN address.  If you are running this server at home, you then need to port forward from your router the specific port your service is listening to to your LAN address of the server.

---

### Post by Dangertux on 2012-03-18
No-ip claims that 8245 (or something like that) needs to be allow both in and outbound, however it actually only needs outbound access to update successfully update the DNS record.

Hope this helps.

---

### Post by augustkk on 2012-03-18
very new at this...

I guess what I was trying to ask was this... The domain name I created points to my router.  Now I want to forward that to my server, example 192.168.1.50, and then to a specific port.  Does one type that manually or is there a way of putting it under with the doname name?

Hope i'm not confusing anyone, I'm confused myself

---

### Post by bubylou on 2012-03-18
You need to port forward manually on your router.

---

### Post by rubylaser on 2012-03-19
The default port for Subsonic's web interface is 4040 unless you've changed the port via /etc/default/subsonic,  so that's what you'd need to port forward.  With my Subsonic server at home, I set up an OpenVPN connection and connect without needing to port forward any ports.  This is one less potential hole into my network from the outside.

---

### Post by augustkk on 2012-03-19
thanks guys i got it working!

---

### Post by augustkk on 2012-03-19
I'll look into openVPN too.

---

