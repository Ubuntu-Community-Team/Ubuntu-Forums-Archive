---
title: "Postfix not playing nice ..."
date: 2009-07-24
forum: Server Platforms
---

### Post by GWBouge on 2009-07-24
I've had Apache/MySQL/PHP working for some time, but in a new project I decided to install Postfix to be able to send out registration e-mails.  I followed the following guide:

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

all the way through to testing.  Now somehow external requests aren't getting through ... 'localhost' and '127.0.0.1' in the address bar work fine, but anything outside of the local machine just hangs.  Everything seemed to work fine just after the initial install of Postfix (sudo aptitude install postfix), but after I went through the rest of the guide, it decided it didn't like it, heh.  Never received any errors throughout the guide, nor have I changed anything directly in the apache or my router config.

any ideas?

---

### Post by GWBouge on 2009-07-24
couple restarts later, and it works ... I'll take it  =oD

---

