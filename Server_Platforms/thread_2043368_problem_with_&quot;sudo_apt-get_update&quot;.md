---
title: "problem with &quot;sudo apt-get update&quot;"
date: 2012-08-16
forum: Server Platforms
---

### Post by levinie001 on 2012-08-16
on ubuntu 12.04,problem below occured when running"sudo apt-get update":

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dis](http://us.archive.ubuntu.com/ubuntu/dis) ... slation-en Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.91.24). - connect (101: Network is unreachable) [IP: 91.189.91.24 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

how can i update the soure.list.And i'm the user in China,is this the reason?

---

### Post by albandy on 2012-08-16
> **levinie001 said:**
> on ubuntu 12.04,problem below occured when running"sudo apt-get update":

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dis](http://us.archive.ubuntu.com/ubuntu/dis) ... slation-en Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.91.24). - connect (101: Network is unreachable) [IP: 91.189.91.24 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

how can i update the soure.list.And i'm the user in China,is this the reason?

the ip 91.189.91.24 works, so maybe you're blocked.
Replace to local mirror.

You can change your software source in software-center edit menu.

---

### Post by HugoSerrano on 2012-08-16
Hello!

> connect (101: Network is unreachable) 

You got Internet in that machine? Can you ping google.com?

Regards!

---

