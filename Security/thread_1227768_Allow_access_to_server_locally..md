---
title: "Allow access to server locally."
date: 2009-07-31
forum: Security
---

### Post by zxi on 2009-07-31
Hello,

I setup my Ubuntu home server today, and wanted to allow access to it locally only.
Say for example my work server, I need to hop on a vpn to access some webpages, I just want my home network to be able to access this server via SSH.

How would I do this?


Thank you in advance!

---

### Post by cariboo on 2009-07-31
If your sever isn't outward facing, and you don't expect to be accessing it externally, just install openssh-server, the have a look at bodhi's [ssh howto]("http://bodhizazen.net/Tutorials/ssh/").

---

