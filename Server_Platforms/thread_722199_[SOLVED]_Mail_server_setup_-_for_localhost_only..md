---
title: "[SOLVED] Mail server setup - for localhost only."
date: 2008-03-12
forum: Server Platforms
---

### Post by jay019 on 2008-03-12
Hi all,

Want I want to do is set up a mail server just for localhost.

I would like to send email from PHP and Java apps to say "me@localhost" via "smtp.localhost" and then use Thunderbird to connect to say "pop.localhost" to download them and check that they work properly.

What woud be the easiest way to make this happen?

Cheers. 
Jay

---

### Post by nirse on 2008-03-12
Have you tried [this]("https://help.ubuntu.com/community/PostfixBasicSetupHowto") Howto?
For me it worked like a charm.

Good luck,

NIrse

---

### Post by jay019 on 2008-03-12
Cheers.

Yeah, postfix is all I needed. 
I was suprised that it was so easy to setup for local only mail, was expecting it to be a nightmare.

---

