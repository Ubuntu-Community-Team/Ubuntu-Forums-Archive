---
title: "exim4-heavy did not force login"
date: 2012-08-28
forum: Server Platforms
---

### Post by rohezal on 2012-08-28
Hi guys,

I was able to force ssl for an exim4 server. But I can send mails without login in. This is pretty bad :(. 

If I use auth information I get:

535 Incorrect authentication data

If I dont use authentification I can send as much spam as I like. This is a very bad situation. Where In the config can I force authentification before loging in?

Kind regards
rohezal 

Edit: Interesting if I mail to someone else without login I get: relay not permitted, only at my own mail (user@server can send to user@server nice).

---

### Post by rohezal on 2012-08-28
Ok it works now, had to remove the forcel tsl from the acl_ stuff (deny !tsl *) so it could get emails :)

---

