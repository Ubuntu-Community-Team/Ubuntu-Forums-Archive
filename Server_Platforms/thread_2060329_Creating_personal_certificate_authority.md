---
title: "Creating personal certificate authority?"
date: 2012-09-19
forum: Server Platforms
---

### Post by cipherboy_loc on 2012-09-19
First of all, it has been a while since I last posted here, so feel free to move this to wherever you think it will get the most attention. That said.

I was thinking the other day of setting up a HTTPS server for a personal website of mine. I have done this multiple times, so it would be fairly easy to do. However, I have the problem of certificates. I do not want to invest in getting a new signed and trusted certificate every single time I want to create a new HTTPS server (more frequently than one would think as I cycle through projects often enough), so I create my own, self-signed certificate every time. However, when I first go to the website, I of course face certificate errors, because it is self signed. My question is thus: would it be possible to create a personal certificate authority, add the certificates to my browsers, and then sign my own personal certificates with those keys, such that, when I create a new HTTPS server config, I would not have to deal with the self signed certificate errors. Is this doable, or would it be fairly impractical and not worth the time?


Thanks,
Cipherboy

---

### Post by kennethconn on 2012-09-20
[https://help.ubuntu.com/12.04/serverguide/certificates-and-security.html](https://help.ubuntu.com/12.04/serverguide/certificates-and-security.html)

Fine for test purposes or in-house, but not recommended for most business cases.

---

### Post by cipherboy_loc on 2012-09-20
Okay, thanks. 


Marking as solved,
Cipherboy

---

