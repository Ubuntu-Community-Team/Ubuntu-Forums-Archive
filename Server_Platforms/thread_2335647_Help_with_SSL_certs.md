---
title: "Help with SSL certs"
date: 2016-08-31
forum: Server Platforms
---

### Post by courtney2 on 2016-08-31
I think I screwed up pretty bad on this, not sure what to do and what the fix is. I had one instance of Ubuntu Server in a VM that was running a web page and I encrypted with Lets Encrypt. This was a new machine and VirtualBox freaked out and made my VM inaccessible before I could backup my certs. I decided to switch Ubuntu Server to a host installation and now my web server is in an LXD container. But now my problem is after retrieving a new cert from Let's Encrypt, my new server identity is no longer trusted and I'm not sure what I can do about it. Is there a fix or am I just hosed?

---

### Post by darkod on 2016-08-31
When you say you "encrypted a web page", what exactly do you mean? The SSL cert is usually only for the communication client-server. It doesn't actually encrypt the web page in the real meaning of the term.

On the other hand, did you encrypt the hdd content? That is a different story.

Any active ssl cert should work with your web page. Before ordering the new cert, did you create the CSR request on the new server and did you save the private key? That's the only thing you need to make your cert work.

---

### Post by courtney2 on 2016-09-01
Yeah sorry I typed that in a bit of a frenzy haha. I mean encrypting the connections with a secure SSL/TLS connection. Server-side encryption isn't in the scope of my question. I used the certbot tool that is provided by them. And after some research I am leaning towards this being a good Q for the Let's Encrypt forums. Just not sure if there's an apache thing I'm missing or if doing LXC containers could cause some cert issues? My problem has lead to an endless redirect Plus bad certs. An HTTP connection provides no problems

---

### Post by darkod on 2016-09-01
Unfortunately I have no idea how that works. All certs I have done so far included the standard creating of the CSR file and private key on the machine, then sending the CSR to a CA to create the cert, and then installing it on the machine.

For apache, you simply specify it in the site .conf file.

But since you are not doing it that way (if I understood correctly), I have no idea...

---

