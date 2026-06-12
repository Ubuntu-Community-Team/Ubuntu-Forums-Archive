---
title: "Setting a personal"
date: 2010-11-29
forum: Security
---

### Post by geo909 on 2010-11-29
Hello all,

I have an office at my university, where I could have a machine constantly turned on. I was wondering the following; would that be possible to have a computer there acting as a proxy to which I am going to connect from my home, so that people may see the university ip but not the ip at home? 

If so, could you please give me some directions, links, etc on how to start setting up something like this?

Thanks in advance

---

### Post by CharlesA on 2010-11-29
You can do that, yes, but I would suggest speaking with the IT guys first and getting their OK, since you'd basically be piggy-backing off their connection.

Is the whole idea to hide yer IP? If so, there are many proxy services out there, but in the end, your IP will be recorded somewhere.

---

### Post by HermanAB on 2010-11-29
Yes of course.  I would simply use SSH server, though you may have to run it on port 443.

---

### Post by geo909 on 2010-11-30
Thanks for your replies! I'll google around and try to figure out how to do that.

---

### Post by pricetech on 2010-11-30
Not sure why you would want to do that, but yes it can be done.  You'll need the assistance and consent of the university's IT department to do it though.

---

### Post by SeijiSensei on 2010-11-30
> **pricetech said:**
> Not sure why you would want to do that, but yes it can be done.  You'll need the assistance and consent of the university's IT department to do it though.

Access to journals is one likely reason.  Universities buy subscriptions with academic publishers for access to their journals online, but often you have to be connecting from one of the universities' IP addresses to be authenticated.

geo909:  If I were you, I'd consider using OpenVPN with the office computer as a server and a simple shared-key for encryption.  "sudo apt-get install openvpn" is all you need to install it.  For configuration, take a look at [this]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html").

---

### Post by DodgeV83 on 2010-11-30
I would use the "OpenVPN Access Server"

[http://openvpn.net/index.php/access-server/download-openvpn-as.html](http://openvpn.net/index.php/access-server/download-openvpn-as.html)

I literally had it setup within 1 minute of the download completing, It's free for up to two simultaneous users, which should be good enough for your needs.

---

