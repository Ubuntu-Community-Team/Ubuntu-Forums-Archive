---
title: "Mail server that allows / in the address"
date: 2010-09-10
forum: Server Platforms
---

### Post by turbozmike on 2010-09-10
Help!
I dont know how to find this out other than building and testing.

I need to be able to do email/address@domain.com

---

### Post by clrg on 2010-09-10
You can't. An email address like foo/bar@meh.com is invalid. 

Please read the RFCs or have a look at [http://en.wikipedia.org/wiki/E-mail_address#Syntax](http://en.wikipedia.org/wiki/E-mail_address#Syntax)

---

### Post by turbozmike on 2010-09-10
It is in fact RFC standard, if you read the article you linked it even says as much except ! # $ % * / ? ^ ` { | } ~ are usually not used and will be dropped by most mail handlers.

Domino servers alow these characters and is the reason for this quesiton.

---

### Post by clrg on 2010-09-10
Nevertheless, you'll run into problems. A lot of email providers only allow dots, hyphens and underscores.

---

### Post by turbozmike on 2010-09-10
I agree with that 100%.  Poor way to setup the system.

---

