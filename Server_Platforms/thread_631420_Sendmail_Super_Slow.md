---
title: "Sendmail Super Slow"
date: 2007-12-04
forum: Server Platforms
---

### Post by mrhinman on 2007-12-04
Anyone else run into the problem of sendmail being excessively slow?  It takes sometimes 30 seconds to execute.  I've been unable to find anything on the subject here.

Dapper Drake 6.06 Server

---

### Post by MJN on 2007-12-04
I think most will be using Postfix so specific Sendmail knowledge may well be thin on the ground.

What aspect of the process is slow?

Mathew

---

### Post by mrhinman on 2007-12-04
> **MJN said:**
> I think most will be using Postfix so specific Sendmail knowledge may well be thin on the ground.

What aspect of the process is slow?

Mathew

Well, when I'm using PHP mail(), it takes a very long time to complete the script.

I fairly sure it requires sendmail to function.

---

### Post by demynted on 2007-12-04
I am experiencing the same problems on my CentOS 5 box. It happens when i send a mail from squirrel mail or send mail from a form or script. The email actually gets sent immediately (I know because i will send to myself at another email box and it comes in right away) however the page always hangs and the browser status bar moves slow. Even inside Webmin, the emails sent do the same thing...

~Demynted

[www.Dem360.com](www.Dem360.com)

---

### Post by elnur on 2007-12-13
I got the same problem. And OS startups very slowly because of sendmail.
Any idea? Mb smth in sendmail configuration?

---

### Post by jeangaud on 2007-12-21
I'm having the same issue... sendmail is slow to start

---

