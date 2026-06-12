---
title: "ubuntu server tinkering for edu"
date: 2012-09-15
forum: Security
---

### Post by broecher on 2012-09-15
Hi,

I just bought an old machine at a rummage sale to play with and I made it an ubuntu server (9.04 because 12.4 wont install) on my home network which also has machines that have our personal data on them. The other machines have things like our precious family photos and files that contain our passwords.

I have it now as just a local 'headless' samba server (with nothing on it).  I would like to be able to play with this ubuntu server machine trying things like ftp, ssh, email, website (things open to the internet).... all just for educational purposes for me, never serving anything important.

I don't know much about the things I want to try so there will be a lot of trial and error. My question is how do I make sure I don't accidentally expose my other machines on my network with the personal data? Or is this even a problem? Should I get another router or something like that to psychically separate the server from the other machines?

Just to be clear the server will not contain anything important, just other machines on the same home network.

Thanks so much!

So far, I have set ufw status: active
22, allow, anywhere

---

### Post by mr-woof on 2012-09-15
How is your network setup at the moment? Do you have a router and all machines behind that router?

---

### Post by broecher on 2012-09-15
yup, all on one router.

---

