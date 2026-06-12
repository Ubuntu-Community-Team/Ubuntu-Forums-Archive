---
title: "Setup server with SSL"
date: 2009-05-11
forum: Server Platforms
---

### Post by Larry Anderson on 2009-05-11
I'm working on trying to set up a server with an SSL connection but am sure I don't have it right yet.

I have the FQDN (i.e. server2.example.com) set up pointing to my router (i.e. 123.45.6.7) and it goes to the server and communications works.

But am unsure how to set up the server so it knows it is "server2.example.com" so I can generate the CSR for the SSL certificate.

It sounds like I have to deal with etc/hosts, but the texts on configuring /etc/hosts seem kind of confusing, do I put in server2.example.com or mycomputer.server2.example.com?

Any assistance would be appreciated. :)

---

### Post by cdenley on 2009-05-11
When you create a CSR, you are prompted for the "Common Name". This should be your FQDN. The server doesn't need to know it is "server2.example.com", it will respond to any SSL requests on port 443 the server receives.

---

